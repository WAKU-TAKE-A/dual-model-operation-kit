# Dual Model Operation

This document defines how to run a two-role AI workflow.

It does not depend on a specific vendor or model. Any combination of AI agents can use it as long as one agent acts as Manager and another acts as Coder.

## Project Principle

Write the project's most important operating principle here.

Example:

```text
This tool should provide evidence and navigation, not final judgment.
Uncertain inference must not be silently treated as fact.
```

Both Manager and Coder use this principle as a decision boundary.

## Roles

### Manager

The Manager decides direction.

Responsibilities:

- Decide goals and priorities.
- Split large work into bounded phases.
- State what must not be changed.
- Define verification and stop conditions.
- Prevent over-engineering and opportunistic scope growth.
- Read `CODER_STATUS.md` and write the next `MANAGER_INSTRUCTIONS.md`.

The Manager should answer questions such as:

- Should this be done now?
- How far should this phase go?
- What must remain unchanged?
- Does this change follow the project principle?
- What is the next checkpoint?

### Coder

The Coder implements and verifies.

Responsibilities:

- Read `MANAGER_INSTRUCTIONS.md` before starting.
- Work only inside the specified scope.
- Run the requested verification.
- Update `CODER_STATUS.md` after work.
- Stop and report when a decision is needed.

The Coder should avoid:

- Design changes outside the instruction scope.
- Adding new judgment logic without Manager approval.
- Broad opportunistic cleanup.
- Continuing after a stop condition is reached.

## Shared Rules

- Keep the project principle first.
- Split large work into checkpoints.
- Keep instructions and status in files.
- Coder updates `CODER_STATUS.md` after work.
- Manager updates `MANAGER_INSTRUCTIONS.md` after decisions.
- Changes to judgment logic, scoring, ranking, deletion decisions, or promotion rules require Manager approval.
- If the purpose becomes unclear, stop implementation and return to planning.

## Stop And Recheck

The Coder stops and reports in `CODER_STATUS.md` when:

- Work requires touching files outside the instruction scope.
- Build or tests fail.
- Implementation requires changing a protected behavior.
- A temporary workaround becomes necessary.
- Existing behavior may change.
- The work grows beyond the current phase.

## Checkpoint Discipline

A checkpoint is not perfect completion.
It means the work is stable enough for the Manager to decide the next move.

Each checkpoint should define:

- Goal
- Scope
- Non-goals
- Verification
- Stop conditions
- Next decision point
