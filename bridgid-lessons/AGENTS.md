# English-learning project instructions

## Learner and purpose

- The learner is a native Russian speaker studying English through private lessons.
- Help the learner understand how English works, not merely obtain corrected text.
- Default to explanations in Russian. Keep English examples, alternatives, and exercises in English.
- Infer the learner's level gradually from their work; do not assign a CEFR level without enough evidence.

## Teaching principles

- Separate these judgments clearly:
    1. grammatically incorrect;
    2. grammatically possible but unnatural;
    3. natural but dependent on register, dialect, or context;
    4. a stylistic preference rather than a rule.
- Explain the reason for each important correction in plain Russian.
- When useful, contrast the English construction with the likely Russian intuition that caused the mistake.
- Write readable teaching prose, not a diagnostic report or a completed checklist. Prefer short connected paragraphs;
  use tables for genuine comparisons, not as a substitute for explaining expressions.
- For every expression taught in the source, provide its own heading in `vocabulary.md`, a natural Russian translation,
  contextual meaning, useful collocations or construction, register and tone, and 2–3 realistic English examples with
  Russian translations. Vary the situations so the examples reveal how the expression is used.
- Explain how a listener is likely to understand the expression in context, including relevant implications,
  ambiguity, or limits. Avoid generic claims such as "native speakers say this". Add American/British labels only
  when the distinction matters. Generated examples illustrate plausible usage; do not present them as sourced quotations.
- Treat idioms and phrasal verbs as vocabulary in the same file. Explain a literal image when it helps, but do not
  invent an etymology or force a literal explanation onto every expression.
- For grammar, give the smallest rule that explains the source example, then an explained contrast. Keep it theoretical.
- Do not use Russian-letter pronunciation guides unless the user asks. Prefer IPA plus a practical pronunciation note
  when pronunciation matters.
- Never claim that all native speakers interpret a phrase identically. State meaningful ambiguity, regional variation,
  or context dependence.
- Preserve the learner's intended meaning and voice when rewriting.

## Lesson workflow

When the user pastes lesson notes and asks for a full analysis:

1. Keep the raw material verbatim. Never silently overwrite or "clean up" the only copy.
2. Create one canonical lesson directory under `lessons/YYYY/`, named `YYYY-MM-DD-short-topic/`. Every lesson directory
   must contain these three theory files:
    - `lesson.md`
    - `grammar.md`
    - `vocabulary.md`
3. Use the corresponding files under `templates/lesson/` as the starting structure and adapt them to the material.
   Keep all three files even when one category has no material; in that case, add a short explicit note instead of
   inventing content. Adapt the structure for readability and remove template comments and empty placeholders.
4. Use the lesson files as follows:
    - `lesson.md`: small metadata block, navigation to the two companion files, short factual summary of the lesson,
      optional important clarifications with links to detailed explanations, and the original notes verbatim;
    - `grammar.md`: grammar rules, explanations of corrections, and explained contrasts;
    - `vocabulary.md`: all expressions taught in the source, including words, collocations, idioms, and phrasal verbs.
      Put expression-specific corrections, pronunciation, register, and listener interpretation here.
      Put sentence-level grammar corrections in `grammar.md`; link between files where needed rather than duplicating.
      Do not add "Что уже получается", "Главный приоритет", or a separate "Как это слышит носитель" section to
      `lesson.md`. Do not infer progress or weaknesses from a list of expressions taught by the teacher.
5. If the date or topic is missing, make a reasonable visible assumption. Ask only when the missing fact would
   materially change the result.
   If a source date conflicts with an existing lesson or with another date marker, do not silently choose one: preserve
   the source wording and explicitly record the uncertainty before merging or replacing existing material.
6. Distinguish teacher-provided wording, learner wording, and Codex suggestions whenever the source makes that possible.
   Formatting such as bold text may indicate a teacher-provided answer or emphasis; do not automatically classify it as
   a learner error.
7. Cover every expression presented as learning material in the source, especially expressions highlighted in bold
   and supplied with explanations. Check the whole source for unbolded teaching items too. Bold headings, task
   instructions, or grammatical emphasis are not automatically vocabulary entries. Do not extract every incidental
   basic word. Cover repeated expressions once per lesson, including any different meanings taught there.
8. Treat `knowledge/README.md` as a compact cross-lesson map, not as a second copy of the teaching material. Add or
   update concise topic entries that link to the relevant lesson files. Keep detailed explanations inside lesson
   directories.
9. Whenever a lesson is created or migrated, update the chronological index in `lessons/README.md`. Add one concise
   entry with the date, topic, and a relative link to that lesson's `lesson.md`; update an existing entry instead of
   creating a duplicate.
10. Update only genuinely reusable cross-lesson items in:
    - `knowledge/README.md`
    - `review/mistakes.md`
    - `review/queue.md`
11. Avoid duplicate index entries and explanations. If a topic already exists in the knowledge map, add the new lesson
    reference or refine the existing label. When a topic recurs in a new lesson, explain only the new context or nuance
    there and link related lessons where useful. Each expression must still have a self-contained explanation of its
    use in the current lesson; a link alone does not replace its translation and examples.
12. Keep all three lesson files theoretical. Generate practice only on request, following the practice workflow below.
    Preserve teacher-provided exercises inside the verbatim source; do not add new exercises or answer blocks to theory.

When migrating legacy lessons or a combined notes file:

- split the source by explicit lesson date before analysing it;
- keep each lesson's source block verbatim in that lesson's `lesson.md`;
- preserve existing analyses until their content has been transferred and verified;
- do not silently merge lessons whose dates or boundaries are uncertain;
- add every migrated lesson to `lessons/README.md` and verify that its index link resolves;
- update relative links after files move;
- when converting an old four-file lesson, transfer idioms into individual sections in `vocabulary.md` and verify
  coverage before removing `idioms.md`; update incoming links, including links in the knowledge map;
- existing lessons may retain the old structure until explicitly reworked. A template change alone does not require
  rewriting them. Preserve source text and user-authored answers during migration. Move existing generated practice
  into the lesson's `practice/` directory, recording that it was migrated rather than newly completed;
- stop adding new teaching material to the legacy `knowledge/grammar.md`, `knowledge/idioms.md`, and
  `knowledge/vocabulary.md`; migrate useful content into lesson directories and the compact knowledge map instead.

If the user asks a one-off language question, answer it directly. Do not create or update repository files unless they
ask to save it or it is clearly part of processing a lesson.

## Practice and review workflow

- Create practice only when the user requests it. Generate it for the requested lesson and adapt it to the learner's
  actual answers during the session; do not prefill theoretical lessons with exercises.
- Save a requested lesson practice session in that lesson's `practice/YYYY-MM-DD-short-topic.md`, using the session
  date, not the lesson date. Create `practice/` only when needed. For multiple sessions with the same name and date,
  use `-02`, `-03`, etc.; never overwrite an earlier session. Link back to `../lesson.md`.
- For practice spanning multiple lessons, keep one canonical session in the most recent participating lesson's
  `practice/` directory and link every participating lesson in the session file.
- Prefer retrieval practice over rereading: cloze questions, correction tasks, translation with context, and original
  sentence production.
- Use the learner's real recurring errors as distractors, but do not reproduce an error without clearly marking it as
  incorrect.
- When reviewing, hide answers until after the questions and use `templates/review.md` when creating a file.
- Adapt that template to the requested activity; do not require every exercise type. During interactive practice,
  present one prompt at a time and reveal feedback after the learner's response. Save actual responses and feedback
  when available; never invent results or populate progress fields before the learner has answered.
- Suggested intervals are 1, 3, 7, 14, and 30 days; adapt them based on actual performance.
- Mark an item mastered only after successful use in a new sentence on more than one occasion.

## File conventions

- Use Markdown and UTF-8.
- Lesson prose may be in Russian; examples and quoted source text remain in English.
- Use relative links between project files.
- Dates use `YYYY-MM-DD`.
- Lesson directories use `lessons/YYYY/YYYY-MM-DD-short-topic/`; filenames inside them are fixed as `lesson.md`,
  `grammar.md`, and `vocabulary.md`. Optional practice files live in the lesson's `practice/` subdirectory.
- Keep metadata small and human-editable; do not add a database or generated tooling unless requested.
- Never modify files outside this `bridgid-lessons` directory for a lesson task.

## Quality check

Before finishing a saved lesson analysis, verify that:

- the original notes are preserved;
- all three theory files exist and `lesson.md` links to its two companion files;
- `lessons/README.md` lists the lesson once and links to its `lesson.md`;
- corrections do not change the intended meaning;
- explanations cover why, naturalness, and register where relevant;
- examples sound plausible in real conversation;
- every expression taught in the source has its own vocabulary heading, contextual translation, explanation,
  register/tone, listener interpretation, and several examples;
- theory contains no generated exercises, unsupported learner assessments, or empty template scaffolding;
- the knowledge map contains no obvious duplicate topic entries or copied long explanations;
- if practice was requested, it is saved separately with a date in its filename and tests the requested material
  or evidenced weak points; results reflect actual learner responses.
