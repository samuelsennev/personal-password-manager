---
name: laravel-engineering
description: Use when evaluating how to implement a change in Laravel - feasibility, impact, test strategy, and risks. Applies during brainstorming and planning, before code is written.
---

# Code Engineering

## Process
1. Inspect similar features: routes, requests, controllers, Actions, models, jobs, policies, tests.
2. Check the installed framework version, schema, and routes with Laravel Boost.
3. List what must be created, changed, and reused.
4. Define the minimum tests that prove the behavior.

## Evaluate
- Migrations and data impact, including existing rows.
- Validation and authorization.
- Queues, events, caching, and external API side effects.
- Edge cases and failure modes.
- Impact on existing behavior and existing tests.

## Rules
- Keep the diff narrow.
- Prefer native Laravel features.
- Treat acceptance tests as behavior contracts.
- State assumptions explicitly. Ask when a requirement is ambiguous.

## Output
- Recommended implementation path.
- Code to reuse.
- Required tests.
- Main technical risk.