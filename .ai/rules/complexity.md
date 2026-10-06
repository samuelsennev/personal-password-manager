# Complexity budget

## Default rule

Modify an existing owner before creating a new abstraction.

A new production class is allowed only when all are true:

1. An existing class cannot own the behavior without mixing unrelated responsibilities.
2. The behavior is used by at least two independent callers now, not hypothetically.
3. The new class has one concrete domain responsibility.
4. The task explicitly authorizes the new class.

Otherwise, keep the behavior in the existing Action, Model, Policy,
FormRequest, Tool, Controller, or Vue component that already owns it.

## Forbidden by default

Do not create:
- Interfaces with one implementation.
- Abstract base classes.
- Generic services, managers, coordinators, planners, resolvers, handlers,
  factories, repositories, registries, pipelines, strategies, adapters,
  builders, command buses, event buses or workflow engines.
- New DTOs merely to wrap an array already used once.
- New database tables for temporary conversational state.
- New events/listeners for synchronous work that can stay in the Action.
- A new layer just to make code "cleaner" or "future-proof".

## Stop condition

If a task appears to require any forbidden item:
1. Stop implementation.
2. Explain the exact constraint.
3. Show the smallest alternative without it.
4. Ask for explicit approval.

## Change budget

Unless explicitly authorized:
- Touch no more than 8 production files.
- Create no more than 2 production files.
- Do not change database schema.
- Do not rename or move existing files.
- Do not refactor unrelated code.