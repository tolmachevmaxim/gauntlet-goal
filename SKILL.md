---
name: gauntlet-goal
description: Converts any concrete, non-trivial task—software, product, UI, documents, research, data, automation, or external operations—into one self-contained, ready-to-paste Codex /goal objective with an inspectable quality bar, measurable acceptance criteria, and a persistent builder-critic Gauntlet Loop. Use when the user explicitly invokes $gauntlet-goal or asks for a long-running /goal with multi-agent execution and independent quality review.
---

# Gauntlet Goal

Turn any concrete, non-trivial user task into one self-contained objective for Codex `/goal`. Generate the goal only: do not start `/goal`, create agents, or perform the underlying task.

Write the goal in the user's language unless they request another language. Preserve the user's scope, constraints, authorization boundaries, and requested deliverable. Universal means task-domain agnostic; it does not grant permission for extra side effects.

## Frame the task

Extract the intended outcome, actual artifact, target environment, scope, constraints, available evidence, permissions, and binary or measurable acceptance criteria.

Ask one concise question only when a missing fact would materially change the outcome or authorization. Otherwise state the smallest necessary assumption inside the goal and give the orchestrator a fail-closed stop if that assumption is false. Never invent a repository, account, recipient, source of truth, or permission.

## Choose the quality bar

Give future critics an external comparison in this order:

1. the user's reference artifact or explicit example;
2. an authoritative real-world exemplar or standard;
3. a measurable target, test suite, benchmark, rubric, or reference implementation.

If no defensible bar exists, make discovery and justification of one the orchestrator's first task. State what the critic will compare and how it will inspect the real result. Do not substitute adjectives such as "excellent" or "production-ready."

Use only the relevant domain adapter; do not turn the goal into a generic checklist:

- software or service: clean setup, relevant tests, runtime behavior, and operational failure paths;
- UI or visual work: rendered screens, target viewports, interaction states, accessibility, and overflow/layout checks;
- documents or content: source fidelity, audience fit, structure, editorial quality, and final rendered artifact;
- research or data: primary-source quality, reproducibility, correctness, uncertainty, and decision usefulness;
- external operations: real target state, permissions, idempotency or reversibility, and post-action read-back.

## Required operating model

The goal must direct one lead orchestrator to:

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

The builder never grades its own work. The critic inspects the real artifact: pixels, runtime behavior, rendered output, tests, measurements, external state, or final prose rather than a builder-written summary.

## Completion contract

Separate these three concepts in the generated goal:

- **Quality bar:** the external comparison that supplies direction and resists premature "good enough" judgments.
- **Acceptance criteria:** binary or measurable conditions that must hold for the requested outcome.
- **Stop conditions:** success, explicit user stop, stated budget or compute cap, or a genuine external blocker that the orchestrator has evidenced.

Success requires every hard acceptance criterion to pass and one fresh end-to-end critic round to find no material gap that would make the result lose against the chosen bar. If the bar is deliberately aspirational, report the remaining gap honestly instead of claiming the artifact surpassed it.

The goal must require evidence from the real deliverable and real target environment when applicable. It must not allow arbitrary round limits or completion based only on implementation, static source, a builder summary, or partial tests.

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
