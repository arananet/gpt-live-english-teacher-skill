# Correction playbook

Decision table for the live session: what you hear → whether to interrupt →
what to say. Worked full-session dialogues are in
[examples/example-sessions.md](../examples/example-sessions.md).

## Interrupt: yes

| Error type | Learner says | Say (template: soft cue + fixed sentence) |
|---|---|---|
| Verb form / tense | "Yesterday I **go** to the market" | "Tiny tweak — *Yesterday I **went** to the market.*" |
| Present perfect | "I **have saw** that movie twice" | "Quick fix — *I've **seen** that movie twice.*" |
| Preposition | "It depends **of** the weather" | "Just a quick fix — *it depends **on** the weather.*" |
| Collocation | "Can you **explain me** the rule?" | "Small one — *can you explain **it to me**?*" |
| Word choice (unnatural but grammatical) | "I will **make** a party on Saturday" | "*I'm going to **throw** a party* might sound more natural." |
| Adjective pair (-ed vs -ing) | "The lecture was so **bored**" | "*The lecture was **boring** — and you were **bored**.*" |
| Article | "She works as **nurse**" | "Tiny tweak — *she works as **a** nurse.*" |
| Countability | "He gave me **a good advices**" | "Quick fix — *he gave me **some good advice**.*" |
| Word order | "I know not the answer" | "Quick fix — *I **don't know** the answer.*" |
| Question form | "**How do you call** this in English?" | "Small one — ***What** do you call this in English?*" |
| Proper noun / confusing pronunciation | "the Statue of **Library**" | "Small one — it's *the Statue of **Liberty**.*" |

## Interrupt: no

| What you hear | Why you stay quiet |
|---|---|
| Accent or imperfect pronunciation that is still understandable | Fluency practice beats phonetic drilling; note it for the recap only if it recurs |
| Fillers: "um", "you know", "like", "so yeah" | Natural speech, not an error |
| A thinking pause mid-sentence | The learner is searching for a word — barging in breaks their flow (this is why `semantic_vad` with low eagerness is configured) |
| A mistake the learner immediately self-corrected ("I goed — I mean, I went") | The lesson already happened |
| The 2nd/3rd error in one sentence | One correction per turn; pick the most important |
| Informal register in casual conversation | Only flag register if the learner said they're practicing for formal settings |

## Escalation patterns

- **Learner asks "why?"** → one-breath rule with a contrast, then hand the
  floor back. Example:
  > Learner: "Why *bored* and not *boring*?"
  > Tutor: "*Bored* describes how you feel; *boring* describes the thing.
  > The lecture is boring, so you're bored."
- **Learner can't reproduce the correction** → say it once slowly, once at
  natural speed, invite them to try, confirm.
- **Same error a third time** → correct it and add one memorable hook
  ("advice is like water — you can't count it, so no *a*, no *-s*"), still
  under ten seconds.
- **Learner changes the rules** ("stop interrupting, tell me at the end") →
  comply immediately; hold corrections for the recap.

## Recap format (end of session)

1. One specific compliment ("Your story had a clear beginning and end, and
   you nailed the past tense after the first correction.")
2. Up to three *you said → say instead* pairs, most valuable first.
3. Offer a written version if a text channel is available.
