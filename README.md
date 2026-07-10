# 🗣️ Live English Teacher Skill

[![Model: GPT-Live-1](https://img.shields.io/badge/model-GPT--Live--1-10a37f?logo=openai&logoColor=white)](https://openai.com/index/introducing-gpt-live/)
[![API fallback: gpt-realtime](https://img.shields.io/badge/API%20fallback-gpt--realtime-6e6e80?logo=openai&logoColor=white)](https://developers.openai.com/api/docs/guides/realtime)
[![Skill Format](https://img.shields.io/badge/format-SKILL.md-blueviolet)](SKILL.md)
[![Spec-driven: OpenSpec](https://img.shields.io/badge/spec--driven-OpenSpec-orange)](.openspec/specs/live-english-teacher/spec.md)
[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/arananet/gpt-live-english-teacher-skill/pulls)

A skill that turns a live voice session on OpenAI's
[**GPT-Live**](https://openai.com/index/introducing-gpt-live/) full-duplex
voice models into a gentle, always-on English tutor: you talk, it listens,
and the moment you make a grammatical mistake or use a non-native expression
it jumps in — *"Tiny tweak — last weekend I **went** to my cousin's
house."* — and hands the floor right back.

GPT-Live listens and speaks **at the same time**, deciding many times per
second whether to speak, keep listening, or stay quiet. That's what makes
this skill's core promise — correction the instant the flawed phrase ends,
silence while you pause to think — a native model capability instead of a
turn-detection hack.

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
| [`references/system-prompt.md`](references/system-prompt.md) | Drop-in session instructions (GPT-Live and fallback) |
| [`references/session-config.json`](references/session-config.json) | API fallback: Realtime API `session.update` payload |
| [`references/correction-playbook.md`](references/correction-playbook.md) | Error type → interrupt? → template decision table |
| [`examples/example-sessions.md`](examples/example-sessions.md) | Worked example sessions, annotated |
| [`.openspec/`](.openspec/) | OpenSpec workspace: [capability spec](.openspec/specs/live-english-teacher/spec.md) and archived changes |

## Quick start

**On GPT-Live (available now in ChatGPT Voice; GPT-Live-1 is the default
model for Go/Plus/Pro, GPT-Live-1 mini for Free):** supply the
[system prompt](references/system-prompt.md) as the session's instructions,
then just start talking: *"I want to practice my English by talking to you —
please correct me whenever I make a mistake."*

**On the API (until GPT-Live-1 ships there — OpenAI has a notify-me
sign-up):**

1. Open a [Realtime API](https://developers.openai.com/api/docs/guides/realtime)
   connection (WebRTC in the browser, WebSocket server-side).
2. Send the [`session.update`](references/session-config.json) payload with
   the [system prompt](references/system-prompt.md) as `instructions`.
   Key fallback settings: model `gpt-realtime`, `semantic_vad` turn
   detection with **low eagerness** (approximating GPT-Live's native
   patience with thinking pauses), and input transcription enabled (so the
   recap can quote what you actually said).
3. When GPT-Live-1 lands in the API, swap the model id and drop the VAD
   tuning — full-duplex GPT-Live times its own interruptions.

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
