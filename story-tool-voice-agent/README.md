# Story Tool

**A voice agent that helps people find the story they tell themselves about a frustrating pattern, and retell it in a way that's true and powerful.**

> **Status:** pilot, built on ElevenLabs' voice agent platform.

## The problem

Most of us have a pattern that keeps showing up in our work or life, and a tidy one-sentence story that explains it. The story usually gets easy agreement, so we stop questioning it. But a story that earns quick nods is often protecting something, and the real change starts when someone notices where the story is a perspective rather than the whole truth.

That kind of noticing usually happens with a good coach, and coaching doesn't scale. I wanted to see whether a carefully designed voice conversation could guide someone to that first moment of insight, then hand them on to a coach for the deeper work.

I built it after finding my own story with my coach's help. For years I explained why jobs kept ending with "tech is volatile." The pattern turned out to be in how I took responsibility for other people's moods.

## What it does

A calm AI guide walks the person through seven stages in a spoken conversation:

1. **The pattern:** something that keeps happening and frustrates them
2. **The story:** how they explain it, in one sentence, and how people react
3. **The series:** whether the pattern followed them when the situation changed
4. **The flinch:** the part of the story they least want questioned, and what it protects
5. **The third explanation:** if it isn't all them and it isn't all others, what else is shaping it
6. **The rewrite:** the pattern retold as a strength, in their own words
7. **The fork:** keep practicing the new story, take it to a coach, or both

Return visits open with a short check-in: did the story show up, what did you feel, what did you do?

## Design decisions

**Voice, not text.** Reflection happens out loud. Turns are one to three sentences, one question at a time, and the guide lets silence happen instead of filling it.

**The flinch is the heart.** The rewrite only comes after it. Reframing a story you haven't looked at honestly just produces a nicer-sounding version of the same story.

**Curiosity, never verdicts.** The guide never says "you sound defensive." When it notices a sudden "but" or a long justification, it asks what shifted and what it might be protecting, never framing it as catching the person out.

**A human story, honestly told.** At each stage the guide can share a moment from my own experience, always as "Rudd shared that..." and never as its own. It says plainly that it's an AI and not a coach or therapist.

**Safeguards override everything.** It never diagnoses or hints at a condition. If someone mentions trauma, self-harm or serious distress, it stops the exercise, points them to a counselor and a crisis line, and stays warm. It's designed to point people toward trained help, not to be the place they work through heavy material.

**Consent up front.** The first message says it's a pilot, conversations are saved, I'll read them to improve the experience, and they can ask for everything to be deleted.

**Ends with a handoff, then reinforcement.** The fork points people toward a coach or other professional, and the check-ins help the new story become a habit instead of a one-time insight.

## Files

`agent-setup.md` holds the full setup: the first message, the system prompt, voice guidance and data-retention settings, ready to paste into the agent.
