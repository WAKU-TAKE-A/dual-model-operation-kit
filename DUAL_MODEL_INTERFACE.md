# Dual Model File Interface

This document defines the file-based interface between the Manager AI and the Coder AI.

The goal is to separate current status from next instructions.
These files are not a replacement for the full conversation history. They are a minimal handoff protocol.

## Files

### `CODER_STATUS.md`

Updated by the Coder.

Purpose:

- What has been completed
- Files changed
- Verification performed
- Current phase or checkpoint
- Whether the phase is complete
- Whether the next phase is safe to start
- Questions for the Manager

This is the file to give to the Manager when asking for the next instruction.

### `MANAGER_INSTRUCTIONS.md`

Updated by the Manager.

Purpose:

- What to do next
- What not to do
- Decision boundaries
- Priority
- Implementation scope
- Verification
- Stop conditions
- Concrete instructions for the Coder

This is the file to give to the Coder before implementation starts.

## Workflow

1. Coder reads `MANAGER_INSTRUCTIONS.md`.
2. Coder implements or investigates only within the stated scope.
3. Coder verifies the work.
4. Coder updates `CODER_STATUS.md`.
5. Manager reads `CODER_STATUS.md`.
6. Manager makes the next decision.
7. Manager updates `MANAGER_INSTRUCTIONS.md`.

## Required Sections For `MANAGER_INSTRUCTIONS.md`

- `Current Phase`
- `Current Status`
- `Basic Principle`
- `Current Decision`
- `Instruction For Coder`
- `Scope`
- `Boundaries`
- `Verification`
- `Stop Conditions`
- `Coder Status Update Required`

## Required Sections For `CODER_STATUS.md`

- `Current Phase`
- `What Changed`
- `Verification`
- `Current Result`
- `Open Questions`
- `Next Recommendation`

## Rules

- Coder reads `MANAGER_INSTRUCTIONS.md` before starting work.
- Coder updates `CODER_STATUS.md` after work.
- Manager reads `CODER_STATUS.md` before making the next decision.
- Manager updates `MANAGER_INSTRUCTIONS.md` after making a decision.
- Coder must not add judgment logic without Manager instruction.
- Manager must state the current phase or checkpoint.
- Coder must state which phase or checkpoint the result belongs to.

## Onboarding Another AI

When handing work to another AI, provide these files in this order:

1. `README.md`
2. `DUAL_MODEL_OPERATION.md`
3. `DUAL_MODEL_INTERFACE.md`
4. `MANAGER_INSTRUCTIONS.md`
5. `CODER_STATUS.md`

The Coder AI should prioritize `Boundaries` and `Stop Conditions` in `MANAGER_INSTRUCTIONS.md`.

The Manager AI should read `Current Result` and `Open Questions` in `CODER_STATUS.md` before writing the next instruction.

## File Hygiene

- Compress old information.
- Keep the latest status at the top.
- Move long design discussions into separate files.
- Keep `MANAGER_INSTRUCTIONS.md` and `CODER_STATUS.md` as entry points, not archives.
