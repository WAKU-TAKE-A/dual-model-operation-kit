# Manager Instructions

Last updated: YYYY-MM-DD

## Instruction ID

`I-0001`

Increment this ID whenever this instruction file is updated.
Do not reuse an old ID, even when the current phase or checkpoint remains the same.

## Current Phase

`<project area>`: `<phase/checkpoint name>`

## Current Status

Summarize the latest Coder report.

- Completed:
- Remaining:
- Verification:
- Notes:

## Objective Alignment

Reference: `DUAL_MODEL_OPERATION.md` / `Project Objective`

State how this instruction advances the project objective.

- `<contribution to the project objective>`

## Principle Application

Reference: `DUAL_MODEL_OPERATION.md` / `Project Principle`

State how the project principle applies to this instruction.

- `<application to the current instruction>`

## Persistent Decisions

List important active decisions that future instructions must not forget.
Copy each active item into the next version of this file.
Remove an item only after the Manager explicitly decides that it no longer applies.
Do not use this section for routine status or temporary issues.

- `<decision to preserve or None>`

## Manager Decision

State whether the previous Coder report is accepted and what happens next.

Status: `<Not Yet Reviewed | Accepted | Needs Follow-up>`

- Next phase:
- Why now:
- Non-goals:

## Instruction For Coder

Write the concrete instruction.

Example:

```text
Move <responsibility> out of <file>.
The goal is <goal>.
Do not change behavior.
```

## Scope And Boundaries

Allowed changes:

- `<file or responsibility>`

Must not change:

- `<file or behavior>`

New files allowed:

- `<new file or None>`

## Required Shape

Use this section only when a specific code or file shape is necessary.
Otherwise write `Not specified` and let the Coder follow the existing project style.

```text
<expected call shape, layout, or Not specified>
```

## Acceptance Criteria

List one to three observable conditions that must be true for Manager review.

- `<condition that must be true>`
- `<behavior that must remain unchanged>`

## Verification

Minimum verification:

```powershell
<build or test command>
```

Additional verification:

```powershell
<optional command>
```

## Optional Repository Review

Use repository review commands only when the project is already managed by Git and the commands provide useful information.
Do not create a Git repository only to run these commands.

```powershell
git diff --stat
git status --short
```

Expected repository changes:

- `<expected change or Not applicable>`

## Stop Conditions

Stop immediately and report if:

- Work requires touching files outside scope.
- A protected behavior must change.
- The current work causes a new build or test failure.

Wait for Manager approval before continuing if:

- The goal, scope, or acceptance criteria are ambiguous.
- Judgment logic must change without explicit approval.
- A temporary workaround or materially different implementation becomes necessary.
- The work grows beyond the current phase.

Continue within scope and report afterward if:

- A pre-existing build or test failure remains unchanged.
- An unrelated issue is discovered.
- Optional verification cannot be run.

## Coder Status Update Required

After work, update `CODER_STATUS.md`.

Include:

- Current Phase
- Files changed
- Acceptance criteria results
- Build/test results
- Whether work is in progress, blocked, or ready for Manager review
- Recommended next step
- Questions for Manager

## Additional Context

Add clarification only when it helps the Coder execute the current instruction.
