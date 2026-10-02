# The Philosophy Behind Dev Unknown

## Why this skill exists

Development does not always begin with everything needed to reach the result. Requirements may be vague, constraints may be undiscovered, and important questions may emerge only when something actually runs. Some assumptions are difficult to identify in advance; others take more effort to uncover through analysis than through a small, concrete implementation.

Dev Unknown captures a way for a developer and an AI assistant to collaborate under those conditions. It is deliberately invoked when uncertainty is part of the work, not imposed on tasks whose requirements and implementation are already understood.

The name refers to what is still unknown during development, not to a lack of competence. The aim is to make progress while learning what the solution must be.

## The working rhythm

The starting point is the developer's established rhythm:

**Write a small piece of code -> test it functionally -> harden it -> repeat.**

The assistant should follow that rhythm rather than attempting to complete a speculative solution in one uninterrupted run. It should recognize where the developer would pause, help assess whether the behavior makes sense, consolidate what has been accepted, and then resume.

An increment is not a fixed number of functions, files, or lines. It is the smallest useful change whose behavior can be observed and judged. It should either move the solution forward or answer a question that affects the next step.

This is not a sequence of disposable prototypes with all quality work postponed until the end. Each confirmed increment is hardened before the next one begins.

## Code is also a way to learn

Analysis remains useful, but its immediate purpose is to make the next increment responsible and informative. The process should not require a complete specification before any implementation, nor should it replace thought with trial and error.

Working behavior gives the conversation something concrete to examine. It can reveal a misunderstood interaction, an unexpected constraint, or an assumption that neither collaborator could easily have articulated beforehand.

The plan must adapt to that evidence. An earlier agreement about the next step is no longer sufficient if the current increment has invalidated its assumptions.

## Similar to TDD, but not the same

The similarity to TDD is the short feedback loop. The difference is the sequence and the question being answered first.

Functional verification asks: **Does this behavior achieve what we actually want?**

Hardening asks: **Can we make the accepted behavior reliable, maintainable, and protected against regressions?**

New unit tests belong to hardening, not to an automatic phase inserted between writing the increment and trying it functionally. Writing them too early can turn an unsettled assumption into a precise, repeatable test of the wrong expectation.

This is not an argument against automated testing. Functional verification may itself be automated, and existing checks remain enabled. The distinction concerns the purpose and timing of new tests, not a blanket preference for manual execution.

## Remember deferred tests without interrupting discovery

While implementing, the assistant may notice behaviors that deserve unit coverage later. It should preserve those observations near the relevant code:

`todo: test submitting the same request twice does not create a duplicate`

The comment names an observable behavior and its expected outcome, rather than merely saying "add tests." It is a reminder for the current increment's hardening, not a substitute for a test or permission to accumulate permanent testing debt.

When hardening, implement the relevant coverage and remove the satisfied comment. If the behavior has been discarded or changed, revise or remove the reminder accordingly.

## Autonomy should depend on evidence and agreement

The workflow is a collaboration protocol, not just an ordering of technical activities.

For each increment, the developer and assistant decide how functional verification will happen. If an automated check can conclusively verify agreed expectations, the assistant can proceed directly to hardening. Otherwise, it prepares the functional check and waits for the developer's feedback.

Automation cannot settle an ambiguous requirement merely by testing an expectation invented by the assistant. Technical success and confirmation of the intended behavior are different things.

After hardening, the assistant may continue when the next increment is already agreed and still appropriate. If not, it proposes the next step and waits.

The pause is therefore not ceremonial. It exists when evidence is missing or a shared decision is needed, while avoiding repeated permission requests for work already agreed.

## Make assumptions visible without turning work into an interview

Not every unknown requires an immediate question. The assistant can make local, reversible implementation choices while exposing assumptions that matter to the current increment.

It should stop before deciding something that changes the expected behavior, scope, or direction of the solution. Questions that do not yet affect the work can wait until there is better evidence.

This avoids both extremes: endless upfront clarification and uninterrupted autonomous coding built on hidden assumptions.

Hardening can wait until functional confirmation; precautions needed to run the code safely cannot. Learning through execution must not put data or external systems at unnecessary risk.

## What efficiency means here

Efficiency means shortening the distance between an assumption and useful feedback, limiting rework, and spending effort on behavior worth keeping. It does not mean maximizing uninterrupted code production or minimizing every interaction.

After each increment, a brief account of what was verified, what was learned, and what remains uncertain is enough to maintain shared understanding. The protocol does not require a separate planning document or a growing administrative framework.

The operational skill stays short because the essential mechanism is small: agree on an observable step, implement transparently, verify it, harden it, and continue with the knowledge gained. This document preserves the reasoning without burdening every invocation with it.
