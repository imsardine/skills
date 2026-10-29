# Official Generator and API References

Checked on 2026-10-29. Recheck relevant sources when executing; published npm versions and the upstream development branch may differ.

## Generation

- [Getting started](https://joplinapp.org/api/get_started/plugins/): official Yeoman starter using `generator-joplin` and `yo joplin`.
- [Generator implementation](https://github.com/laurent22/joplin/blob/dev/packages/generator-joplin/generators/app/index.js): writes into the current destination; does not create a project subdirectory or initialize Git. Create the directory and initialize Git first.
- [Bundled generator documentation](https://github.com/laurent22/joplin/blob/dev/packages/generator-joplin/generators/app/templates/GENERATOR_DOC.md): currently specifies `yo@4.3.1` and shows `yo --node-package-manager npm joplin`. Verify compatibility with the chosen published generator instead of treating this as a timeless pin.

Inspect installed tool versions and the selected published release. A `dev` branch package version is not proof of the latest npm version. Prefer isolated tooling; follow environment permissions for installations.

The inspected generator prompts for plugin ID, display name, description, author, repository, homepage, and npm package name. Its `silent` option does not bypass new-project metadata prompts. Do not invent metadata flags. If automated interaction is unreliable, inspect the installed generator and use a real interactive session rather than guessing a stream of answers.

A freshly initialized `.git` does not conflict with template targets; an arbitrary nonempty directory may. The generator writes `.gitignore` and may install dependencies itself. Inspect results before repeating installation.

After generation, the skill stages the original output before making edits. This is a review baseline without a commit. Mark later non-ignored additions with `git add -N -- <path>` so `git diff` shows both modifications and new-file contents. Ignored files stay excluded. `git status` alone does not establish the baseline.

The current build workflow uses `npm run dist`. Discover artifact locations from generated scripts and actual files: documentation has differed on paths. Retain generated tooling rather than hand-building a packager.

## Metadata and repository inclusion

- [Plugin ID validator](https://github.com/laurent22/joplin/blob/dev/packages/lib/services/plugins/utils/validatePluginId.ts): check the final ID rather than just the suffix. New IDs must be 16–256 characters, use letters/digits/dots/underscores/hyphens, and have alphanumeric endpoints.
- [Generator name derivation](https://github.com/laurent22/joplin/blob/dev/packages/generator-joplin/generators/app/utils.js): npm package defaults come from the display name, not the ID.

- [Manifest reference](https://joplinapp.org/help/api/references/plugin_manifest/): platforms, minimum versions, categories, and screenshot schema.

The [official publishing requirements](https://github.com/laurent22/joplin/blob/dev/packages/generator-joplin/generators/app/templates/GENERATOR_DOC.md#publishing-the-plugin) specify that the npm package name starts with `joplin-plugin-`, `package.json` keywords include `joplin-plugin`, and `publish/` contains the built `.jpl` and `.json` files for automatic repository inclusion. The generator normally supplies these settings. Verify them during scaffolding and preserve them in subsequent development. The `joplin.plugin.` ID prefix is a separate project convention.

Keep the generator's starter source code unchanged. Scaffolding adjusts metadata, declares desktop/mobile platforms, and adds project guidance; selecting or implementing a custom cross-platform example is outside this workflow.

## Discoverability

The deployed [directory search implementation](https://joplinapp.org/plugins/bundle-components.js), checked on the date above, searches display name, description, and author, with an exact-ID match too. Npm package naming or README text does not substitute for a useful description. This observation concerns the website, not every Joplin search surface; recheck before depending on implementation details.
