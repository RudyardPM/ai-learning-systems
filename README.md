# AI Learning Systems

Most training ends when the session does. People nod, go back to their desks, and do what they did before. I build learning systems that keep working after I'm gone, and lately a lot of that work has been building AI agents ("skills") that coach, review, and practice alongside people in their real work.

This repo holds an assessment and four of those skills. Each folder has the actual source (a `SKILL.md` with the instructions the AI follows, or the assessment page) and a README that explains the problem it solves and why I designed it the way I did.

## Start here: the assessment

**[AI Learning Mental Models](ai-learning-mental-models/)**: a 4-minute self-assessment built around one moment. When AI hands you an answer, what do you do next? 21 real-world scenarios show which of seven mental models you lean on most, and which one you barely use. **[Take it here](https://claude.ai/artifact/DvfQsp2fDayKfgEkwbZ4g4).**

## The skills

| Skill | What it does | Why it matters |
| --- | --- | --- |
| [Job Aid Reviewer](job-aid-reviewer/) | Scores a job aid against a 7-dimension rubric and drafts fixes for approval | Quality control for a performance-support library, so content holds up when an executive reads it |
| [Job Aid Improvement Interviewer](job-aid-improvement-interviewer/) | Walks the author through each proposed fix, one decision at a time | Turns a long review into fast, owned decisions instead of a wall of feedback |
| [AI Product Coach](pm-potential-ai-product-coach/) | Coaches a PM live through using AI as a thinking partner on real work | Builds the habit of pressure-testing your own thinking, not outsourcing it |
| [PM Interview Mock Tutor](pm-interview-mock-tutor/) | Runs a realistic mock PM interview with short tutor nudges in the moment | Practice with feedback at the moment of the mistake, not in a summary afterward |

## How they fit together

The first two are a pair. I built a library of job aids for a product organization using the 5D framework (Discover, Define, Design, Deliver, Drive), with every job aid following the same PERFORM structure. The reviewer audits each page. The interviewer takes the reviewer's proposed fixes and walks me through them one at a time, then pushes the approved changes back to Confluence.

The coach and the tutor are both practice environments. One is for PMs doing real work with AI. The other is for PMs preparing to interview.

The assessment comes first. It shows which habits a person or team leans on and which they skip, and the coach then practices the missing ones on real work.

## The design principles underneath all of it

**Reinforcement over one-time events.** A workshop is race day. These tools are the training base: something people can return to at the moment they need it.

**AI challenges the thinking, it doesn't replace it.** Every coaching skill makes the person state what they believe first, instructs the AI to argue against it, names a specific way AI could be wrong, and hands the decision back. No skill here makes the call for the user.

**Teach at the moment of need.** Feedback lands best when the mistake is fresh. The mock tutor drops a one-line nudge mid-conversation instead of saving everything for the end. The improvement interviewer asks for one decision at a time.

**Specific beats general.** Rubrics name exact failure patterns ("steps that say 'gather data' without saying what data, from where"). Vague criteria produce vague reviews.

**Humans approve, then AI acts.** Anything that changes a real document waits for explicit approval.

## Using these

Each `SKILL.md` is written for Claude's skills feature, but the instructions read as plain English and work as a system prompt in most AI tools. The job aid skills reference a client's Confluence setup. Details from that engagement are replaced with `[placeholders]`.

## About me

I'm Rudyard Hopkins. I run [PM Potential](https://pmpotential.com), helping product organizations build learning habits that outlast any one engagement. My background is product management. My focus now is talent development and making change actually stick.
