# AI Product Coach

**A live, Socratic coach that pairs a product manager with AI to pressure-test their thinking on real work.**

## The problem

Most product teams have adopted AI the easy way: paste a problem into a chat window, copy the answer back out. That's outsourcing the thinking. It produces confident, plausible output that nobody really checked, and it can put proprietary information at risk. Banning the tool doesn't fix it. Building the judgment to use it well does.

Generic "AI tool training" doesn't build that judgment either. People need practice on their own work, with someone pushing back.

## What it does

A PM brings a real task: a metric they're about to commit to, a research synthesis, a prioritization call. The coach runs the same pattern every time, and says it out loud so the PM can reuse it without the coach:

**Assess → Gather context → Structure the request → Use AI → Reflect → Apply Product judgment**

1. Asks what the PM currently believes, before AI says anything.
2. Asks for specific evidence, and pushes back once if the answer is a category ("I have some data").
3. Builds the prompt *with* the PM, naming each part: role, evidence, evaluation standard, the instruction to argue against the PM, output shape, and an explicit line that AI doesn't make the call.
4. Plays that skeptical reviewer live.
5. Asks the PM one reflection question about the exchange.
6. Optionally critiques the PM's own prompt-writing, naming the single weakest part and the one-line fix.
7. Names a specific way the AI output just produced could be wrong, or says honestly that nothing stood out.
8. Hands the decision back, with what evidence should inform it.

## Design decisions

**The PM's belief comes first, always.** If AI goes first, it anchors the PM. If the PM goes first, AI has something to challenge. This step can't be skipped.

**Name the failure mode from what actually happened.** The skill carries a bank of AI failure modes (false alignment, causal leap, false precision, metric substitution, and others), but it has to pick the one that's genuinely at risk in this session's output. No stock examples.

**No repeats in a session.** Content banks of "AI truths" and thinking moves rotate so a PM working through several tasks gets a different lesson each time.

**One piece of feedback, not a rewrite.** Prompt critique names the single weakest element. More than one stops being feedback.

**Meet people where they are.** The coach reads how much scaffolding someone wants and adjusts along a progression from using AI as an assistant to using it as a critical thinking partner. It never lectures about why AI matters.

**It never makes the product decision.** Every session ends with the decision in the PM's hands.

## How it connects

This is the live, on-demand counterpart to the AI Opportunity sections in the [job aid library](../job-aid-reviewer/). The job aids teach the pattern in writing at each step. The coach lets a PM practice it on whatever's in front of them today.

It ships with a default four-stage product framework (Idea, Draft, Build and Release, Evaluate) but switches to the client's own stages when they have them.
