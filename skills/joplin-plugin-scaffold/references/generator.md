# Generator Technical Reference

Findings checked on 2026-10-29. Recheck version-sensitive details against the selected published release; upstream `dev` may differ from npm.

## Toolchain and generator behavior

- [Official getting-started guide](https://joplinapp.org/api/get_started/plugins/): installation and starter workflow.
- [Bundled generator documentation](https://github.com/laurent22/joplin/blob/dev/packages/generator-joplin/generators/app/templates/GENERATOR_DOC.md): the checked version specifies `yo@4.3.1` and shows `yo --node-package-manager npm joplin`. This is a compatibility clue, not a permanent version pin.
- [Generator implementation](https://github.com/laurent22/joplin/blob/dev/packages/generator-joplin/generators/app/index.js): writes into its current destination without creating a project subdirectory or initializing Git. It writes `.gitignore` and may install dependencies itself. It has no custom nonempty-directory rejection; actual path collisions still matter.

The inspected generator prompts for plugin ID, display name, description, author, repository, homepage, and npm package name. Its `silent` option does not bypass new-project metadata prompts. If automated interaction is unreliable, inspect the installed generator and use an interactive session rather than guessing a stream of answers.

Generator documentation has differed on artifact locations. The selected release's generated scripts and actual output determine the paths.

## Metadata constraints and sources

- [Plugin ID validator](https://github.com/laurent22/joplin/blob/dev/packages/lib/services/plugins/utils/validatePluginId.ts): new IDs require 16–256 characters, using only letters, digits, `.`, `_`, and `-`, with alphanumeric endpoints. Validate the whole ID: `joplin.plugin.a` is too short even though its suffix is nonempty.
- [Generator package-name derivation](https://github.com/laurent22/joplin/blob/dev/packages/generator-joplin/generators/app/utils.js): the suggested npm name comes from the display name, not the plugin ID.
- [Official publishing requirements](https://github.com/laurent22/joplin/blob/dev/packages/generator-joplin/generators/app/templates/GENERATOR_DOC.md#publishing-the-plugin): source for automatic repository-inclusion conditions and the `.jpl` / `.json` publishing artifacts.
- [Manifest reference](https://joplinapp.org/help/api/references/plugin_manifest/): field schema, platforms, minimum versions, categories, and screenshots.

## Directory search behavior

The deployed [directory search implementation](https://joplinapp.org/plugins/bundle-components.js), checked on the date above, searches display name, description, and author, with an exact-ID match too. Npm package naming or README text does not substitute for a useful description. This observation concerns the website, not every Joplin search surface; recheck before depending on implementation details.
