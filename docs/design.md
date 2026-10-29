# Joplin Plugin Scaffolding Skill Design

Status: Agreed during the design interview on 2026-10-29.

## Outcome and scope

Create a reusable skill in this repository for new Joplin plugin projects. Existing-project repair, upgrades, and publishing operations are outside the first version's scope. Installation into personal Codex skills is a separate later decision.

Completion means a project retaining the official generator's starter code, with a project-level `AGENTS.md` and a successfully built `.jpl` artifact. Building does not establish runtime compatibility.

## Project creation

Create the plugin directory, run `git init` inside it, then run `yo joplin` in that same directory. The generator neither creates the project subdirectory nor initializes Git. Use the official generator rather than maintaining a full template.

Immediately after generation, inspect `git status --short` and stage the original generated project as a baseline after checking ignore rules. Keep subsequent metadata and README edits unstaged. Mark every later added, non-ignored file with `git add -N -- <path>` so its contents also appear in `git diff`; leave ignored files excluded. At handoff, review staged output separately from the working-tree diff, which must include both modifications and additions. Do not commit: this split makes the skill's changes relative to the generator visible.

Declare both desktop and mobile support in the manifest. Retain the official generator's starter source code and build configuration; scaffolding does not add custom commands, toolbar buttons, or feature code. Keep the generated minimum-version values unless an explicit requirement calls for a change.

## Metadata

Distinguish npm package name (`joplin-plugin-xxx`), plugin ID (`joplin.plugin.xxx`), and plugin display name. The [official publishing documentation](https://github.com/laurent22/joplin/blob/dev/packages/generator-joplin/generators/app/templates/GENERATOR_DOC.md#publishing-the-plugin) requires the npm package name to start with `joplin-plugin-` and `package.json` keywords to include `joplin-plugin` for automatic repository inclusion. Preserve and verify these generator-provided settings during scaffolding. The plugin ID prefix `joplin.plugin.` is the user's naming convention, not an official requirement.

Names and IDs may deserve discussion, but metadata deliberation must not block scaffolding. Infer reasonable initial values from the purpose, reuse explicit choices, and report the values used. Discuss alternatives when requested. Default descriptions to English and explain the purpose with natural search terms.

## Influence beyond scaffolding

Generate a project-level `AGENTS.md` that carries these requirements to subsequent developers and AI agents:

- Understand the problem a feature solves and its concrete use cases; ask the developer when unclear.
- Maintain README content from the plugin user's perspective: value, scenarios, and operation rather than accumulated implementation notes.
- Suggest screenshot subjects and placement where they clarify a feature or workflow.
- Before publishing, review display name, description, README, screenshots, categories, and identity metadata.

Scaffolding must update the initial README with the actual display name and known purpose, written for ordinary plugin users. A generic `# Joplin Plugin` heading is insufficient when project information is available. A title and a short purpose statement are enough when information is limited. Include specific scenarios or usage details only when known; retain the link to `GENERATOR_DOC.md` for technical details. Scaffolding status, branding deliberations, provisional metadata, and verification reports belong in the developer handoff rather than the README introduction.

The broader documentation requirements guide future development. Scaffolding need not produce a complete user guide, screenshots, or publication-ready metadata. Preserve useful generator documentation without turning this task into a development tutorial.

## Delivery

Skill instructions, assets, glossary, and design records are written in English. Keep the skill self-contained and automatically discoverable. Validate its structure and review realistic behavior before delivery.

## Validation performed

- The skill-creator structural validator passed.
- All Markdown files were checked for English content and resolving local links.
- An independent read-only forward check used a link-review starter request with undecided branding. It correctly proceeded with initial metadata, preserved the directory → Git → generator sequence, and carried future documentation requirements into project `AGENTS.md`.
- The review highlighted invalid short IDs; explicit ID validation was added. Its custom-example recommendation was superseded by the decision to retain the official starter code.
- This validates instructions and structure, not an executed generator installation or `.jpl` build. No generated plugin or runtime tests were performed as part of creating this skill.
- The user's first actual run at `/tmp/joplin-scaffold-test` retained the generic README and left all project files untracked. Inspection confirmed both observations. The skill was revised to require an initial README update and a staged generator baseline before post-generation edits. The revised execution flow has not yet been rerun end to end.
- Inspection of the user's next run at the same path found README prose about starter code, undecided branding, and verification status. The initial README instruction was narrowed to known user-facing information, with process context kept in the developer handoff. This revision has passed structural validation but has not yet been rerun end to end.
