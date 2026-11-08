# Joplin Plugin Scaffolding Skill Design

Status: Design agreed on 2026-10-29; refined through subsequent review.

## Purpose and document ownership

Provide a reusable skill for creating new Joplin plugin projects. Feature implementation, existing-plugin repair, upgrades, and publishing are separate tasks.

The [skill](../../../skills/joplin-plugin-scaffold/SKILL.md) owns the execution workflow and completion criteria. Its [generator reference](../../../skills/joplin-plugin-scaffold/references/generator.md) owns version-sensitive technical findings and official source links. This record explains the choices behind that workflow.

## Design decisions

### Build on the official starter

Keeping the official generator's code and build configuration avoids maintaining a competing template or introducing custom example features. Mobile belongs in the initial project scope so later development considers both platforms from the outset; declaring support and building successfully do not establish runtime compatibility.

### Continue in the project's working directory

Scaffolding normally follows a design discussion in the same directory. Existing documents are context to preserve and integrate, regardless of which tool produced them. Keeping the skill's location independent of the project supports that continuity without requiring a particular interview skill.

### Make the agent's changes reviewable

A clean Git starting point prevents earlier work from being confused with scaffolding changes. The user retains control of committing or stashing that earlier work. A separate generator baseline then makes the agent's subsequent integration edits visible, including added files. The workflow stops short of committing so the developer can review that distinction.

### Use initial metadata without blocking on branding

Names and descriptions deserve thought, but settling branding is not a prerequisite for creating the project. The default plugin ID convention is a preference; official package-discovery requirements still apply. English descriptions are the default for a broadly understandable directory listing. Functional wording matters because the directory searches names and descriptions.

### Serve users now and contributors later

The initial README should say what is known about the plugin's purpose, without turning into a report about scaffolding or naming deliberations. A short introduction is enough when information is limited.

Project-level agent guidance carries documentation and publication expectations into future development. The [output template](../../../skills/joplin-plugin-scaffold/assets/AGENTS.md) owns those instructions. Integrating it into existing guidance preserves decisions that preceded scaffolding and lets future agents work without this skill installed.

## Delivery choices

Keep skill instructions and project documentation in English, and retain normal automatic skill discovery. This repository is the maintained source; installing a personal copy is a separate action.

## Validation performed

- The skill-creator structural validator passed.
- All Markdown files were checked for English content and resolving local links.
- An independent read-only forward check used a link-review starter request with undecided branding. It correctly proceeded with initial metadata, preserved the directory → Git → generator sequence, and carried future documentation requirements into project `AGENTS.md`.
- The review highlighted invalid short IDs; explicit ID validation was added. Its custom-example recommendation was superseded by the decision to retain the official starter code.
- This validates instructions and structure, not an executed generator installation or `.jpl` build. No generated plugin or runtime tests were performed as part of creating this skill.
- The user's first actual run at `/tmp/joplin-scaffold-test` retained the generic README and left all project files untracked. Inspection confirmed both observations. The skill was revised to require an initial README update and a staged generator baseline before post-generation edits. The revised execution flow has not yet been rerun end to end.
- Inspection of the user's next run at the same path found README prose about starter code, undecided branding, and verification status. The initial README instruction was narrowed to known user-facing information, with process context kept in the developer handoff. This revision has passed structural validation but has not yet been rerun end to end.
