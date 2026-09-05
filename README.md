# 🦈 SharkFin — Your Local AI Agent : SharkFin v1.10

Local-first AI Agentic automation (inspired by OpenClaw) for operators, founders, and power users.

SharkFin Agents runs on your machine, executes real workflows, writes files, orchestrates multi-agent work, and improves itself with Forge. It is built for people who want an AI agent that produces work, not just chat output.

SharkFin ships with Playbooks that you can run now. Including Playbooks for LinkedIn job seekers, Tik Tok content creators, and Executive GMAIL inbox daily summaries/action plans.

Our App supports both OpenAI and Anthropic models.

Runs: Ubuntu +22.04 and MAC OS. Free for now.

Star our Repo if you enjoy our app. Follow on X @SharkfinAI and website: https://sharkfinapp.netlify.app for news and official updates. 

## Why SharkFin 

- Local-first runtime with transparent execution
- Forge for playbook AI Agents generation, validation, and self-improvement
- Ghostwriter for brand drafting, scheduling, and managed content loops
- Multi-agent orchestration for research, writing, analysis, and file-producing workflows
- Optional Nvidia NemoClaw guardrails for higher-trust execution
- Built-in playbooks for inbox workflows, content, SEO, memory, careers, and TikTok planning

## 1.0.10 Updates

**Teach a task once. Reuse the workflow. Inspect the result.**

SharkFin turns repeatable work into local AI workflows: decision briefs, research summaries, content drafts, and reusable automations. Forge helps you describe a task, generate a playbook, simulate it, and inspect what a live run produced.

Start with the **Founder Decision Brief**. Give SharkFin a real decision and your context; its multi-agent workflow writes a local Markdown brief you can review and reuse.

**Free to use today. Bring your own model.** Cloud model providers may charge for usage. Model prompts go to the local or cloud provider you configure; local-first does not mean every task runs offline.

[Install from npm](https://www.npmjs.com/package/sharkfin) | [Customer Guide](https://github.com/sharkfinAI/sharkfinApp/blob/main/AppREADME.md) | [Playbook Guide](https://github.com/sharkfinAI/sharkfinApp/blob/main/PlaybookGuide.md) | [Report an Issue](https://github.com/sharkfinAI/sharkfinApp/issues)

## Get Your First Result

Requires **Node.js 20 or newer** and npm.

```bash
npm install -g sharkfin@1.0.10
sharkfin --version
sharkfin register
```

During registration, configure a working model provider. Supported choices include OpenAI, Anthropic, Grok, Ollama, a compatible local endpoint, and Nemotron. Telegram, Discord, Gmail, and Calendar are optional: accept the default **No** to skip them. You can connect them later.

Preview the first mission, then run it with your model:

```bash
sharkfin mission start --goal "Choose our highest-value priority this week" --context "We are a two-person software team. We have ten trial users, limited engineering time, and need better activation." --simulate
sharkfin mission start --goal "Choose our highest-value priority this week" --context "We are a two-person software team. We have ten trial users, limited engineering time, and need better activation."
sharkfin forge runs
sharkfin outcomes
```

**What you get:** a Markdown brief containing your goal and a team recommendation, with prompts asking the team to identify assumptions, risks, and a seven-day action plan. The live command prints the artifact path and run ID. By default, the brief is written under:

```text
~/.sharkfin/playbooks/outcomes/founder-decision-brief-<timestamp>.md
```

Simulation makes no model calls and does not write the brief; it records a local run proof. A live run requires a working model connection. Artifact checks validate declared requirements such as headings and file size, not the factual correctness of the recommendation.

<details>
<summary>Linux installation fails with an EACCES permission error?</summary>

Install under your own account instead of using a system-owned npm directory:

```bash
npm_config_prefix="$HOME/.local" npm install -g sharkfin@1.0.10
export PATH="$HOME/.local/bin:$PATH"
sharkfin register
```

Add the PATH setting to your shell profile if you want it to persist across terminals.

</details>

## What Is New in v1.0.10

- **Forge Outcome Studio:** inspect generated workflows, simulate them, review run proofs, and draft repairs for failed runs.
- **A first useful mission:** the Founder Decision Brief combines analyst, writer, and reviewer roles into a file-producing workflow without requiring email or messaging integrations.
- **Signed playbook packs:** export, verify, and install reusable workflows with an explicit signer-trust decision.
- **Local outcome tracking:** inspect seven-day outcome summaries rather than relying only on activity logs.
- **Clearer onboarding and readiness:** optional integrations stay optional, and configuration status is distinguished from a successfully tested connection.

The release includes **16 bundled playbooks**. Run `sharkfin playbooks list` to see what is installed.

## Forge: From a Task to Reusable Automation

Instead of repeating the same prompt every week, describe the workflow and the artifact you want:

```bash
sharkfin forge "Create a playbook named weekly-priority-brief. Ask an analyst and a reviewer to evaluate three priorities supplied as an input. Write a Markdown brief in the allowed playbook output directory with sections for recommendation, assumptions, risks, and next actions. Declare artifact checks for the output."
```

Forge uses your configured model to generate the playbook and simulates it before saving. Review the generated workflow before live execution. Use the actual playbook ID printed by Forge in the commands below:

```bash
sharkfin forge inspect <playbook-id>
sharkfin forge test <playbook-id>
sharkfin playbooks run <playbook-id>
sharkfin forge runs
```

If the workflow declares required inputs, supply them with `--set key=value`, using the names shown by `forge inspect`.

For explicitly authorized generation and immediate execution:

```bash
sharkfin forge "Create a reusable workflow for my task and declare its expected output" --run --approve
```

`--approve` is required with Forge's `--run`; it does not bypass execution policies. Simulation is a preview, not proof that external services, credentials, or model responses will work in a live run.

### Self-Learning You Can Inspect

SharkFin uses recent action logs to suggest workflow improvements. You stay in control of which suggestions become saved automations.

```bash
sharkfin logs --limit 20
sharkfin forge suggest
sharkfin forge suggest --show-prompt
sharkfin forge runs
sharkfin forge repair <failed-run-id>
```

Repair drafts and tests a proposed fix by default. Add `--save` only when you want to promote the repair to a saved playbook. Review it before running it against live services.

With the runtime running and both `forge.enabled` and `forge.proactiveSuggestions` enabled, Forge can also periodically review activity and suggest improvements. This is workflow learning and reuse, **not automatic model retraining** or unrestricted self-modification.

## Work You Can Put to Use

| Need | Start With | Result |
| --- | --- | --- |
| Decide what to work on next | `sharkfin mission start --goal "Your decision"` | A local Founder Decision Brief |
| Repeat a proven task | `sharkfin playbooks list` | Discover reusable workflows, then inspect and run one |
| Get multiple perspectives | `sharkfin agents run "Compare three ways to improve trial activation" --agents analyst,writer,reviewer` | A coordinated response to your goal |
| Turn documents into reusable context | `sharkfin knowledge ingest ./notes --recursive` | Indexed local knowledge for cited retrieval |
| Draft consistent brand content | Ghostwriter example below | Local drafts and platform-specific variants |
| Review email efficiently | `inbox-executive-brief` or `gmail-thread-followup-draft` | Inbox summaries or follow-up drafts after Gmail setup |

Bundled workflows also cover document briefs, memory-assisted follow-ups, SEO, job-search planning, and content calendars. Integrations and inputs differ by playbook; inspect or simulate before a live run. A content workflow is not a promise of direct access to the platform it writes about.

### Ghostwriter: Draft First, Publish Deliberately

```bash
sharkfin ghostwriter start "FounderBrand" --mode draft-only --cadence manual --topics "local AI, founder lessons"
sharkfin ghostwriter run-now FounderBrand --brief "Draft a founder update about improving customer onboarding. Do not invent customer quotes or performance numbers."
sharkfin ghostwriter status FounderBrand
```

Ghostwriter maintains a local brand workspace and generates drafts, including LinkedIn, X, and YouTube variants. The example is manual and draft-only: it does not publish your content.

Optional social integration uses **SharkBook HTTP**, not a direct database connection. It does not provide native publishing to LinkedIn, X, or YouTube. Ghostwriter management remains CLI-only in this release.

## Core Commands

| Command | Purpose |
| --- | --- |
| `sharkfin register` | Configure your identity, model, and optional integrations |
| `sharkfin mission list` | Discover starter missions |
| `sharkfin mission start --goal "..."` | Run the Founder Decision Brief |
| `sharkfin forge "..."` | Generate a reusable playbook |
| `sharkfin forge inspect <name>` | Review a workflow's plan and requirements |
| `sharkfin forge test <name>` | Simulate a workflow without live tool execution |
| `sharkfin forge runs` | Inspect recorded run history |
| `sharkfin forge repair <run-id>` | Draft and test a repair |
| `sharkfin playbooks list` | List installed playbooks |
| `sharkfin playbooks run <name>` | Execute a saved playbook |
| `sharkfin playbooks lint --user` | Check customer playbooks for validation problems |
| `sharkfin agents run "..." --agents analyst,writer,reviewer` | Run a multi-agent task |
| `sharkfin ghostwriter status` | View Ghostwriter workspaces |
| `sharkfin outcomes` | Review local seven-day outcome summaries |
| `sharkfin logs --limit 20` | Review recent action logs |
| `sharkfin doctor` | Diagnose local setup and workflow issues |
| `sharkfin capabilities` | Report available, configured, degraded, or unsupported capabilities |
| `sharkfin start` | Run the long-running headless chat and scheduling runtime |
| `sharkfin console` | Open the interactive terminal dashboard |
| `sharkfin --help` | See top-level commands; use `<command> --help` for options |

Standalone missions, Forge commands, and playbook runs do not require `sharkfin start`. The runtime stays in the foreground until stopped with Ctrl+C; it is not a terminal chat prompt and does not detach itself.

Connect integrations after registration when you need them:

```bash
sharkfin telegram-auth
sharkfin discord-auth
sharkfin email-auth
sharkfin calendar-auth
```

## Knowledge, Jobs, and Everyday Tools

**Cited knowledge:** ingest local documents, search them, inspect sources, and delete sources. Automatic recall is opt-in:

```bash
sharkfin knowledge ingest ./notes --recursive
sharkfin knowledge search "What did we decide about onboarding?"
sharkfin knowledge sources
sharkfin knowledge auto-recall enable
sharkfin knowledge auto-recall disable
```

**Durable jobs:** schedule playbooks with persisted state, retry handling, history, cancellation, and authenticated webhook triggers. Keep the scheduling runtime running to process due work; persistence does not make a stopped application execute jobs. Start with `sharkfin jobs --help`.

**Everyday operations:** web search and fetching, PDF text extraction, browser operations, Gmail, Calendar, Telegram, and Discord support research and productivity workflows. Availability depends on configuration and the specific operation. The current browser is an HTTP/HTML automation layer, **not a full Chromium browser with JavaScript execution**.

## Optional NemoClaw Compatibility Controls

Enable, inspect, or disable the optional security layer:

```bash
sharkfin security enable nemoclaw
sharkfin security status
sharkfin security disable nemoclaw
```

In v1.0.10, this adds **SharkFin-side policy checks and audit metadata**. Tools do **not** execute through NVIDIA OpenShell. Enabling compatibility controls is not a sandbox deployment, NVIDIA certification, or a guarantee that a workflow is safe.

SharkFin's execution gateway also applies approval, policy, dry-run, and audit handling. Review generated workflows and grant only the access they need. Disabling NemoClaw compatibility controls does not remove the application's other execution safeguards.

## Share Signed Playbook Packs

Package a workflow for another SharkFin installation:

```bash
sharkfin playbooks pack export founder-decision-brief --out founder-decision-brief.sharkpack
sharkfin playbooks pack verify founder-decision-brief.sharkpack
```

Before installing someone else's pack, inspect the verification result and confirm the signer fingerprint through a trusted channel. If you decide to trust that signer:

```bash
sharkfin playbooks pack install founder-decision-brief.sharkpack --yes --trust-signer
```

A signature establishes pack integrity relative to its signing key, not the author's real-world identity or the safety of the workflow. Review installed playbooks before execution. Marketplace and SharkHub are not included in this release.

## Troubleshooting and Local Data

```bash
sharkfin doctor
sharkfin doctor --json
sharkfin capabilities --json
sharkfin playbooks lint --all
sharkfin logs --limit 20
```

**Doctor checks local setup and flags actionable issues**, including configuration, playbook validation, and filesystem-related problems. Capabilities distinguishes configured features from degraded or unsupported ones. These checks do not contact your model provider: a configured API key or endpoint is not proof of a working connection.

By default, SharkFin stores application state under `~/.sharkfin`, including playbooks, logs, run records, and Ghostwriter workspaces. Configured output locations may differ. Cloud model calls and connected services can receive task data; review your provider and integration settings before processing sensitive information.

Browser Teach Mode and MCP are not usable integrations in v1.0.10; reserved experimental settings should not be treated as delivered functionality.

## Documentation and Feedback

- [Customer Guide](https://github.com/sharkfinAI/sharkfinApp/blob/main/AppREADME.md): setup and product walkthroughs. Some sections may describe earlier releases; this README covers v1.0.10.
- [Playbook Guide](https://github.com/sharkfinAI/sharkfinApp/blob/main/PlaybookGuide.md): workflow examples and playbook concepts.
- [npm Package](https://www.npmjs.com/package/sharkfin): published installation package.
- [GitHub Issues](https://github.com/sharkfinAI/sharkfinApp/issues): report a problem or request a workflow.

If a workflow fails, include your SharkFin version, operating system, command, and a sanitized error excerpt. Never post API keys, tokens, private documents, or unredacted logs.

**Try one real task, inspect the artifact, then rerun the workflow when you need it again.** If it saves you time, share a sanitized example and tell us what outcome you want SharkFin to handle next.


## 1.08 Updates
What is ready:

- Published npm install
- CLI agent
- Playbooks
- Forge playbook generation and self-improvement suggestions
- Multi-agent orchestration for concrete research-and-writing workflows
- Optional NemoClaw security layer
- 69 built-in tools across Gmail, Calendar, browser, web research, cited knowledge, durable jobs, filesystem, messaging, and SEO workflows
- Standalone auth commands for Telegram, Discord, Gmail, and Calendar
- Ghostwriter local drafting, scheduling, brand loops, and optional SharkBook publishing
- Built-in `sharkfin doctor` health diagnostics
- Customer playbook linting and recoverable Forge fallback quarantine
- Upgrade-safe bundled playbooks that preserve customer edits
- Hardened `web.fetch` URL validation for generated workflows
- Cited local knowledge with source labels, line ranges, and opt-in automatic recall
- Restart-safe one-time, cron, and authenticated-webhook jobs with retries and history
- Rich browser tabs, profiles, keyboard, forms, uploads, downloads, waits, PDF, and screenshot operations
- Gmail search and attachments, Calendar mutation/free-busy, and richer Telegram/Discord messaging
  
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
See AppREADME.md for tools, llm, and setup instructions.

** Your SharkFin output data lives in the .sharkfin folders. Output of Agents playbook runs lives in the .sharkfin/playbooks folder. You can Create custom folders in the playbooks folders if needed and update the location in the .yml files. **

example: 
.sharkfin
  -playbooks
    /jobsearch tiktok seo

Start with one built-in workflow:

```bash
** Register your gmail and auth in the sharkfin register or sharkfin email-auth **
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

In `v1.0.8`, Forge can:

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
sharkfin start
sharkfin playbooks run inbox-executive-brief
sharkfin forge "Create a playbook that saves a daily founder market brief to markdown" --run
```

GitHub: https://github.com/sharkfinAI/sharkfinApp
