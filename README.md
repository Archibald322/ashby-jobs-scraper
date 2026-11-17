# Ashby ATS Tech & AI Jobs Scraper

[![Apify Actor](https://img.shields.io/badge/Apify-Actor%20Store-orange?logo=apify)](https://apify.com/moneygain/ashby-jobs-scraper)
[![Python Version](https://img.shields.io/badge/Python-3.10%20%7C%203.11%20%7C%203.12-blue?logo=python)](https://github.com/Archibald322/ashby-jobs-scraper)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> **Live Apify Store Actor:** [https://apify.com/moneygain/ashby-jobs-scraper](https://apify.com/moneygain/ashby-jobs-scraper)

This repository provides an open-source Python runner and documentation for **[Ashby ATS Tech & AI Jobs Scraper](https://apify.com/moneygain/ashby-jobs-scraper)**.

---

## ⚡ Quickstart

### Option 1: Run in Cloud (No Code)
Launch directly from your browser via the Apify Store console:
👉 **[Open Ashby ATS Tech & AI Jobs Scraper on Apify Store](https://apify.com/moneygain/ashby-jobs-scraper)**

### Option 2: Run via Python SDK
```bash
git clone https://github.com/Archibald322/ashby-jobs-scraper.git
cd ashby-jobs-scraper
pip install -r requirements.txt
export APIFY_TOKEN="your_apify_token_here"
python run.py
```

---

# ⚡ Ashby ATS Tech Jobs & Career Feeds Scraper

**Scrape Ashby ATS tech jobs data to JSON, CSV, or Excel in seconds without browser overhead.** Extract real-time engineering vacancies, salary brackets, equity offerings, department structures, workplace flexibility (Remote/Hybrid/Onsite), and direct candidate application links from **AshbyHQ.com** — the premier next-generation Applicant Tracking System (ATS) used by top tech companies like OpenAI, Linear, Ramp, Supabase, Replit, and Vercel.

Designed for AI recruiting platforms, HR tech startups, outbound talent headhunters, executive search firms, and autonomous AI agents. Built with ultra-lightweight direct ATS API requests, **zero browser overhead**, and **100% Pay-Per-Event (PPE) pricing** — you only pay for verified job postings delivered.

---

## ⚡ Speed & Value Comparison

| Feature | Our Lightweight Ashby ATS Scraper | Heavy Browser Scrapers (Playwright / Puppeteer) |
|---|---|---|
| **Memory Consumption** | **128 MB – 256 MB** | 2 GB – 4 GB |
| **Startup Fee** | **$0.00 (Zero Start Fee)** | $0.05 – $0.10 per run |
| **Speed per Job Board** | **0.15s – 0.3s (Pure API)** | 10s – 25s per company board |
| **Pricing Model** | **Pay-Per-Event ($0.005 / job)** | Expensive Monthly Flat Fee ($40–$60/mo) |
| **Data Cleanliness** | **Flattened string arrays, normalized compensation** | Broken nested objects, raw DOM tags |
| **Proxy Requirement** | **0% Proxy needed (Zero bandwidth cost)** | Expensive Residential Proxies required |

---

## 📦 Sample JSON Output

```json
{
  "id": "e44c2780-606b-4e83-847e-8c31cb15a4b7",
  "title": "Senior AI Systems Engineer",
  "company": "Linear",
  "companyUrl": "https://jobs.ashbyhq.com/linear",
  "applyUrl": "https://jobs.ashbyhq.com/linear/e44c2780-606b-4e83-847e-8c31cb15a4b7/application",
  "department": "Engineering",
  "team": "Platform",
  "location": "San Francisco, CA",
  "secondaryLocations": ["New York, NY", "Remote US"],
  "isRemote": true,
  "workplaceType": "Remote",
  "employmentType": "FullTime",
  "compensation": "$180,000 - $240,000 + Equity",
  "publishedAt": "2026-11-17T10:00:00.000Z",
  "scrapedAt": "2026-11-17T11:00:00.000000+00:00"
}
```

---

## 🎯 Use Cases & Business Value

- **Automated Tech Job Aggregators**: Build automated niche job boards for AI Engineers, Frontend, Backend, or Remote-only careers pulling from hundreds of top Ashby job boards.
- **Talent Intelligence & Headhunting**: Monitor headcount expansion, hiring spikes, and new department formations at hyper-growth tech unicorns.
- **Salary & Compensation Benchmarking**: Aggregate verified base pay ranges and equity packages across tier-1 software companies.
- **Autonomous AI Career Agents**: Feed real-time job openings directly into autonomous job application and talent matching agents via **Apify MCP Server**.

---

## ⚙️ Input Parameters

| Parameter | Type | Default | Description |
|---|---|---|---|
| `companies` | Array | `["linear", "supabase", "ramp"]` | List of Ashby company identifiers or full job board URLs (e.g. `linear`, `supabase`, `https://jobs.ashbyhq.com/replit`). |
| `department` | String | `""` | Optional department filter (e.g. `Engineering`, `Product`, `Design`, `Sales`, `Marketing`). |
| `location` | String | `""` | Optional location filter (e.g. `San Francisco`, `New York`, `Remote`, `London`). |
| `onlyRemote` | Boolean | `false` | When `true`, filters strictly for remote-eligible openings (`isRemote: true` or `workplaceType: Remote`). |
| `maxItems` | Integer | `10` | Maximum number of verified job records to scrape and push to dataset (Prefilled for instant 5-second test runs). |

---

## 🤖 Integrate with AI Agents & No-Code Platforms

### 1. Claude Desktop & Cursor via Apify MCP Server
Connect this actor directly to Cursor, Claude Desktop, Windsurf, or LangChain agents using the official Apify MCP Server:

```json
{
  "mcpServers": {
    "apify": {
      "command": "npx",
      "args": ["-y", "@apify/mcp-server"],
      "env": {
        "APIFY_TOKEN": "YOUR_APIFY_API_TOKEN"
      }
    }
  }
}
```
*Prompt example:*
> *"Find 15 remote engineering jobs at Linear, Supabase, and Ramp using ashby-jobs-scraper and give me the salary ranges and application links."*

### 2. n8n Automation Workflows
1. Add an **Apify Node** or **HTTP Request Node** in your n8n workflow.
2. Select `Run an Actor` with Actor ID: `moneygain/ashby-jobs-scraper`.
3. Pipe fresh engineering jobs into Discord, Telegram channels, Notion databases, or Slack alerts.

### 3. Make.com (Integromat)
1. Add the **Apify Module** ➔ `Run Actor and get dataset items`.
2. Schedule daily runs across your target company watchlists and filter for new `publishedAt` dates.

### 4. Clay.com Enrichment
1. Use the **Apify Integration** inside Clay.
2. Pull active hiring roles for target B2B accounts to identify high-intent buyer signals.

### 5. Python SDK Integration
```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_API_TOKEN")
run_input = {
    "companies": ["linear", "supabase", "ramp"],
    "onlyRemote": True,
    "maxItems": 20
}
run = client.actor("moneygain/ashby-jobs-scraper").call(run_input=run_input)

for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(f"[{item['company']}] {item['title']} | {item['compensation']} -> {item['applyUrl']}")
```

---

## ❓ Frequently Asked Questions (SEO FAQ)

### Q1: Is it legal to scrape job postings from Ashby?
**Yes.** All job postings extracted by this actor are publicly listed career advertisements published by companies specifically to attract candidates. The scraper accesses only public posting data without bypassing authentication or private applicant tracking records.

### Q2: How much does it cost to extract 1,000 jobs?
Under our **Pay-Per-Event (PPE)** pricing, you only pay **$0.005 per verified job posting**, so 1,000 jobs cost **$5.00**. There are zero startup costs, zero compute charges, and subscribers on Apify Bronze/Silver/Gold tiers receive automatic volume discounts up to 20% ($4.00 per 1,000).

### Q3: Can I export Ashby jobs to Excel, CSV, or Google Sheets?
**Yes.** Apify provides 1-click export options in JSON, CSV, XML, Excel (.xlsx), and HTML table formats. You can also sync datasets automatically to Google Sheets or Airtable via Apify Webhooks.

### Q4: Do I need residential proxies to scrape Ashby?
**No.** Ashby's public career board endpoints do not block standard cloud IPs. Our lightweight HTTP architecture connects directly, saving you 100% of proxy bandwidth costs.

### Q5: How often are job boards updated?
Job listings are live and reflect real-time openings. Whenever a company opens or closes a role on Ashby, running this actor retrieves the up-to-the-minute hiring state.

---

## 🔗 Explore More High-Speed B2B Scrapers & Enrichers by Our Team

Supercharge your data pipelines, sales outreach, and AI agents with our suite of lightweight, Pay-Per-Event scrapers:

| Scraper | Segment / Target | Key Value | Store Link |
|---|---|---|---|
| **TrustMRR SaaS Startups Scraper** | SaaS Revenue & M&A Data | Stripe-verified MRR, 30d revenue, active subscriptions & founder contacts | [Open on Apify Store](https://apify.com/moneygain/trustmrr-startups-scraper) |
| **Ashby ATS Tech Jobs Scraper** | Next-Gen ATS Career Feeds | Direct ATS API extraction, salaries, departments & remote flags | [Open on Apify Store](https://apify.com/moneygain/ashby-jobs-scraper) |
| **Clutch B2B Agencies Scraper** | B2B Agencies & IT Services | Decoded direct websites, review ratings, hourly rates & service focus | [Open on Apify Store](https://apify.com/moneygain/clutch-agencies-scraper) |
| **Wellfound Startup Talent Scraper** | AI & Tech Startup Jobs | Startup jobs, compensation ranges, equity & tech stack tags | [Open on Apify Store](https://apify.com/moneygain/wellfound-jobs-scraper) |
| **TheProtocol.it IT Careers Scraper** | IT Salaries & Vacancies | Verified salary brackets, tech requirements & seniority levels | [Open on Apify Store](https://apify.com/moneygain/theprotocol-scraper) |
| **Bulldogjob Tech Recruitment Scraper** | Tech Recruitment Feeds | B2B/Employment rates, tech tags & recruiter contacts | [Open on Apify Store](https://apify.com/moneygain/bulldogjob-scraper) |
