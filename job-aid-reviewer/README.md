# Job Aid Reviewer

**An AI quality reviewer for a performance-support library, built for a product organization at a healthcare data company.**

## The problem

I was building a library of job aids for a product team: short, practical guides a PM opens when they're stuck on a specific task like writing a JTBD statement or sizing a market. Every job aid followed the same seven-part PERFORM structure (Purpose, Entry Conditions, Required Inputs, Follow the Process, Obstacles, Resources, Measure Success) and each one closed with an "AI Opportunity" section teaching PMs to use AI on that step.

At that volume, quality drifts. One page tells PMs to "gather the relevant data" without saying what data. Another points to a section of the planning template that doesn't exist. Another has an AI section that's just a generic prompt. And the person who decides whether the library is trustworthy enough to give her team is a senior director who will notice all of it.

I needed a reviewer that held every page to the same standard she would.

## What it does

1. Pulls the live job aid from Confluence (never a stale copy).
2. Checks any claim about the downstream planning template against the real template pages.
3. Scores the page 1 to 5 on seven dimensions: instructional clarity, client context accuracy, PM best practice, worked example quality, PERFORM completeness, Confluence findability, and AI Opportunity quality.
4. Writes specific observations, plus 3 to 6 hard questions in the voice of the senior director.
5. Drafts proposed fixes, then waits. Nothing changes in Confluence until I approve it.

## Design decisions

**The reviewer is a persona, not a checklist.** Framing the review through a real executive's eyes ("What data, specifically, and from what system? If the PM has to ask someone, this step has failed.") produced sharper findings than neutral criteria did. It also prepared me for the actual review meeting.

**Verify against ground truth every time.** Early job aids kept telling PMs their work "feeds the Discover section of the Brief." There is no section by that name. So the skill now fetches the real template and checks names word for word, instead of trusting memory or a previous review.

**The AI section has six required parts, and the failure mode matters most.** A practice prompt alone teaches nothing. Each AI Opportunity section needs a step-specific framing, the context to gather, a prompt that tells AI to argue against the PM, a list of what AI can actually help with, a *named* way AI tends to get this step wrong, and a statement of what the PM still owns. A section with no named failure mode can't score above 3. That's the piece that stops people from accepting the first plausible answer.

**Teach the practice on its own authority.** Job aids don't cite outside authors or named frameworks. If the method later diverges from a book, the job aid shouldn't break.

**Edit surgically.** When approved changes go back to Confluence, the skill edits the page's HTML in place and preserves Confluence's internal IDs, instead of regenerating the page and losing formatting.

## How it connects

Its output feeds the [Job Aid Improvement Interviewer](../job-aid-improvement-interviewer/), which turns the list of proposed fixes into one-at-a-time decisions.

*Client names, people, page IDs and product names are replaced with `[placeholders]`. The method is unchanged.*
