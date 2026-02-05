# Target & Power Mapping Rules (v1)

## Purpose
Adjust language, authority, and phrasing based on the relationship
and power dynamic between the sender and the target.

This rule set ensures that messages remain appropriate,
credible, and non-escalatory for the given target type.

---

## Canonical Buckets

The system maps all targets into one of the following buckets:

- peer_equal
- senior_authority
- junior_subordinate
- support_agent
- external_third_party
- group_entity
- unknown_target

These buckets are authoritative and must always be present
before message generation.

---

## Bucket Rules

### 1) peer_equal
**Examples:** coworker, sibling, friend, neighbor

**Language Guidance**
- Use balanced, conversational professionalism
- Requests may be phrased directly but politely
- Avoid commands or deferential language

**Constraints**
- No authoritative instructions
- No excessive hedging

---

### 2) senior_authority
**Examples:** manager, landlord, administrator, escalation contact

**Language Guidance**
- Use respectful and structured phrasing
- Frame requests as clarifications or formal asks
- Acknowledge role or responsibility implicitly

**Constraints**
- Do not issue directives
- Avoid casual or overly familiar language
- No accusatory framing

---

### 3) junior_subordinate
**Examples:** direct report, child, trainee

**Language Guidance**
- Use clear, supportive instructions
- Maintain calm authority
- Provide expectations without intimidation

**Constraints**
- No threats or punitive language
- Avoid emotional frustration

---

### 4) support_agent
**Examples:** customer support, billing, maintenance

**Language Guidance**
- Be precise and procedural
- Reference facts, dates, or identifiers when relevant
- Keep tone task-oriented

**Constraints**
- No emotional appeals
- No pressure tactics
- Avoid unnecessary backstory

---

### 5) external_third_party
**Examples:** vendor contact, service provider, external client

**Language Guidance**
- Use formal-neutral phrasing
- Clearly define scope and responsibility
- Avoid internal assumptions or blame

**Constraints**
- No internal jargon
- No emotional language

---

### 6) group_entity
**Examples:** team, department, HOA, organization

**Language Guidance**
- Use collective language (“the team”, “this group”)
- Avoid personal attribution
- Keep statements generalized and neutral

**Constraints**
- No individual blame
- No emotional framing

---

### 7) unknown_target
**Examples:** unclear recipient, mixed audience

**Language Guidance**
- Default to conservative, neutral phrasing
- Avoid assumptions about authority or familiarity

**Constraints**
- No directives
- No informal language
- No emotional signaling

---

## Cross-Cutting Enforcement Rules

- Tone Pack rules always apply on top of target rules
- Target rules may restrict tone expression but never override intent
- If a conflict arises:
  1) Safety
  2) Target rules
  3) Tone pack
  4) Intent core

---

## Output Expectation
The generated message should feel appropriate for the recipient’s role,
avoiding overreach, submission, or unintended escalation.
