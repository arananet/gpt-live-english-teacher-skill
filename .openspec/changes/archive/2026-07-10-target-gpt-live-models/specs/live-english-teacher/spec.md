# live-english-teacher (delta)

Full current text lives in
[`.openspec/specs/live-english-teacher/spec.md`](../../../../specs/live-english-teacher/spec.md).

## MODIFIED Requirements

- Requirement: Realtime runtime configuration → **Live model runtime
  configuration** — the skill now targets the full-duplex GPT-Live family
  (GPT-Live-1 / GPT-Live-1 mini) wherever available; `gpt-realtime` with
  `semantic_vad` (low eagerness) + input transcription becomes the explicit
  API fallback, with a migration scenario for when GPT-Live-1 ships in the
  API.

## ADDED Requirements

- Requirement: **Full-duplex conduct** — instant correction delivery,
  sparing backchanneling, and yielding mid-sentence (then re-offering) when
  the learner talks over a correction.
