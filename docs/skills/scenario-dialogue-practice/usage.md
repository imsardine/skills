# Scenario dialogue practice

Practice both roles in a scenario, one line at a time. The system supplies each line in your native language, and you express it in your target language. Use your native language for any words you cannot express, including an entire line if necessary.

## Start a round

Ask your agent to follow the skill:

```text
Read and follow /path/to/skills/skills/scenario-dialogue-practice/SKILL.md.

Help me practice ordering at a cafe. My native language is Traditional
Chinese, and I want to practice American English. Use 10 lines.
```

Replace `/path/to/skills` with the location of your clone. You can choose another scenario, language pair, pronunciation variety, or length. The agent infers the native and target languages from context and asks if either is uncertain. The default length is 10 lines total across both roles.

Before practice, the agent identifies the scenario, roles, goal, length, and pronunciation variety. English defaults to American pronunciation; other languages use a common standard variety unless your request or context indicates otherwise.

Google Translate is the default service for listening links. You can instead request Bing Translator, LazyPy, or Yandex Translate, either at the start or later. The agent briefly identifies the service during setup and proceeds with Google Translate if you do not choose another.

## During practice

Each prompt contains a progress marker, a role, and one native-language dialogue line. You take turns playing both characters. For example, a Chinese cue might be:

```text
1/10 · 店員
你想喝什麼？
```

Respond in the target language, using native-language wording wherever needed. The next prompt advances to the next role's planned line regardless of mistakes. After each non-final answer, the agent replies only with the next cue's progress marker, role, and native-language line. It records your answer silently, without repeating it or adding acknowledgments, praise, or comments about possible errors. All feedback, including reference answers and corrections, comes after practice.

There is no help or skip option: use your native language to complete the attempt instead. You may explicitly end early. Changing the scenario ends the current round and produces its learning material before starting a new round.

## After practice

After normal completion or an early ending, the agent automatically creates a standalone `.md` file and provides a downloadable link or file attachment. A review displayed in chat does not replace the downloadable file. It contains:

- The scenario, language settings, roles, and completed/planned count.
- Each role's full native-language line quoted exactly as shown during practice, followed by your response preserved verbatim. The original line appears in its own labeled field, even if the entry also has a scenario or topic heading.
- A natural target-language reference expression, a link to your selected listening service, and explanations in your native language.
- Vocabulary notes for native-language portions, with target-language IPA, usage, and examples.

Feedback distinguishes word choice, grammar, and contextual meaning, and identifies already-natural answers without inventing errors. An early ending includes attempted lines only; unattempted lines remain unrevealed for possible later practice.

## Listen to the suggested expressions

Each reference expression appears in a blockquote with a `🔊` listening link directly after it, on the same Markdown line and in the same paragraph:

```markdown
> I can't hear you clearly. [🔊](https://translate.google.com/?sl=en&tl=zh-TW&text=I%20can%27t%20hear%20you%20clearly.&op=translate)
```

Optional alternatives and complete vocabulary example sentences also have an inline `🔊` link after the expression. Open it, then press the speaker button in the original-text field for Google Translate, Bing Translator, or Yandex Translate; in LazyPy, press the play button. The exact suggested expression is prefilled; a service's translated result is not the reference answer. No MP3 files need to be downloaded or stored with the Markdown.

Playback voices and supported languages depend on the service, so the link guarantees a particular pronunciation variety only when the service supports selecting it. The reference wording and IPA notes still follow your selected variety. If a language or voice is unavailable, you can choose another service. Listening links appear after practice, alongside the learning material.

Request an output filename or destination if desired. The skill uses conversation content that remains available; it discloses missing history rather than reconstructing your exact answers.
