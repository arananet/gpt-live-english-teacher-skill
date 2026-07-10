# Target the GPT-Live model family

## Why

OpenAI introduced GPT-Live (GPT-Live-1 and GPT-Live-1 mini) on July 8,
2026 — full-duplex voice models that listen and speak simultaneously and
decide many times per second whether to speak, keep listening, pause, or
backchannel. That is exactly the capability this skill's "jump in
immediately" behavior needs: the previous `gpt-realtime` target could only
approximate it with `semantic_vad` turn-detection tuning. GPT-Live powers
ChatGPT Voice at launch; API availability is announced but not yet shipped.

## What Changes

- Retarget the skill to GPT-Live-1 (GPT-Live-1 mini where cost requires),
  keeping `gpt-realtime` on the Realtime API as the documented fallback
  until GPT-Live reaches the API
- Add full-duplex conduct rules: instant correction delivery, sparing
  backchanneling ("mhmm") during correct speech, native patience with
  thinking pauses, yielding mid-sentence when the learner talks over a
  correction, and no dead air when delegating to a background model
- Extend the system prompt with a full-duplex rule (degrades gracefully on
  half-duplex `gpt-realtime`, where platform VAD handles barge-in)
- Annotate `references/session-config.json` as the API fallback, with the
  migration step for when GPT-Live-1 ships in the API
- **MODIFIED** spec requirement: `Realtime runtime configuration` →
  `Live model runtime configuration`; **ADDED** requirement:
  `Full-duplex conduct`

## Impact

- Affected specs: `live-english-teacher`
- Affected files: `SKILL.md`, `references/system-prompt.md`,
  `references/session-config.json`, `references/correction-playbook.md`,
  `README.md`
