---
name: laravel-architecture
description: Use when choosing or reviewing the structure of a change in a Laravel application - layers, boundaries, contracts between backend and frontend, and where new code should live. Not for writing implementation code.
---

# Code Architecture

## Process
1. Find the closest existing feature and read how it is structured.
2. Map the change onto existing layers before proposing new ones.
3. Define the contract first: routes, authorization, request fields, response or Inertia props, persistence.
4. Choose the smallest design that meets confirmed requirements.

## Rules
- Reuse existing patterns and folders from AGENTS.md.
- Create an abstraction only with 2 or more concrete uses today.
- Extract repeated code on the third occurrence.
- Controllers validate, call one Action, and return a response.
- Keep domain boundaries: code from one context does not reach into another context's internals.
- Prefer framework primitives (Form Requests, Policies, Eloquent, queues, events) over custom equivalents.
- Add a dependency only with an explicit need.

## Output
- Chosen structure and files affected.
- Contract between layers.
- Rejected alternatives, one reason each.
- Risks and open questions.