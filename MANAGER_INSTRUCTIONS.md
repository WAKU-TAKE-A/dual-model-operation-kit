# Manager Instructions

Last updated: YYYY-MM-DD

## Current Phase

`<project area>`: `<phase/checkpoint name>`

## Current Status

Summarize the latest Coder report.

- Completed:
- Remaining:
- Verification:
- Notes:

## Basic Principle

State the project's most important principle.

Examples:

- This tool provides evidence, not final judgment.
- Uncertain inference must not be treated as fact.
- Behavior changes must be explicit.

## Current Decision

State the Manager decision for this phase.

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

## Scope

Allowed changes:

- `<file or responsibility>`

Protected areas:

- `<file or behavior>`

Candidate new files:

- `<new file>`

## Required Shape

Describe the expected code or file shape.

```text
<expected call shape or layout>
```

## Boundaries

Allowed:

- `<allowed change>`

Do not change:

- `<protected behavior>`

Explicitly forbidden:

- `<forbidden change>`

## Verification

Minimum verification:

```powershell
<build or test command>
```

Additional verification:

```powershell
<optional command>
```

## Diff Review

Check these after implementation:

```powershell
git diff --stat
git status --short
```

Expected diff:

- `<expected diff>`

## Stop Conditions

Stop and report if:

- Build or tests fail.
- Work requires touching files outside scope.
- Existing behavior must change.
- Judgment logic must change.
- A temporary workaround becomes necessary.

## Coder Status Update Required

After work, update `CODER_STATUS.md`.

Include:

- Current Phase
- Files changed
- Build/test results
- Whether the phase is complete
- Recommended next step
- Questions for Manager

## Manager Note

Add Manager-only clarification here.
Use this section to prevent ambiguity for the Coder.
