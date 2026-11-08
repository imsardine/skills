---
name: learn-english-after-chat
description: Turn the current conversation into a Markdown English-learning resource with the user's original wording, detailed Traditional Chinese explanations, and natural American English alternatives. Use when the user asks to practice English using their conversation with AI.
---

# Learn English after chat

Create a standalone Markdown document from the conversation available in the current thread. The goal is to help the user understand how to express their own intentions naturally in American English.

## Select the conversation

- Follow any user-specified scope. Otherwise cover the substantive conversational turns in chronological order, including clarifications, changed decisions, review comments and relevant assistant responses. Omit skill boilerplate, tool calls and command execution details. Condense repeated acknowledgments only when no learning opportunity or context is lost.
- Preserve each selected user message verbatim, including spelling, punctuation and mistakes. Keep user messages and assistant responses distinct, including when feedback came from a review tool. Never present a paraphrase as a verbatim quotation; if an assistant turn is shortened, make clear it is an excerpt or summary. Do not invent turns or fill gaps from inference.
- Work only with conversation content actually available. If earlier content is unavailable or summarized, explicitly disclose the limitation; do not reconstruct or quote it as exact text. Do not exclude Chinese user turns silently: include them where substantive, indicate they were originally in Chinese and offer an English way to express the same intent.

## Explain and rewrite

For each user turn, immediately after the original, write a Markdown blockquote containing (1) an explanation in Traditional Chinese and (2) a natural American English version. Separate the explanation and rewrite with a blank quoted line. Use multiple quoted bullet points when the original has several meaningful differences.

Explain the specific differences between the user's wording and the suggested version: what changes, why, and when the original or an alternative is appropriate. Cover meaningful grammar, word choice, register, tone, sentence structure and shifts in emphasis; prioritize the distinctions needed to apply the lesson in a new situation. Give brief contrasting examples when they clarify usage. Explicitly distinguish incorrect or unclear language from a correct informal phrase or an equally valid stylistic choice. Do not invent grammar rules or imply a preferred alternative is mandatory. Keep the rewrite faithful to the user's intent and uncertainty, without adding decisions or politeness not implied by context. If the original is already natural, say so and offer an optional alternative rather than inventing an error.

Use assistant turns only to maintain conversational context, without English correction annotations for the assistant. Keep each assistant response in its original language, including excerpts and summaries: summarize English responses in English and Chinese responses in Chinese. Headings by topic are optional. Use this format:

```markdown
User: [user's original wording]

> [繁體中文說明，清楚指出差異及其原因；必要時分點]
>
> [natural American English version]

AI: [assistant's original wording, or clearly labeled excerpt/summary]
```

If the original turn is multiline, preserve the original line breaks. Use Markdown-safe formatting for original text that would otherwise be interpreted as a heading, blockquote or list, while retaining the `User:` / `AI:` structure.

## Deliver

Write a `.md` file. Respect the user's requested destination or naming; otherwise use a descriptive filename in the current workspace, without overwriting an existing file unintentionally. Link the finished document in the response. If the user supplies later review comments, apply them across the document wherever they express a general preference, as well as to the cited examples.
