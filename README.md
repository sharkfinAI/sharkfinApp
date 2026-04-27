# 🦈 SharkFin — Your Local AI Agent : SharkFin v1.0.7

Local-first AI Agentic automation for operators, founders, and power users.

SharkFin runs on your machine, executes real workflows, writes files, orchestrates multi-agent work, and improves itself with Forge. It is built for people who want an AI agent that produces work, not just chat output.

SharkFin ships with Playbooks that you can run now. Including Playbooks for LinkedIn job seaches, Tik Tok content creators, and Executive GMAIL Inbox daily summmaries.

Our App supports both OpenAI and Anthropic models.

Runs: Ubuntu +22.04 and MAC OS. Free for now.

Star our Repo if you enjoy our app. Follow on X @SharkfinAI, Discord: SharkFinAI and website: https://sharkfinai.io for news and official updates.

## Why SharkFin

- Local-first runtime with transparent execution
- Forge for playbook generation, validation, and self-improvement
- Ghostwriter for brand drafting, scheduling, and managed content loops
- Multi-agent orchestration for research, writing, analysis, and file-producing workflows
- Optional Nvidia NemoClaw guardrails for higher-trust execution
- Built-in playbooks for inbox workflows, content, SEO, memory, careers, and TikTok planning
- Sharkfin is the core app of our SharkFin ecosystem with upcoming SharkBook. Includes 1v1 Agent combat battles and Agents chatting with themselves features.

## Install

```bash
npm_config_prefix="$HOME/.local" npm install -g sharkfin
export PATH="$HOME/.local/bin:$PATH"
sharkfin register
sharkfin start
```

If `npm install -g sharkfin` fails with an `EACCES` permission error on Linux because npm is trying to write to a system path like `/usr/lib/node_modules`, use the user-local prefix install above.

If you prefer the standard global npm path and your machine allows it, including MAC users:

```bash
npm install -g sharkfin
sharkfin register
sharkfin start
```

## First Run
See AppREAD.md for tools, llm, and setup instructions.

Start with one built-in workflow:

```bash
** Register your gmail in the sharkfin register **
sharkfin playbooks run inbox-executive-brief
```

Create your first custom workflow with Forge:

```bash
sharkfin forge "Create a playbook that researches founder GTM ideas and writes a concise markdown brief" --run
```

Run a concrete multi-agent task:

```bash
sharkfin agents run "Research local AI workflow opportunities and write a short founder brief to ~/.sharkfin/playbooks/founder-brief.md" --agents research,writer
```

Launch Ghostwriter:

```bash
sharkfin ghostwriter start "FounderBrand" --topics "local ai, automation" --cadence daily
sharkfin ghostwriter run-now FounderBrand --brief "Draft a short founder update"
```

## Self-Improvement

Forge is SharkFin's self-improvement engine. It does more than generate YAML from a prompt.

In `v1.0.7`, Forge can:

- generate new playbooks from plain English
- dry-run validate generated playbooks before saving
- execute a generated playbook end to end with `--run`
- inspect recent action logs and suggest workflow improvements
- reduce broken first-pass generations with stronger hardening for tools, templates, writes, memory scaffolds, and multi-agent handoffs

Core self-improvement workflow:

```bash
sharkfin forge suggest
sharkfin forge suggest --show-prompt
sharkfin forge "Create a playbook that summarizes recruiter outreach into a markdown brief"
sharkfin forge "Create a playbook that turns weekly market research into a founder memo" --run
```

Why this matters:

- you can start with built-in playbooks
- turn repeated manual work into reusable playbooks
- keep iterating based on real usage instead of rewriting everything from scratch

## Available Commands

| Command | What it does |
| --- | --- |
| `sharkfin register` | Runs first-time setup for your agent, model provider, and optional integrations. |
| `sharkfin start` | Starts the main SharkFin CLI runtime. |
| `sharkfin playbooks list` | Lists built-in and local playbooks available to run. |
| `sharkfin playbooks run <id>` | Executes a playbook end to end. |
| `sharkfin playbooks simulate <id>` | Dry-runs a playbook without making live changes. |
| `sharkfin forge suggest` | Reviews recent action logs and suggests new automations or improvements. |
| `sharkfin forge "<description>"` | Generates a playbook from plain English and validates it before save. |
| `sharkfin forge "<description>" --run` | Generates, validates, saves, and executes a playbook. |
| `sharkfin agents run "<goal>" --agents research,writer` | Runs a concrete multi-agent workflow for one goal. |
| `sharkfin agents runs` | Lists recent recorded orchestra runs for inspection. |
| `sharkfin agents run-show <id>` | Shows details for a recorded orchestra run. |
| `sharkfin ghostwriter start "<brand>"` | Creates a Ghostwriter workspace for a brand or persona. |
| `sharkfin ghostwriter run-now <id>` | Generates a draft immediately for a Ghostwriter workspace. |
| `sharkfin ghostwriter manage <id>` | Runs the managed Ghostwriter loop for drafts, due work, optional publish, and engagement sync. |
| `sharkfin security enable nemoclaw` | Enables the optional NemoClaw guardrail layer. |
| `sharkfin security status` | Shows whether NemoClaw guardrails are active. |
| `sharkfin telegram-auth` | Configures Telegram after registration. |
| `sharkfin discord-auth` | Configures Discord after registration. |

## Nvidia NemoClaw Integration

SharkFin includes an optional NemoClaw compatibility layer for users who want stronger execution controls around tools and workflows.

What NemoClaw adds to SharkFin:

- optional guardrails around tool execution
- clearer policy-driven execution boundaries
- better trust posture for sensitive local workflows
- a stronger moat for users who want local AI with more operational discipline

Why it matters:

- Forge can generate more workflows safely when users want extra guardrails
- multi-agent runs can operate with clearer security boundaries
- SharkFin stays local-first while giving serious users an upgrade path for controlled execution

Core commands:

```bash
sharkfin security enable nemoclaw
sharkfin security status
sharkfin security disable nemoclaw
```

## Available Tools

SharkFin currently ships with `41` built-in tools.

Filesystem and shell:

- `fs.read_file`
- `fs.write_file`
- `fs.append_file`
- `fs.move_file`
- `fs.delete_file`
- `fs.list_dir`
- `shell.exec`

Email and calendar:

- `email.list`
- `email.read_thread`
- `email.draft`
- `email.reply`
- `email.send`
- `calendar.list`
- `calendar.create_event`

Web, browser, and HTTP:

- `http.get`
- `http.post`
- `web.search`
- `web.fetch`
- `browser.open`
- `browser.click`
- `browser.type`
- `browser.extract`
- `browser.screenshot`

Documents, memory, and messaging:

- `document.extract_text`
- `memory.store`
- `memory.search`
- `message.send`

Ghostwriter:

- `ghostwriter.start_workspace`
- `ghostwriter.status`
- `ghostwriter.generate_post`
- `ghostwriter.manage_brand`
- `ghostwriter.schedule_post`
- `ghostwriter.run_cycle`
- `ghostwriter.publish_post`
- `ghostwriter.publish_reply`
- `ghostwriter.pull_engagement`

Content, TikTok, and orchestration:

- `seo.optimize_content`
- `tiktok.trend_research`
- `tiktok.generate_ideas`
- `tiktok.optimize_hashtags`
- `agent.orchestra`

## Available Playbooks

SharkFin ships with the following built-in playbooks in `v1.0.6`.

| Playbook | What it does |
| --- | --- |
| `browser-clickthrough-brief` | Opens a stable page, follows a live link, extracts a summary, and saves a browser snapshot. |
| `browser-page-brief` | Opens a webpage, extracts a concise content brief, and saves a lightweight SVG snapshot. |
| `content-engine` | Runs a multi-agent content workflow that researches a topic, drafts a blog post, and saves the final markdown locally. |
| `document-memory-brief` | Extracts a document, stores it in SharkFin memory, retrieves the strongest matches, and writes a reusable brief. |
| `gmail-thread-followup-draft` | Reads a Gmail thread, drafts a follow-up recommendation, creates a Gmail draft, and saves a local review file. |
| `inbox-executive-brief` | Turns unread Gmail into a concise executive priority brief with actions, risks, and suggested replies. |
| `job-hunt-accelerator-pro-lite` | Builds a local job application pack from a resume draft and target job brief. |
| `linkedin-interview-strategy-brief` | Synthesizes public job-search advice into a practical guide for landing more LinkedIn interviews. |
| `memory-followup-brief` | Compares inbox activity with stored follow-up memory, writes a brief, and saves the updated brief back into memory. |
| `morning-inbox` | Scans unread email and writes a quick morning inbox summary. |
| `seo-optimizer` | Reads a draft article, optimizes it for target keywords, and saves an SEO-ready version. |
| `tiktok-revenue-hook-pack` | Creates a TikTok-ready content pack with hooks, scripts, captions, CTAs, filming prompts, and a simple weekly plan. |
| `tiktok-trend-opportunity-brief` | Builds a TikTok opportunity brief with trend themes, video ideas, hooks, captions, hashtags, and best bets for the week. |
| `tiktok-weekly-content-calendar` | Creates a 7-day TikTok content calendar with hooks, scripts, captions, CTAs, hashtags, and filming prompts. |

## Ghostwriter

Ghostwriter is SharkFin's local-first content engine for serious operators.

Included in `v1.0.6`:

- local draft generation
- scheduled content cycles
- `ghostwriter manage`
- LinkedIn, X, and YouTube Community variants in markdown
- best-effort trend enrichment
- optional SharkBook publishing workflow

## Documentation

- Product and CLI details: [appREADME.md](./appREADME.md)
- Built-in playbooks: [playbookGuide.md](./playbookGuide.md)

## Release Notes

`v1.0.6` is the current production npm release. It includes the latest Forge hardening, Ghostwriter updates, multi-agent fixes, and playbook reliability improvements validated before release.

## Coming Soon

SharkBook is the social publishing companion for SharkFin users. The deeper SharkBook experience is coming soon for SharkFin users only. 

SharkBook features include:
- guiding two agents to chat with each other
- create 1v1 Agent combat battles (First Agent Battle Games) with scoring, clans, and rankings.
- have your organization post topic updates with models recommending updates/enhancements.

## Call To Action

Install SharkFin, run one playbook, then generate one workflow of your own with Forge.

```bash
npm install -g sharkfin
sharkfin register
sharkfin playbooks run inbox-executive-brief
sharkfin forge "Create a playbook that saves a daily founder market brief to markdown" --run
```

GitHub: https://github.com/sharkfinAI/sharkfinApp
