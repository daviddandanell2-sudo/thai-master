# Tracking Plan

## What We Track

The tracking system measures traffic, engagement, leads, and conversions across all page types.

## Traffic Metrics

### Page Visits
- Total page views by page
- Unique visitors by page
- New vs. returning visitors
- Traffic source (organic search, direct, referral, social)

### Organic Search Traffic
- Search queries that led to each page
- Average position for target keywords
- Click-through rate from search results
- Impressions by keyword

### Page Performance by Type
- Location page traffic
- Subject page traffic
- Curriculum page traffic
- Blog article traffic
- Home page traffic

## Engagement Metrics

### Time on Page
- Average time on page by page type
- Pages with high bounce rate
- Scroll depth (how far users read)

### Internal Link Clicks
- Which internal links are clicked most
- Which pages drive the most internal navigation
- Pages with low internal link engagement

## Lead Metrics

### WhatsApp Clicks
- Total WhatsApp clicks
- WhatsApp clicks by page
- WhatsApp click rate (clicks / page views)

### Form Submissions
- Total form submissions
- Form submissions by page
- Form submission rate
- Form abandonment rate

### Consultation Bookings
- Total consultation requests
- Consultation requests by page
- No-show rate for consultations

### Call Clicks
- Total call clicks (if phone number is clickable)
- Call clicks by page

## Conversion Metrics

### Lead to Tutor Match
- Number of inquiries that result in tutor matching
- Time from inquiry to first session
- Inquiry-to-match rate by page type

### Conversion Rate by Page Type
- Location page conversion rate
- Subject page conversion rate
- Curriculum page conversion rate
- Blog article conversion rate

### Lead Quality by Source
- Which pages produce the highest quality leads
- Which keywords produce the highest quality leads
- Which locations have the highest conversion value

## Content Performance Metrics

### Blog Performance
- Most-read blog articles
- Blog articles that drive the most service page visits
- Blog articles with highest conversion rates
- Blog topics that perform best

### Page Improvement Signals
- Pages with high traffic but low conversion
- Pages with low traffic but high conversion
- Pages with high bounce rates
- Pages with declining traffic

## Business Questions Answered

The tracking system must answer these questions:

1. **Which cities are creating leads?**
   - Track: Form submissions and WhatsApp clicks by location page
   - Report: Monthly lead volume by city

2. **Which subjects are creating leads?**
   - Track: Form submissions and WhatsApp clicks by subject page
   - Report: Monthly lead volume by subject

3. **Which curricula are creating leads?**
   - Track: Form submissions and WhatsApp clicks by curriculum page
   - Report: Monthly lead volume by curriculum

4. **Which blog articles support conversions?**
   - Track: Service page visits originating from blog articles
   - Track: Conversions from blog article traffic
   - Report: Blog ROI ranking

5. **Which pages need improvement?**
   - Track: High traffic + low conversion pages
   - Track: High bounce rate pages
   - Report: Priority improvement list

6. **Which pages should be expanded?**
   - Track: High conversion rate pages with low traffic
   - Track: Pages with growing organic traffic
   - Report: Expansion opportunity list

7. **Which pages should be removed or merged?**
   - Track: Low traffic + low conversion pages
   - Track: Pages with overlapping keywords
   - Report: Consolidation recommendations

## Report Structure

### Weekly Reports (`reports/analytics/`)
- Traffic summary
- Lead volume
- Conversion rate
- Top performing pages
- Pages needing attention

### Monthly Reports (`reports/seo-audits/`)
- Keyword ranking changes
- Organic traffic trends
- New keyword opportunities
- Technical SEO issues

### Quarterly Reports (`reports/content-audits/`)
- Content performance review
- Content gap analysis
- Blog topic performance
- Content improvement priorities

### Market Research Reports (`reports/market-research/`)
- Competitor activity
- Market trend observations
- New location/subject opportunities
- Parent feedback summary

## Tracking Implementation

### Required Tools
- Google Analytics 4 (traffic and behavior)
- Google Search Console (search performance)
- WhatsApp Business API or link tracking (WhatsApp clicks)
- Form tracking (form submissions)
- Call tracking (if using dedicated phone numbers)

### Event Tracking Setup
- `page_view` — automatic
- `whatsapp_click` — manual, on all WhatsApp buttons
- `form_submit` — manual, on contact form
- `consultation_book` — manual, on consultation request
- `internal_link_click` — manual, on contextual links
- `scroll_75` — manual, when user scrolls 75% of page

### Dashboard Priorities
1. Daily: Lead volume and source
2. Weekly: Traffic trends and top pages
3. Monthly: Conversion rates and keyword rankings
4. Quarterly: Content performance and market insights
