# Context Normalization Rules (v1)

## Purpose
Normalize raw user input into a clear, factual context
that can be safely and consistently used by downstream prompts.

This layer exists to stabilize output quality regardless of
user writing style, emotional tone, or verbosity.

---

## Input Fields

The following inputs may be provided by the UI:

- happened
- not_happened
- flags (boolean indicators)

All fields are optional except `happened`,
which must meet minimum length requirements upstream.

---

## Normalization Principles

- Preserve factual meaning, not wording
- Remove emotional framing, judgment, or speculation
- Convert fragmented input into clear, neutral prose
- Do not add new facts or assumptions

This step must not introduce interpretation,
blame, or inferred intent.

---

## Field Rules

### 1) happened

**Goal**
Produce a concise, factual description of past events.

**Rules**
- Use past tense only
- Remove emotional language and intensifiers
- Merge fragmented sentences into one coherent paragraph
- Keep only verifiable actions, dates, and outcomes
- Target length: 60–160 words (soft guideline)

**Prohibited**
- Opinions or interpretations
- Adjectives expressing frustration or intent
- Repetition of the same event

---

### 2) not_happened

**Goal**
State what remains unresolved or outstanding.

**Rules**
- Describe current status only
- Use neutral, present-tense phrasing
- Limit to one or two sentences
- Do not restate the full background

**Prohibited**
- Complaints or blame
- Emotional or rhetorical language
- Speculation about motives

---

### 3) flags

Flags provide situational modifiers.
They do not generate standalone sentences,
but may influence phrasing downstream.

Available flags:

- pending  
  Indicates a response or action is awaited.

- prior_contact  
  Indicates the user has already reached out at least once.

- deadline  
  Indicates a time-bound constraint exists.

- affects_others  
  Indicates impact beyond the sender and recipient.

- no_urgency  
  Indicates the matter is not time-sensitive.

**Rules**
- Do not narrate flags explicitly
- Use flags only to subtly shape clarity or emphasis
- Flags must never change intent or tone directly

---

## Output Format

Return a normalized context object with:

- normalized_happened
- normalized_not_happened (if present)

Do not include flags in the output text.

Example (conceptual):

- normalized_happened: factual paragraph
- normalized_not_happened: concise status sentence

---

## Safety Constraints

- Never invent dates, amounts, or actions
- Never soften or intensify beyond the provided facts
- Never include legal language unless already present
- Never suggest next steps or advice

---

## Output Expectation

The normalized context should read as if written
by a calm, neutral third party summarizing events,
ready to be used by any Intent, Tone, or Format
without distortion.
