# Joplin Plugin Scaffold

A coding-agent skill for creating Joplin plugin projects with the official generator, desktop and mobile platform declarations, and guidance for future contributors.

## Use the skill

Clone this repository and open it in your coding agent. Ask the agent to read the skill and create a project in a new directory, for example:

```text
Read and follow skills/joplin-plugin-scaffold/SKILL.md.

Create a Joplin plugin project in /tmp/note-link-review.
Its purpose is to help users review links between notes.
```

From another working directory, provide the absolute path to the skill's `SKILL.md` instead. Keep the entire skill folder available so the agent can read its references and copy its assets.

Project creation requires Git, Node.js, npm, and access to the official generator and package dependencies. The agent checks toolchain compatibility before generation. Provide any naming or metadata preferences with your request; otherwise it can infer initial values from the plugin's purpose.

## What you get

- An official-generator project with its starter source code and build configuration preserved.
- Explicit desktop and mobile support in the manifest.
- Project metadata and a short README using the known plugin name and purpose.
- A project `AGENTS.md` guiding later development, user documentation, screenshots, and publication review.
- A packaged `.jpl`, checked through the generated build workflow. Packaging alone does not verify runtime compatibility.

The skill focuses on creating the project. Feature implementation and publishing follow separately.

## Review the changes

The original generator output is staged as a baseline without a commit. Later edits remain unstaged, and new non-ignored files use intent-to-add so their contents appear in the diff.

From the generated project directory:

```sh
git diff --cached --stat
git diff
git status --short
```

This lets you review what the agent changed or added after generation.

## Test and contribute

Test scaffolding in a fresh agent session with a new destination directory. Check the generated README, metadata, unchanged starter code, Git diff, and build artifact. Then open a separate session in the generated project to check whether its `AGENTS.md` guides subsequent development.

Report issues with this skill in the [upstream issue tracker](https://github.com/imsardine/skill-joplin-plugin/issues). Fork maintainers can track their own work in their fork's Issues; the repository guidance resolves that target from Git remotes.

For maintenance, see the [design record](docs/design.md), [glossary](GLOSSARY.md), and repository [agent guidance](AGENTS.md).
