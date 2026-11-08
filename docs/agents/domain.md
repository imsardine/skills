# Domain Documentation

This repository uses a single context:

- `GLOSSARY.md`: shared domain vocabulary.
- `docs/adr/`: architectural decisions, created when needed.
- `docs/skills/<skill-name>/design.md`: the relevant skill's design decisions.

Before exploring, read the glossary and any ADRs relevant to the task.
Read the relevant skill's design record when changing its behavior.
Proceed silently when optional domain documents do not exist.

Use glossary terms consistently. Surface conflicts with existing ADRs
rather than silently overriding them. Use domain-modeling when resolving
new terminology or recording a decision; create documents lazily.
