---
name: learn-english-from-notes
description: Create American English review exercises from marked Markdown notes, with Taiwan Traditional Chinese explanations. Use to process [[ ... ]] learning targets and {{ ... }} follow-up questions in notes.
---

# Learn English from notes

Teach natural, practical American English in context and build material for review and Chinese-to-English practice. Write explanations in Taiwan Traditional Chinese, using Taiwan vocabulary and phrasing.

## Start and select the note

Run when asked to process a note. Answer questions about the workflow normally.

Use the explicitly specified note; otherwise use the note being discussed. Ask if the target is ambiguous.

Read the complete current Markdown, including existing HTML comments and exercises. Follow the available tools' instructions for reading and editing, including pagination when needed. Ask for missing content if the complete note is unavailable; never reconstruct it.

## Recognize learning requests

Process `[[ ... ]]` learning targets and their associated `{{ ... }}` follow-ups only in the following locations:

- `[[ ... ]]` in the original text, including embedded `{{ ... }}` questions. Treat the questions separately from the English target.
- `{{ ... }}` in an HTML comment associated with an original-text learning item.
- `{{ ... }}` in explanations or dialogue examples within `## 英文字詞練習 #todo/lang`.
- `[[ ... ]]` in existing dialogue examples within that practice section, using the local-annotation rule below.

Preserve both types of marker literally in inline code and fenced code blocks. Leave `{{ ... }}` unrelated to English learning or outside these locations unanswered and unchanged. If nothing requires processing or maintenance, leave the note unchanged.

Normalize each original-text target into a reusable learning item:

- Use base-form verbs and singular nouns, except meaningful plurals.
- Preserve natural, complete collocations and fixed patterns; use context rather than mechanically stripping endings or splitting expressions.
- One marker may yield multiple independently useful items. Merge repeated instances of the same item instead of creating duplicate exercises.
- Explain the meaning used in the original context first.

Examples: `[[ran into]]` becomes `run into`; `[[dependencies]]` becomes `dependency`; `[[two orders of magnitude {{ 跟 order（順序）有什麼關係？ }}]]` becomes `orders of magnitude`. A marked `stealth` may yield `in stealth` when that is the contextual expression.

## Annotate the original text

Remove processed `[[` and `]]`, retaining the enclosed original English exactly. Transfer embedded follow-up questions into the item's teaching content and remove their processed `{{ ... }}` from the original.

At the end of each affected original paragraph, group one HTML comment per learning item in that paragraph's first-occurrence order. Reuse the item's existing comment in that paragraph. Place comments outside existing Markdown syntax ranges so links, emphasis, lists, tables, and extended syntax remain valid. Preserve all other original wording, punctuation, capitalization, whitespace, order, and Markdown structure.

Use this HTML comment format in the original text and practice examples:

```text
<!-- 字詞: /美式 IPA/ 所在情境中的意思與用法 -->
```

For example:

```markdown
The team has been working in stealth for two years.<!-- in stealth: /ɪn stɛlθ/ 低調保密地進行；此處表示團隊尚未公開專案，持續私下開發 -->
```

Keep comments concise and contextual; put detailed comparisons in the practice section. Use common American IPA in comments and exercises. Verify uncertain pronunciation with a reliable pronunciation source when available; mark unavailable IPA rather than inventing it.

## Maintain the practice section

Maintain exactly one `## 英文字詞練習 #todo/lang` section at the end of the note. Each normalized learning item has one subsection. Order subsections strictly by the item's first appearance in the original text, including previously processed occurrences. New items belong in that order rather than automatically at the end. Select the most informative source occurrence for the quotation when an item occurs repeatedly.

Follow this structure with one blank line between items and no additional teaching headings. Replace placeholders with actual content; use as many examples as needed.

```markdown
## 英文字詞練習 #todo/lang

### [normalized expression]
/[American IPA]/

> [Complete original sentence with the **target expression**, preserving inline code.] [Natural Taiwan Traditional Chinese translation.]

**用字遣詞（word choice）**：[Contextual meaning, collocations, useful comparisons, and answers to follow-up questions; bold the target and explicitly compared English expressions.]

1. A: [English line with **learning expressions**.] B: [English reply.] A：[Chinese translation.] B：[Chinese translation.]
2. A: [Another independent English exchange if needed.] B: [English reply.] A：[Chinese translation.] B：[Chinese translation.]
```

### Original quotation and translation

Quote one complete original sentence containing the target, preserving its exact wording and actual inflection. Remove processed `[[ ... ]]` delimiters, `{{ ... }}` questions, HTML comments, and decorative Markdown such as emphasis and highlights. Strip Markdown link syntax and URLs while preserving the display text and meaningful formatting, especially inline code. Preserve technical syntax, code contents, and CSS selectors. Never shorten, paraphrase, or fabricate the sentence.

Bold the current target's actual form in the quotation. In word-choice explanations and dialogue examples, bold both the target and explicitly compared English expressions. Keep English wording and inline code syntax intact when applying bold.

For example, this source:

```markdown
We [[ran into]] an issue after updating the [`config.json`](https://example.com/config) file, so we had to ==roll back== the deployment.
```

produces this quotation under `### run into`:

```markdown
> We **ran into** an issue after updating the `config.json` file, so we had to roll back the deployment. 更新 `config.json` 檔案後，我們遇到了一個問題，因此不得不將部署回復到先前的版本。
```

Translations must be natural while preserving significant meaning, tense, number, voice, and event order. Dialogue translations also preserve participants, negation, conditions, and tone so the learner can practice translating them back into English.

### Word choice and dialogue examples

Explain the target's core meaning, tone, context, and common collocations. Compare expressions that help a learner distinguish or use it: near synonyms, confusing sentence patterns, and similar spellings or pronunciations even when their meanings differ. Explain differences in emphasis, scope, register, and interchangeability. Answer the item's follow-up questions. Select comparisons for learning value rather than padding the explanation with related words.

Use the fewest independent, natural A/B exchanges that cover every important use and explicitly compared expression at least once. Every numbered example contains both speakers' English lines followed immediately by their Taiwan Traditional Chinese translations, on the same list item. Start numbering at `1.` and continue consecutively.

Prefer varied settings from software development and collaboration, independent travel, and daily life. Each item need not cover every setting. Include useful everyday American collocations naturally, without forcing a situation to fit vocabulary. Combine teaching points when natural; add examples only to cover a remaining distinction.

## Follow-up questions and repeated runs

For each eligible `{{ ... }}` question, update its learning item consistently across original-text HTML comments, word choice, and examples wherever needed. Keep comments brief and detailed teaching in the practice section. Cover newly introduced comparisons in examples. Remove the processed question while preserving surrounding Markdown, HTML structure, and unrelated content.

For `[[ ... ]]` inside an existing practice dialogue example, remove the processed delimiters and add or update only a short HTML comment at the end of that example. Do not create a new learning subsection, example, or paragraph for this local target. Synchronize any embedded `{{ ... }}` question with the owning learning item.

On repeated runs:

- Reuse the existing practice section, item subsections, and HTML comments. Merge duplicates while retaining useful content and each paragraph's relevant comments.
- Retain correct, complete explanations and examples. Change only errors, omissions, new questions, and required formatting repairs; do not grow content merely because the skill runs again.
- Check existing quotations for intact original sentences and inflections, removal of decorative formatting, preserved technical syntax and inline code, and appropriate target bolding. Repair inline code lost when link syntax was removed, using the original text as evidence.
- Check target and comparison bolding in word-choice explanations and examples, comparison coverage, synchronization, and first-occurrence order. Preserve content unrelated to this learning task.

## Verify and deliver

Before saving, verify that all eligible `[[ ... ]]` targets and `{{ ... }}` questions were handled, the original text and Markdown remain intact, and comments and exercises agree. Check the required order, format, American IPA, translation detail, and example coverage. Leave one practice section and no duplicate items or redundant examples.

If tools support editing the target, apply the changes to the original note rather than creating a copy. Prefer precise edits that preserve unrelated text. Read back the result to verify successful changes. If direct editing is unavailable but the full note is available, output the complete modified Markdown for the user to apply.

Finish with a minimal summary in the user's language: the number of expressions processed and practice items added and updated. If existing content was adjusted, briefly give the adjustment and reason. Omit word lists, descriptions of unchanged content, and a second rendering of the note after direct editing. With the full-Markdown fallback, include the same brief summary. If an operation fails, report only what remains incomplete and why; claim only verified completion.
