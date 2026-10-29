---
name: joplin-plugin-scaffold
description: Scaffold a new Joplin plugin with the official generator, desktop and mobile support, and project instructions for future development. Use for new plugin projects, rather than repairing existing plugins or publishing releases.
---

# Joplin Plugin Scaffold

Create a buildable starter and leave durable guidance for subsequent contributors. The scope is scaffolding, not implementing the planned plugin or publishing it.

## Establish initial values

Reuse the user's purpose, destination, and metadata choices. Ask only for missing information that prevents identifying the intended project or destination. Naming deliberation need not block creation: infer useful initial values, discuss alternatives when requested, and report values actually used.

Keep these identities distinct:

| Field | Meaning | Value or rule |
| --- | --- | --- |
| `package.json` → `name` | npm package identity | Required prefix: `joplin-plugin-` |
| `src/manifest.json` → `id` | Joplin plugin identity | `joplin.plugin.xxx` |
| `src/manifest.json` → `name` | User-facing display name | A readable name |

Joplin's automatic repository inclusion requires the npm package name to start with `joplin-plugin-` and `package.json` keywords to include `joplin-plugin`. Preserve and verify both settings from the generator. The plugin ID prefix `joplin.plugin.` is a naming convention rather than an official requirement. Derive a compatible suffix from the purpose, preserving explicit valid choices. Write an initial English description using concrete functional terms. Thoughtful review is needed before publication, but provisional metadata is sufficient here. Leave unknown author/repository details unset where supported rather than inventing people or URLs.

Validate the complete plugin ID against the official rules, including length: the checked implementation requires 16–256 characters, only letters, digits, `.`, `_`, `-`, and alphanumeric endpoints. For example, `joplin.plugin.a` is too short. Explain invalid explicit choices and propose a valid alternative. Explicitly supply the npm package name: the generator derives its default from the display name, not the plugin ID.

## Generate the project

Read [references/generator.md](references/generator.md) for official sources and execution caveats. Verify generator availability and toolchain compatibility; record the versions used. Prefer compatible installed or task-local tooling over changing global tools.

1. Create a new plugin directory. Inspect an existing destination first: an empty directory can be used; existing project files require resolving the destination with the user rather than overwriting them.
2. Inside the plugin directory, run `git init`.
3. From that same directory, run the official `yo joplin` generator. Supply metadata through its actual prompts; do not assume metadata CLI flags exist. Use a PTY when interaction requires it.
4. Before making post-generation edits, run `git status --short` and review the generator output and ignore rules. Keep dependencies, build artifacts, and temporary tooling excluded. Stage the original generated project with `git add -- .`, then run `git status --short` again to confirm the baseline. Leave it staged without committing.
5. Install generated project dependencies if the generator has not done so. Use its npm workflow and retain the lockfile. Surface an external blocker instead of claiming successful generation.

Retain the official generator's starter source code, TypeScript/build configuration, and minimum-version values. Set `src/manifest.json` to explicitly include `"platforms": ["desktop", "mobile"]`, and apply the chosen metadata. Update the README and add project guidance as described below; leave custom commands, toolbar buttons, and feature implementation to subsequent development. Keep all post-generation changes unstaged so the index remains the original generator baseline.

## Update the initial README

Write for ordinary plugin users. Replace the generic `# Joplin Plugin` heading with the actual display name and introduce the known purpose directly. A title and one useful sentence are enough when little else is known: for example, "A Joplin plugin for reviewing links between notes." Add scenarios or usage details only when supplied by the user or supported by implemented behavior.

Keep scaffolding details, branding deliberations, provisional metadata, and build/runtime verification reports in the developer handoff rather than the README introduction. Retain the link to `GENERATOR_DOC.md` for technical details. Let additional user documentation and screenshots grow with the project instead of filling gaps with process commentary.

## Carry requirements into future development

Copy [assets/AGENTS.md](assets/AGENTS.md) into the plugin root as `AGENTS.md`. This is an output asset for future contributors, not an expansion of the current task. Keep it standalone so a later agent does not need this skill installed. Adapt project-specific facts and explicit user preferences. Read back the result to confirm the README, mobile, identity, and publication guidance survived.

Retain useful generator documentation. The README must reflect known project information now; a complete user guide, screenshots, categories, and release metadata can follow later. Do not fabricate completed features or screenshot files to fill gaps.

## Verify and hand off

Run the generated project's build/package command (`npm run dist` in the current official workflow). Check actual output: a nonempty `.jpl` must exist, and its manifest must agree with the intended ID, display name, and desktop/mobile platforms. Inspect the archive or generated packaging output as appropriate; do not infer artifact paths from old documentation.

Review generated files for defaults conflicting with chosen metadata. Verify the npm name prefix and required package keyword, and confirm the starter source code remains as generated. Confirm the README uses the display name and known purpose, and `AGENTS.md` is present. Run applicable generated checks; avoid adding a test framework solely for an unchanged starter.

Before the final review, identify every new, non-ignored file and mark it with `git add -N -- <path>` (intent-to-add), including `AGENTS.md`. This makes additions visible in `git diff` without staging their contents. Respect ignore rules; do not force-add ignored files.

Finish with `git status --short`, `git diff --cached --stat`, and `git diff`. The staged contents show the original generator output; the working-tree diff must show all later modifications and non-ignored additions. Confirm no non-ignored new files remain absent from the diff. Check that source/build files have no unexpected changes relative to the staged baseline. Preserve this split for review; do not stage the later file contents or commit them.

Report the project path, three identity values, description, tool versions, artifact path, and checks actually performed. Summarize modifications and additions visible in the diff relative to the staged generator baseline. Distinguish build success from runtime tests. Mention that project `AGENTS.md` carries future README and publication expectations. Leave commits, remotes, publishing, and personal skill installation to their respective authorized tasks.
