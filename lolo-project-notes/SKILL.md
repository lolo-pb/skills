---
name: lolo-project-notes
description: Use when the user asks to read, consult, create, update, maintain, or edit project notes, especially lolo-notes.md or a compatible legacy notes file. Use when the user asks to keep project structure, architecture, repository flow, or existing project notes in mind. Do not use merely because ordinary coding work is requested.
---

Keep a `lolo-notes.md` file at the root directory describing, very generally, the overall structure and flow of the project.

## Note File Discovery

Before creating `lolo-notes.md`, check the repository root for an existing project notes file. Check at least:

1. `lolo-notes.md`
2. `lolo-agent-notes.md`
3. `LOLO.md`
4. `NOTES.md`
5. Other Markdown files with clearly similar note-oriented names

If `lolo-notes.md` exists, use it.

If only a legacy or similarly named notes file exists, use that file instead of creating a duplicate. Do not rename it automatically. In the final response, identify the file used and ask whether it should be renamed to `lolo-notes.md`.

If multiple possible legacy files exist and it is unclear which one is authoritative, ask the user which file to use before editing. In consult mode, read the most clearly relevant file and mention the ambiguity.

## Access Rules

Use the notes file selected above in two modes:

- **Consult mode**: Read the notes and keep them in mind while developing, but do not edit them.
- **Edit mode**: Create or update the notes only when the user explicitly asks to edit, update, maintain, rewrite, or take notes.

Do not create or modify the notes file during ordinary coding tasks unless the user explicitly asks for note updates.

If the notes appear stale, incomplete, or contradicted by the codebase, mention that in the final response and ask whether they should be updated.

## 1. Simplicity

**Minimum notes that describe structure.**

- Keep it short, if i have specific questions i will ask them.
- No massive unreadable text blobs. 
- If you write 200 lines and it could be 50, rewrite it.

Write as if you were talking with someone who hasnt slept for 2 week, because he hasn't.

## 2. Conceptual Structure And Flow

- Don't go into exact implementation details, keep explanations genereal and high level. 
- Explain layers and code separation.
- Explain the flow of data and users through the code.
- Explain scripts involved with running and building.
- Mention specific files if necesary.
- Mention specific folders that may have specific purpouses if necesary.

"if necesary" Refers to things that stand out from the rest of the code. Like a global helper file, a folder just for binaries or a folder just for shell scrips... etc.

## 3. Updates

When notes become stale or structure changes, replace old notes. Dont acumulate massive amounts of useless text. it must be readable and simple to understand.

## 4. Format

Use titles, code segments and simple formatting things but avoid using significant text formating because the notes might be read as simple text rather than with a nice .md reader.

To describe the flow of the program do use small graphs or arrows to simply ilustrate it.
For example:

for entities and folder structure use:
```
AirportState
├── flights
│   ├── passengers and allowances
│   ├── bag-drop state
│   ├── assigned pier
│   └── bags
├── piers
├── carts
├── active bag-drop stations
└── tracking subscriptions
```
or

For specific section flow:
```
main
  -> initialize Jolt runtime
  -> select an aircraft or use the command-line choice
  -> construct Simulation
       -> create physics world and floor
       -> create the selected drone definition
       -> create generic Drone from definition
       -> size motor command buffer from the drone
       -> create sensors and controllers
  -> initialize SDL, OpenGL, ImGui, and Renderer
  -> play the skippable startup animation
  -> run the interactive frame loop
```

And for more complex flow, layer separation and full app flow, use mermaid.js to make graphs.

## 5. Suggestions

If there is a potentially better way of structuring the project or you are not totally confident of something you wrote, add these comments at the bottom of the selected notes file and mention that you did.

---

**These guidelines are working if:** changes being made are not massive, with well structured codebases and respected over time.
