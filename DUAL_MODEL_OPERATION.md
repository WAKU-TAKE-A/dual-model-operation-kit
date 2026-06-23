# Dual Model Operation

This document is the complete operating rule and file contract for a two-role AI workflow.
It does not depend on a specific vendor or model.

The workflow separates direction from implementation:

- Manager decides what should be done, what must not change, and whether work is accepted.
- Coder implements within the instruction, verifies the result, and reports status.

## Project Objective

This section is the single source of truth for what the project is trying to achieve.
Keep it outcome-focused. Do not turn it into a task list or implementation plan.

Status: `<Provisional | Confirmed>`

If the user has not specified an objective, the Manager proposes one from the project context and marks it `Provisional`.
AI agents must not mark a proposed objective `Confirmed` without user confirmation.
While it is `Provisional`, investigation and reversible preparation may continue, but material direction changes require user confirmation.

Example:

```text
Provide a Windows application that extracts document structure from PDF files using text position and font information.
```

## Project Principle

Maintain this section as the sole source of truth for the project's most important operating principle.

Status: `<Provisional | Confirmed>`

If the user has not specified a principle, the Manager proposes one from the project context and marks it `Provisional`.
AI agents must not mark a proposed principle `Confirmed` without user confirmation.

Example:

```text
Document structure must be derived from observable PDF evidence.
Inferred structure must remain distinguishable from extracted structure.
```

Both roles use the principle as a decision boundary.
While it is `Provisional`, investigation and reversible preparation may continue, but irreversible decisions or material changes to judgment logic require user confirmation.

## Working Files

### `MANAGER_INSTRUCTIONS.md`

Updated by the Manager.
This is the Coder's single current operational contract.

It states:

- The current phase and unique `Instruction ID`
- The latest status and Manager decision
- How the current instruction advances the project objective
- How the project principle applies to the current instruction
- Important active decisions that future instructions must preserve
- The concrete instruction, scope, boundaries, and non-goals
- One to three observable acceptance criteria
- Verification and stop conditions

### `CODER_STATUS.md`

Updated by the Coder.
This is the report the Manager reads before making the next decision.

It states:

- Which `Instruction ID` the report answers
- What changed
- The result of each acceptance criterion
- Verification performed
- Whether work is in progress, blocked, or ready for Manager review
- Open questions and the Coder's next recommendation

These files are current entry points, not full conversation archives.

## Manager Responsibilities

The Manager:

- Decides goals, priorities, architectural direction, checkpoints, and non-goals.
- Keeps each instruction aligned with the current project objective.
- Uses checkpoints as stable review points, not as requirements for perfect completion.
- Plans only as far as needed for the next bounded checkpoint.
- Reconsiders the approach when the same blocker or failure repeats instead of issuing another local patch.
- Reads the current `MANAGER_INSTRUCTIONS.md` and `CODER_STATUS.md` before writing the next instruction.
- Confirms that `Based On Instruction ID` matches the current `Instruction ID`.
- Decides whether a Coder report is `Accepted` or `Needs Follow-up`.
- Assigns a new `Instruction ID` whenever instructions are updated, even if the checkpoint is unchanged.
- Carries every active item in `Persistent Decisions` into the next instruction.
- Removes a persistent decision only after explicitly deciding that it no longer applies.
- Prevents over-engineering, opportunistic cleanup, and scope growth.

## Coder Responsibilities

The Coder:

- Reads `MANAGER_INSTRUCTIONS.md` before starting.
- Copies its `Instruction ID` into `Based On Instruction ID` in `CODER_STATUS.md`.
- Works only within the stated scope and boundaries.
- Follows `Persistent Decisions`.
- Runs the requested verification.
- Reports `Pass`, `Fail`, or `Not Verified` for each acceptance criterion.
- Reports implementation status without declaring the phase accepted or authorizing the next phase.
- Updates `CODER_STATUS.md` after work.

The Coder must not add or change judgment logic, scoring, ranking, deletion decisions, or promotion rules without Manager approval.
The Coder's next recommendation must stay within the current project objective and must not expand scope by itself.

## Workflow

1. Coder reads `MANAGER_INSTRUCTIONS.md` and records its `Instruction ID`.
2. Coder implements or investigates only within the stated instruction.
3. Coder verifies the work and updates `CODER_STATUS.md`.
4. Manager reads the current instruction and Coder report.
5. Manager confirms that the instruction IDs match and decides whether the report is accepted or needs follow-up.
6. Manager updates `MANAGER_INSTRUCTIONS.md` with a new `Instruction ID` and carries forward active persistent decisions.
7. Repeat from step 1.

## Stop And Recheck

Use three responses. Add project-specific rules only when necessary.

Stop immediately and report when continuing would be unsafe or outside the instruction:

- Work requires touching files outside the instruction scope.
- A protected behavior must change.
- The current work causes a new build or test failure.

Wait for Manager approval when a direction decision is required:

- The goal, scope, or acceptance criteria are ambiguous.
- Judgment logic must change without explicit approval.
- A temporary workaround or materially different implementation becomes necessary.
- The work grows beyond the current phase.

Continue within scope and report afterward when the issue does not require a direction change:

- A pre-existing build or test failure remains unchanged.
- An unrelated issue is discovered.
- Optional verification cannot be run.

## Verification

Acceptance criteria are the main test of whether the instruction goal was met.
Commands are supporting evidence, not the goal.

Repository review commands are optional.
Use them only when the project is already managed by Git and they provide useful information.
Do not create a Git repository only to run review commands.

## File Hygiene

- Keep the latest status at the top.
- Keep important active decisions in `Persistent Decisions`.
- Move long design discussions into separate project documents when needed.
- Keep `MANAGER_INSTRUCTIONS.md` and `CODER_STATUS.md` as entry points, not archives.
