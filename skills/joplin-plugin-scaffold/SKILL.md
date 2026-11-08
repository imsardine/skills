---
name: joplin-plugin-scaffold
description: Scaffold a new Joplin plugin with the official generator, desktop and mobile support, and project instructions for future development. Use for new plugin projects, rather than repairing existing plugins or publishing releases.
---

# Joplin Plugin Scaffold

Create a buildable starter and leave durable guidance for subsequent contributors. The scope is scaffolding, not implementing the planned plugin or publishing it.

## Establish initial values

Use the current working directory as the plugin root unless the user explicitly specifies another destination. Read the skill from its installed or external location while performing project work in the plugin root. Create or switch project directories only when explicitly requested.

Reuse the user's purpose and metadata choices. Ask only for missing information that prevents identifying the intended project. Naming deliberation need not block creation: infer useful initial values, discuss alternatives when requested, and report values actually used.

The plugin directory may already contain planning artifacts from a design interview. Read applicable agent instructions and relevant glossary, design records, ADRs, specs, or tickets before inferring values. Carry settled decisions into the scaffold without repeating the interview. Preserve these files and their links in the same directory.

Read [references/generator.md](references/generator.md) before validating metadata or selecting the generator toolchain. It records the ID constraints, generator behavior, compatibility caveats, and official sources to verify.

Keep these identities distinct:

| Field | Meaning | Example |
| --- | --- | --- |
| `package.json` → `name` | npm package identity | `joplin-plugin-xxx` |
| `src/manifest.json` → `id` | Joplin plugin identity | `joplin.plugin.xxx` |
| `src/manifest.json` → `name` | User-facing display name | A readable name |

Joplin's automatic repository inclusion requires the npm package name to start with `joplin-plugin-` and `package.json` keywords to include `joplin-plugin`. Preserve and verify both settings from the generator. The plugin ID prefix `joplin.plugin.` is a naming convention rather than an official requirement. Derive a compatible suffix from the purpose, preserving explicit valid choices. Write an initial English description using concrete functional terms. Thoughtful review is needed before publication, but provisional metadata is sufficient here. Leave unknown author/repository details unset where supported rather than inventing people or URLs.

Validate the complete plugin ID against the referenced official constraints. Explain invalid explicit choices and propose a valid alternative. Explicitly supply the npm package name rather than assuming the generator's suggested value matches the chosen identity.

## Generate the project

Verify generator availability and toolchain compatibility; record the versions used. Prefer compatible installed or task-local tooling over changing global tools.

1. Inspect the plugin root's contents, using the current working directory by default. Planning documents from any tool or workflow are a supported starting point. Identify overlapping generator paths before generation. Preserve existing README, agent instructions, and `.gitignore` patterns; integrate compatible content after generation. Resolve contradictory requirements with the user. Existing plugin source/build files may indicate an existing-project task outside this skill's scope.
2. Inside the plugin directory, run `git init` if it does not already have its own repository. Preserve its history and remotes. Require `git status --short --untracked-files=all` to be empty before generation. If it lists staged, unstaged, or untracked files, ask the user to commit or stash their work and wait for a clean status. Mention that a stash must include untracked files when applicable. Leave this cleanup to the user; do not stage, commit, stash, or discard pre-existing work. An empty new repository satisfies this check.
3. From that same directory, run the official `yo joplin` generator. Supply metadata through its actual prompts; do not assume metadata CLI flags exist. Use a PTY when interaction requires it. Keep pre-existing files at conflict prompts rather than force-overwriting them; incorporate any needed generator settings during subsequent integration.
4. Before making post-generation edits, run `git status --short` and review the generator output and `.gitignore` patterns. Keep dependencies, build artifacts, and temporary tooling excluded. Stage the original generator output with `git add -- .`, then run `git status --short` again to confirm the baseline. Pre-existing committed planning documents remain unchanged. Leave the generator baseline staged without committing.
5. Install generated project dependencies if the generator has not done so. Use its npm workflow and retain the lockfile. Surface an external blocker instead of claiming successful generation.

Retain the official generator's starter source code, TypeScript/build configuration, and minimum-version values. Set `src/manifest.json` to explicitly include `"platforms": ["desktop", "mobile"]`, and apply the chosen metadata. Update the README and add project guidance as described below; leave custom commands, toolbar buttons, and feature implementation to subsequent development. Keep all post-generation changes unstaged so the index remains the original generator baseline.

## Update the initial README

Write for ordinary plugin users. If a README already exists, integrate the known name and purpose into it while retaining useful content and links. Otherwise replace the generator's generic `# Joplin Plugin` heading with the actual display name and introduce the known purpose directly. A title and one useful sentence are enough when little else is known: for example, "A Joplin plugin for reviewing links between notes." Add scenarios or usage details only when supplied by the user or supported by implemented behavior.

Keep scaffolding details, branding deliberations, provisional metadata, and build/runtime verification reports in the developer handoff rather than the README introduction. Retain the link to `GENERATOR_DOC.md` for technical details. Let additional user documentation and screenshots grow with the project instead of filling gaps with process commentary.

## Carry requirements into future development

Use [assets/AGENTS.md](assets/AGENTS.md) for the plugin root's `AGENTS.md`. Create it when absent; otherwise merge the relevant guidance into the existing file, preserving project instructions and pointers to design artifacts without duplicating sections. This is an output asset for future contributors, not an expansion of the current task. Keep it standalone so a later agent does not need this skill installed. Adapt project-specific facts and explicit user preferences. Read back the result to confirm existing guidance and the README, mobile, identity, and publication requirements survived.

Retain useful generator documentation. The README must reflect known project information now; a complete user guide, screenshots, categories, and release metadata can follow later. Do not fabricate completed features or screenshot files to fill gaps.

## Verify and hand off

Run the generated project's build/package command (`npm run dist` in the current official workflow). Check actual output: a nonempty `.jpl` must exist, and its manifest must agree with the intended ID, display name, and desktop/mobile platforms. Inspect the archive or generated packaging output as appropriate; do not infer artifact paths from old documentation.

Review generated files for defaults conflicting with chosen metadata. Verify the npm name prefix and required package keyword, and confirm the starter source code remains as generated. Confirm the README uses the display name and known purpose, and `AGENTS.md` is present. Run applicable generated checks; avoid adding a test framework solely for an unchanged starter.

Before the final review, identify every new, non-ignored file and mark it with `git add -N -- <path>` (intent-to-add), including `AGENTS.md`. This makes additions visible in `git diff` without staging their contents. Respect ignore rules; do not force-add ignored files.

Finish with `git status --short`, `git diff --cached --stat`, and `git diff`. The staged diff records generator changes from the clean starting point; the working-tree diff must show all later modifications and non-ignored additions. Confirm no non-ignored new files remain absent from the diff. Check that source/build files have no unexpected changes relative to the staged baseline. Preserve this split for review; do not stage the later file contents or commit them.

Report the project path, three identity values, description, tool versions, artifact path, and checks actually performed. Summarize modifications and additions visible in the diff relative to the staged generator baseline. Distinguish build success from runtime tests. Mention that project `AGENTS.md` carries future README and publication expectations. Leave commits, remotes, publishing, and personal skill installation to their respective authorized tasks.
