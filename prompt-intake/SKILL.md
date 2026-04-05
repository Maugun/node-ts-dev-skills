---
name: prompt-intake
description: Normalize an incoming user request before acting by identifying the true goal, constraints, expected deliverable, ambiguity, and missing critical information without changing the user's intent. Use when Codex needs to understand a prompt more clearly before planning or implementation.
---

# Prompt Intake

Normalize the user's prompt before acting.

Extract the real objective.
Preserve the user's intent.
Clarify constraints and expected output.
Detect ambiguity before implementation begins.

Do not rewrite the user's intent into a different task.
Do not over-question simple requests.
Do not ask for clarification unless the missing information materially affects correct execution.

## Workflow

1. Read the prompt carefully.
2. Identify the main objective.
3. Identify explicit constraints.
4. Identify implicit constraints that are strongly suggested by context.
5. Identify the expected deliverable.
6. Check whether important ambiguity remains.
7. If needed, ask only the minimum useful clarification questions before proceeding.

## Internal Normalization

Before taking action, normalize the prompt internally into:

1. objective
2. constraints
3. assumptions
4. deliverable
5. risks or ambiguity

This normalization can stay internal.
Only expose it explicitly when it helps execution or clarification.

## When To Ask Questions

Ask the user a question only when the answer is important to correct development work.

Good reasons to ask:

1. the task is materially ambiguous
2. multiple implementation paths have different consequences
3. a missing requirement could cause the wrong solution
4. the repository does not answer a critical setup or architecture choice

Do not ask when:

1. the repository already answers the question
2. a reasonable assumption is low-risk
3. the task is simple and direct

## Question Quality Rules

When clarification is needed:

1. ask the fewest questions possible
2. ask only high-impact questions
3. keep them short and specific
4. prefer questions that unblock implementation immediately

## Common Pitfalls

- Do not paraphrase so aggressively that the original intent changes.
- Do not ask broad exploratory questions when one precise question is enough.
- Do not turn every prompt into a planning ceremony.
- Do not skip clarification when the missing information could lead to the wrong implementation.
