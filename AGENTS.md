<!-- tokensaver:global-instructions:start (auto-synced from %USERPROFILE%\.claude\CLAUDE.md — edit the source there, not here) -->
<!-- source: C:\Users\rsper\.claude\CLAUDE.md -->
# User Instructions

- Windows 11, PowerShell 7. Bash here is Git Bash: no python3 or node heredocs (they hang); write scripts with Write and run them. No `sed -i` or `awk` on CRLF files. Commit messages via a file and `git commit -F <file>`.
- Line endings: GitHub convention. Git stores LF; write LF, never CRLF.
- Keep always-loaded instructions small. Before adding any rule, use the `instruction-placement` skill.
- Repo rules and config override these skills.
- Default branch is `main`. Branch from it and open PRs to it, unless the repo's rules name another base.
- Submodules: when you branch or create a worktree for the superproject, branch each submodule too, with the same name, from the same base. Keep them in sync: the superproject's pointer names a commit on that submodule branch. Push submodule branches before the superproject.
- Open questions: ask them before doing any work on a task, including planning, except while implementing a plan (see below). Do not work around guesses.
- Ask every question with the AskUserQuestion form, never as typed text. One question per form entry; never bury a question in a summary.
- Ask before writing backwards-compat code (fallbacks, legacy-path handling, migration shims): ask whether to fix or add the data/code instead.
- Output terse. No trailing summaries, no recaps of what the user already saw.
- Approved plans: follow the `implement-plan` skill (saving, review, unit progress, questions, commits, archiving).
- Use Haiku subagents by default for parallel, isolated, or research work, without asking first. Escalate to sonnet only per `docs/subagent-model-selection.md`, and ask before any sonnet retry.
- Use the TokenSaver MCP (`mcp__TokenSaver__*` tools) for code work and follow its server instructions.


<!-- source: F:\source\mcp\CLAUDE.md -->
# CLAUDE.md

Orchestration/glue repo (`mcp`) over two submodules — no application source of its own:
- `DraftModel/` — rsperry79/DraftModel: Ollama-compatible router (DraftModel.Loader) + libs/chat.
- `TokenSaver/` — rsperry79/TokenSaver: TokenSaver.MCP server, AgentHelpers.* adapters, VS Code ext.

Work inside the relevant submodule when touching its code — each is its own git repo with its own
CLAUDE.md/docs. Empty submodule folder → `git submodule update --init --recursive`.

Build/run commands and orchestration-layer pitfalls live in `.claude/rules/` — path-scoped, load
on demand.

<!-- source: F:\source\mcp\TokenSaver\CLAUDE.md -->
# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

`TokenSaver.MCP` is an ASP.NET Core MCP server (net10.0) that exposes workspace indexing, code
search, context building, file editing, and Ollama calls as MCP tools to Claude and other AI
clients. Ships with a VS Code extension (`TokenSaver.VsCodeExt`) and per-agent context-formatting
adapters (`TokenSaver.AgentHelpers.*`).

This is its own git repo, usually vendored as a submodule under the `mcp` orchestration repo. Work
here, not at the parent, when touching TokenSaver code.

## Environment
Detailed guidance lives in the "Environment" sub-doc, loaded on demand.
## Architecture
Detailed guidance lives in the "Architecture" sub-doc, loaded on demand.
## Gotchas
Detailed guidance lives in the "Gotchas" sub-doc, loaded on demand.
## Versioning

Nerdbank.GitVersioning derives all versions from `version.json` + git height. No manual per-release
bumps outside `version.json`. See `docs/versioning.md`.
<!-- tokensaver:global-instructions:end -->
