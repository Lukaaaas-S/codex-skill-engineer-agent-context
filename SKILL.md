---
name: engineer-agent-context
description: Engineer context systems for long-running AI agents. Use when Codex needs to design or review prompt stability, context windows, file-backed memory, reference loading, task state, attention refresh, tool visibility, observation retention, or context compression policies for agent workflows.
---

# Engineer Agent Context

Use this skill to design how an agent should manage information over time. Keep active context small, stable, and task-relevant; move bulky material into files or references.

## Owned Inputs

Stable instructions, volatile task facts, long sources, logs, examples, memory needs, tool observations, failure evidence, and compression constraints.

## Owned Outputs

Context policy, active-context rules, file-backed memory plan, reference-loading policy, attention refresh rules, and failure trace retention policy.

## Shared References

- `references/shared/boundaries/agent.md`
- `references/shared/boundaries/cross-family.md`
- `references/shared/sources/source-policy.md`

## Hard Boundaries

- Own only this skill's task-triggered output.
- Use shared references instead of copying pattern logic into this skill.
- Hand off full workflow design to design-agent-workflows and code execution loops to run-coding-agent-loop.
- Read `references/source-map.md` and shared references only when provenance, boundary checks, or deeper pattern detail is needed.

## Workflow

1. Separate stable instructions from volatile task data.
2. Identify what must stay in active context: current goal, constraints, open risks, current plan, and latest evidence.
3. Move large sources, logs, and examples into files with clear paths.
4. Keep restorable pointers for removed material: file path, URL, ID, trace name, or source title.
5. Decide how the agent refreshes attention during long tasks.
6. Define what failure evidence should remain visible.
7. Specify when to reread source material before making claims.

## Decision Rules

- Keep prompt prefixes stable; put changing timestamps and task-local facts late.
- Prefer append-only observations for long-running loops.
- Use the filesystem as external context for long documents and logs.
- Preserve failed attempts when they prevent repeated errors.
- Use concise checklists to keep the current goal near the agent's attention.
- Do not compress away information unless the agent can recover it later.

## Context Policy Template

Use this structure in outputs:

- Stable prefix: enduring instructions and tool policy.
- Active state: current goal, plan, constraints, latest observations.
- External references: paths to long source files or source maps.
- Failure memory: concise list of failed attempts and why they failed.
- Refresh cadence: when the agent restates the goal or updates the plan.
- Cleanup rule: what can be removed from active context after being recorded elsewhere.

## When To Read References

- Read `references/source-map.md` for provenance.
- Read pattern cards in `references/shared/patterns/` when the task needs more detail:
  - `references/shared/patterns/stable-prefix-cache.md`
  - `references/shared/patterns/filesystem-as-context.md`
  - `references/shared/patterns/attention-recirculation.md`
  - `references/shared/patterns/failure-mode-map.md`

## Quality Bar

- The policy states what goes in active context versus files.
- Every compression is restorable or explicitly lossy.
- The agent has a mechanism to avoid drift.
- Failure evidence is neither hidden nor allowed to swamp the task.
