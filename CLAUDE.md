# CLAUDE.md

This file provides guidance for Claude Code when working in this repository.

## Project Overview

**The Agency** is a collection of 147+ specialized AI agent personalities defined as Markdown files with YAML frontmatter. Agents are organized into divisions (engineering, design, marketing, sales, product, testing, specialized, game-development, etc.) and designed to be used with Claude Code, GitHub Copilot, Cursor, Windsurf, and other AI tools.

This is a content repository, not a traditional codebase — there is no runtime, backend, or compiled code.

## Repository Structure

- `engineering/`, `design/`, `marketing/`, `sales/`, `product/`, `project-management/`, `testing/`, `support/`, `spatial-computing/`, `specialized/`, `game-development/`, `academic/`, `paid-media/` — agent definition files (`.md`)
- `strategy/` — strategic coordination docs and playbooks
- `examples/` — multi-agent workflow examples
- `integrations/` — tool-specific integration configs (claude-code, cursor, windsurf, aider, etc.)
- `scripts/` — bash tooling (`convert.sh`, `install.sh`, `lint-agents.sh`)
- `.github/workflows/lint-agents.yml` — CI pipeline

## Agent File Format

Each agent is a Markdown file with required YAML frontmatter:

```yaml
---
name: Agent Name
description: Short description
color: hex_color
---
```

Recommended sections in the body: **Identity**, **Core Mission**, **Critical Rules**. Minimum content: 50 words.

## Commands

### Lint agents (validates structure of all agent files)

```bash
./scripts/lint-agents.sh
```

### Convert agents to tool-specific formats

```bash
./scripts/convert.sh
```

### Install agents to a local tool

```bash
./scripts/install.sh --tool claude-code
```

## CI/CD

Pull requests modifying agent files trigger `.github/workflows/lint-agents.yml`, which runs `scripts/lint-agents.sh`. It checks:

- YAML frontmatter presence and required fields (`name`, `description`, `color`)
- Recommended sections (Identity, Core Mission, Critical Rules) — warnings only
- Minimum content length (50 words)

## Conventions

- Agent filenames follow the pattern: `division-role-name.md` (e.g., `engineering-frontend-developer.md`)
- All agents are self-contained — one file per agent, no cross-file dependencies
- Contributions follow `CONTRIBUTING.md` guidelines
- Generated integration files (in `integrations/`) are gitignored — do not commit them manually
- License: MIT
