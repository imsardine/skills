# Joplin Plugin Contributor Guidance

## Understand the user problem

Before developing a feature, establish the problem it solves and a concrete use case. Reuse the developer's explanation; ask when motivation or scenarios are unclear rather than inventing them. Let that understanding shape implementation and documentation.

## Preserve desktop and mobile support

This project starts with both platforms declared in `src/manifest.json`. Check API availability, dependencies, and user access on both as features evolve. A successful build alone does not demonstrate runtime compatibility. Record actual tests and resolve changes to supported platforms explicitly with the developer.

## Keep identities distinct

- `package.json` → `name`: npm package identity; must start with `joplin-plugin-` for Joplin's automatic repository inclusion.
- `src/manifest.json` → `id`: Joplin plugin identity, initially following `joplin.plugin.xxx`.
- `src/manifest.json` → `name`: user-facing display name.

The plugin ID prefix is a project convention; the npm name prefix is an official repository-inclusion requirement. Preserve `joplin-plugin` in `package.json` keywords as well. Preserve the plugin ID after distribution: changing it changes the identity and plugin data location rather than simply renaming the display label. Discuss a deliberate migration with the developer when necessary.

## Maintain a user-facing README

The README is public product documentation, including presentation in the Joplin plugin directory. As features evolve, explain the problem solved, useful scenarios, operation, and relevant limitations. Describe implemented behavior accurately. Put implementation notes in developer documentation when they do not help users operate the plugin.

Introduce the plugin's known purpose directly, even if that only warrants a short paragraph. Keep scaffolding history, naming deliberations, and internal verification reports in developer handoffs. Expand the README as user-relevant information becomes available.

Ask the developer for motivation and real examples when missing. Suggest screenshots where a visual clarifies the result or a workflow step, specifying what to capture and where it should appear. Use actual screenshots of implemented behavior; keep proposed captures explicitly pending until available.

## Review before publication

When publication is requested, review these items with the developer as needed:

- Display name and description accurately convey purpose. Default descriptions to English unless the developer chooses otherwise; naturally include functional search terms. The plugin directory matches names and descriptions, so a distinctive name alone may not explain functionality.
- The README explains user value, representative use cases, and actual operation, with current limitations and helpful screenshots.
- Screenshot files or URLs exist, show current behavior, and have useful labels. Check current schema and website hosting requirements.
- Categories match actual functionality and use supported values.
- The npm package name starts with `joplin-plugin-` and `package.json` keywords include `joplin-plugin`, as required by the [official publishing documentation](https://github.com/laurent22/joplin/blob/dev/packages/generator-joplin/generators/app/templates/GENERATOR_DOC.md#publishing-the-plugin).
- Package name, plugin ID, version, platforms, minimum versions, and real repository/homepage details are deliberate and consistent with the release.

Consult the current [official manifest reference](https://joplinapp.org/help/api/references/plugin_manifest/) for category and screenshot requirements. Initial metadata and pending screenshots do not establish release readiness. These instructions guide future work; publishing, creating remotes, or uploading assets requires authorization for that task.
