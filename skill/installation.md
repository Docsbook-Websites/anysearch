---
title: Skill Installation — AnySearch Agent Skill
description: Download, install, and verify the AnySearch Skill package for Claude Code, OpenCode, Cursor, Windsurf, and other agent platforms.
---

# Skill Installation

AnySearch Skill is a unified search skill package for AI agent platforms. Download and place it in your agent's skill directory to get started.

<!-- widget:stepper -->

### Download & install

Download the Skill zip from GitHub, extract it, and move it to the skill directory for your platform.

| Agent platform | Skill directory |
|---|---|
| Claude Code | `~/.claude/skills/anysearch` |
| OpenCode | `~/.opencode/skills/anysearch` |
| Cursor / Windsurf | `<project>/.skills/anysearch` |
| OpenClaw | `~/.openclaw/skills/anysearch` |
| Other platforms | `<agent_skill_dir>/anysearch` |

**Tip:** OpenClaw users can install directly via `openclaw skills install anysearch` — no manual download needed.

```bash
# Download
curl -L -o anysearch-skill.zip https://github.com/anysearch-ai/anysearch-skill/archive/refs/heads/main.zip

# Extract
unzip anysearch-skill.zip

# Move to skill directory (OpenCode example — adjust path for your platform)
mv anysearch-skill ~/.opencode/skills/anysearch
```

### Set up your API key

An API key is optional but strongly recommended. Without one, all search features still work via anonymous access, but with lower rate limits and quota.

```bash
cp .env.example .env
# Edit .env and set: ANYSEARCH_API_KEY=your_api_key_here
```

```bash
# Linux / macOS
export ANYSEARCH_API_KEY=your_api_key_here

# Windows CMD
set ANYSEARCH_API_KEY=your_api_key_here

# Windows PowerShell
$env:ANYSEARCH_API_KEY="your_api_key_here"
```

**Tip:** create a free API key at [anysearch.com/console/api-keys](https://anysearch.com/console/api-keys). Priority order: CLI flag > `.env` file > environment variable > anonymous access.

### Verify installation

Detect available runtimes and run the entry test to confirm everything works.

```bash
# Check in priority order (Python > Node.js > Shell)
python --version # Requires >= 3.6, needs requests library
node --version    # Requires >= 12, no external dependencies
```

```bash
# Python
python <skill_dir>/scripts/anysearch_cli.py doc

# Node.js
node <skill_dir>/scripts/anysearch_cli.js doc

# PowerShell (Windows)
powershell -ExecutionPolicy Bypass -File <skill_dir>/scripts/anysearch_cli.ps1 doc

# Bash (Linux/macOS)
bash <skill_dir>/scripts/anysearch_cli.sh doc
```

```bash
python <skill_dir>/scripts/anysearch_cli.py search "hello world" --max_results 1
```

**Tip:** a successful JSON response from the entry test confirms the installation is working. Replace `<skill_dir>` with the actual path to your skill directory.

<!-- /widget -->

## Related

- [MCP Server](../mcp/installation.md) — Alternative integration path, no local skill directory needed
- [Authentication](../get-started/authentication.md) — API key vs. anonymous access
