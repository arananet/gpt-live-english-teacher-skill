# 🗣️ Live English Teacher Skill

[![Model: gpt-realtime](https://img.shields.io/badge/model-gpt--realtime-10a37f?logo=openai&logoColor=white)](https://platform.openai.com/docs/models/gpt-realtime)
[![Skill Format](https://img.shields.io/badge/format-SKILL.md-blueviolet)](SKILL.md)
[![Spec-driven: OpenSpec](https://img.shields.io/badge/spec--driven-OpenSpec-orange)](.openspec/specs/live-english-teacher/spec.md)
[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/arananet/gpt-live-english-teacher-skill/pulls)

A skill that turns a live voice session on OpenAI's latest realtime speech
model (**`gpt-realtime`**) into a gentle, always-on English tutor: you talk,
it listens, and the moment you make a grammatical mistake or use a
non-native expression it jumps in — *"Tiny tweak — last weekend I **went**
to my cousin's house."* — and hands the floor right back.

## How it works

> **Learner:** Last weekend I go to my cousin's house in the countryside.
> **Tutor:** Tiny tweak — *last weekend I **went** to my cousin's house.*
> **Learner:** …and we made a barbecue in the garden.
> **Tutor:** *We **had** a barbecue* might sound more natural.
> **Learner:** Why not *made*? We cooked it ourselves.
> **Tutor:** In English you *have* a barbecue, the same way you *have* a
> party or *have* dinner. *Make* sounds like you're building the grill.

The tutor interrupts for grammar, wrong prepositions, unnatural word choice,
and confusing proper nouns — and stays quiet for accent, fillers, thinking
pauses, and anything you already fixed yourself. About one correction per
turn, explanations only when you ask, and a ≤3-item *you said → say instead*
recap at the end. Two full worked dialogues are in
[`examples/example-sessions.md`](examples/example-sessions.md).

## Repository layout

| Path | What it is |
|---|---|
| [`SKILL.md`](SKILL.md) | The skill: teaching behavior + runtime setup |
| [`references/system-prompt.md`](references/system-prompt.md) | Drop-in text for `session.instructions` |
| [`references/session-config.json`](references/session-config.json) | Ready-to-send Realtime API `session.update` payload |
| [`references/correction-playbook.md`](references/correction-playbook.md) | Error type → interrupt? → template decision table |
| [`examples/example-sessions.md`](examples/example-sessions.md) | Worked example sessions, annotated |
| [`.openspec/`](.openspec/) | OpenSpec workspace: [capability spec](.openspec/specs/live-english-teacher/spec.md) and archived change proposal |

## Quick start

1. Open a [Realtime API](https://platform.openai.com/docs/guides/realtime)
   connection (WebRTC in the browser, WebSocket server-side).
2. Send the [`session.update`](references/session-config.json) payload with
   the [system prompt](references/system-prompt.md) as `instructions`.
   Key settings: model `gpt-realtime`, `semantic_vad` turn detection with
   **low eagerness** (so thinking pauses aren't treated as end-of-turn), and
   input transcription enabled (so the recap can quote what you actually said).
3. Start talking: *"I want to practice my English by talking to you — please
   correct me whenever I make a mistake."*

Agent runtimes that support the [Agent Skills](https://code.claude.com/docs/en/skills)
format can instead drop this repo into their skills directory and let the
agent load `SKILL.md` on demand.

## Spec-driven with OpenSpec

The required behavior is specified in
[`.openspec/specs/live-english-teacher/spec.md`](.openspec/specs/live-english-teacher/spec.md)
as SHALL-requirements with Given/When/Then scenarios; changes are proposed
under `.openspec/changes/` and archived once shipped. Project conventions
live in [`.openspec/project.md`](.openspec/project.md).

## License

[MIT](LICENSE)
