# 🦈 SharkFin — Your Local AI Agent

**Local-first. Action-oriented. Trust-first. Self-learning. Multi-agent.**    
The open-source personal AI agent that runs 100% on your machine, connects to your chats, executes real tasks, and gets smarter every day.

A production-ready personal AI agent that lives in your chats and *does* things that you want it to do. 

SharkFin is a local AI agent that runs on your machine, works from the CLI, executes real workflows, and helps you automate work that normally eats your time.

This is not just a chatbot. SharkFin can read, write, browse, search memory, orchestrate multiple agents, generate its own playbooks, and turn repeatable work into reusable automation.

## Why SharkFin?
- **Real local execution**: Run an AI agent on your own machine, not behind someone else’s black box.
- **Cutting-edge automation**: Browser actions, Gmail workflows, memory search, document extraction, SEO optimization, and multi-agent task execution.
- **Transparency first**: Inspect playbooks, dry-run workflows, and see what the agent is doing.
- **Forge self-improvement**: Describe a workflow in plain English and SharkFin can generate a new playbook for it.
- **Built for serious users**: CLI-native, scriptable, extensible, and fast to iterate with.

## Install

For the current release, the recommended install from NPM.

```bash
npm install -g sharkfin
sharkfin register
sharkfin start

```

If `npm link` fails on Linux due to permissions:

```bash
npm_config_prefix="$HOME/.local" npm link
export PATH="$HOME/.local/bin:$PATH"
```

## Current Release Notes

What is ready:

- Source install
- CLI agent
- Playbooks
- Forge playbook generation
- Multi-agent orchestration
- Optional NemoClaw security layer
- Gmail, browser, web research, memory, filesystem, messaging, and SEO workflows
- Standalone auth commands for Telegram, Discord, Gmail, and Calendar
- Nvidia NemoClaw Security

Coming soon:

- SharkBook: Agentic AI combat battles.
- Ghostwriter social automation
- Mythos LLM defense

## Optional NemoClaw Security Layer

SharkFin supports an optional NemoClaw security layer for customers who want stronger guardrails around tool execution.

What NemoClaw adds:

- optional policy-based guardrails around tool execution
- stronger trust and enterprise-style controls without changing the default local-first experience
- a simple on/off flow so customers can enable it only when they want the extra layer

Core commands:

```bash
sharkfin security enable nemoclaw
sharkfin security status
sharkfin security disable nemoclaw
```

## Before You Register

`sharkfin register` is the fastest way to get started, but it goes much more smoothly if you have your integrations ready first.

What SharkFin will ask you for during registration:

- your agent name
- your primary LLM provider and model
- optional Telegram bot setup
- optional Discord bot setup
- optional Gmail OAuth setup
- optional Google Calendar OAuth setup

### LLM Provider

You will choose one of these providers during registration:

- `openai`
- `anthropic`
- `grok`
- `ollama`
- `local`

If you choose `openai`, `anthropic`, or `grok`, have your API key ready.

If you choose `ollama` or `local`, have your server URL ready. Typical defaults:

```bash
http://localhost:11434/v1
http://localhost:8080/v1
```

### Gmail OAuth

If you want inbox workflows, email drafting, thread reading, and follow-up automations, prepare Gmail before or during registration.

What you need:

1. Create a Google Cloud project
2. Enable the Gmail API
3. Create OAuth 2.0 credentials for a **Desktop app**
4. Download the OAuth JSON
5. Save it here:

```bash
~/.sharkfin/google-credentials.json
```

Then authenticate either during `sharkfin register` or later with:

```bash
sharkfin email-auth
```

SharkFin stores the Gmail token here after authentication:

```bash
~/.sharkfin/google-email-token.json
```

### Google Calendar OAuth

If you want calendar-based playbooks or event creation, use the same Google credentials file:

```bash
~/.sharkfin/google-credentials.json
```

Before authenticating Calendar:

1. Enable the Google Calendar API in the same Google Cloud project
2. Make sure your OAuth client is still a **Desktop app**

Then authenticate either during registration or later with:

```bash
sharkfin calendar-auth
```

SharkFin stores the Calendar token here:

```bash
~/.sharkfin/google-token.json
```

### Telegram Setup

If you want SharkFin to run through Telegram, prepare a bot first.

What you need:

1. Open `@BotFather` in Telegram
2. Run `/newbot`
3. Create a bot name and username
4. Copy the bot token
5. Send `/start` to your bot from the chat or group you want SharkFin to use

During registration, SharkFin will:

- verify your token
- try to auto-discover chat IDs
- ask which chat IDs you want to allow

If auto-discovery finds nothing, you can paste chat IDs manually.

You can also add or update Telegram later without re-running full registration:

```bash
sharkfin telegram-auth
```

### Discord Setup

If you want SharkFin in Discord, prepare a bot in the Discord Developer Portal first.

What you need:

1. Go to `https://discord.com/developers/applications`
2. Create an application and bot
3. Copy the bot token
4. Enable Message Content intent if you want natural chat workflows
5. Invite the bot to your server

You can configure Discord either during `sharkfin register` or later with:

```bash
sharkfin discord-auth
```

During registration, SharkFin will ask for:

- the Discord bot token
- optional channel IDs to restrict where the bot listens

### SharkHub

SharkHub, the Playbooks Hub, and Marketplace are not part of the current customer release.

Those features are coming soon and should not be treated as required setup for SharkFin today.

## First 5 Minutes

1. Run registration:

```bash
sharkfin register
```

What to expect:

- SharkFin will ask you to name your agent
- you will choose your primary LLM provider and model
- you can optionally configure Telegram, Discord, Gmail, and Calendar in the same flow

If you do not have every integration ready yet, that is fine. You can skip them and come back later.

2. Start the agent:

```bash
sharkfin start
```

This launches SharkFin in CLI mode and starts the local agent process.

3. Open a second terminal and try:

```bash
sharkfin playbooks run inbox-executive-brief
```

This is the fastest wow-factor demo in the product. It turns inbox activity into a sharp executive brief with priorities, risks, and next actions.

4. Generate your own playbook:

```bash
sharkfin forge "track my sales leads from Gmail emails"
```

This shows SharkFin's self-learning side: describe a workflow in plain English and let Forge build the playbook for you.

5. Try a multi-agent task:

```bash
sharkfin agents run "write a short executive summary of this week's priorities" --agents analyst,writer
```

This runs a coordinated multi-agent workflow instead of a single-pass response.

6. Forge your own workflow:

```bash
sharkfin forge "create a playbook that summarizes unread Gmail threads and drafts follow-ups"
```

If Gmail is not authenticated yet, do that next:

```bash
sharkfin email-auth
```

If Calendar is not authenticated yet, do that next:

```bash
sharkfin calendar-auth
```

## Core Commands

```bash
sharkfin start
sharkfin register
sharkfin console
sharkfin playbooks list
sharkfin playbooks run <name>
sharkfin playbooks simulate <name>
sharkfin forge "<goal>"
sharkfin agents run "<goal>" --agents analyst,writer
sharkfin security enable nemoclaw
sharkfin security status
sharkfin security disable nemoclaw
sharkfin email-auth
sharkfin calendar-auth
sharkfin telegram-auth
sharkfin discord-auth
sharkfin logs --limit 20
```

## Safety And Responsibility

SharkFin is designed to be transparent and patchable, but you are responsible for the playbooks, prompts, agents, and actions you choose to run.

Do not use SharkFin for malicious activity, harmful automation, abuse, or unauthorized access.


## 🔥 New in v1.6: Forge Self-Improvement
Type `sharkfin forge` in the CLI and go from idea to runnable automation:

**Describe -> Forge -> Run -> Improve**

- Turn plain-English requests into playbooks
- Get safer YAML and stronger tool validation
- Receive proactive forge suggestions while SharkFin is running
- Build your own automation library without hand-writing every workflow

What makes Forge important is that it is not just a prompt-to-YAML shortcut.

Forge is SharkFin's workflow creation engine:

- it generates playbooks using SharkFin's real registered tools instead of inventing fake capabilities
- it validates structure, tool params, templates, paths, and data flow before saving a result
- it retries when the generated workflow is invalid or too weak for the requested task
- it compounds over time because each useful playbook becomes part of your own growing local automation library
- it can suggest new automations from recent usage patterns, which makes SharkFin feel more like a system that improves with you instead of resetting every session

This is one of SharkFin's clearest moats: customers are not only using an agent, they are steadily building a reusable library of agentic workflows tailored to how they actually work.

## What Customers Get

- A local AI agent you control
- Reusable playbooks for repeatable work
- A growing toolset for files, email, browser, web research, memory, documents, messaging, SEO, calendar, and agents
- Multi-agent orchestration for larger tasks
- Forge playbook generation from plain-English requests
- Optional NemoClaw guardrails for customers who want an extra security layer
- A transparency trail so you can see what happened and what was produced

## Best First Experience

If you want the fastest “this saved me 20 minutes” demo, start with:

```bash
sharkfin playbooks run inbox-executive-brief
```

That playbook turns your inbox into a concise executive summary with priorities, risks, and next actions.

Other strong demos:

```bash
sharkfin playbooks run browser-clickthrough-brief
sharkfin playbooks run memory-followup-brief
sharkfin playbooks run seo-optimizer
```

## What SharkFin Is Good At Today

- Inbox summaries and follow-up workflows
- Browser-based research and page briefs
- Memory-backed assistant workflows
- Multi-step file and reporting automations
- Multi-agent drafting and synthesis

##  Ghostwriter

Ghostwriter is a SharkFin-only moat: a local-first personal brand engine that helps customers research topics, generate content, queue drafts, schedule publishing workflows, and later connect that workflow to optional SharkBook social distribution.

The most compelling Phase 4 use cases are:

- **Personal brand content engine**: a founder, consultant, or coach runs Ghostwriter to generate weekly post drafts, hooks, captions, and a publishing queue without living inside social media all day.
- **Community growth copilot**: a customer uses Ghostwriter to review engagement, generate reply suggestions, and improve future content based on what is actually working inside SharkBook.

Example CLI:

```bash
sharkfin ghostwriter start "FounderBrand"
sharkfin ghostwriter run-now FounderBrand
sharkfin ghostwriter status
```

What customers would get:

- a saved Ghostwriter brand workspace
- local draft posts and content ideas
- a scheduled queue for review or approval
- optional SharkBook publishing once enabled
- a clear transparency trail for every generated draft, schedule, and reply suggestion

Typical status output:

```text
Ghostwriter Swarm: FounderBrand
Mode: draft-only
Platform: sharkbook
Drafts queued: 5
Posts published this week: 2
Reply suggestions queued: 8
Next run: 2026-03-27 09:00
Top topic cluster: local AI workflows for consultants
```

### Why This Matters To SharkFin

If Ghostwriter ships well, it should improve SharkFin's strategic value more than a simple incremental tool would.

Why:

- it creates a repeatable, high-frequency use case instead of one-off agent usage
- it gives SharkFin a clearer wedge into founders, creators, consultants, and agencies
- it increases the chance of retention because customers come back for ongoing content output, not just occasional workflow automation
- it creates a stronger product story: SharkFin is not just an agent runner, it is a revenue and audience growth system

It is better to think about Ghostwriter as a valuation multiplier on product narrative, retention, and monetization potential, not as something that automatically adds a fixed dollar amount by itself.

## Tools List

SharkFin currently ships with **41 built-in tools** across the workflows customers care about most.

**Email**
- `email.list`
- `email.read_thread`
- `email.draft`
- `email.reply`
- `email.send`

**Files**
- `fs.read_file`
- `fs.write_file`
- `fs.append_file`
- `fs.move_file`
- `fs.delete_file`
- `fs.list_dir`

**Browser**
- `browser.open`
- `browser.click`
- `browser.type`
- `browser.extract`
- `browser.screenshot`

**Memory**
- `memory.store`
- `memory.search`

**Documents**
- `document.extract_text`

**Calendar**
- `calendar.list_events`
- `calendar.create_event`

**Web + Messaging + System**
- `web.search`
- `web.fetch`
- `http.get`
- `http.post`
- `message.send`
- `shell.exec`

**AI + Orchestration**
- `seo.optimize_content`
- `agent.orchestra`

## Self-Learning And Multi-Agent Workflows

SharkFin does more than run single commands.

**Self-learning with Forge**
- Generate new playbooks from a goal like `sharkfin forge "track my sales leads from Gmail emails"`
- Save repeatable automations into your personal playbook library
- Improve how you work over time instead of starting from scratch every session

Self-learning in SharkFin does not mean hidden model retraining or black-box behavior. It means SharkFin can observe workflow patterns, suggest new automations, and help you convert successful tasks into reusable playbooks you control.

What Forge does for customers:

- translates a plain-English workflow request into a runnable playbook that uses real SharkFin tools
- hardens the generated playbook with schema checks, tool-aware validation, safer defaults, and retries
- helps medium and harder workflows land more reliably, including web research, memory-backed playbooks, document extraction, and multi-agent synthesis
- makes your best workflows reusable so tomorrow's work starts from a working system instead of a blank prompt
- turns SharkFin into a compounding productivity asset, because every successful playbook adds to your local operating system for work

Why this matters:

- most AI products give you a one-time answer
- Forge helps you turn repeated work into a durable asset
- that asset stays local, inspectable, editable, and reusable
- over time, the customer gets more leverage from the product because SharkFin is learning their workflows, not just answering isolated prompts

Example progression:

```bash
sharkfin forge "create a playbook that researches local AI agent businesses, stores key notes in memory, searches for monetization insights, and writes a concise report"
sharkfin playbooks run market-memory-pack
```

What this produces for the customer:

- a saved playbook they can rerun instead of rewriting the task later
- a repeatable workflow that can combine research, memory, and synthesis
- output files they can inspect, edit, and reuse
- a stronger base for future Forge suggestions and related automation ideas

How customers should use self-learning:

- start with one repeated task you already do every week
- use `sharkfin forge "<goal>"` to turn that task into a reusable playbook
- run the generated playbook and keep the workflows that save real time
- refine the goal when you want a stronger second version or a more specific output
- build a small library of trusted playbooks instead of relying on one-off prompts

How to view logs and inspect what SharkFin is doing:

```bash
sharkfin logs --limit 20
sharkfin playbooks list
sharkfin playbooks run <name>
```

What to look for:

- recent tool activity and successful workflow runs in `sharkfin logs`
- the saved playbook name in your local library after Forge creates it
- the output files created when you rerun that playbook

For customers, this is the practical self-learning loop:

1. Describe the work.
2. Let Forge generate the workflow.
3. Run it and inspect the logs.
4. Keep and reuse the workflows that prove valuable.

**Multi-agent execution**
- Run specialist agents together for research, analysis, and writing
- Use `agent.orchestra` inside playbooks
- Launch multi-agent jobs directly from the CLI

Example:

```bash
sharkfin agents run "write a short executive summary of this week's priorities" --agents analyst,writer
```

This is one of SharkFin's most powerful advantages: it can both create new workflows for you and execute complex work through coordinated agents.



## Beta Status

SharkFin is in active beta. Post bugs. 

That means:

- the core product is usable now
- some integrations still need polish
- the best-supported install path is source clone
- new releases will continue to improve reliability, security, and onboarding

## Support

- GitHub: `https://github.com/sharkfinAI/sharkfinApp`
- X @SharkfinAI
- webpage: https://sharkfinai.io
- Community: see project community links in the main repo materials

If you want the engineering and internal details, use the main [README.md](/sharkfin/README.md). This file is the customer-facing quick guide.
