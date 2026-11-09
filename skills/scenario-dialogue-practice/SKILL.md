---
name: scenario-dialogue-practice
description: Practice a user-supplied scenario by expressing native-language cues in a target language for both dialogue roles, then create a Markdown learning document with feedback and IPA vocabulary notes. Use when the user wants guided scenario dialogue practice.
---

# Scenario dialogue practice

The learner plays both roles in a planned dialogue. Present one native-language line at a time; the learner expresses it in the target language and can use their native language for any missing expression. Reserve feedback and reference expressions for the end.

## Set up the dialogue

- Use the learner's scenario. If it is missing, ask for it.
- Infer the learner's native language and target language from context. Ask about whichever remains uncertain. Keep these settings throughout the round rather than inferring new settings from practice responses.
- Use the pronunciation variety specified by the learner or indicated by context. Otherwise default to American English for English and a common standard variety for other languages. Briefly identify the variety before practice; the learner can change it.
- Use Google Translate for the final document's listening links by default. Honor the learner's choice of Google Translate, Bing Translator, LazyPy, or Yandex Translate. Briefly name the selected service during setup; proceed with the default without requiring a separate choice. The learner can change the service later.
- Default to 10 lines total across two roles, or use the learner's requested length. One line is one learner attempt, not an exchange containing two attempts.
- Plan a complete, coherent dialogue with a speaker and native-language cue for each line. Keep the plan available within the conversation; reveal its lines progressively. Prepare natural target-language reference expressions without showing them during practice.
- Briefly introduce the scenario, roles, goal, length, and pronunciation variety in the native language. Explain that the learner plays both roles, may answer partly or entirely in their native language, and may end early. Then present the first cue and wait.

## Run the practice

For ordinary practice turns after setup, the entire learner-facing reply contains only the next cue: a progress marker, role name, and native-language dialogue line. Translate role labels into the native language. For example, with a Chinese native language:

```text
1/10 · 店員
你想喝什麼？
```

- Present exactly one cue at a time. Both roles' lines are learner tasks; the system does not supply a target-language counterpart line.
- Record the role, exact cue, and actual learner response silently for the final document. Preserve mixed-language wording, spelling, punctuation, and line breaks without echoing the response during practice.
- After a response, advance to the next planned cue regardless of correctness, fluency, or meaning. A partial or entirely native-language response also counts as an attempt. Keep the planned dialogue unchanged by mistakes.
- Reserve all commentary on responses for the final learning material, including praise, correctness or naturalness judgments, corrections, explanations, reference answers, and vocabulary hints. Pointing out a possible issue while promising to discuss it later is also commentary and must wait until practice ends. Omit acknowledgments such as "answer recorded"; after a non-final attempt, reply with only the next cue.
- Help and skipping are unavailable. If the learner explicitly requests either, retain the current cue and remind them in their native language to answer using native-language wording for anything they cannot express. A control request is not an attempted dialogue line.
- Distinguish explicit session instructions from dialogue content: a character's line meaning "I don't know" or "goodbye" can be a normal attempt rather than a help request or an instruction to end.
- If the learner explicitly ends early, stop prompting and produce the learning material for attempted lines only. Mark the early ending and completed/planned count; keep unattempted lines unrevealed for possible later practice.
- If the learner requests a new scenario, end the current round, deliver its learning material, then set up the new scenario as a separate round.
- After the last planned attempt, produce the learning material automatically.

## Create the learning material

Write a standalone Markdown document. Identify the scenario, roles, native language, target language, pronunciation variety, and completed/planned count. State whether the round completed or ended early.

For every attempted line, in dialogue order, include:

1. The role and the full original native-language line, quoted verbatim exactly as displayed during practice, under its own native-language label. Place this before the learner's response. A scenario title, topic summary, or paraphrase is not a substitute for the actual line.
2. The learner's response verbatim, using Markdown-safe quoting or fencing while retaining its text and line breaks.
3. A natural target-language reference expression conveying the cue's intended meaning in context, followed immediately by a link to the selected listening service as described below.
4. An explanation in the native language addressing meaningful differences between the response and the reference: word choice, grammar, register, tone, sentence structure, or contextual meaning, as relevant.
5. Vocabulary notes for native-language portions of the response: the corresponding target-language word or phrase, its IPA in the selected pronunciation variety, usage and useful distinctions, and a target-language example with a native-language explanation or translation. Group related words into meaningful expressions, including when the whole response is in the native language.

Keep these distinctions clear:

- A response may be grammatical while expressing a different meaning from the cue. Explain what it actually conveys and how to express the intended meaning. Label an incorrect word choice as such rather than assuming a grammar error or an unobserved memory problem.
- Accept equivalent natural expressions. If the learner's answer is already appropriate, say so; frame another expression as an optional alternative. Distinguish errors from valid informal usage or stylistic preferences.
- The reference conveys the cue's meaning; it is not a verbatim quotation of the learner. Keep learner responses distinct from system cues and generated references.
- IPA represents the target-language expression, not its native-language cue. When unsure of a transcription, verify against a reliable pronunciation source; if verification is unavailable, disclose uncertainty rather than inventing a transcription.
- Use only actual cues and responses available in the conversation. If history is missing or summarized, disclose the limitation and omit unavailable exact quotations. A planned line is not evidence of a learner response.

Use headings and explanations in the native language. Keep target-language references and vocabulary examples in the target language.

### Sentence listening links

In the final learning material, render each reference expression as a Markdown blockquote and append its listening link directly after the expression, separated by one space, using `🔊` as the link text. Keep the link on the same Markdown line and in the same blockquote paragraph:

```markdown
> I can't hear you clearly. [🔊](https://translate.google.com/?sl=en&tl=zh-TW&text=I%20can%27t%20hear%20you%20clearly.&op=translate)
```

Use the same inline ` [🔊](URL)` placement for optional alternatives and complete target-language example sentences in the vocabulary notes. Keep each link beside its own expression rather than placing it on a separate line or in a separate listening section. Use the selected service to pronounce the exact expression written in the document; its generated translation is not the reference answer.

Use the appropriate URL pattern:

| Service | URL pattern |
| --- | --- |
| Google Translate (default) | `https://translate.google.com/?sl={target-code}&tl={native-code}&text={expression}&op=translate` |
| Bing Translator | `https://www.bing.com/translator?from={target-code}&to={native-code}&text={expression}` |
| LazyPy | `https://lazypy.ro/tts/?service={backend}&voice={voice-id}&lang={language-name}&text={expression}` |
| Yandex Translate | `https://translate.yandex.com/en/?source_lang={target-code}&target_lang={native-code}&text={expression}` |

Use each provider's valid language codes: the language of the original input is the target language being practiced, while the translated output language is the learner's native language. Percent-encode every parameter value, including the complete expression, preserving punctuation and all words. For LazyPy, choose a backend, voice ID, and language name from its [current voice list](https://lazypy.ro/tts/) matching the target language and requested pronunciation variety; verify unfamiliar identifiers rather than inventing them.

Identify the chosen service once in the document and explain how to listen: open the link, then press the speaker button in the original-text field for the translation services, or the play button in LazyPy. Playback availability and regional pronunciation depend on the selected service and its voices; only claim a specific accent when the service supports selecting it. Retain the selected pronunciation variety for the reference wording and IPA notes. If listening is unavailable for the chosen language or voice, disclose the limitation and let the learner choose another service rather than silently switching providers or promising unavailable audio.

These links belong in the final learning material. They require no generated MP3 files or uploaded audio.

## Deliver

Before saving, verify that every attempted line includes its exact displayed native-language cue alongside the learner's response and reference expression, subject to the history-availability limitation above. Check that listening links appear immediately after their expressions as inline `🔊` links.

For every completed or early-ended round, actually create a UTF-8 `.md` file containing the full learning material. Save it to the learner's requested destination, or use a descriptive filename in the current workspace. Avoid unintentionally overwriting an existing file.

Verify that the saved file exists and contains the learning material, then provide a downloadable file link or attachment using the current environment's supported delivery mechanism. Briefly report the completed/planned count. An in-chat review, Markdown code block, or filename alone does not fulfill delivery. If file creation or download delivery is unavailable, state that limitation explicitly rather than claiming a downloadable artifact exists.
