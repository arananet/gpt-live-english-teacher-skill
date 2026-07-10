# Project Context

## Purpose

`gpt-live-english-teacher-skill` packages a reusable agent skill
([SKILL.md](../SKILL.md)) that turns a live voice session on OpenAI's
`gpt-realtime` model into a spoken-English tutor: the learner talks, the
tutor jumps in immediately and gently whenever it hears a grammatical
mistake or a non-native expression, then hands the floor back.

Worked example dialogues live in
[examples/example-sessions.md](../examples/example-sessions.md).

## Tech Stack

- Agent Skills format (`SKILL.md` with YAML frontmatter + progressive
  disclosure into `references/` and `examples/`)
- OpenAI Realtime API, model `gpt-realtime` (speech-to-speech), configured
  via `references/session-config.json`
- Markdown documentation; no build step, no runtime code in this repo

## Project Conventions

### Structure

- `SKILL.md` — entry point; behavior contract and runtime setup
- `references/` — files loaded on demand: system prompt, session config,
  correction playbook
- `examples/` — worked example sessions
- `.openspec/` — this spec workspace (`specs/` for current truth,
  `changes/` for proposals; archived changes move to `changes/archive/`)

### Spec conventions

- Requirements use SHALL and each requirement carries at least one
  `#### Scenario:` in Given/When/Then form
- Capability names are verb-noun, kebab-case
- Example dialogue in specs and docs is invented for illustration, not
  taken from recordings of real sessions

### Domain notes

- "Interrupt" means a short spoken correction immediately after a flawed
  phrase, not seizing the conversation
- CEFR levels (A2–C1) are used for calibration language
