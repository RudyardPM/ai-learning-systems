---
name: job-aid-improvement-interviewer
description: Takes proposed improvements from a job aid review and presents them to the user one at a time in multiple choice or long answer format, waiting for a decision before moving to the next. Use this skill whenever the user asks to work through review improvements, says "take me through the improvements one at a time," references proposed fixes from a job aid review, or wants to decide on each improvement before it is implemented. Also trigger when the user has just completed a job aid review and says something like "let's go through these" or "start the improvements."
---

# Job Aid Improvement Interviewer

A lightweight skill that takes the proposed improvements from a completed job aid review and presents each one as a structured decision — one at a time — in either multiple choice or long answer format depending on what the decision requires.

---

## How it works

When triggered, ask the user to either:
- Paste the proposed improvements from the review, or
- Confirm which job aid was just reviewed so the improvements can be referenced from context

Then present each improvement one at a time using the format below. Do not present the next improvement until the user has responded to the current one.

---

## Format for each improvement

**Improvement [N] of [total] — [Short title of the improvement]**

State the issue in one sentence.

If the fix is straightforward with clear options, present as **multiple choice**:

> **A)** [Option — e.g. implement as written]
> **B)** [Option — e.g. modify the wording, tell me what to change]
> **C)** [Option — e.g. skip this improvement]

If the fix requires judgment, nuance, or custom input from the user — such as wording a worked example, deciding on tone, or choosing between structurally different approaches — present as **long answer**:

> [Describe the proposed fix clearly. Then ask: "How would you like to handle this?" or "What wording would you prefer?"]

---

## Decision handling

**If the user selects A (implement as written):**
Confirm you will implement it and ask: "Do you want me to push this to Confluence now, or hold all changes until the end?"

**If the user selects B (modify):**
Ask what they want changed. Once they tell you, confirm the revised wording and ask: "Push to Confluence now or hold until end?"

**If the user selects C (skip):**
Acknowledge and move immediately to the next improvement. No commentary.

**If the user says "did it on my own" or equivalent:**
Acknowledge, mark it complete, and move to the next improvement immediately.

**If the user says "hold all changes until end":**
Collect all approved improvements, then push them all in a single Confluence update at the end.

**If the user says "push each one as we go":**
Push to Confluence after each approval before presenting the next improvement.

---

## Tracking

Keep a running mental tally as you go. After the final improvement is decided, present a brief summary:

**Review complete — [Job Aid Title]**

| Improvement | Decision |
|-------------|----------|
| [Title] | Implemented / Modified / Skipped / Done independently |
| ... | ... |

Then ask: "Ready to move to the next job aid?"

---

## Tone

Keep responses short. The user is making decisions — not reading analysis. State the issue, present the options, wait. Do not re-explain the review or add commentary between improvements unless the user asks.

---

## Edge cases

**If the user has not yet run a review:** Do not trigger this skill. The job-aid-reviewer skill should be run first.

**If the user wants to re-order the improvements:** Allow it. Ask which improvement they want to tackle next and jump to it.

**If the user wants to combine improvements into a single Confluence update:** Default to this behavior — it is more efficient and reduces version noise.
