# Gauntlet Goal

A portable Agent Skill that turns any concrete, non-trivial task into a ready-to-paste `/goal` objective with an inspectable quality bar, measurable acceptance criteria, and an independent builder-critic loop.

## Install

This directory is a self-contained skill package. Clone or copy it into the native skill root of the target agent:

- Codex: `~/.agents/skills/gauntlet-goal/` or `~/.codex/skills/gauntlet-goal/`
- Claude Code: `~/.claude/skills/gauntlet-goal/`
- Cursor: `~/.cursor/skills/gauntlet-goal/` or `.agents/skills/gauntlet-goal/`
- Gemini CLI: `~/.gemini/skills/gauntlet-goal/` or `.agents/skills/gauntlet-goal/`

`SKILL.md` is the portable instruction source. `agents/openai.yaml` contains Codex-specific UI and invocation metadata.

## Invoke

In Codex, invoke explicitly with `$gauntlet-goal`. The skill is explicit-only by design: it prepares the `/goal` objective and does not execute the goal itself.

## Contents

- `SKILL.md` — portable skill instructions
- `agents/openai.yaml` — Codex metadata
