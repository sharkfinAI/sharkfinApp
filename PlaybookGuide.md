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

Writes:
- `tiktok-content-engine-blog.md` by default, or the file set in `output_path`

Run:

```bash
sharkfin playbooks run content-engine
```

#### SEO Content Optimizer (`seo-optimizer`)
Purpose: Read a draft article, optimize it for target keywords, and save an SEO-ready version with metadata and recommendations.

Writes:
- `content-draft.md`
- `content-optimized.md`

Run:

```bash
sharkfin playbooks run seo-optimizer
```

#### TikTok Revenue Hook Pack (`tiktok-revenue-hook-pack`)
Purpose: Build a TikTok-ready content pack from a business offer, including hooks, short scripts, captions, CTAs, filming prompts, and a simple 7-day posting plan.

Writes:
- `tiktok-revenue-brief.md`
- `tiktok-revenue-hook-pack.md`

Run:

```bash
sharkfin playbooks run tiktok-revenue-hook-pack
```

#### TikTok Trend Opportunity Brief (`tiktok-trend-opportunity-brief`)
Purpose: Build a TikTok opportunity brief for a niche, including trend themes, video ideas, hooks, captions, hashtags, CTAs, and best bets to film this week.

Writes:
- `tiktok-trend-opportunity-brief.md`

Run:

```bash
sharkfin playbooks run tiktok-trend-opportunity-brief
```

#### TikTok Weekly Content Calendar (`tiktok-weekly-content-calendar`)
Purpose: Generate a 7-day TikTok content calendar with daily hooks, short scripts, captions, CTAs, hashtags, and filming prompts.

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
Purpose: Synthesize practical public advice on tailoring LinkedIn applications, recruiter-friendly resumes, networking, and follow-up strategies into a jobseeker guide.

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
