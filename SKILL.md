---
name: dev-unknown
description: Collaborative, discovery-driven development through small increments, functional verification, and hardening. Use when the user invokes dev-unknown to work through unclear requirements or assumptions together. Not a default workflow for fully understood tasks.
---

# Dev Unknown

Use working code to discover what is missing, validate assumptions, and build shared understanding. Analyze enough for the next step, not the entire solution upfront.

**Loop: small increment -> functional verification -> hardening -> next agreed increment.**

## 1. Agree on the next increment

Choose the smallest observable behavior that advances the work or resolves an uncertainty. Agree on the expected outcome and how to verify it. Size the increment by what can be meaningfully judged, not by lines or files.

For each increment, decide with the user whether functional verification will be automated or shared. Reuse agreements already made; do not ask for redundant approval.

## 2. Implement and expose assumptions

Make relevant assumptions explicit. Proceed independently on local, easily reversible implementation choices. Ask before resolving ambiguity that changes the expected behavior, scope, or solution direction. Defer questions that do not affect the current step.

Defer new unit tests to hardening. Near the relevant code, leave comments using its native syntax:

`todo: test <specific behavior and expected outcome>`

Keep existing checks enabled. Never postpone safeguards needed to run the increment safely, especially around data and external side effects.

## 3. Verify the behavior

Do not insert a new unit-test phase between implementation and functional verification.

- If the agreed functional verification is automated and conclusively passes, proceed directly to hardening.
- Otherwise, explain what to try, the expected result, and the assumptions being checked. Wait for the user's feedback before hardening.
- If verification fails, adjust the increment and verify again. If it exposes uncertainty about the requirement, discuss it rather than treating it as merely a bug.

A successful execution is not proof that the behavior is right. Never use an expectation you invented to validate an unconfirmed requirement. An unavailable or inconclusive check is not a pass.

## 4. Harden what has been confirmed

Review the code, address relevant fragility and edge cases, add unit tests and other necessary coverage, and simplify where useful. Resolve the `todo: test` comments; remove them only when covered or no longer applicable.

Run the relevant tests and existing checks to ensure hardening preserves the confirmed behavior. Avoid speculative robustness and unrelated refactoring. Surface blockers instead of silently carrying unfinished hardening into the next increment.

## 5. Continue only on an agreed step

Briefly state what was verified, what was learned, and what remains uncertain. Keep this in the conversation unless the project or user requires a persistent record.

Proceed if the next increment is already agreed and remains valid in light of what was learned. Otherwise, propose it and wait. Repeat until the agreed goal is complete.

**Pause for missing evidence or a shared decision, not as a ritual.**

For the reasoning behind this protocol, see [philosophy.md](philosophy.md). Read it only when that background is needed.
