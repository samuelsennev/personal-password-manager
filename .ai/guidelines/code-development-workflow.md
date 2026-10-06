# Workflow

1. Scan: map the current state
2. Brainstorming: decide the approach
3. Plan: break the work into small steps
4. Acceptance tests: define "done" in code
5. Execution: implement in slices, guided by the tests
6. Review: simplify and validate

General rule: each stage delivers a short artifact. Do not move on without it.

## 1. Scan
**Goal:** understand what already exists before proposing anything.

- Locate the files, models, Actions, routes, and tests related to the task.
- Identify the closest similar code to use as a style model.
- Query Laravel Boost (version docs, database schema, last error).
  Artifact: a list of up to 10 lines with "relevant files", "reusable code", and "constraints found".
  Exit: you can state what will be reused and what will be created.

## 2. Brainstorming
**Participants:** `architect`, `engineer`, `frontend-designer`.

- Each agent proposes one approach in up to 5 lines, with its main risk.
- Each agent critiques the others' proposals once.
- Choose the simplest approach that meets the requirements. Tie: the one that reuses the most existing code.
  Limit: 2 rounds.
  Success criteria (all must hold):
- One approach is chosen, and each discarded approach has a recorded reason.
- Ambiguous requirements became questions for the human or explicit assumptions.
- No new abstraction without at least 2 concrete uses today.
- The solution follows KISS, DRY (rule of three), and AGENTS.md.

**Artifact:** a decision in 5 to 10 lines.

## 3. Plan
**Input:** the brainstorming decision.

- Split the work into small vertical slices (each delivers testable behavior).
- For each slice: files to create or change, the test that validates it, dependencies.
- Explicitly list what is out of scope.

**Artifact:** a numbered checklist.

**Exit:** human approval. Without approval, do not implement.

## 4. Acceptance tests
**Agent:** `laravel-test-developer`.

- Write Pest feature tests that describe the final behavior of each slice.
- Run them and confirm they fail for the right reason (missing functionality, not a syntax error).

**Exit:** red tests, committed as the starting point.

## 5. Execution
**Agent:** `laravel-backend-developer` and `laravel-frontend-developer`.

For each slice in the plan:
1. Write the necessary unit tests and watch them fail.
2. Implement the minimum to make them pass.
3. Run the slice's tests, then the related suite.
4. Run Pint.
5. Commit the slice.

If an acceptance test needs to change, stop and record the reason for the human to validate.

**Limit:** after 3 failed attempts on the same slice, stop and report the error with what was already tried.

## 6. Review
**Agent:** `laravel-code-simplifier`.

- Look for redundancy, duplication, weak names, and unnecessary complexity in the diff.
- Run the full suite and static analysis.

**Exit:** green tests, minimal diff, and a 5-line summary (what changed, files, tests, pending decisions).