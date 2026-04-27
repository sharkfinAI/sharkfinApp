# SharkFin Playbooks Guide

This guide documents the current built-in playbooks shipped from the top-level `playbooks/` folder.


## Playbook Basics

List all available playbooks:

```bash
sharkfin playbooks list
```

Simulate a playbook before approving actions:

```bash
sharkfin playbooks simulate <playbook-id>
```

Run a playbook:

```bash
sharkfin playbooks run <playbook-id>
```

## Before You Run

Some built-in playbooks are ready to run as-is. Others are designed to ship with starter inputs so customers can see the workflow immediately and then replace those inputs with real data.

Best practice:

- run the playbook once to understand the output shape
- then open the playbook YAML and replace the starter variables or seeded source text with your real content
- if a playbook uses `email.*`, make sure Gmail auth is configured first with `sharkfin email-auth`

The most common fields customers will want to customize are:

- `variables:` values near the top of the playbook
- seeded source text inside `fs.write_file` steps
- search queries inside `web.search` steps
- output file names if you want a different saved filename

## Built-in Playbooks

SharkFin currently ships with **14** top-level built-in playbooks.

### Email and Inbox

#### Morning Inbox (`morning-inbox`)
Purpose: Scan unread email and write a lightweight morning summary.

Writes:
- `morning-inbox-summary.txt`

Run:

```bash
sharkfin playbooks run morning-inbox
```

#### Inbox Executive Brief (`inbox-executive-brief`)
Purpose: Analyze unread Gmail messages and turn them into an executive-style action brief with priorities, risks, and suggested next steps.

Writes:
- `inbox-executive-brief.md`

Run:

```bash
sharkfin playbooks run inbox-executive-brief
```

#### Gmail Thread Follow-up Draft (`gmail-thread-followup-draft`)
Purpose: Read a recent Gmail thread, generate a concise follow-up recommendation, create a Gmail draft, and save a local review file.

Writes:
- `gmail-thread-followup-draft.md`

Run:

```bash
sharkfin playbooks run gmail-thread-followup-draft
```

#### Memory Follow-up Brief (`memory-followup-brief`)
Purpose: Compare recent inbox activity with stored memory, generate a follow-up brief, and save the new brief back into memory for future runs.

Writes:
- `memory-followup-brief.md`

Run:

```bash
sharkfin playbooks run memory-followup-brief
```

### Browser and Research

#### Browser Page Brief (`browser-page-brief`)
Purpose: Open a webpage, extract a concise structured summary, and save a lightweight SVG snapshot.

Writes:
- `browser-page-brief.md`
- `browser-page-brief.svg`

Run:

```bash
sharkfin playbooks run browser-page-brief
```

#### Browser Clickthrough Brief (`browser-clickthrough-brief`)
Purpose: Open a starting page, follow a real link, summarize the destination, and save a browser snapshot.

Writes:
- `browser-clickthrough-brief.md`
- `browser-clickthrough-brief.svg`

Run:

```bash
sharkfin playbooks run browser-clickthrough-brief
```

### Content and SEO

#### Content Engine (`content-engine`)
Purpose: Run a multi-agent research and writing workflow that produces a blog post draft on a chosen topic.

Customize before serious use:
- update `topic` in the playbook `variables:` block
- update `output_path` if you want a different file name
- treat the default topic as a starter example, not a required production topic

Writes:
- `tiktok-content-engine-blog.md` by default, or the file set in `output_path`

Run:

```bash
sharkfin playbooks run content-engine
```

#### SEO Content Optimizer (`seo-optimizer`)
Purpose: Read a draft article, optimize it for target keywords, and save an SEO-ready version with metadata and recommendations.

Customize before serious use:
- update `target_keywords` in the `variables:` block
- replace the seeded draft content with your real article text
- optionally change the audience and content type in the `seo.optimize_content` step

Important:
- this playbook does not take a URL by default
- if you want to optimize content from a live URL, you would need to modify the playbook to fetch that source first

Writes:
- `content-draft.md`
- `content-optimized.md`

Run:

```bash
sharkfin playbooks run seo-optimizer
```

#### TikTok Revenue Hook Pack (`tiktok-revenue-hook-pack`)
Purpose: Build a generated TikTok-ready content pack from a business offer, including hooks, short scripts, captions, CTAs, filming prompts, and a simple 7-day posting plan.

Notes:
- This is a local content-planning workflow.
- It does not pull live TikTok analytics or publish to TikTok directly.

Customize before serious use:
- update `niche`
- update `offer`
- update `audience`
- update `revenue_goal`
- update `tone`

Writes:
- `tiktok-revenue-brief.md`
- `tiktok-revenue-hook-pack.md`

Run:

```bash
sharkfin playbooks run tiktok-revenue-hook-pack
```

#### TikTok Trend Opportunity Brief (`tiktok-trend-opportunity-brief`)
Purpose: Build a generated TikTok opportunity brief for a niche, including theme ideas, video ideas, hooks, captions, hashtags, CTAs, and best bets to film this week.

Notes:
- This uses built-in planning patterns and the provided niche context.
- It does not pull live TikTok platform trend data.

Customize before serious use:
- update `niche`
- update `audience`
- update `goal`

Writes:
- `tiktok-trend-opportunity-brief.md`

Run:

```bash
sharkfin playbooks run tiktok-trend-opportunity-brief
```

#### TikTok Weekly Content Calendar (`tiktok-weekly-content-calendar`)
Purpose: Generate a 7-day TikTok content calendar with daily hooks, short scripts, captions, CTAs, hashtags, and filming prompts.

Notes:
- This is a generated weekly planning workflow based on the supplied niche, offer, and audience.
- It does not schedule posts on TikTok or use live TikTok analytics.

Customize before serious use:
- update `niche`
- update `offer`
- update `audience`
- update `weekly_goal`
- update `tone`

Writes:
- `tiktok-weekly-content-calendar-brief.md`
- `tiktok-weekly-content-calendar.md`

Run:

```bash
sharkfin playbooks run tiktok-weekly-content-calendar
```

### Documents and Memory

#### Document Memory Brief (`document-memory-brief`)
Purpose: Create a sample source document, extract its text, store it in memory, retrieve matching entries, and write a reusable brief.

Customize before serious use:
- replace the seeded source document with your real notes or document text
- update `memory_key` if you want to store it under a different memory namespace
- update `search_query` so retrieval matches your real use case

Writes:
- `document-memory-source.md`
- `document-memory-brief.txt`

Run:

```bash
sharkfin playbooks run document-memory-brief
```

### Career

#### Job Hunt Accelerator Pro Lite (`job-hunt-accelerator-pro-lite`)
Purpose: Build a local job application pack from a resume draft and a target job brief, then save tailored materials for manual review and submission.

Customize before serious use:
- update `target_role` in the `variables:` block
- replace the seeded resume text with your real resume
- replace the seeded target job brief with the real job description or your own pasted role notes
- optionally change the output file names if you want separate files per company or role

Writes:
- `job-hunt-lite-resume.md`
- `job-hunt-lite-job-brief.md`
- `job-hunt-lite-application-pack.md`
- `job-hunt-lite-tracker.txt`

Run:

```bash
sharkfin playbooks run job-hunt-accelerator-pro-lite
```

#### LinkedIn Interview Strategy Brief (`linkedin-interview-strategy-brief`)
Purpose: Synthesize practical public web advice related to LinkedIn applications, recruiter-friendly resumes, networking, and follow-up strategies into a jobseeker guide.

Customize before serious use:
- update the four `web.search` queries if you want guidance for a specific role, industry, geography, or seniority level
- optionally tighten the final synthesis prompt to focus on a narrower jobseeker audience
- optionally change the output filename if you want separate briefs for different job-search tracks

Writes:
- `linkedin-interview-strategy-brief.md`

Run:

```bash
sharkfin playbooks run linkedin-interview-strategy-brief
```

## Notes on Requirements

- Playbooks that use `email.*` tools require a connected email integration.
- Playbooks that use `memory.*` tools work best when memory is configured and available.
- Browser playbooks require browser tooling support in the running SharkFin environment.
- Multi-agent playbooks depend on a working LLM provider and are most reliable when the goal clearly asks for one final deliverable.
- Some playbooks seed starter files so they can run out of the box; replace those files with your real inputs when needed.

## Creating Your Own Playbooks

Use Forge to generate a new playbook idea:

```bash
sharkfin forge
sharkfin forge "Create a playbook that summarizes new leads and saves a local brief"
```

Then test it:

```bash
sharkfin playbooks simulate my-new-playbook
sharkfin playbooks run my-new-playbook
```
