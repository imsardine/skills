# Learn English from notes: Design

## Purpose and source

Turn marked English words, expressions, and sentence patterns in a Markdown note into contextual American English explanations and Chinese-to-English review exercises. Explanations and translations use Taiwan Traditional Chinese.

The [original prompt](source-prompt.md) is archived verbatim for comparison with the skill. It records the historical input; the [skill](../../../skills/learn-english-from-notes/SKILL.md) owns the current execution rules.

Unlike conversation review or scenario dialogue practice, this workflow annotates an existing note and maintains its vocabulary practice section.

## Confirmed decisions

- Run when asked to process a note. Answer questions about the workflow normally.
- Treat markers inside inline code and fenced code blocks as literal content. Preserve them without processing.
- Preserve contextual normalization, source text, concise HTML comments, the prescribed practice format, follow-up synchronization, and repeat-run maintenance.
- Use `[[ ... ]]` for learning targets and `{{ ... }}` for supplementary thoughts and questions. Call `<!-- ... -->` an **HTML comment** consistently.
- Process `{{ ... }}` only when it relates to English learning and appears in a supported location. Preserve unrelated notes and questions outside those locations.

## Target selection

Use an explicitly specified note first; otherwise use the note being discussed. Ask if the target is ambiguous or the complete contents are unavailable.

Follow available tools' instructions to read the complete note, update the original, and read back the result. Keep tool-specific mechanics in the tools' own documentation.

## Packaging and discovery

The [usage guide](usage.md) provides invocation and marker examples. Keep execution self-contained in one instruction file with UI metadata. The source archive is repository documentation, not a runtime dependency.

Use the name `learn-english-from-notes` to distinguish note annotation from open-ended tutoring and the collection's conversation-review and scenario-practice workflows. Normal skill discovery remains available for requests to process marked notes.

Repository instructions and documentation are in English. Taiwan Traditional Chinese is retained in output literals, such as the practice heading and word-choice label, because it is part of the learning format.
