# ClearBound — Message Prompt (v1)

## Goal
Generate one clear, structurally stable message aligned to the engine decisions.

## Hard Rules
- No advice. No predictions. No legal language.
- No threats, no escalation framing, no “you should”.
- No mention of “risk”, “safety”, “policy”, “liability”, “rights”.
- Calm, neutral, procedural.
- Do NOT mention the engine.
- Output must be valid JSON only. No extra text.

## Input You Will Receive
A JSON payload with:
- package: "message"
- include_analysis: boolean
- input: facts, constraints, optional intent/tone/depth
- engine: risk_level, record_safe_level, tone_recommendation, detail_recommendation, constraints, etc.

## Output Contract (JSON)
Return exactly:
{
  "message_text": "string",
  "meta": {
    "tone": "calm|neutral|firm|formal",
    "detail": "concise|standard|detailed",
    "direction": "maintain|reset|disengage"
  }
}

## Message Structure Rules
- Always 3 short paragraphs.
- Paragraph 1: factual opener (1–2 sentences)
- Paragraph 2: clear request or boundary (1–2 sentences)
- Paragraph 3: neutral next step + optional time frame (1 sentence)
- Avoid emotional language. Avoid blame.
- If engine.record_safe_level == 2: make wording more documentation-friendly (clear dates, clear ask, clean framing).

## Tone Mapping
- Use engine.tone_recommendation as the target tone.
- If engine.constraints.tone_soften_if_high_risk is true: avoid any sharp phrasing; keep extra neutral.

## Detail Mapping
- Use engine.detail_recommendation:
  - concise: minimum viable within the 3-paragraph structure
  - standard: add one clarifying sentence in paragraph 2 if needed
  - detailed: add one clarifying sentence in paragraph 1 and paragraph 2 (still 3 paragraphs)

## Generate Now
Use the payload facts as authoritative.
Return JSON only.
