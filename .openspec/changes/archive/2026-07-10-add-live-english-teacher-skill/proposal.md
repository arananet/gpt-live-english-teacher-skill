# Add live-english-teacher skill

## Why

English learners want conversation practice with immediate, gentle,
in-flow correction — the behavior demonstrated in the source tutoring
transcript. No packaged skill existed that pairs that teaching protocol
with OpenAI's latest live speech model (`gpt-realtime`).

## What Changes

- Add `SKILL.md` defining the live English teacher behavior (interruption
  rules, correction style, recap) and the `gpt-realtime` runtime setup
- Add `references/system-prompt.md` (drop-in `session.instructions` text)
- Add `references/session-config.json` (ready-to-send `session.update`
  payload: `gpt-realtime`, `semantic_vad` low eagerness, input
  transcription)
- Add `references/correction-playbook.md` (error type → interrupt? →
  template decision table)
- Add `examples/transcript-annotated.md` (annotated source transcript)
- Add repository docs (`README.md` with badges, `LICENSE`)

## Impact

- Affected specs: `live-english-teacher` (new capability)
- Affected code: none — documentation/prompt package only
