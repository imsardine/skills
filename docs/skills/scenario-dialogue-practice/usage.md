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

## During practice

Each prompt contains a progress marker, a role, and one native-language dialogue line. You take turns playing both characters. For example, a Chinese cue might be:

```text
1/10 · 店員
你想喝什麼？
```

Respond in the target language, using native-language wording wherever needed. The next prompt advances to the next role's planned line regardless of mistakes. Reference answers and corrections come after practice.

There is no help or skip option: use your native language to complete the attempt instead. You may explicitly end early. Changing the scenario ends the current round and produces its learning material before starting a new round.

## After practice

The agent creates and links a standalone Markdown file automatically. It contains:

- The scenario, language settings, roles, and completed/planned count.
- Each attempted cue with your response preserved verbatim.
- A natural target-language reference expression and explanations in your native language.
- Vocabulary notes for native-language portions, with target-language IPA, usage, and examples.

Feedback distinguishes word choice, grammar, and contextual meaning, and identifies already-natural answers without inventing errors. An early ending includes attempted lines only; unattempted lines remain unrevealed for possible later practice.

Request an output filename or destination if desired. The skill uses conversation content that remains available; it discloses missing history rather than reconstructing your exact answers.
