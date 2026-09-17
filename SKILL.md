---
name: gauntlet-goal
description: Generates a ready-to-paste Codex /goal objective that applies the Gauntlet Loop to a concrete task. Use only when the user explicitly invokes this skill to formulate a long-running, multi-agent goal with an external quality bar, builder-critic loops, orchestration, and verifiable completion criteria.
---

# Gauntlet Goal

Turn the user's task into one self-contained objective for Codex `/goal`. Generate the goal only. Do not start the goal, create agents, or perform the task.

Follow the method in [How to Run a Gauntlet Loop](https://somethingbig.ai/gauntlet-loop). Preserve the user's scope, constraints, authorization boundaries, and requested deliverable.

## Prepare the goal

1. Extract the intended outcome, actual artifact, scope, constraints, available evidence, and hard acceptance criteria.
2. Choose a concrete quality bar the future critics can inspect. Prefer, in order:
   - a user-supplied reference artifact;
   - an authoritative real-world exemplar;
   - a measurable target, test suite, benchmark, rubric, or reference implementation.
3. If no defensible bar is available, make discovery and justification of the bar the orchestrator's first task. Never replace it with adjectives such as "excellent" or "production-ready."
4. Ask one concise question only when a missing fact would materially change the outcome or authorization. Otherwise state the smallest necessary assumption inside the generated goal.
5. Write in the user's language unless they request another language.

## Required operating model

The generated goal must direct one lead orchestrator to:

- own the outcome and inspect the actual working environment;
- choose the implementation approach instead of following a prescribed architecture;
- decompose the work into the smallest important units that can be built and judged independently;
- decide which units can run in parallel without unsafe shared-state conflicts;
- assign each important unit to a builder and a separate critic;
- give each critic fresh context containing the goal, quality bar, relevant rules, and real artifact, but not the builder's reasoning or self-assessment;
- have the critic compare the real output with the bar, using blind A/B comparison when feasible;
- when the output loses, have the critic name the single largest meaningful gap and return it to the builder for the next pass;
- repeat without a fixed round count until the unit passes, the user stops the run, or an explicit resource limit is reached;
- integrate the units and use a fresh smoothing critic after each major wave when separate improvements create inconsistencies;
- maintain a lightweight live progress artifact suited to the work, such as a page, workbench document, screenshots, test results, or an evidence ledger;
- verify the complete integrated result against the bar and acceptance criteria before claiming completion.

The builder never grades its own work. The critic inspects pixels, runtime behavior, rendered output, tests, measurements, or final prose rather than a builder-written summary.

## Completion contract

Separate three concepts in the generated goal:

- **Quality bar:** the external comparison that supplies direction and resists premature "good enough" judgments.
- **Acceptance criteria:** binary or measurable conditions that must hold for the requested outcome.
- **Stop conditions:** success, explicit user stop, stated budget or compute cap, or a genuine external blocker that the orchestrator has evidenced.

Success requires all hard acceptance criteria to pass and one fresh end-to-end critic round to find no material gap that would make the result lose against the chosen bar. If the bar is deliberately aspirational, report the remaining gap honestly instead of claiming the artifact surpassed it.

The goal must forbid arbitrary round limits and completion based only on implementation, static source, a builder summary, or partial tests. It must require evidence from the real deliverable and real target environment when applicable.

## Output contract

Return exactly one fenced plain-text block ready to paste after `/goal`. Do not add analysis, setup advice, or a second version outside the block.

Use this compact structure inside the block:

```text
Outcome
[Concrete result and artifact.]

Scope and constraints
[Boundaries, sources of truth, permissions, assumptions, and target environment.]

Quality bar
[Inspectable reference or the rule for finding and justifying one.]

Acceptance criteria
- [Observable criterion]

Gauntlet operating loop
[Lead orchestrator, decomposition, builder-critic pairs, fresh-context review of real artifacts, largest-gap feedback, continued looping, integration smoothing, and progress evidence.]

Stop conditions
[Verifiable success plus user, resource, and blocker stops.]

Final evidence
[What the orchestrator must show so completion can be independently checked.]
```

Keep the goal outcome-led. Include enough mechanics to preserve the Gauntlet Loop, but let the lead agent choose the architecture, decomposition, tools, and exact work sequence.
