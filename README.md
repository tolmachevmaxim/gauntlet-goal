# Gauntlet Goal

A portable Agent Skill that turns any concrete, non-trivial task into a ready-to-paste `/goal` objective with an inspectable quality bar, measurable acceptance criteria, and an independent builder-critic loop.

## Install

This directory is a self-contained skill package. Clone or copy it into the
native skill root of the target agent:

- Codex: `~/.agents/skills/gauntlet-goal/`; `~/.codex/skills/` is the legacy root.
- Claude Code: `~/.claude/skills/gauntlet-goal/`
- Cursor: `~/.cursor/skills/gauntlet-goal/` or `.agents/skills/gauntlet-goal/`
- Gemini CLI: `~/.gemini/skills/gauntlet-goal/` or `.agents/skills/gauntlet-goal/`
- Antigravity IDE: `~/.gemini/antigravity/skills/gauntlet-goal/` or workspace `.agents/skills/gauntlet-goal/`
- ZCode: `~/.zcode/skills/gauntlet-goal/`
- Devin: commit it to `.agents/skills/gauntlet-goal/` in the repository.

`SKILL.md` is the portable instruction source. `agents/openai.yaml` contains Codex-specific UI and invocation metadata.

Grok and Perplexity use product-managed Skill libraries. Aider uses explicit
Markdown conventions or a selected `--read` file, so neither product discovers
this folder automatically.

## Invoke

In Codex, invoke explicitly with `$gauntlet-goal`. The skill is explicit-only by design: it prepares the `/goal` objective and does not execute the goal itself.

## Contents

- `SKILL.md` — portable skill instructions
- `agents/openai.yaml` — Codex metadata
