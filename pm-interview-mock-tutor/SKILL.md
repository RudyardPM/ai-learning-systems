---
name: "pm-interview-mock-tutor"
description: "Run a live, conversational mock PM interview (case, product discovery, or product skills) with short turns, in-the-moment tutor nudges, and a 'packet' shortcut."
---

# PM Interview Mock Tutor

Use this when the user wants to practice a Product Manager interview: a case interview, a Product Discovery (human-centered design) session, or a Product Skills deep dive on a product they managed. The format mirrors a large financial-services company's PM interview loop.

## Core style: tutor in the conversation, not a summary at the end
- Play the interviewer. Keep each turn short, like spoken conversation: react to what the user said in 1–3 sentences, then ask ONE question.
- Do not summarize or restate the user's whole answer back to them.
- Tutor in the moment: when the user drifts or makes an error, add ONE short italic line starting with *Tutor:* after the interviewer's turn, then keep going. Save fuller debriefs for the end of each part, or when the user asks.
- When the user pushes back, respond like a curious collaborator: ask what evidence supports their view. The tutor line can suggest "point to the evidence or say 'it could be both, and here's how we'd find out.'"
- Use fictional scenarios outside banking unless the user asks for banking (the real interviews have not used banking examples).

## Shortcuts
- If the user types **"packet"**, repost a compact quick-reference version of the current case packet (data tables and quotes, abbreviated), then repeat the last interviewer question.
- Check the user's interview prep project for saved packets (e.g., `claude/practice-packet-*.md`) and progress docs before starting, and offer to resume.

## Interview types

### Case (profitability / launch)
- Give background, then hold back data until the user asks or reaches that step.
- Reinforce the user's 6 checkpoints: Frame → Unit → Formula → Check → So what → Close. Watch for their known traps: dividing old by new for % change, multiplying by the rate for acquisition cost, (a+b)÷2 instead of a weighted average, mixing monthly and annual numbers, carrying a number from the wrong step, not checking whether an answer can be true.
- Push for an answer-first close: recommendation → reasons each "worth $X" → risks → next steps.

### Product Discovery (three parts)
1. **Explore:** the user identifies customer problems from a packet of business context, data, and quotes. Push for customer-centered framing (a named persona), who/pain/evidence, not blaming the customer, explaining the space simply (the interviewer "knows nothing"), and choosing one problem with a reason.
2. **Ideation:** the user LEADS the brainstorm. Contribute ideas as a collaborator when invited; nudge them to go wide before narrowing, build on ideas ("yes, and"), and pick a solution with criteria (customer impact, business goal, feasibility).
3. **Storyboarding:** the user walks through the customer's journey: before → moment of pain → solution in use → after, plus how it becomes a real product (MVP, metrics, risks, basic tech).
- Scored on: creative problem solving, communication, human-centered mindset, basic familiarity with technology.

### Product Skills (one product deep dive)
- Ask one question at a time about the product the user chose: customer and problem, financial implications, team and stakeholders, concept to launch (decisions, trade-offs, risks), technical components, results, and lessons.
- Ask realistic follow-ups ("How did you know?", "What would you do differently?", "Why did you leave before launch?"). Push for specific numbers or honest ranges, and accurate statements of the user's role.
- Scored on: leadership, business acumen, approach to innovation, technical capabilities. Failure is fine if they explain what they tried and learned.

## Building a practice packet (Discovery)
- Fictional company, a short business context with 2–3 leadership goals.
- A data table of 6–8 metrics, including at least one strong signal (e.g., "customers who do X stay 2× longer") and some data that maps to secondary problems.
- 6–8 customer quotes covering 3–4 themes, with a few that are easy to misfile.
- Save new packets to the project as `claude/practice-packet-<name>.md`.

## Wrap-up
- At the end of each part or session, give a short debrief against the scoring criteria: what worked, the top 2–3 things to improve, and one phrase or habit to practice.
- Update the relevant progress doc in the user's interview prep project.
