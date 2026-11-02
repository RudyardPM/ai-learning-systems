---
name: job-aid-reviewer
description: "Review a 5D Framework job aid for content quality, client context accuracy, PM best practice alignment, worked example quality, PERFORM structure completeness, knowledge-base optimization, and AI Opportunity section quality. Use whenever the user asks to review a job aid, audit content quality, run a quality check, check a job aid against the standard, or asks whether a job aid is ready. Also use when the user says \"review this page\" or references a job aid by its 5D ID (e.g. Discover 1.2, Design 2.3)."
---

# 5D Job Aid Reviewer

A structured review skill for auditing 5D Framework job aids published in a client's Confluence space. Reviews one job aid at a time. Produces a scored assessment, qualitative observations, clarifying questions framed from a senior product operations leader's perspective, and draft proposed improvements for the consultant's approval.

> **Portfolio note:** This is a sanitized version of a skill built for a real client engagement with a healthcare data company. Client names, people, page IDs and product names have been replaced with placeholders in `[brackets]`. The method is unchanged.

---

## Context

**Client:** [Client] — healthcare data company. Follow the client's own brand styling for its name everywhere.
**Framework:** 5D (Discover, Define, Design, Deliver, Drive)
**Phase structure:** Each phase contains job aids organized as PERFORM sections (Purpose, Entry Conditions, Required Inputs, Follow the Process, Obstacles, Resources, Measure Success)
**Consultant:** PM Potential
**Reviewer persona:** The client's Sr. Director of Product Operations — the executive who reads these and decides whether to trust the content with her team
**Atlassian connector:** Available. Use `Atlassian Rovo:getConfluencePage` to pull live Confluence content before reviewing.

---

## Step 0 — Access the job aid

If the user names a specific job aid or provides a page ID or URL, fetch it immediately from Confluence using `Atlassian Rovo:getConfluencePage` with `contentFormat: "markdown"` and `cloudId: "[client-cloud-id]"`.

If the user provides a title only, search first using `Atlassian Rovo:search` to get the page ID, then fetch.

Do not proceed to review without reading the live Confluence content. The Confluence version is the authoritative source.

---

## Step 0.5 — Ground truth: the Initiative Brief template

Every job aid claim about "where this feeds" or "what section of the Brief this supports" must be checked against the real Initiative Brief template family, not assumed. Before finalizing any review that references the Brief, fetch and cross-check against the relevant page(s) below.

| Page | Page ID | Contents |
|------|---------|----------|
| `[Initiative Name] Brief` (main) | [page-id] | Summary → Problem Definition (A/B/C/D) → Business Rationale → Market Sizing and WTP Summary → Solution Definition (incl. 5-row Solution Validation table) → Proposed Path → Engineering Feasibility & Plan → GTM & Launch Strategy Summary |
| `[Initiative Name] - DISCOVER` | [page-id] | JTBD, What We Know / Need to Learn, Research Inputs (A/B/C), Capability/Story Map, Competitive Intelligence + SWOT + Counter-positioning, Win/Loss, Assumptions & Risks, Exit Criteria checklists |
| `[Initiative Name] - DEFINE` | [page-id] | Define-phase backup detail (fetch when a Define job aid references Brief content) |
| `[Initiative Name] - DESIGN` | [page-id] | A–G sections; G. Engineering Feasibility maps directly to job aids like Design 1.6 (risk table columns, dependency table columns, "Technically achievable as designed" as row 5 of Solution Validation) |
| `[Initiative Name] - DELIVER` | [page-id] | Deliver-phase backup detail |
| `[Initiative Name] - DRIVE` | [page-id] | Drive-phase backup detail |

**Critical fact:** there is no literal "Discover section" heading anywhere in the Brief family. Discover-phase work (JTBD, interview learnings, etc.) lives on the `- DISCOVER` sub-page and rolls up into the main Brief's **Problem Definition** section — not a section called "Discover." A job aid that tells the PM "this feeds the Discover section of the Brief" is imprecise at best and wrong at worst; the correct phrasing names the actual section (e.g. "Problem Definition" or "Research Inputs").

When a job aid makes a specific claim about Brief structure (a section name, a table's columns, a row count, a checklist), fetch the matching page above and verify the claim word-for-word before scoring. Do not rely on memory of a previous review's findings — Brief pages can change.

---

## Step 1 — Score across seven dimensions

After reading the page, score each dimension from 1 to 5 using the rubric below. Then provide qualitative observations for each.

### Scoring scale
| Score | Meaning |
|-------|---------|
| 5 | Excellent — no changes needed |
| 4 | Good — minor polish only |
| 3 | Acceptable — one or two meaningful gaps |
| 2 | Needs work — multiple issues affecting usefulness |
| 1 | Not ready — fundamental problem that blocks value |

---

### Dimension 1: Instructional Clarity
*Can a PM at the client follow this without asking anyone — including the consultant?*

**Check for:**
- Each step is actionable — the PM knows what to do, not just what to think about
- Decision points have clear criteria — when to advance, when to pause, when to go back
- The Standard Check at the end of Measure Success is specific enough to be self-evaluated
- Nothing requires interpretation — ambiguous language is the most common failure here
- Jargon is explained the first time it appears
- No step assumes knowledge not established in earlier steps or earlier job aids
- Any reference to a specific Initiative Brief section name, table, or field is verified against Step 0.5 — not paraphrased from memory

**Common failures the reviewer persona has flagged:**
- Job aids that describe a process without teaching the skill behind it
- Steps that say "gather data" without specifying what data, from where, in what format
- AI Opportunity sections that are generic prompts rather than client-specific thinking partners
- Referencing a Brief section by a name that does not exist (e.g. "the Discover section of the Brief" when the real section is "Problem Definition")

---

### Dimension 2: Client Context Accuracy
*Does this reflect how the client actually works — terminology, org structure, product vocabulary, and data architecture?*

**Check for:**
- The client's name follows its brand styling throughout
- Correct product vocabulary: [client product names], archiving, interoperability, data migration, interfaces, patient records — not generic SaaS language
- Org structure is reflected accurately: PMs receive escalation calls directly (no CSM layer), implementation engineers as a data source, sales reps as the commercial signal source
- Data signal sources are complete — not limited to customer interviews alone (also: escalation calls, Jira/ticket data, sales signals, usage data, external/regulatory signals)
- Economic units are client-specific: interface, archive, file, transaction, patient record, API call
- No CRM assumed where the client does not have one
- References to tools are accurate: Jira Product Discovery (JPD), Confluence, the client's LMS for courses

**Common failures:**
- Saying "consult your CRM" in a context where the client has no CRM
- Using generic data source language that excludes escalation calls as a primary channel
- A superseded worked example used where the approved replacement is more accurate
- Using the wrong economic unit for the product area being described
- Assuming a CSM (Customer Success Manager) layer exists between the customer and the PM — the client's PMs take escalation calls directly; any reference implying a CSM intermediary or hand-off should be flagged

---

### Dimension 3: PM Best Practice Alignment
*Are the product management concepts taught here correct — not just consistent with 5D, but sound in practice?*

**Check for:**
- JTBD statements follow correct format: When [situation], I want to [action], so that [outcome]
- Problem statements separate observation from conclusion
- Prioritization language is evidence-based, not opinion-based
- Discovery thinking is present — the job aid teaches the PM to validate, not assume
- The cost-of-inaction framing is outcome-oriented, not feature-oriented
- User stories follow INVEST criteria when present
- Acceptance criteria distinguish happy path, failure path, and compliance boundary (for PHI-sensitive contexts)
- Hypothesis statements are specific, testable, grounded, and solution-directional
- AI Opportunity sections teach the PM to use AI as a thinking partner — not as a shortcut that replaces thinking
- No named external framework, author, or methodology is cited by name inside the job aid text

**Flag (do not insert attribution):** If a concept is demonstrably incorrect or misleading from a PM practice standpoint, flag it as "conceptually at risk" and describe the concern without citing external frameworks by name in the job aid itself. Proactively flag any named external citation even when the underlying concept is factually correct — job aids should teach the practice on their own authority, not by attributing it to an outside person or book. Treat an accurate-but-attributed claim and an inaccurate-and-attributed claim the same way: both get flagged, and the proposed fix in both cases is to restate the idea in the job aid's own voice with no external name attached.

---

### Dimension 4: Worked Example Quality
*Is the worked example specific, realistic, and correctly framed for the client?*

**Check for:**
- The example uses a client-relevant product area (archiving, interoperability, data migration, patient record retrieval)
- The persona is specific — not "a user" or "a customer" but a named role (e.g. care transitions coordinator at a hospital network account)
- The example uses the correct economic unit for the product area
- The example follows through the full step — it does not stop halfway
- For PHI-sensitive contexts, compliance boundary requirements are present
- The example does not use a superseded framing where the approved replacement example is more accurate
- The example is internally consistent — numbers, names, and references do not contradict each other within the job aid
- If this job aid's worked example is continued, referenced, or built on in an adjacent job aid (same epic, sequential step numbers), any proposed change to the example is checked against those other job aids so the fix does not orphan a reference elsewhere — flag the other job aid(s) that would also need the coordinated edit rather than fixing this one in isolation

---

### Dimension 5: PERFORM Structure Completeness
*Are all PERFORM sections present, correctly used, and proportionate?*

**Check for:**
- **P — Purpose:** Answers "what does this job aid do and what question does it answer?" Not just a description — must include the orienting question.
- **E — Entry Conditions:** Specifies when to use this job aid AND what must be true before starting. Not just "use this when X" — must include prerequisite state.
- **R — Required Inputs:** Lists specific inputs, not categories. "CRM data" is a category. "Lost deal notes from the past 12 months in the CRM" is a specific input.
- **F — Follow the Process:** Steps are numbered, each has a "Why" rationale. No step is a list of things to think about — every step produces a tangible output.
- **O — Obstacles:** Names failure modes specific to the client's context — not generic PM cautions. Must include at least three obstacles.
- **R — Resources:** Links to predecessor and successor job aids. Not just a list of tools.
- **M — Measure Success:** Includes a Standard Check written as a self-evaluation test. The check must be specific enough that a PM can answer yes or no without asking for help.
- If this job aid's output is described as feeding the Initiative Brief, confirm (via Step 0.5) that the destination section actually exists and is named correctly — an output with no confirmed home in the real Brief structure is a completeness gap, not just a wording issue.

**Flag:** Missing sections, sections that exist but are empty or templated, steps without rationale, Standard Check that is not a yes/no question.

---

### Dimension 6: Confluence Optimization and Transferability
*Is this page structured to be discovered, used, and exported effectively?*

**Check for:**
- **Page title** is a natural language action phrase — what a PM would search for when stuck (e.g. "How to Write a User Story" not "Design 2.2")
- **Labels/tags** applied: check for phase label (discover, define, design), asset type label (job-aid, course, template), topic labels (jtbd, prioritization, pricing, etc.)
- **H1/H2/H3 heading structure** is consistent — Confluence AI uses headings for retrieval
- **Navigation links** to previous and next job aid are present (Next section / Previous section)
- **AI Opportunity section** is present and client-specific — not a generic prompt
- **Markdown export readiness:** headings are clean, no inline images that would not transfer, no Confluence-specific macros that would break in export
- **Cross-client transferability:** the content could be re-skinned for a different client without client-specific terms becoming blockers — client references are confined to examples and context callouts, not embedded in the instructional steps
- **Broken staging image URLs:** any image src beginning with `blob:` is a broken reference that will not render for readers — flag explicitly and by name, do not lump into generic "image" feedback
- Named external citations (see Dimension 3) are also a transferability problem, not just an attribution problem — flag under both dimensions

**Recommended tags to check:**
- Phase: `discover` | `define` | `design` | `deliver` | `drive`
- Type: `job-aid` | `short-course` | `template` | `reference`
- Topic: `jtbd` | `prioritization` | `customer-interview` | `business-case` | `prd` | `pricing` | `win-loss` | `hypothesis` | `acceptance-criteria` | `user-story`
- Status: `reviewed` | `draft` | `pilot`

---

### Dimension 7: AI Opportunity Section Quality
*Does this job aid's AI Opportunity section build genuine AI-enabled product thinking — or is it just a prompt?*

The AI Opportunity section is not a chatbot shortcut. It is a deliberate practice environment for developing AI-enabled PMs. The progression it is building toward is: **Assistant → Creative Ideation → Critical Thinking Partner → AI-Enabled Product Leader.**

The practice pattern that must be embedded in every AI Opportunity section:
**Assess → Gather context → Structure the request → Use AI → Reflect → Apply Product judgment**

**Six required components — check for all six:**

1. **Framing statement** — A 1–2 sentence statement about what AI can and cannot do in this specific step. Must be step-specific, not generic. Must make clear that AI challenges and extends thinking rather than replaces it.

2. **Relevant context guidance** — A bulleted list of the specific context the PM should gather before using AI. Context items must be specific to this step (e.g. "JTBD statement," "five actionability tests," "baseline value and source") — not generic ("background information").

3. **Structured practice prompt** — A full example prompt the PM can adapt. The prompt text itself (not just the closing section) must:
   - Instruct AI to act as a skeptical reviewer, not a confirmer
   - Ask AI to use only the information provided — no gap-filling with assumptions
   - Ask AI to make the strongest argument *against* the PM's current position
   - Explicitly state, in the prompt language, that AI does not make the final decision — the PM does. This statement must be inside the prompt the PM would actually paste, not only implied by a later section.
   - Reference the specific framework, criteria, or test relevant to this step

4. **What AI can help with** — A standalone bulleted list, separate from the framing statement, specific to this step. Not "AI can help you think through this." Specific: "AI can identify where the evidence supports or weakens the metric." If this list is merged into the framing statement rather than presented as its own list, treat component 4 as missing.

5. **Named AI failure mode** — One specific, named failure (e.g. "Causal leap," "False alignment") with:
   - What the failure looks like — a realistic example of AI producing the flawed output
   - Why it is wrong — what the PM needs to catch that AI missed
   - How to test for it — a specific action the PM takes to verify AI's conclusion

6. **Product judgment still matters** — A closing statement that names explicitly what the PM owns and is accountable for in this step, even after using AI.

**Common failures:**
- Generic prompt that could apply to any step in any framework ("Act as a product expert and review my work")
- No AI failure mode named — treating AI as reliable without teaching skepticism
- "Product judgment still matters" is absent or is a boilerplate closing
- Framing statement says AI "can help" without specifying what it challenges or extends
- Practice pattern (Assess → Gather context → Structure → Use → Reflect → Apply judgment) is absent
- Relevant context items are categories, not specifics
- "AI doesn't decide" is stated only in the closing section and never appears inside the actual prompt text
- "What AI can help with" is folded into the framing statement instead of standing as its own list

**Scoring guide for Dimension 7:**
- 5 — All six components present, step-specific, and correctly framed
- 4 — Five of six components present; minor gap in one
- 3 — Four components present; practice prompt present but not fully structured; OR no AI failure mode
- 2 — Prompt present but generic; missing three or more components
- 1 — No AI Opportunity section, or section is a single generic prompt with no supporting structure

---

## Step 2 — Produce the review output

Format the output as follows. Do not skip any section.

---

### JOB AID REVIEW — [Title] ([5D ID])
**Reviewed:** [Date]
**Confluence page:** [URL]
**Reviewer standard:** Senior Director of Product Operations

---

#### Scores

| Dimension | Score (1–5) | One-line verdict |
|-----------|-------------|-----------------|
| 1. Instructional Clarity | X | |
| 2. Client Context Accuracy | X | |
| 3. PM Best Practice Alignment | X | |
| 4. Worked Example Quality | X | |
| 5. PERFORM Structure Completeness | X | |
| 6. Confluence Optimization | X | |
| 7. AI Opportunity Section Quality | X | |
| **Overall** | **X.X** | |

Overall score = average of seven dimensions, rounded to one decimal place.

**Readiness verdict:**
- 4.5–5.0 → **Ready — no changes required**
- 3.5–4.4 → **Ready with minor polish**
- 2.5–3.4 → **Needs revision before this is used with the team**
- Below 2.5 → **Hold — fundamental issues to address first**

---

#### Qualitative Observations

For each dimension that scores below 5, write 2–4 specific observations. Name the exact section, sentence, or element that needs attention. Do not be general.

---

#### Clarifying Questions
*(Framed as questions a Senior Director of Product Operations would ask when reviewing this material with the consultant)*

Write 3–6 questions. These should be the questions the reviewer would ask in a review meeting that would be uncomfortable to answer without having done the work properly. Frame them as direct, executive-level questions — not gentle suggestions.

Examples of the right tone:
- "Step 3 tells the PM to 'gather the relevant data' — what data, specifically, and from what system? If the PM has to ask someone, this step has failed."
- "The worked example references a scenario that has been superseded. Why is this still here?"
- "The AI Opportunity section is identical in language to the generic prompt format we moved away from. What specifically does this teach our PMs that they could not figure out on their own?"
- "There is no mention of escalation calls as a signal source. Given that this is our primary direct-client channel, what is the PM supposed to do when their only customer contact is an escalation call?"
- "This job aid says it feeds the 'Discover section' of the Brief — there is no section by that name. Which actual section does this output belong to, and does the team know that?"

---

#### Proposed Improvements

For each dimension that scores below 4, write one or two draft improvements — specific edits or additions that would raise the score. Present each as:

**Issue:** [What is wrong]
**Proposed fix:** [Specific replacement text, new section, or structural change]
**Impact:** [Which dimension this addresses and by how much it would move the score]

Keep proposed fixes tight — this is for the consultant to approve and implement, not a full rewrite.

---

## Step 3 — Await approval

After delivering the review, ask: "Which of these proposed improvements would you like me to implement directly in Confluence?"

If the user approves one or more, use `Atlassian Rovo:updateConfluencePage` to implement only the approved changes. Do not make unapproved changes.

**Safe Confluence editing procedure:** Never edit from a markdown fetch — markdown loses panel/macro formatting (info panels, custom panels, expand macros). Instead: (1) fetch the page fresh with `contentFormat: "html"`; (2) use `getContentFormatGuide` if unfamiliar with a macro's HTML shape; (3) locate the exact block to change and make a precise, byte-level replacement rather than reconstructing the page; (4) preserve every `data-local-id` attribute on every div/paragraph touched or left untouched — these are Confluence's internal identity keys and must not be dropped, regenerated, or reordered; (5) submit the full modified HTML body via `updateConfluencePage` with a clear `versionMessage` describing what changed and why.

---

## Edge cases

**If the page has no AI Opportunity section:** Score Dimension 7 as 1. Flag as a gap in Dimension 5 (PERFORM structure) and Dimension 6 (Confluence optimization) as well. Note that the AI apprenticeship strategy requires this section in every job aid and it is being retrofitted across the library. In Proposed Improvements, draft a complete AI Opportunity section using all six required components, tailored to the specific step this job aid covers.

**If the AI Opportunity section exists but is a generic prompt only:** Score Dimension 7 as 2. Identify which of the six required components are missing and draft them in Proposed Improvements. The practice prompt must instruct AI to challenge, not confirm. The framing statement must be step-specific. The AI failure mode must be named with an example.

**If the AI Opportunity section has a prompt but no named AI failure mode:** Score Dimension 7 no higher than 3 regardless of other components. The AI failure mode is the most important teaching element — it is what prevents the PM from accepting AI's first plausible-sounding conclusion. Draft a named failure mode specific to the step in Proposed Improvements.

**If the page uses a superseded worked example:** Flag in Dimension 4 and point to the approved replacement example.

**If the client's name styling is wrong anywhere on the page:** Flag every instance in Dimension 2. This is a non-negotiable terminology standard.

**If the Standard Check in Measure Success is not a yes/no question:** Flag in Dimension 5. The Standard Check must be answerable without the PM asking anyone for help.

**If the page has no labels:** Flag in Dimension 6. Recommend the specific labels that apply based on phase and content type.

**If the job aid references the Initiative Brief and the reference does not match Step 0.5's ground truth:** Flag in Dimension 1 (clarity/accuracy of the claim) and Dimension 5 (completeness — does the output actually have a confirmed home). Propose the corrected section name or table reference rather than removing the Brief reference altogether — the connection to the Brief is usually valuable, just imprecisely worded.

**If the page is written as a narrative "course script" (Part 1 / Part 2 / Part 3, prose walkthrough) rather than PERFORM sections:** Score Dimension 5 low regardless of how good the narrative content is — PERFORM structure is a navigability and reference requirement, not just a stylistic preference. In Proposed Improvements, draft a restructuring into PERFORM sections that preserves the existing narrative content as the substance of Follow the Process, rather than discarding it.
