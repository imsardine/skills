# Joplin Plugin Scaffold

A coding-agent skill for creating Joplin plugin projects with the official generator, desktop and mobile platform declarations, and guidance for future contributors.

## Use the skill

Keep a clone of this repository wherever you store skills. Start your coding agent from the plugin project's working directory, where you may already have discussed its design. Ask the agent to read the external skill and scaffold in the current directory:

```text
Read and follow /path/to/skill-joplin-plugin/skills/joplin-plugin-scaffold/SKILL.md.

Scaffold the Joplin plugin in the current working directory.
Its purpose is to help users review links between notes.
```

Replace `/path/to/skill-joplin-plugin` with the location of your clone. Keep the entire skill folder available so the agent can read its references and copy its assets. The skill's location is independent of the plugin's working directory.

The skill reads existing planning documents in the project, reuses decisions, and integrates README and agent guidance while preserving existing content.

Project creation requires Git, Node.js, npm, and access to the official generator and package dependencies. The agent checks toolchain compatibility before generation. Provide any naming or metadata preferences with your request; otherwise it can infer initial values from the plugin's purpose.

Start with a clean Git status. Commit or stash existing work, including untracked files when applicable, before scaffolding. The agent will wait for you to handle existing changes rather than stage or stash them for you.

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

Test scaffolding in a fresh agent session whose working directory is a test plugin project. Reference the skill by its external path. Check the generated README, metadata, unchanged starter code, Git diff, and build artifact. Then open a separate session in that project to check whether its `AGENTS.md` guides subsequent development.

Report issues with this skill in the [upstream issue tracker](https://github.com/imsardine/skill-joplin-plugin/issues). Fork maintainers can track their own work in their fork's Issues; the repository guidance resolves that target from Git remotes.

For maintenance, see the [design record](docs/design.md), [glossary](GLOSSARY.md), and repository [agent guidance](AGENTS.md).
