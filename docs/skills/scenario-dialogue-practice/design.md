# Scenario dialogue practice: Design

The [skill](../../../skills/scenario-dialogue-practice/SKILL.md) owns the execution instructions. The [usage guide](usage.md) provides examples.

## Purpose

Practice a learner-supplied scenario by presenting native-language cues for both dialogue roles and asking the learner to express every line in a target language. Consolidate the learning material after the dialogue.

## Requirements supplied by the user

- The learner supplies the scenario.
- The system cues the next utterance in the learner's native language.
- The learner responds in the target language and may use native-language wording for any portion they cannot express, including the entire line.
- The learner practices both roles, taking each role's turn in dialogue order.
- The dialogue follows its original plan regardless of whether a response is correct.
- At the end, produce learning material similar to `learn-english-after-chat`, explaining how to express each utterance in context.
- Give additional vocabulary and usage explanations for native-language portions of learner responses, with IPA for the corresponding target-language expressions.

## Resolved choices

### Language and pronunciation

- Support different native and target languages rather than fixing Traditional Chinese and American English.
- Use **native language** for both cues and explanations. A separate "source language" concept is unnecessary in this skill.
- Use IPA for the target language. The initial request for American IPA has been generalized to target-language IPA.
- Infer both the native language and the target language from context. Ask the learner to specify whichever language remains uncertain.
- Use the pronunciation variety requested by the learner or indicated by context; otherwise default to American English for English and a common standard variety for other languages. Briefly identify the variety before practice and allow the learner to change it. Keep IPA consistent with that variety.

IPA represents speech sounds across spoken languages; it is not an English-only notation. The International Phonetic Association's [handbook recordings](https://www.internationalphoneticassociation.org/node/125) demonstrate its application to a wide variety of language sound systems.

### Roles and practice presentation

- The learner plays both dialogue roles and practices expressing every line in the target language.
- The system presents one native-language line at a time, labeled with the current role, such as `Clerk: [native-language line]`.
- After the learner attempts that line, the system presents the next role's native-language line according to the dialogue plan.
- After setup, ordinary practice replies contain only the next cue's progress marker, role name, and native-language line. Record answers silently. All response commentary belongs in the final learning material: praise and identifying a possible issue for later discussion still evaluate the answer and interrupt practice. Echoing answers and record-keeping acknowledgments are also omitted. Explicit session controls retain their behavior below.
- Target-language reference lines are revealed in the final learning material. System-supplied target-language dialogue during practice could reveal vocabulary or sentence patterns for subsequent attempts.
- Final learning material covers both roles because both roles' lines are learner practice turns.

### Dialogue plan and length

- Plan the complete dialogue before presenting the first practice line. Introduce the scenario, roles, and practice goal, then reveal the lines one at a time.
- Default to 10 dialogue lines in total across both roles. Each line is one learner attempt; this is not 10 exchanges of two lines each.
- The learner can specify a different dialogue length.
- Continue along the planned dialogue regardless of response correctness, with correction and explanation deferred until the final learning material.

### Error classification

- A grammatically valid response can still use the wrong vocabulary for the native-language cue. For example, expressing "iced tea" when the cue specifies "hot latte" is a word-choice and meaning mismatch; it does not by itself demonstrate a grammar error.
- Explain the observable difference between the response and the cue, distinguishing word choice, grammar, and contextual appropriateness where relevant.
- A vocabulary-memory mix-up may explain a wrong word, but a single response does not establish that cause. Describe what was expressed and the intended expression without asserting an unobserved cause.

### Practice controls

- Help and skipping are not available during practice. Native-language wording is the fallback for any expression the learner cannot produce in the target language, including a whole-line native-language response.
- A native-language response counts as an attempt and advances the planned dialogue. It supplies material for the final vocabulary explanations.
- If the learner explicitly asks for help or to skip, retain the current line and remind them that they can answer partly or entirely in their native language. Reserve target-language assistance for the final learning material.
- The learner may end the dialogue early.
- After an early ending, cover attempted lines only and mark the session as ended early, reporting completed lines against the planned total, such as `3/10`.
- Keep unattempted lines unrevealed for possible later practice rather than including them as completed practice in the learning material.
- A request to change the scenario ends the current round. Produce its learning material before planning a new round.

## Learning material

Follow the approach of [learn-english-after-chat](../learn-english-after-chat/design.md): preserve actual learner wording, explain meaningful differences, offer natural expressions, and deliver a standalone Markdown file. This skill is self-contained and does not require loading the other skill at runtime.

Each attempted line includes the role and original native-language cue, verbatim learner response, target-language reference expression, and explanations in the native language. Use native-language portions as vocabulary practice targets, adding corresponding target-language expressions, IPA, usage, and examples. Identify already-natural responses without inventing errors, and accept equivalent expressions rather than requiring an exact reference match.

Quote the full native-language line exactly as displayed during practice in its own labeled field before the learner's response. A scenario heading or topic summary cannot replace this line: the learner needs the actual prompt to compare the intended meaning, their attempt, and the reference expression.

Every completed or early-ended round delivers an actual UTF-8 `.md` file with the full learning material and a downloadable file link or attachment. An in-chat review alone is insufficient. Verify the saved artifact before linking it; report any unavailable file-delivery capability without inventing a download link.

## Packaging

Keep execution instructions in one `SKILL.md` with UI metadata in `agents/openai.yaml`. No scripts, external skill dependencies, or output templates are needed. Repository documentation is written in English; practice and learning explanations follow the learner's native language.
