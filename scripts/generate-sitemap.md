# Generate Sitemap Workflow

## Purpose

Workflow for generating and maintaining the XML sitemap.

## When to Run

- After creating new pages
- Before publishing a batch
- Weekly as maintenance
- After removing or merging pages

## Workflow Steps

### Step 1: Scan Content Tree
Read all files in `/content/` and identify all pages.

### Step 2: Build URL List
For each page, create:
- Full URL
- Last modified date (from file modification time)
- Priority (based on page type)
- Change frequency

### Step 3: Assign Priorities

| Page Type | Priority | Change Frequency |
|---|---|---|
| Home | 1.0 | weekly |
| Location | 0.8 | monthly |
| Subject | 0.8 | monthly |
| Curriculum | 0.8 | monthly |
| Location+Subject | 0.6 | monthly |
| Blog | 0.6 | weekly |
| About | 0.5 | monthly |
| Contact | 0.5 | monthly |

### Step 4: Generate XML
Create XML sitemap following the standard format:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://example.com/</loc>
    <lastmod>2024-01-15</lastmod>
    <changefreq>weekly</changefreq>
    <priority>1.0</priority>
  </url>
</urlset>
```

### Step 5: Validate
- All URLs are absolute
- No duplicate URLs
- No broken URLs
- XML is well-formed

### Step 6: Save and Report
Save to `sitemap.xml` in the root or appropriate directory.

Create a report:

```markdown
# Sitemap Update Report

## Date
{YYYY-MM-DD}

## URLs Included
{Number}

## New URLs
- {URL}

## Removed URLs
- {URL}

## File Location
{path}
```

## Sitemap Index

If the site grows beyond 50,000 URLs, create a sitemap index:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<sitemapindex xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <sitemap>
    <loc>https://example.com/sitemap-pages.xml</loc>
  </sitemap>
  <sitemap>
    <loc>https://example.com/sitemap-blog.xml</loc>
  </sitemap>
</sitemapindex>
```

## Robots.txt

Ensure `robots.txt` references the sitemap:

```
Sitemap: https://example.com/sitemap.xml
```
