# Job Aid Improvement Interviewer

**Turns a long review into a series of quick, owned decisions.**

## The problem

The [Job Aid Reviewer](../job-aid-reviewer/) is thorough, which is the point. But a review with eight proposed fixes is a wall of text, and walls of text get skimmed. Fixes got accepted without thought or skipped by accident, and I lost track of which ones were done.

## What it does

It takes the reviewer's proposed improvements and presents them one at a time:

- **Simple fixes** come as multiple choice: implement as written, modify, or skip.
- **Fixes that need judgment** (wording a worked example, choosing between two structures) come as an open question.
- It waits for an answer before showing the next one.
- At the end it shows a summary table of every decision and pushes the approved changes to Confluence, either all at once or one by one.

## Design decisions

**One decision at a time.** Cognitive load is the enemy of good editing. Seeing one issue with clear options produces better choices than seeing all of them at once.

**Match the format to the decision.** Multiple choice for the obvious ones keeps momentum. Open questions for the nuanced ones keep the author in charge of their own voice.

**Short turns, no commentary.** The tone rule is "state the issue, present the options, wait." I'm making decisions, not rereading analysis.

**Batch by default.** Holding approved changes for a single Confluence update cuts down on version noise in the page history.

**"I did it myself" is a valid answer.** Sometimes the fastest fix is a manual one. The skill marks it done and moves on without fuss.

This small skill is a good example of a broader habit: designing the *experience* of receiving feedback, not just the feedback itself.
