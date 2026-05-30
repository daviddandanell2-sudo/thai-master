# Hermes Control System

**Source:** Swarm audit `11-HERMES-CONTROL.md` — full specification for the Hermes AI orchestrator integration with Private Tutoring Thailand.

**Status:** Design complete. Implementation scheduled for Month 2 (Week 3-4). See `docs/6-MONTH-PLAN.md`.

---

## 1. External Service Credentials & Access

### 1.1 Google Search Console API

| Field | Specification |
|---|---|
| **Credential type** | OAuth 2.0 Client ID (Desktop App) or Service Account JSON |
| **Why Hermes needs it** | Pull search performance data (clicks, impressions, CTR, position) for all PTB URLs; run URL inspection to check indexing status; read index coverage reports |
| **How to obtain** | 1. Go to Google Cloud Console <br> 2. Create/select project `hermes-ptb` <br> 3. Enable **Search Console API** <br> 4. Go to APIs & Services > Credentials > Create Credentials > OAuth Client ID (Desktop app) <br> 5. Download `client_secret.json` <br> 6. Run OAuth consent flow once to get `refresh_token` <br> 7. Store both in `~/.hermes/secrets/gsc_credentials.json` |
| **Required scope** | `https://www.googleapis.com/auth/webmasters.readonly` |
| **What Hermes can do** | Query `searchanalytics/query` for clicks/impressions/position by URL/query/device/country. Call `urlInspection/indexes/inspect` for single-URL index status. List verified sites via `sites.list`. Read index coverage data. |
| **What must be hard-blocked** | ANY write operation to GSC (e.g., requesting indexing, modifying properties, removing URLs). GSC API is read-only in Hermes. |
| **Risk boundary** | Read-only. No state changes on Google's side. Safe for auto-execution. |

```json
// ~/.hermes/secrets/gsc_credentials.json
{
  "client_id": "xxx.apps.googleusercontent.com",
  "client_secret": "xxx",
  "refresh_token": "xxx",
  "scope": "https://www.googleapis.com/auth/webmasters.readonly",
  "token_uri": "https://oauth2.googleapis.com/token"
}
```

### 1.2 Google Analytics 4 Data API

| Field | Specification |
|---|---|
| **Credential type** | Service Account JSON key (recommended) or OAuth 2.0 |
| **Why Hermes needs it** | Pull session data, page views, events (WhatsApp clicks, form submissions), user demographics, traffic sources for PTB property |
| **How to obtain** | 1. In Google Cloud Console, enable **Google Analytics Data API** <br> 2. Create Service Account: IAM & Admin > Service Accounts > Create <br> 3. Grant "Viewer" role on the GA4 property: GA4 Admin > Property Access Management > Add the service account email with Viewer role <br> 4. Download JSON key <br> 5. Store at `~/.hermes/secrets/ga4_service_account.json` |
| **Required scope** | `https://www.googleapis.com/auth/analytics.readonly` |
| **Property ID** | GA4 property ID for privatetutoringthailand.com (format: `GA4_MEASUREMENT_ID` + `GA4_PROPERTY_ID` numeric) |
| **What Hermes can do** | Run `runReport` and `runRealtimeReport` queries. Extract: sessions by page, event counts (WhatsApp click = `whatsapp_click`, form submit = `form_submit`), user acquisition by channel, engagement rate. Filter by page path, date range. |
| **What must be hard-blocked** | Creating/modifying GA4 properties, data streams, audiences, conversion events, or custom definitions. No write access. |
| **Risk boundary** | Read-only analytics data. No configuration changes. Safe for auto-execution. |

```json
// ~/.hermes/secrets/ga4_service_account.json
{
  "type": "service_account",
  "project_id": "hermes-ptb",
  "private_key_id": "xxx",
  "private_key": "-----BEGIN PRIVATE KEY-----\nxxx\n-----END PRIVATE KEY-----\n",
  "client_email": "hermes-ga4@hermes-ptb.iam.gserviceaccount.com",
  "client_id": "xxx",
  "auth_uri": "https://accounts.google.com/o/oauth2/auth",
  "token_uri": "https://oauth2.googleapis.com/token"
}
```

### 1.3 Google Indexing API

| Field | Specification |
|---|---|
| **Credential type** | Service Account JSON key (separate from GA4 — dedicated account recommended) |
| **Why Hermes needs it** | Programmatically notify Google when new pages are published or existing pages are updated, so they get crawled and indexed faster |
| **How to obtain** | 1. Create a dedicated Service Account in Google Cloud Console <br> 2. Enable **Indexing API** in Google Cloud Console <br> 3. In Google Search Console, add the service account email as an Owner of the property (required for Indexing API) <br> 4. Download JSON key <br> 5. Store at `~/.hermes/secrets/indexing_service_account.json` |
| **Required scope** | `https://www.googleapis.com/auth/indexing` |
| **What Hermes can do** | Send `urlNotifications.publish` with type `URL_UPDATED` or `URL_DELETED`. This is a **notification-only** API — it tells Google "this URL changed, please crawl it." It does NOT guarantee indexing or manipulate rankings. |
| **What must be hard-blocked** | Sending notifications for URLs not owned by PTB. Bulk-spamming notifications (rate limit: 200 req/day per property). Using `URL_DELETED` type (reserved for actual content removal). Sending notifications for non-existent or 404 URLs. |
| **Risk boundary** | Notification-only. Cannot directly modify index. Abuse triggers rate limiting or API revocation. **Approval required** before each batch notification. Hermes queues the request, David approves the URL list, then Hermes sends. |

### 1.4 Vercel API

| Field | Specification |
|---|---|
| **Credential type** | Vercel Access Token (personal, scoped to team/project) |
| **Why Hermes needs it** | Check deployment status and build logs, list deployed URLs, verify domain health (SSL, DNS), trigger production deploys |
| **How to obtain** | 1. Go to Vercel Dashboard <br> 2. Settings > Tokens > Create Token <br> 3. Name: `hermes-ptb-readonly` (for read) or `hermes-ptb-deploy` (for deploy) <br> 4. Scope: Restrict to PTB project only <br> 5. Copy token <br> 6. Store at `~/.hermes/secrets/vercel_token.txt` |
| **Required scope** | Read: `project` (read deployments, builds, domains). Deploy: `project` + `deployment` (create deployments). |
| **What Hermes can do** | GET `/v6/deployments` — list recent deployments, filter by project. GET `/v13/deployments/{id}` — deployment detail. GET `/v2/deployments/{id}/builds` — build logs. GET `/v9/projects/{id}/domains` — domain status. POST `/v13/deployments` — trigger new deployment (approval-gated). |
| **What must be hard-blocked** | Deleting projects, removing domains, modifying environment variables, accessing other projects. Token must be scoped to PTB project only. |
| **Risk boundary** | Read ops are safe for auto-execution. Deploy trigger requires approval. Token scoped to single project limits blast radius. |

### 1.5 GitHub API

| Field | Specification |
|---|---|
| **Credential type** | Personal Access Token (classic) or Fine-Grained PAT |
| **Why Hermes needs it** | Read repo file tree, check TRACKING.md state, read last N commits and changed files, trigger Actions workflows via `workflow_dispatch`, check CI status |
| **How to obtain** | 1. Go to GitHub Settings > Developer Settings > Personal Access Tokens > Fine-grained tokens <br> 2. Generate new token <br> 3. Resource owner: David's account <br> 4. Repository access: Select both content-control-repo and website-repo <br> 5. Permissions: Contents: Read, Actions: Read and Write, Metadata: Read, Pull Requests: Read <br> 6. Store at `~/.hermes/secrets/github_token.txt` |
| **Required scope** | Fine-grained: `contents:read`, `actions:read`, `actions:write`, `metadata:read`, `pull_requests:read` |
| **What Hermes can do** | GET file tree, commits, file contents (TRACKING.md). POST workflow dispatch. GET CI status. |
| **What must be hard-blocked** | Pushing commits directly, creating/deleting files via API, force-pushing, modifying branch protection, managing webhooks, inviting collaborators. No direct repo writes. All writes go through GitHub Actions workflows triggered by `workflow_dispatch`. |
| **Risk boundary** | Actions-based workflow triggers are the only write path. Direct file modification is BLOCKED. Even workflow triggers require approval. |

### 1.6 Claude CLI (via MCP / CLI Tool)

| Field | Specification |
|---|---|
| **Credential type** | Claude API key (`ANTHROPIC_API_KEY` env var) + Claude CLI session |
| **Why Hermes needs it** | Spawn Claude Code/CLI as a subprocess with specific prompt files and repo paths to execute agent tasks (content generation, SEO analysis, code review). Capture structured JSON output from agent runs. |
| **How to obtain** | 1. Install Claude CLI <br> 2. Get API key from Anthropic Console > API Keys <br> 3. Export `ANTHROPIC_API_KEY=sk-ant-xxx` in `~/.hermes/.env` <br> 4. Verify: `claude --version` |
| **What Hermes can do** | Spawn `claude` subprocess with: `--prompt-file <path>`, `--cwd <repo>`, `--output-format json`, max token limits, allowed tools list. Capture stdout/stderr as structured output. Log full command + output. Kill process if exceeds timeout (5 min default). |
| **What must be hard-blocked** | Running without prompt file validation (must be from approved list). Allowing filesystem writes outside repo boundaries. Running with `--dangerously-skip-permissions`. Unlimited token budgets. Network access to non-essential domains. |
| **Risk boundary** | Agent runs are sandboxed: read-only on repo (via git worktree), writes only to designated output directory, network access blocked via firewall rules, max execution time enforced. Output is captured, not applied, until David approves. |

### 1.7 BFL.ai API (Programmatic Image Generation)

| Field | Specification |
|---|---|
| **Credential type** | BFL API Key (obtain from api.us1.bfl.ai or BFL developer portal) |
| **Why Hermes needs it** | Generate hero images, blog post illustrations, social media graphics for PTB content programmatically |
| **How to obtain** | 1. Create account at BFL Developer Portal <br> 2. Generate API key from dashboard <br> 3. Store at `~/.hermes/secrets/bfl_api_key.txt` |
| **What Hermes can do** | POST image generation requests with prompt, aspect ratio, seed. Poll for result. Download generated image to `assets/generated/`. Log generation parameters and cost. |
| **What must be hard-blocked** | Any request exceeding credit limit. NSFW/adult content generation (PTB is a family-friendly education brand). Batch generation above daily budget (cap at 10 images/day). |
| **Risk boundary** | Each generation costs API credits. Approval required for every request. Prompts must pass a content policy filter (education/family-safe keywords only). Max 10 images/day hard cap. |

### 1.8 Credential Storage & Security Summary

All credentials stored in `~/.hermes/secrets/` with permissions `600` (owner read/write only):

```
~/.hermes/
├── .env                          # Environment variables (ANTHROPIC_API_KEY)
├── secrets/
│   ├── gsc_credentials.json      # GSC OAuth credentials
│   ├── ga4_service_account.json  # GA4 service account key
│   ├── indexing_service_account.json  # Indexing API service account
│   ├── vercel_token.txt          # Vercel access token
│   ├── github_token.txt          # GitHub fine-grained PAT
│   └── bfl_api_key.txt           # BFL API key
```

**Security rules:**
- All secret files: chmod 600
- No secrets committed to any repo (`.gitignore` enforces)
- Hermes loads secrets at startup, never logs them
- Secrets rotated every 90 days (Hermes logs rotation due dates)
- `.env` file sourced only by Hermes process, never by shell

---

## 2. Automated Reports Specification

### 2.1 Daily Rank Snapshot

| Field | Specification |
|---|---|
| **Report name** | `daily-rank-snapshot` |
| **File path** | `exports/reports/YYYY-MM-DD-rank-snapshot.json` |
| **Trigger** | Cron: `0 6 * * *` (daily 06:00 Bangkok time) |
| **Data sources** | GSC `searchanalytics/query` API — last 28 days |
| **What it checks** | Top 30 keywords by clicks. Position vs. previous day (delta). New keywords entering top 30. Keywords dropping out of top 30. |
| **Output format** | JSON array of 30 objects: `{ keyword, clicks, impressions, ctr, position, position_delta, page }` |
| **Alert threshold** | Any keyword with `position_delta >= 3` (dropped 3+ positions) triggers SEO drift alert |
| **Queued action** | If drift detected > queue alert in dashboard + add to `alert_feed`. If drift > 5 positions, flag for immediate review. |

### 2.2 Weekly Organic Report

| Field | Specification |
|---|---|
| **Report name** | `weekly-organic-report` |
| **File path** | `exports/reports/YYYY-MM-DD-weekly-organic.json` |
| **Trigger** | Cron: `0 7 * * 1` (Monday 07:00 Bangkok time) |
| **Data sources** | GSC `searchanalytics/query` (7 days), GA4 `runReport` (7 days sessions) |
| **What it checks** | Total organic sessions. Total clicks from GSC. Total impressions. Average CTR. Average position. Breakdown by page type. Week-over-week change %. |
| **Alert threshold** | Sessions drop > 20% week-over-week. Clicks drop > 15%. |
| **Queued action** | If threshold breached > create alert card in dashboard + add to weekly summary email queue. |

### 2.3 Weekly Lead Report

| Field | Specification |
|---|---|
| **Report name** | `weekly-lead-report` |
| **File path** | `exports/reports/YYYY-MM-DD-weekly-leads.json` |
| **Trigger** | Cron: `0 7 * * 1` (Monday 07:00 Bangkok time, runs after organic report) |
| **Data sources** | GA4 `runReport` — events filtered by `event_name IN ('whatsapp_click', 'form_submit', 'phone_click')` |
| **What it checks** | Total WhatsApp button clicks. Total form submissions. Total phone number clicks. Conversion rate (leads / sessions). By page. Week-over-week change. |
| **Alert threshold** | Conversion rate drops below 2%. Zero leads in a 7-day period. |
| **Queued action** | If zero leads > flag "LEAD DROUGHT" alert. If conversion rate < 2% > queue content quality scan on top 10 landing pages. |

### 2.4 Post-Deploy Validation

| Field | Specification |
|---|---|
| **Report name** | `post-deploy-validation` |
| **File path** | `exports/reports/YYYY-MM-DD-deploy-validation.json` |
| **Trigger** | Event: Vercel deployment `succeeded` webhook (or polled every 5 min after deploy trigger) |
| **What it checks** | 1. All key URLs return HTTP 200 <br> 2. `sitemap.xml` exists and is valid XML <br> 3. All sitemap URLs are accessible (200) <br> 4. No build errors in Vercel logs <br> 5. Core Web Vitals check <br> 6. robots.txt exists and allows Googlebot <br> 7. No broken internal links (spider top 20 pages) |
| **Alert threshold** | Any check = `fail` > immediate alert. 3+ `warn` > alert. |
| **Queued action** | If any check fails > halt pipeline, create alert, notify David. |

### 2.5 Content Quality Scan

| Field | Specification |
|---|---|
| **Report name** | `content-quality-scan` |
| **File path** | `exports/reports/YYYY-MM-DD-content-quality.json` |
| **Trigger** | Cron: `0 8 * * 3` (Wednesday 08:00). Also triggered by lead report threshold breach. |
| **What it checks** | For each content page: word count (target: 800+ words). CTA presence. Internal links count (target: 3+ per page). Meta title and description present. H1 present and unique. Image alt tags. No placeholder text ("Lorem ipsum", "TODO", "TBD"). |
| **Alert threshold** | Any page with < 300 words. Any page without CTA. Any page with placeholder text. |
| **Queued action** | If issues found > create content fix tasks in alert feed. If > 5 pages have issues > queue Claude agent for content review. |

### 2.6 SEO Drift Alert

| Field | Specification |
|---|---|
| **Report name** | `seo-drift-alert` |
| **File path** | `exports/alerts/YYYY-MM-DD-seo-drift.json` |
| **Trigger** | Threshold: Daily rank snapshot detects 3+ position drop week-over-week for any keyword |
| **Output format** | JSON array: `[{ keyword, previous_position, current_position, drop, affected_page, severity: 'warn'|'critical' }]` |
| **Alert threshold** | Drop 3-4 positions = `warn`. Drop 5+ = `critical`. |
| **Queued action** | `warn` > add to alert feed, flag for weekly review. `critical` > immediate dashboard alert + queue Claude agent for SEO analysis on affected page. |

### 2.7 Index Coverage Alert

| Field | Specification |
|---|---|
| **Report name** | `index-coverage-alert` |
| **File path** | `exports/alerts/YYYY-MM-DD-index-coverage.json` |
| **Trigger** | Cron: `0 */4 * * *` (every 4 hours). Also post-deploy. |
| **What it checks** | Compare current index status vs last check for all tracked URLs. Flag any URL that changed from `Indexed` to `Not indexed`, `Crawled - currently not indexed`, or `Discovered - currently not indexed`. |
| **Alert threshold** | Any URL going from Indexed → Not indexed = immediate alert. 3+ URLs = critical. |
| **Queued action** | Single URL de-indexed > add to alert feed. 3+ URLs > immediate alert + queue Indexing API notification (approval-gated) + queue content quality scan. |

### 2.8 Report Generation Pipeline

```
Cron triggers → Handler reads APIs → Data transformed → 
JSON written to exports/reports/ or exports/alerts/ → 
Dashboard reads JSON → Alert feed updated → 
If threshold breached → Alert created + queued action
```

All reports append to `exports/reports/index.json` (manifest of all generated reports with timestamps and file paths).

---

## 3. Permission Matrix

### 3.1 Full Permission Matrix

| # | Action | Category | Permission Level | Condition/Schedule |
|---|---|---|---|---|
| 1 | Pull GSC search analytics | Read | Auto-approved | Daily 06:00 |
| 2 | Pull GSC URL inspection | Read | Auto-approved | Every 4 hours |
| 3 | Pull GA4 session data | Read | Auto-approved | Daily 06:00 |
| 4 | Pull GA4 event data | Read | Auto-approved | Daily 06:00 |
| 5 | Read GitHub file tree | Read | Auto-approved | On trigger |
| 6 | Read GitHub commits | Read | Auto-approved | On trigger |
| 7 | Read TRACKING.md | Read | Auto-approved | On trigger |
| 8 | Check GitHub CI status | Read | Auto-approved | Post-deploy |
| 9 | Read Vercel deployments | Read | Auto-approved | Every 5 min |
| 10 | Read Vercel build logs | Read | Auto-approved | Post-deploy |
| 11 | Check Vercel domain health | Read | Auto-approved | Daily 06:00 |
| 12 | Verify URLs (HTTP 200 check) | Read | Auto-approved | Post-deploy |
| 13 | Generate rank snapshot report | Write (local) | Auto-approved | Daily 06:00 |
| 14 | Generate organic report | Write (local) | Auto-approved | Weekly Mon 07:00 |
| 15 | Generate lead report | Write (local) | Auto-approved | Weekly Mon 07:00 |
| 16 | Generate deploy validation | Write (local) | Auto-approved | Post-deploy event |
| 17 | Generate content quality scan | Write (local) | Auto-approved | Weekly Wed 08:00 |
| 18 | Write alert JSON | Write (local) | Auto-approved | On threshold |
| 19 | Flag SEO drift alert | Alert | Auto-approved | On threshold (3+ pos drop) |
| 20 | Flag index coverage alert | Alert | Auto-approved | On threshold (de-indexed URL) |
| 21 | Flag lead drought alert | Alert | Auto-approved | On threshold (0 leads/7d) |
| 22 | Flag traffic drop alert | Alert | Auto-approved | On threshold (-20% sessions) |
| 23 | Queue page build task | Write | Approval required | David reviews |
| 24 | Trigger GitHub Actions workflow | Write | Approval required | David reviews |
| 25 | Trigger Vercel deploy | Deploy | Approval required | David reviews |
| 26 | Run Claude agent | Execute | Approval required | David reviews |
| 27 | Generate image via BFL.ai | Execute | Approval required | David reviews |
| 28 | Send Indexing API notification | Write | Approval required | David reviews |
| 29 | Modify content files directly | Write | **BLOCKED** | Never |
| 30 | Delete any files | Delete | **BLOCKED** | Never |
| 31 | Modify CLAUDE.md or AGENTS.md | Write | **BLOCKED** | Never |
| 32 | Modify docs/EXECUTION-LOOP.md | Write | **BLOCKED** | Never |
| 33 | Push commits directly to GitHub | Write | **BLOCKED** | Never |
| 34 | Force-push or rewrite history | Write | **BLOCKED** | Never |
| 35 | Create/delete GitHub branches | Write | **BLOCKED** | Never |
| 36 | Modify environment variables | Write | **BLOCKED** | Never |
| 37 | Access non-PTB repos | Read | **BLOCKED** | Never |
| 38 | Run shell commands outside repo | Execute | **BLOCKED** | Never |
| 39 | Send network requests outside APIs | Execute | **BLOCKED** | Never |
| 40 | Exceed BFL daily quota | Execute | **BLOCKED** | Never |

### 3.2 Approval Flow

```
Action requested → Permission engine evaluates →
  AUTO: Execute immediately, log action
  APPROVAL_REQUIRED: Add to action queue panel →
    David clicks "Approve" or "Deny" →
      Approve: Execute, log action
      Deny: Log denial, do not execute
  BLOCKED: Log blocked attempt, return error
```

### 3.3 Default Deny Rule

Any action NOT in the permission matrix is **BLOCKED by default**. No exceptions.

---

## 4. Machine-Executable Execution Loop

### 4.1 Hermes-Controlled Execution Loop

| Step | Action | Who | Output | Triggers Next |
|---|---|---|---|---|
| 1 | Pull latest content & tracking state | Hermes auto | Parsed task list, recent change summary | Step 2 |
| 2 | Run daily data pull (GSC + GA4) | Hermes auto | Rank snapshot + traffic data JSON | Step 3 |
| 3 | Generate reports (rank, organic, leads) | Hermes auto | 3 JSON report files | Step 4 |
| 4 | Evaluate thresholds & alerts | Hermes auto | Alert JSON if thresholds breached | Step 5 (if alerts) or Step 6 |
| 5 | Surface alerts in dashboard | Hermes auto | Alert cards visible in UI | Step 6 |
| 6 | Check if build/deploy needed | Hermes auto | Build decision (yes/no) | Step 7 (if yes) or Step 9 |
| 7 | Prepare build payload | Hermes auto | Build payload: `{ files, commit_sha, target_branch }` | Step 8 |
| 8 | Request deploy approval | Hermes + approval | Approval request in dashboard | Step 9 (on approval) |
| 9 | Trigger GitHub Actions workflow | Hermes (approved) | Workflow run ID, queued status | Step 10 |
| 10 | Monitor build progress | Hermes auto | Build status: in_progress → success/failure | Step 11 (on success) or Step 12 (on failure) |
| 11 | Post-deploy validation | Hermes auto | Deploy validation JSON (pass/fail per check) | Step 13 |
| 12 | Handle build failure | Hermes auto | Failure report with error details | Alert feed + human review |
| 13 | Index notification (post-deploy) | Hermes + approval | Notification sent for approved URLs | Loop complete |

### 4.2 Execution Loop State Machine

```
[INIT] → Pull State → Generate Reports → Evaluate Alerts → 
  ├─ Alerts? → Surface Alerts ─┐
  └─ No alerts ────────────────┘
         ↓
  Check Build Needed? ──No──→ [WAIT_FOR_CRON] → (back to INIT)
         ↓ Yes
  Prepare Payload → Request Approval → 
    ├─ Denied → Log → [WAIT_FOR_CRON]
    └─ Approved → Trigger Build → Monitor → 
        ├─ Fail → Alert → Human Review → [WAIT_FOR_HUMAN]
        └─ Success → Validate Deploy → 
            ├─ Fail → Alert → Human Review
            └─ Pass → Request Index Notify → 
                ├─ Denied → [WAIT_FOR_CRON]
                └─ Approved → Send → [WAIT_FOR_CRON]
```

### 4.3 Loop Timing

| Phase | Trigger | Max Duration |
|---|---|---|
| Data pull + reports | Cron (06:00 daily) | 5 minutes |
| Threshold evaluation | After reports | 30 seconds |
| Build + deploy (approval-gated) | On task status change | Human-dependent approval + 5 min build |
| Post-deploy validation | Deploy success webhook | 3 minutes |
| Index notification | Post-validation approval | 1 minute |
| Alert surfacing | Real-time | Immediate |

---

## 5. PTB Control Panel Dashboard Design

### 5.1 Dashboard Layout

The PTB section is an additional panel in the existing Hermes dashboard.

```
+-------------------------------------------------------------+
|  HERMES AI ORCHESTRATOR          [PTB Panel] [Settings]    |
+-------------------------------------------------------------+
|  5 METRIC CARDS (top row)                                   |
|  +--------+ +--------+ +--------+ +--------+ +--------+    |
|  | Organic| |  Leads | | Deploy | |  Index | |  Agents|    |
|  |Sessions| |  /7d   | | Status | |Coverage| |  Active|    |
|  | 1,247  | |   23   | |   ✅   | |  94%   | |   0/7  |    |
|  | ↑ 12%  | | ↑ 15%  | | Ready  | |  47/50 | |  Idle  |    |
|  +--------+ +--------+ +--------+ +--------+ +--------+    |
|  ALERT FEED (left, 40%)           ACTION QUEUE (right, 60%)|
|  +------------------------+       +----------------------+ |
|  | 🔴 SEO Drift: "math    |       | ⏳ Pending Approvals  | |
|  |    tutor bangkok" -3   |       | [Deploy] Trigger     | |
|  |    positions (2h ago)  |       | production deploy    | |
|  |                        |       | [Approve] [Deny]     | |
|  | 🟡 Index: 1 URL de-    |       |                      | |
|  |    indexed (4h ago)    |       | [Agent] Run SEO      | |
|  |                        |       | analysis on /math-   | |
|  | 🟢 Deploy: Successful  |       | tutor-bangkok        | |
|  |    (2024-01-15 08:30)  |       | [Approve] [Deny]     | |
|  +------------------------+       +----------------------+ |
|  AGENT RUN LOG (full width, bottom)                         |
|  +--------------------------------------------------------+ |
|  | Time     | Agent      | Action          | Status | Out  | |
|  +--------------------------------------------------------+ |
|  ONE-CLICK DEPLOY (bottom right)                            |
|  [🚀 Deploy Production]          Last deploy: 2024-01-15    |
+-------------------------------------------------------------+
```

### 5.2 Metric Cards Specification

| # | Card Title | Metric | Data Source | Alert State |
|---|---|---|---|---|
| 1 | Organic Sessions | 7-day organic sessions from GA4 | `ga4.ts` | Yellow if -10%, Red if -20% |
| 2 | Leads (7d) | WhatsApp clicks + form submits from GA4 | `ga4.ts` | Yellow if < 10, Red if 0 |
| 3 | Deploy Status | Latest Vercel deployment state | `vercel.ts` | Red if last deploy failed |
| 4 | Index Coverage | Indexed / Total tracked URLs | `gsc.ts` | Yellow if < 90%, Red if de-indexed |
| 5 | Active Agents | Currently running / total worker agents | Claude process monitor | Yellow if agent failed |

### 5.3 Alert Feed Specification

- **Position:** Left column, 40% width, scrollable
- **Max items:** 50 alerts, auto-purge after 7 days
- **Sort:** Newest first
- **Severity levels:** 🔴 Critical, 🟡 Warning, 🟢 Info, ⚪ Normal
- **Auto-refresh:** Every 60 seconds

### 5.4 Action Queue Panel Specification

- **Position:** Right column, 60% width
- **Shows:** Only `APPROVAL_REQUIRED` actions pending David's review
- **Each item displays:** Action name, requested timestamp, affected resources, [Approve] and [Deny] buttons
- **Auto-refresh:** Every 10 seconds
- **Max age:** Actions auto-expire after 24 hours (marked "Expired")

### 5.5 One-Click Deploy Button

- **States:** Ready (green), Pending (yellow), Blocked (red), Deploying (blue spinner)
- **Click behavior:** If blocked → Show reason. If ready → Add deploy action to queue (still requires approval).

---

## 6. Build Priority Order

### 6.1 Priority Rankings

| Priority | Build Task | Effort | Value Unlocked | Dependencies |
|---|---|---|---|---|
| **P0** | GSC handler — read-only analytics + URL inspection | 4h | All SEO data: rank tracking, index monitoring, CTR analysis | GSC API credentials |
| **P0** | GA4 handler — read-only session/event data | 4h | All traffic and lead data: sessions, conversions, WhatsApp clicks | GA4 service account |
| **P1** | Report generators (7 report types) | 6h | Automated daily/weekly reporting | GSC + GA4 handlers |
| **P1** | Permission broker — interactive approval UI | 4h | Safe execution of write/deploy actions | Dashboard UI |
| **P2** | GitHub handler — read commits, TRACKING.md, trigger workflows | 3h | Repo visibility, CI monitoring, workflow dispatch | GitHub PAT |
| **P2** | Vercel handler — deployments, build logs, domain health | 3h | Deploy monitoring, post-deploy validation | Vercel token |
| **P2** | Alert engine — threshold detection + alert feed | 3h | Proactive notifications for SEO drift, index issues, traffic drops | Report generators |
| **P3** | Claude handler — spawn agents, capture output | 5h | Run AI agents for content review, SEO analysis, keyword research | Claude CLI + API key |
| **P3** | Post-deploy validation pipeline | 2h | Automated HTTP checks, sitemap validation, CWV verification | Vercel handler |
| **P4** | BFL handler — image generation | 2h | Programmatic image generation for content | BFL API key |
| **P4** | Content quality scan agent | 2h | Automated word count, CTA, meta, link checking | Claude handler |
| **P5** | Real-time dashboard WebSocket updates | 3h | Live updates instead of polling | All handlers |
| **P5** | Indexing API handler — notification only | 2h | Notify Google of new/updated pages | Indexing API credentials |

### 6.2 Build Sequence by Week

| Week | Focus | Tasks | Cumulative Value |
|---|---|---|---|
| **Week 1** | Data foundation | GSC handler + GA4 handler + Report generators (7 types) | Daily/weekly automated reports. SEO monitoring active. |
| **Week 2** | Control layer | Permission broker + GitHub handler + Vercel handler + Alert engine | Full execution loop readable. Approval system live. Deploy monitoring. |
| **Week 3** | Agent integration | Claude handler + Content quality scan + Post-deploy validation | AI agents runnable via dashboard. Content quality automated. |
| **Week 4** | Polish & extend | BFL handler + Indexing API + Real-time updates + Batch ops | Image generation. Index notifications. Premium dashboard UX. |

### 6.3 Critical Path

```
GSC Handler (P0) ──┐
                   ├──→ Report Generators (P1) ──→ Alert Engine (P2) ──→ Dashboard
GA4 Handler (P0) ──┘                                          ↑
GitHub Handler (P2) ──→ Workflow trigger ──────────────────────┘
Vercel Handler (P2) ──→ Deploy validation ─────────────────────┘
Claude Handler (P3) ──→ Content quality ───────────────────────┘
```

---

## 7. Environment Variables

```bash
# ~/.hermes/.env
ANTHROPIC_API_KEY=sk-ant-api03-...
HUB_GSC_CREDENTIALS_PATH=~/.hermes/secrets/gsc_credentials.json
HUB_GA4_CREDENTIALS_PATH=~/.hermes/secrets/ga4_service_account.json
HUB_GA4_PROPERTY_ID=123456789
HUB_GITHUB_TOKEN_PATH=~/.hermes/secrets/github_token.txt
HUB_GITHUB_OWNER=davidwabnitz
HUB_GITHUB_CONTENT_REPO=ptb-content-control
HUB_GITHUB_WEBSITE_REPO=ptb-website
HUB_VERCEL_TOKEN_PATH=~/.hermes/secrets/vercel_token.txt
HUB_VERCEL_PROJECT_ID=prj_...
HUB_BFL_API_KEY_PATH=~/.hermes/secrets/bfl_api_key.txt
HUB_SITE_DOMAIN=privatetutoringthailand.com
HUB_DASHBOARD_PORT=3000
HUB_LOG_LEVEL=info
HUB_READONLY_MODE=true
```
