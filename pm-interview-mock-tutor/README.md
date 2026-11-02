# PM Interview Mock Tutor

**A mock PM interviewer that coaches in the moment instead of grading at the end.**

## The problem

Most interview practice tools give you a scorecard after you finish. By then the moment is gone. You don't remember exactly where the math went sideways or when you started rambling, so the feedback doesn't stick.

Real PM interviews are also conversations, with short turns and follow-ups. A tool that accepts a long monologue and returns a long critique trains the wrong rhythm.

## What it does

It plays the interviewer for three interview formats:

- **Case** (profitability or launch), with data held back until the candidate asks for it.
- **Product Discovery**, in three parts: explore customer problems from a packet of data and quotes, lead an ideation session, then storyboard the solution.
- **Product Skills**, a deep dive on a product the candidate actually managed, with realistic follow-ups like "How did you know?" and "What would you do differently?"

It can generate fictional practice packets (company context, a metrics table with one strong signal, customer quotes with a few that are easy to misfile) and save them for later sessions.

## Design decisions

**Coach at the moment of the mistake.** When the candidate drifts, the interviewer adds one short italic *Tutor:* line, then keeps the interview going. Fuller debriefs wait for the end of each part.

**Short turns, one question.** React in one to three sentences, ask one question. Never restate the candidate's whole answer. That keeps the rhythm close to the real thing.

**Track personal patterns.** The case format reinforces a six-checkpoint routine (Frame, Unit, Formula, Check, So what, Close) and watches for the specific traps a candidate tends to fall into, like averaging two rates instead of weighting them or mixing monthly and annual numbers.

**Pushback is a skill too.** When the candidate disagrees with the interviewer, the tutor nudges toward evidence: "point to the evidence, or say it could be both and here's how we'd find out."

**A "packet" shortcut.** Typing `packet` reposts a compact version of the case data, so nobody has to scroll back through a long conversation.

**Debrief against the real criteria.** Each wrap-up names what worked, the top two or three things to improve, and one habit to practice next time.

This started as my own interview prep, and it's the same coaching philosophy I use with clients. Short practice loops with feedback at the moment of need change behavior faster than a long review after the fact.
