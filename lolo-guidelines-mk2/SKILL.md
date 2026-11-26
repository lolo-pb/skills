---
name: lolo-guidelines-mk2
description: "Use when writing, editing, reviewing, or refactoring code to follow Lolo's general agent workflow: state assumptions, surface ambiguity, prefer simple scoped implementations, avoid speculative abstractions, make surgical changes, and verify work against clear success criteria."
---

## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

When your changes create orphans:
- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

## 5. Layers, ownership and responsibility

This aplies mainly when creating new files and when deciding where new code goes

New file names should be very clear on what they do and what they hold
Each file should hold responsibility and ownerchip of the things they declare, that doesn't only mean that it has to free them, it also means if a data structure is defined somewhere it shouldnt be used freely evrywhere else unless it was specificaly meant to be, it should be clearly handed off to different modules using its parameters, or the structure definition should move up in the file structure. this aplies unless otherwise specified.

Ambiguities should be consulted with the user.

## 6. Preferences

whenever you reference code explicitly say where the code is, file and line.

Do not add, commit or push anything with git unless explicitly asked to.

---

**These guidelines are working if:** fewer unnecessary changes in diffs, fewer rewrites due to overcomplication, and clarifying questions come before implementation rather than after mistakes.
