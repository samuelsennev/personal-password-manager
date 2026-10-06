---
name: brainstorming
description: Use at the start of a non-trivial task to compare approaches and reach a decision before planning. Runs a bounded discussion among the architect, engineer, and frontend designer agents and ends with a recorded decision.
---

# Brainstorming

## Participants
- architect
- engineer
- frontend-designer (only when the task changes a user interface)

## Flow
1. Read the Scan artifact and AGENTS.md.
2. Round 1: each participant proposes one approach in up to 5 lines, with its main risk.
3. Round 2: each participant critiques the other proposals once.
4. Decide. Maximum 2 rounds.

## Decision rule
Choose the simplest approach that meets confirmed requirements. On a tie, choose the one that reuses the most existing code.

## Exit criteria (all must hold)
- One approach is chosen, and each discarded approach has a recorded reason.
- Ambiguous requirements became questions for the human or explicit assumptions.
- No new abstraction without at least 2 concrete uses today.
- The solution follows KISS, DRY (rule of three), and AGENTS.md.

## Artifact
Save a decision of 5 to 10 lines at docs/tasks/{slug}/decision.md:
- Chosen approach
- Rejected alternatives and reasons
- Contract between backend and frontend
- Assumptions and open questions