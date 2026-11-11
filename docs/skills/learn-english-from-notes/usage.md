# Learn English from notes

Turn marked English in a Markdown note into contextual American English explanations and review exercises, with Taiwan Traditional Chinese translations for Chinese-to-English practice.

## Process a note

When the skill is installed, invoke it with the note you want to process:

```text
$learn-english-from-notes Process the Markdown note we are discussing.
```

You can also specify a note link or file, or supply its complete Markdown. Without a specified target, the skill uses the note being discussed in the conversation and asks if the target is ambiguous.

To use a repository checkout without installing the skill:

```text
Read and follow /path/to/skills/skills/learn-english-from-notes/SKILL.md.
Process the note at [note link or file path].
```

Replace `/path/to/skills` with the location of your clone. Ask to process a note to start the workflow; questions about the workflow are answered normally.

## Mark learning targets

Wrap unfamiliar English in `[[ ... ]]`. Add a question inside the marker with `{{ ... }}`:

```markdown
We [[ran into]] an issue after updating the [`config.json`](https://example.com/config) file.
The new version has fewer [[dependencies {{ How is this different from a prerequisite? }}]].
```

The skill preserves the original text, removes processed `[[ ... ]]` delimiters, and adds short HTML comments (`<!-- ... -->`) at paragraph ends. It maintains one `## 英文字詞練習 #todo/lang` section at the end of the note with normalized expressions, American IPA, complete original-sentence quotations, word-choice comparisons, and natural bilingual A/B exchanges. Items follow their first appearance in the original text.

Both `[[ ... ]]` and `{{ ... }}` remain literal inside inline code and fenced code blocks. Thoughts and questions in `{{ ... }}` that are unrelated to English learning or outside supported learning locations also remain untouched.

## Ask follow-up questions

Add `{{ ... }}` to an item's original-text HTML comment or to its practice explanations or dialogue examples. Invoke the skill again to synchronize the relevant explanations and examples and remove the answered question.

Marking an expression with `[[ ... ]]` inside an existing practice dialogue example adds a local HTML comment only; it does not create another practice item. Repeated runs reuse existing items and retain correct explanations and examples.

## Delivery

When editing tools are available, the skill updates the original note and returns only counts and a brief explanation of any necessary adjustments. Otherwise, with the complete note available, it returns the complete modified Markdown and the same short summary. It asks for missing content if the full note is unavailable.
