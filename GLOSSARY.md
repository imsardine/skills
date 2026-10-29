# Joplin Plugin Scaffolding

Shared language for the scaffolding skill and its generated projects.

## Language

**Scaffolding**:
A new, buildable plugin project retaining the official generator's starter code, with metadata and guidance for future contributors.

**Plugin directory**:
The root directory of a new plugin project.

**Npm package name**:
The `name` in `package.json`, identifying the npm package. Joplin's automatic repository inclusion requires it to start with `joplin-plugin-`.

**Plugin ID**:
The `id` in the plugin manifest, identifying the plugin to Joplin. The default convention here is `joplin.plugin.xxx`.

**Plugin display name**:
The `name` in the plugin manifest, presented to users.
