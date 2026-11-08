# Repository Guidance

Maintain the skills in `skills/<skill-name>/` and their documentation in
`docs/skills/<skill-name>/`. The root README is the collection's catalog.
Keep each skill's execution resources self-contained in its skill folder.
Files in a skill's `assets/` directory are output templates, not instructions
for maintaining this repository.

Write skill instructions and project documentation in English.
Before changing a skill's behavior, read its design record at
`docs/skills/<skill-name>/design.md` when present. Update the root catalog
when adding a skill or changing its purpose.

## Agent skills

### Issue tracker

Use GitHub Issues for the working repository, resolving the target from the user's request or Git remotes.
See `docs/agents/issue-tracker.md`.

### Triage labels

Use the five default triage labels.
See `docs/agents/triage-labels.md`.

### Domain docs

Use the single-context glossary and ADR layout.
See `docs/agents/domain.md`.
