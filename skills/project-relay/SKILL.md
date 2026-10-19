---
name: project-relay
description: >-
  Record and read key data and algorithm changes, milestone results, and next
  steps when continuing the same project across tools such as Codex and Claude.
  Use when resuming a project, summarizing progress, or preparing a handoff.
---

# Project Relay

Help the next AI assistant understand where the project stands, which results are trustworthy, and what to do next without relying on previous chat history.

## Project record

Maintain `PROJECT_STATE.md` at the project root. If an equivalent progress document already exists, reuse it instead of creating a duplicate.

Keep the record brief and specific. Leave detailed code, data, and logs in their existing locations; include only essential explanations and paths in the record. Prefer paths relative to the project root so different tools can use them.

## When taking over

1. Read the project record to understand the goal, current method, existing results, and next step.
2. Check the data, code, and results directly relevant to that next step, without rescanning the entire history.
3. Continue from existing work. Redo only the affected parts when relevant inputs or methods have changed, results are missing, or validation has failed.
4. If the record disagrees with the actual files, explain and investigate the discrepancy. Mark anything that cannot be confirmed as "Needs verification" rather than guessing.

## When to update

Update the record only when:

- Key data, preprocessing, algorithms, or important parameters change.
- A stage with a concrete output is completed.
- A failure or blocker affects subsequent work.
- The user requests a handoff, or the current work session is about to end.

Do not log every tool call or copy the conversation into the project record.

## What to record

- **Data:** What data is used, its location, version or scope, and important processing that affects the results.
- **Algorithms:** The current method, code entry point, and key parameters. For important changes, explain what changed, why, and which results are affected.
- **Results:** Output locations, the associated data and methods, and actual validation results. Distinguish validated results, unvalidated results, and results that failed validation.
- **Next step:** Where to resume, what to do, and how to judge completion. Include commands and environment requirements when needed.

Preserve key decisions and reasons for failures that still affect subsequent work. After a method changes, identify which previous results are no longer valid or need to be recomputed.

## Project record template

Adapt the template to the project. Remove fields that do not apply; do not create extra work just to fill every field.

```markdown
# Project State

Last updated:

## Goal and current stage
- Project goal:
- Current progress:

## Current data and methods
- Data location, version, or scope:
- Key preprocessing:
- Method and code entry point:
- Important parameters:
- Run commands and required environment:

## Key changes
- Date: What changed; why; which results are affected.

## Milestone results
- Results and file locations:
- Associated data and method versions:
- Validation performed and its results:
- Parts that are unvalidated, failed validation, or need recomputation:

## Next step
- What to do next:
- Required inputs or prerequisites:
- Completion criteria:
- Current blockers or questions to resolve:
```

## When handing off

After updating the project record, briefly tell the user:

- What was completed in this session.
- Where the project record and results are located.
- Which step the next assistant should start with.

Save the information needed for handoff in project files, not only in the current conversation.
