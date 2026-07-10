# Correction playbook

Decision table for the live session: what you hear → whether to interrupt →
what to say. Every example in the first table comes from the source
transcript ([examples/transcript-annotated.md](../examples/transcript-annotated.md)).

## Interrupt: yes

| Error type | Learner said | Say (template: soft cue + fixed sentence) |
|---|---|---|
| Verb form / tense | "I have never **went** to this city before" | "Tiny tweak — *I've never **been** to this city before.*" |
| Preposition | "I'm very excited **to** this trip" | "Just a quick fix — *I'm very excited **about** this trip.*" |
| Word choice (unnatural but grammatical) | "take some **images for them**" | "*Take some **photos there*** might sound more natural." |
| Proper noun / confusing pronunciation | "Fisherman's **Wolf**" | "Small one — it's *Fisherman's **Wharf**.*" |
| Adjective pair (-ed vs -ing) | "the trip is very excit**ed**" | "*The trip is excit**ing** — and you're excit**ed** about it.*" |
| Article | "I want to be engineer" | "Tiny tweak — *I want to be **an** engineer.*" |
| Word order | "I know not the answer" | "Quick fix — *I **don't know** the answer.*" |

## Interrupt: no

| What you hear | Why you stay quiet |
|---|---|
| Accent or imperfect pronunciation that is still understandable | Fluency practice beats phonetic drilling; note it for the recap only if it recurs |
| Fillers: "yeah yeah", "cool cool cool", "you know" | Natural speech, not an error |
| A thinking pause mid-sentence | The learner is searching for a word — barging in breaks their flow (this is why `semantic_vad` with low eagerness is configured) |
| A mistake the learner immediately self-corrected | The lesson already happened |
| The 2nd/3rd error in one sentence | One correction per turn; pick the most important |
| Informal register in casual conversation | Only flag register if the learner said they're practicing for formal settings |

## Escalation patterns

- **Learner asks "why?"** → one-breath rule with a contrast, then hand the
  floor back. Example from the transcript:
  > Learner: "Why not *exciting*?"
  > Tutor: "*Excited* describes how you feel; *exciting* describes the thing.
  > So you're excited about the exciting trip."
- **Learner can't reproduce the correction** → say it once slowly, once at
  natural speed, invite them to try, confirm.
- **Same error a third time** → correct it and add one memorable hook
  ("*been* for visits, *gone* for one-way trips"), still under ten seconds.
- **Learner changes the rules** ("stop interrupting, tell me at the end") →
  comply immediately; hold corrections for the recap.

## Recap format (end of session)

1. One specific compliment ("Your trip plan was easy to follow, and you
   used *I've never been* correctly the second time.")
2. Up to three *you said → say instead* pairs, most valuable first.
3. Offer a written version if a text channel is available.
