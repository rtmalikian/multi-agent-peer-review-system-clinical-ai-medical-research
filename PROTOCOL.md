# Multi-Agent Peer Review Protocol

### Looped gates before preprint or journal submission, with a persona-based panel chosen per article

Version 1.0 · 5 November 2026 · Raphael Malikian · ORCID 0009-0008-4326-4205

This protocol governs pre-submission peer review for research papers, systematic reviews, meta-analyses, clinical AI and health technology papers, digital health studies and scholarly commentaries. It sits between a finished draft and every external step: preprint deposit, journal submission, arXiv posting, Hugging Face release and conference abstract submission.

---

## 1. Rules that outrank everything else

**Rule 1. Honesty about what this is.** This is pre-submission peer review by AI agents under a human author's direction. It is never called journal peer review, external peer review or independent peer review in any manuscript, cover letter, post or application. The approved wording is: "The draft received structured multi-agent pre-submission peer review under the author's published protocol. The human author reviewed every comment and is accountable for the final text."

**Rule 2. One accountable human.** Agents review. The human author decides, revises and signs off. No agent verdict, however unanimous, submits a paper. No agent disagreement, however inconvenient, is deleted from the record.

**Rule 3. Independence first.** Every reviewer works in a separate session, with the manuscript and its materials only. No reviewer sees another review, a prior draft's reviews, or the author's preferred conclusion before filing their own report. Independence is what makes a panel worth more than one review read five times.

**Rule 4. A Blocker cannot be averaged away.** Severity is not a vote. One reviewer's Blocker outweighs five Accept recommendations until it is fixed or the handling editor shows, in writing, that the Blocker rests on a misreading.

**Rule 5. A comment is answered in the text, or it is not answered.** "Noted", "clarified" and "addressed in discussion" without a tracked change in the manuscript, table, figure, analysis or declarations counts as open. The response matrix links every comment to a page, a change, or a reasoned rebuttal the re-reviewer accepts.

**Rule 6. Numbers are traced, not trusted.** At the final gate, every headline number in the abstract, results and conclusions is traced to the dataset snapshot or analysis output for that paper. A number that cannot be traced is removed or corrected, never explained away.

**Rule 7. Citations are verified, not assumed.** Every reference is checked against a real source: author, year, title, journal or server, and that the source says what the paper claims it says. A citation that cannot be verified does not ship.

**Rule 8. No gate is waived for a deadline.** A paper that misses a submission window because it is still in a revision loop is a paper the system worked for. The loop is the point.

**Rule 9. The record is kept.** Panel assignment sheet, every review, the editorial decision, the response matrix, every loop count and the final sign-off are saved in the paper's own folder, beside the manuscript. A paper with no review record is treated as unreviewed.

**Rule 10. Safety and authority limits are review items.** Reviewers must flag any passage that reads as individual clinical advice, any medication recommendation, any claim about a licence, registration or affiliation the author does not currently hold, and any use of patient-level data without a stated governance basis. These flags are Blockers by definition.

---

## 2. What comprehensive peer review must examine

A review panel, between its members, must cover all twelve domains. The handling editor checks coverage at Gate 3 and sends the paper back if a domain was left unexamined.

### 2.1 Question, contribution and originality
- Is the research question stated in one place, in plain words, with the population, intervention or exposure, comparator and outcome where the study type needs them?
- What does this paper add? A new dataset, a new method, a replication, a correction, a synthesis, a worked example? If the contribution cannot be named, that is a Major.
- Has the same question been answered since the literature search was run? Reviewers check for very recent competing papers.

### 2.2 Literature position
- Are the strongest prior papers cited, including the ones whose findings cut against this paper?
- Is any cited paper described as showing something it does not show?
- Is the search or source date stated, so a reader knows how current the position is?

### 2.3 Design and methods
- Could this design answer this question? Design-question mismatch is a Blocker.
- Eligibility criteria, sampling, setting, dates, comparators, outcome definitions and denominators: stated, fixed in advance where the study type requires it, and followed in the results.
- Deviations from a protocol or a stated plan are listed as deviations, with reasons, never absorbed silently.
- For AI studies: model names and versions, prompts or prompt location, training and evaluation data separation, human oversight, and failure handling.
- For open-source analyses: the exact query, date, inclusion rules and snapshot file that produced the dataset.

### 2.4 Statistics and quantitative claims
- Model and estimator named, with a reason. Intervals reported, not point estimates alone.
- Denominators present for every percentage. Heterogeneity, multiplicity and missing data handled and reported where they apply.
- Poolability judged per outcome in a synthesis. An outcome that cannot be pooled is reported as a finding, not rescued by redefinition.
- Every number in the abstract and conclusions matches a table, a figure or the dataset. Rounding is consistent.
- Sensitivity or robustness checks present where a single choice could flip the headline result.

### 2.5 Results, claims and tone
- Each claim sits in the same paragraph as its evidence. Bold claims are welcome when the paper's own data backs them in that paragraph, and are Majors when they do not.
- Abstract, title and conclusions stay inside the results. A title that promises more than the study delivers is a Major.
- Spin check: favourable framing of null or mixed results, selective reporting of secondary outcomes, and causal language on observational data are all flagged by name.

### 2.6 Bias and limitations
- Limitations are specific to this study: which bias, from which design choice, pushing the result in which direction, by roughly how much if that can be said.
- Generic limitation paragraphs ("small sample, more research needed") are returned for rewriting.
- Author-position bias is a legitimate review topic: where the author built the thing being evaluated, the paper must say so and the panel must test the claims harder, not softer.

### 2.7 Ethics, privacy, safety and governance
- Human participants, patient data, scraped data and community data each need a stated basis: consent, ethics review, public data terms, or a reason no approval was required.
- No re-identifiable examples. Quotes, screenshots and case details are checked for identifiers.
- Clinical safety: no individual treatment advice, no dosing, no instruction a reader could mistake for a recommendation for their own care.
- Regulatory and authority claims checked against fact: licences, registrations, affiliations, endorsements.

### 2.8 Reporting standards
- The correct checklist for the study type is completed and checked item by item against the manuscript at Gate 6: PRISMA 2020 and PRISMA-S for systematic reviews, CONSORT (and CONSORT-AI where relevant) for trials, STROBE for observational studies, STARD for diagnostic accuracy, TRIPOD+AI for prediction models, CARE for case reports, SRQR or COREQ for qualitative work, CHEERS for economic evaluations.
- A checklist claim in the manuscript ("reported per PRISMA 2020") with no completed checklist in the paper's folder is a Major.

### 2.9 Reproducibility and materials
- Dataset snapshot, analysis code or worked calculations, search strings, extraction sheets and figure files are present, named and dated.
- Versions recorded: software, models, prompts, databases and search dates.
- A reviewer who could not, in principle, check a headline result from the materials provided files a Major.

### 2.10 Clarity, structure and audience
- The paper follows the house structure: title page, structured abstract, introduction with purpose and research questions, methods, results with tables and figures, discussion, conclusions with future work, declarations, references.
- A reader one specialty over can follow the argument. Jargon is explained at first use.
- Tables and figures stand alone: title, denominator, units, abbreviations spelled out.

### 2.11 Declarations and transparency
- Funding, conflicts of interest, author contributions and data availability statements are present and accurate.
- A factual AI-assistance note is present in the declarations, and the pre-submission peer review statement uses the Rule 1 wording.
- The public framing rule holds throughout: the author is described as a healthcare founder and operator who bootstrapped and ran a direct primary care clinic as CEO, now building clinical AI. No wording presents the author as currently licensed or practising, and no wording uses a retired-status label for the author.

### 2.12 Venue fit and submission package
- Scope, article type, word count, reference style and figure limits match the target venue.
- Cover letter claims match the paper. No claim in the letter is stronger than the abstract.
- Preprint metadata (title, abstract, keywords, licence, author identifiers including ORCID) match the manuscript exactly.

---

## 3. Severity taxonomy and decisions

### Severity, per comment

| Level | Meaning | Examples |
|---|---|---|
| **Blocker** | The paper must not be submitted while this stands | Design cannot answer the question; a headline number does not trace to the data; an unverifiable citation; a safety or authority problem under Rule 10; patient data with no governance basis |
| **Major** | Submission would mislead a reader or a journal reviewer if unfixed | Claim past the evidence; missing key literature; wrong or unexplained analysis choice; generic limitations; missing checklist; spin in the abstract |
| **Minor** | Should be fixed in this loop, does not block alone | Unclear passage, missing denominator in a secondary table, inconsistent rounding, unexplained abbreviation |
| **Nit** | Optional polish | Word choice, layout, a reference format slip |

### Decisions, per round (Gate 3)

- **Accept.** No Blocker, no Major, Minors fixed or accepted with reasons. Proceed to Gate 6.
- **Minor revision.** No Blocker, Majors absent or answerable with text and table changes only. One loop expected.
- **Major revision.** Any Blocker, or Majors that need new analysis, new literature work or restructuring. Full re-review at Gate 5.
- **Reject and resubmit.** The question, design or dataset cannot support a paper in this form. The paper returns to drafting, and a later version enters at Gate 0 as a new review. This decision is a success state for the system when it is right: it is the gate doing its job before a journal editor has to.

---

## 4. The gates in detail

### Gate 0. Editorial triage
Input: manuscript, dataset snapshot, figures, references, target venue note.
Checks: article type named; materials complete; no Rule 10 problem visible on a first read; venue exists, is free to submit to, and fits the scope.
Output: a one-page triage note, or a return with reasons. Triage takes minutes. Its job is to stop an incomplete paper consuming a full panel.

### Gate 1. Persona assignment
The Persona Selector reads the paper and builds a panel of 5 to 7 reviewers from the buckets in `PERSONA_SELECTION.md`. For each pick it records: persona, experience bucket, years and setting the persona carries, the specific risk in this paper that persona is there to catch, and what that reviewer must not do (for example, the patient reviewer does not rule on model choice; the statistician does not rule on clinical importance).
Buckets not chosen are listed with a reason. A panel with no sceptic, or with no reviewer matched to the paper's main method, fails this gate automatically.

### Gate 2. Independent review
Each reviewer gets: the manuscript, the materials, their persona card, the review domains relevant to their bucket, and the report template. Nothing else.
Each report contains: a summary in the reviewer's own frame, an overall recommendation, comments graded Blocker, Major, Minor and Nit, each comment tied to a page, section, table or line, a check of the domains in their remit with a pass or a flag for each, and one paragraph answering: "If this paper is published as it stands, what is the worst true thing a critical reader could say about it?"
Reports are filed before any reviewer sees another report. Late reports do not hold the gate open past the round deadline the orchestrator sets; a missing remit is noted at Gate 3 and covered by the handling editor or a substitute reviewer from the same bucket.

### Gate 3. Editorial synthesis
The handling editor agent reads all reports and the manuscript, and produces:
- a coverage check across the twelve domains in Section 2,
- a merged comment list that preserves disagreements in full (where two reviewers disagree, both positions are quoted, and the editor rules or escalates, never edits one away),
- a decision under Section 3,
- a revision brief ordered by severity, Blockers first.
Any Blocker the editor believes rests on a misreading is returned to that reviewer with the passage cited, once. If the reviewer stands by it, it stays a Blocker and goes to the human author.

### Gate 4. Revision
The author (human, or an author agent drafting for human approval) produces:
- a revised manuscript with changes visible or logged,
- a response matrix: every comment, its severity, the action taken, and where in the revised text the change lives, or a rebuttal with evidence,
- new analysis, tables or literature work where a comment required it, with the dataset or search record updated and re-dated.
Words-only answers to comments that demand a change are marked unanswered by the orchestrator and the loop continues.

### Gate 5. Re-review
Each reviewer who raised a Blocker or a Major re-reads their own comments against the revised draft and marks each: Resolved, Partly resolved (with what remains), or Unresolved.
Partly resolved and Unresolved Majors loop back to Gate 4. A reviewer may raise a new Major at re-review only if the revision introduced it, and must say so.
Loop counting: one pass through Gates 4 and 5 is one loop. The gate log records the loop count per paper.

### Gate 6. Final integrity gate
A fresh agent, who did not review the paper, runs the integrity checklist:
- every reference verified against its source,
- every headline number traced to the dataset or analysis output,
- abstract, title, tables, figures and conclusions mutually consistent,
- the reporting checklist for the study type completed and matching the text,
- every figure and table page visually inspected in the rendered PDF,
- declarations, conflicts, funding, data availability, AI-assistance note and the Rule 1 peer review statement present and accurate,
- preprint and submission metadata matching the manuscript,
- de-AI copy audit passed for any public-facing text that ships with the paper (abstract, cover letter, posts).
Output: a signed gate log entry, Pass or Fail with the failed items listed. A Fail loops to Gate 4 regardless of how many loops have already run.

### Escalation
After three loops, any Blocker or Major still open stops the system. The orchestrator writes a one-page escalation for the human author: the open point, the reviewer's position, the author's position, and the three honest options (fix it, narrow the claim so the point no longer applies, or withdraw the paper from this round). The human author's decision is recorded in the gate log. There is no fourth silent loop and no override that leaves no trace.

---

## 5. Anti-groupthink and quality controls

- **Separate sessions, separate framings.** Reviewers are not given a shared summary, a house opinion or the author's hopes for the paper.
- **The sceptic is structural.** Every panel includes a sceptic whose remit is the strongest honest case against the headline claim. A panel report set with no serious disagreement in it is treated as a warning sign at Gate 3, not a comfort.
- **Persona rotation.** Where the same paper type recurs (a weekly series, for example), the selector varies persona backgrounds, settings and seniority between papers, so the same blind spots do not recur on schedule.
- **Reviewer calibration.** Persona cards specify seniority in years, setting and past failure modes (the methods reviewer who over-values novelty, the clinician who under-values statistics). A calibrated flaw makes a persona more useful, not less, because the handling editor can weight the report.
- **Disagreement is data.** Inter-reviewer disagreement counts and the topics they cluster on are logged per paper, in the same spirit as reporting screening agreement and extraction discrepancy rates in a systematic review.
- **No reviewer edits the manuscript.** Reviewers comment. Authors revise. Editors decide. Mixing those roles in one agent collapses the friction the system exists to create.

## 6. Outputs per paper

Saved in the paper's own folder before any external submission:

1. `peer-review/panel-assignment.md` (Gate 1)
2. `peer-review/reviewer-1.md` through `reviewer-N.md` (Gate 2)
3. `peer-review/editorial-decision.md` (Gate 3, one per round)
4. `peer-review/response-matrix.md` (Gate 4, updated per loop)
5. `peer-review/rereview.md` (Gate 5, per loop)
6. `peer-review/gate-log.md` (Gates 0 to 6, with loop count and final sign-off)

## 7. Relationship to other standards

This protocol is a pre-submission layer. It does not replace journal peer review, ethics review, PROSPERO registration, trial registration, or a reporting guideline. It borrows its habits from them: COPE guidance on peer review conduct, ICMJE recommendations on manuscript preparation and disclosure, the EQUATOR reporting checklists, and the RAISE principles for reporting AI involvement in evidence work. Where this protocol and a target journal's instructions conflict, the journal's instructions win for that submission, and the conflict is logged.
