# Contribution Guidelines

Thanks for helping keep this list accurate. Please read this page before opening a pull request.

## What belongs here

This list follows work from issue to merged pull request. An entry belongs here when it helps with one stage of that line:

- Concepts and essays that explain how teams run coding agents as a production system.
- Control planes that assign tasks to agents, run them in parallel, and bring results back for review.
- Ways to run coding agents headless or in CI. Interactive agents themselves belong in [Awesome Coding Agents](https://github.com/ahmadyan/awesome-coding-agents).
- Isolation: worktrees, containers, and sandboxes for agent tasks.
- Issue intake, background and cloud agents, review and verification, long-horizon and manager agents, and cost and observability tools.

It also has to be:

- Publicly available today, with public documentation or source code.
- Maintained: the repository is not archived, the project has not announced that it is unmaintained or shutting down, and it has shipped a commit or release in roughly the last six months. Essays are exempt from the activity rule.
- The official project, not a mirror, a rebrand of someone else's work, or a fork without meaningful changes of its own.

General LLM frameworks, prompt collections, and model benchmarks belong elsewhere.

## Entry format

Add one line to the section that fits best:

```markdown
- [Name](https://link.to/official/site-or-repo) - What it does and who makes it, in one or two plain sentences. Open source (MIT).
```

- Link to the official repository, product page, documentation, or the original essay.
- Write the description yourself. Describe what it does; leave out superlatives, rankings, pricing claims, and benchmark numbers.
- Label tools as `Open source (SPDX-ID)`, `Source-available (license name)`, or `Proprietary`. Essays skip the label and name the author or publisher.
- Add `macOS` when a tool only runs on a Mac.
- Keep entries alphabetical within the section (case-insensitive). Descriptions start with a capital letter and end with a period.

## Pull requests

- One entry per pull request. Separate pull requests are easier to review and to revert.
- Use the entry's name as the pull request title, and say in the body which stage of the factory it serves.
- Check that every link resolves and that the repository is not archived.
- Run `npx awesome-lint` before you push.

## Corrections and removals

Open an issue or a pull request when a link breaks, a project is renamed, archived, or shut down, or a description has gone stale. Removing dead entries is as useful as adding new ones.
