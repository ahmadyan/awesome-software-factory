# Awesome Software Factory [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of tools, patterns, and essays for taking work from issue to merged pull request with coding agents.

A software factory is the system around the agents: where work comes in, where each task runs in isolation, how the result is checked and reviewed, and what it costs. This list follows that line from intake to merge. Entries are alphabetical within each section. Tools that only run on a Mac are marked macOS.

## Contents

- [Concepts and essays](#concepts-and-essays)
- [Control planes and factory floors](#control-planes-and-factory-floors)
- [Coding agents](#coding-agents)
- [Isolation and sandboxes](#isolation-and-sandboxes)
- [Issue intake](#issue-intake)
- [Background and cloud agents](#background-and-cloud-agents)
- [Review and verification](#review-and-verification)
- [Long-horizon and manager agents](#long-horizon-and-manager-agents)
- [Cost and observability](#cost-and-observability)
- [Related lists](#related-lists)

## Concepts and essays

Where the idea comes from and how teams run it today.

- [Compound Engineering: How Every Codes With Agents](https://every.to/chain-of-thought/compound-engineering-how-every-codes-with-agents) - Every's four-step process for a team whose engineers direct agents instead of writing code, with each cycle feeding lessons into the next.
- [Effective harnesses for long-running agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents) - Anthropic on keeping an agent productive across many context windows with an initializer step, progress notes, and incremental commits.
- [Harness engineering: leveraging Codex in an agent-first world](https://openai.com/index/harness-engineering/) - OpenAI's account of shipping a product where agents write the code and engineers build the environment, documentation, and checks around them.
- [Ralph Wiggum as a "software engineer"](https://ghuntley.com/ralph/) - Geoffrey Huntley's case for running a coding agent in a plain loop against a specification until the work is done.
- [Software Factories, Light and Dark](https://addyosmani.com/blog/software-factories/) - Addy Osmani on factories that keep people in the loop versus fully automated ones, and what each requires.
- [Software factory](https://en.wikipedia.org/wiki/Software_factory) - History of the term, from 1960s proposals and Japanese software factories to model-driven development.
- [StrongDM Software Factory](https://factory.strongdm.ai/) - StrongDM's notes from building software with agents and no interactive coding, covering specifications, scenario tests, and validation harnesses.
- [The Five Levels: from Spicy Autocomplete to the Dark Factory](https://www.danshapiro.com/blog/2026/01/the-five-levels-from-spicy-autocomplete-to-the-software-factory/) - Dan Shapiro's scale of AI-assisted development, from autocomplete to a factory that runs without people.
- [Understanding Spec-Driven-Development: Kiro, spec-kit, and Tessl](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html) - Birgitta Böckeler compares three tools that make the specification the main artifact agents work from.

## Control planes and factory floors

Where tasks are assigned, run in parallel, and brought back for review.

- [Agent Orchestrator](https://github.com/OrchestratorInc/agent-orchestrator) - Plans, runs, and supervises teams of coding agents from task to merge, with a worktree per task and any agent harness. Open source (Apache-2.0).
- [Agentastic](https://www.agentastic.dev/ai-software-factory) - Native multi-agent IDE that runs provider CLIs in worktrees or containers and keeps tests, browser checks, diff review, and pull requests next to each task; this page describes the software-factory workflow it supports. macOS. Proprietary.
- [Archon](https://github.com/coleam00/Archon) - Workflow engine that defines planning, implementation, validation, review, and pull-request steps as YAML so agents run them the same way every time. Open source (MIT).
- [Fusion](https://github.com/Runfusion/Fusion) - Multi-agent orchestrator that plans, builds, reviews, and ships work across tasks, worktrees, and models. Open source (MIT).
- [Symphony](https://github.com/openai/symphony) - OpenAI's service that watches a project board, starts an isolated agent run for each task, and returns proof of work such as CI status and review feedback. Open source (Apache-2.0).
- [Warp Factories](https://docs.warp.dev/factories/) - Warp's framework for defining factories as code, moving requests through triage, specification, implementation, and review agents on its cloud platform. Proprietary.

## Coding agents

The workers on the line, and the official ways to run them headless in CI.

- [Awesome Coding Agents](https://github.com/ahmadyan/awesome-coding-agents#readme) - Companion list of about 60 terminal coding agents, with makers, licenses, and install commands.
- [Claude Code Action](https://github.com/anthropics/claude-code-action) - Anthropic's GitHub Action that runs Claude Code on pull requests and issues, triggered by mentions, assignments, or explicit prompts. Open source (MIT).
- [Codex GitHub Action](https://github.com/openai/codex-action) - OpenAI's action for running `codex exec` in a workflow with restricted privileges and a proxied API key. Open source (Apache-2.0).
- [GitHub Agentic Workflows](https://github.com/github/gh-aw) - GitHub's way to write repository automations in Markdown that run coding agents inside GitHub Actions with guardrails. Open source (MIT).
- [run-gemini-cli](https://github.com/google-github-actions/run-gemini-cli) - Google's GitHub Action for running Gemini CLI on issues and pull requests. Open source (Apache-2.0).

## Isolation and sandboxes

Somewhere for each task to run without touching the others.

- [Cloudflare Sandboxes](https://developers.cloudflare.com/sandbox/) - Runs untrusted or generated code in Linux virtual machines or isolated Workers on Cloudflare. Proprietary.
- [Container Use](https://github.com/dagger/container-use) - Dagger's tool that gives each coding agent its own containerized environment and Git branch so several can work at once. Open source (Apache-2.0).
- [Daytona](https://www.daytona.io) - Sandbox infrastructure for running AI-generated code. Its open-source repository was archived in 2026 when development moved to a private codebase. Proprietary.
- [Docker Sandboxes](https://docs.docker.com/ai/sandboxes/) - Isolated environments for running coding agents on your machine or on Docker's cloud, managed with the `sbx` CLI. Proprietary.
- [E2B](https://e2b.dev) - Cloud sandboxes where agents can run code, browse, pause, and fork, hosted by E2B or in your own cloud account. Open source (Apache-2.0).
- [Fly.io Sprites](https://fly.io/sprites/) - Linux computers for agents, persistent or disposable, with checkpoint and restore. Proprietary.
- [Git worktrees](https://git-scm.com/docs/git-worktree) - Git's built-in way to check out several branches of one repository in separate directories, the usual first layer of isolation for parallel agents.
- [Modal Sandboxes](https://modal.com/docs/guide/sandboxes) - Secure containers on Modal for executing untrusted user or agent code. Proprietary.
- [Vercel Sandbox](https://vercel.com/docs/sandbox) - On-demand Firecracker microVMs, each with its own filesystem and network, for running agent-generated code. Proprietary.

## Issue intake

Getting work into the factory as tasks an agent can pick up.

- [Backlog.md](https://github.com/MrLesk/Backlog.md) - Task board kept as Markdown files in the repository, with a CLI and kanban view that people and agents share. Open source (MIT).
- [Beads](https://github.com/gastownhall/beads) - Distributed, graph-based issue tracker for agents, backed by Dolt, from the Gas Town project. Open source (MIT).
- [Cyrus](https://github.com/cyrusagents/cyrus) - Watches Linear, GitHub, GitLab, or Slack for issues assigned to it, opens a worktree for each, and runs Claude Code, Codex, or another agent on it. Open source (Apache-2.0).
- [Linear for Agents](https://linear.app/agents) - Linear's support for agents as workspace members that can be assigned issues and report progress. Proprietary.
- [Multica](https://github.com/multica-ai/multica) - Self-hostable board where you assign issues to agent CLIs that report progress, raise blockers, and hand work back for review. Source-available (Apache-2.0 with added conditions).
- [Spec Kit](https://github.com/github/spec-kit) - GitHub's toolkit for spec-driven development, which turns a written specification into a plan and tasks for coding agents. Open source (MIT).

## Background and cloud agents

Hosted agents that take a task, work on it remotely, and come back with a pull request.

- [Claude Code on the web](https://code.claude.com/docs/en/claude-code-on-the-web) - Anthropic's cloud sessions for Claude Code, started from a browser, phone, desktop app, or terminal, with optional automatic fixes on pull requests. Proprietary.
- [Codex Cloud](https://learn.chatgpt.com/docs/cloud) - OpenAI's hosted environment for running Codex tasks in parallel in the cloud and reviewing the results. Proprietary.
- [Cursor Cloud Agents](https://cursor.com/docs/cloud-agent) - Cursor's agents that run in remote environments and connect to GitHub, GitLab, Slack, Linear, and other tools. Proprietary.
- [Devin](https://devin.ai) - Cognition's autonomous software engineer, which runs parallel cloud sessions for engineering teams. Proprietary.
- [Factory](https://factory.com) - Factory's platform for Droids that automate coding, testing, and deployment work across the IDE, the terminal, and team tools. Proprietary.
- [GitHub Copilot cloud agent](https://docs.github.com/en/copilot/how-tos/use-copilot-agents/cloud-agent) - Copilot's agent, formerly called the coding agent, that researches a repository, plans and makes changes, and opens a pull request for review. Proprietary.
- [Jules](https://jules.google) - Google's asynchronous coding agent that works on GitHub repositories in cloud virtual machines. Proprietary.
- [Ona](https://ona.com) - Platform for running background agents in the cloud with governance and kernel-level security, formerly Gitpod. Proprietary.
- [Open SWE](https://github.com/langchain-ai/open-swe) - LangChain's software factory built on Deep Agents, which investigates, implements, validates, and opens pull requests and also reviews them. Open source (MIT).
- [OpenHands](https://github.com/OpenHands/OpenHands) - Open platform for coding agents that runs locally through Agent Canvas, on your own infrastructure, or in OpenHands Cloud. Open source (MIT).

## Review and verification

Checking the output before a person spends time on it.

- [Agent Browser](https://github.com/vercel-labs/agent-browser) - Vercel Labs' browser automation CLI built for AI agents, for example to check their own UI changes. Open source (Apache-2.0).
- [Bugbot](https://cursor.com/bugbot) - Cursor's pull-request reviewer focused on logic bugs. Proprietary.
- [Chrome DevTools MCP](https://github.com/ChromeDevTools/chrome-devtools-mcp) - Gives coding agents a live Chrome with DevTools for debugging, performance traces, and checking their changes. Open source (Apache-2.0).
- [CodeRabbit](https://www.coderabbit.ai) - Pull-request reviewer with line-by-line suggestions and chat in the review thread. Proprietary.
- [GitHub Copilot code review](https://docs.github.com/en/copilot/concepts/agents/code-review) - Copilot reviews of pull requests, with suggested fixes you can apply directly. Proprietary.
- [Graphite](https://graphite.com) - Stacked pull requests and AI code review for teams on GitHub. Proprietary.
- [Greptile](https://www.greptile.com) - Code reviewer that indexes the whole codebase to review each pull request in context. Proprietary.
- [Kodus](https://github.com/kodustech/kodus-ai) - Self-hosted AI code review that works with the model you choose. Open source core (AGPL-3.0).
- [Playwright MCP](https://github.com/microsoft/playwright-mcp) - Microsoft's MCP server that lets agents drive a real browser through Playwright. Open source (Apache-2.0).
- [PR-Agent](https://github.com/The-PR-Agent/pr-agent) - Community-maintained pull-request reviewer that runs in CI, from a webhook, or locally with your own model keys. Open source (MIT).

## Long-horizon and manager agents

Agents that supervise other agents or keep working over hours and days.

- [Gas Town](https://github.com/gastownhall/gastown) - Steve Yegge's workspace manager for running 20 or more coding agents at once, with supervising agents and a merge queue. Open source (MIT).
- [Loki Mode](https://github.com/asklokesh/loki-mode) - Autonomous software factory that takes an issue or specification and checks that what it delivers matches what was asked. Source-available (BUSL-1.1).
- [Paperclip](https://github.com/paperclipai/paperclip) - Self-hosted server and UI that organizes a team of agents around business goals, with org charts, budgets, and governance. Open source (MIT).
- [Ralph Orchestrator](https://github.com/mikeyobrien/ralph-orchestrator) - Rust framework that keeps agents looping on a task, using role-based "hats", until it is done or hits an iteration limit. Open source (MIT).
- [Ruflo](https://github.com/ruvnet/ruflo) - Multi-agent swarm framework for Claude Code, formerly Claude Flow. Open source (MIT).
- [Squad](https://github.com/bradygaster/squad) - Human-led agent teams for GitHub Copilot, with specialists such as frontend, backend, tester, and lead that live in your repository. Open source (MIT).

## Cost and observability

Knowing what the factory spends and what each agent did.

- [ccusage](https://github.com/ccusage/ccusage) - CLI that reports token usage and cost for Claude Code, Codex, and other agent CLIs from their local data. Open source (MIT).
- [Claude Code monitoring](https://code.claude.com/docs/en/monitoring-usage) - Guide to exporting Claude Code usage metrics and events over OpenTelemetry. Proprietary.
- [CodexBar](https://github.com/steipete/CodexBar) - Menu bar and Linux desktop app that shows usage limits and reset times for Codex, Claude Code, and other coding providers. Open source (MIT).
- [Helicone](https://github.com/Helicone/helicone) - AI gateway and LLM observability platform with routing, fallbacks, and cost tracking. Open source (Apache-2.0).
- [Laminar](https://github.com/lmnr-ai/lmnr) - Observability platform built for AI agents, with OpenTelemetry-native tracing. Open source (Apache-2.0).
- [Langfuse](https://github.com/langfuse/langfuse) - Tracing, evaluation, and cost tracking for LLM applications and agents. Open source core (MIT).
- [LiteLLM](https://github.com/BerriAI/litellm) - Gateway that puts many model providers behind one API, with spend tracking and budgets per key or team. Open source core (MIT).

## Related lists

- [Awesome Agentic IDEs](https://github.com/ahmadyan/awesome-agentic-ides) - Agentic IDEs, multi-agent development environments, agent terminals, and remote-control apps.
- [Awesome Coding Agents](https://github.com/ahmadyan/awesome-coding-agents) - Command-line coding agents and harnesses, with makers, licenses, and install commands.
- [Awesome Personal Agents](https://github.com/ahmadyan/awesome-personal-agents) - Always-on personal agents, memory layers, runtimes, and messaging bridges.

## Contributing

Contributions are welcome. Read the [contribution guidelines](CONTRIBUTING.md) first.

---

Maintained by [Adel Ahmadyan](https://github.com/ahmadyan), who builds [Agentastic.dev](https://www.agentastic.dev).
