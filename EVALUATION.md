# Evaluation Plan: Does Persona Diversity Beat Repeated Review?

### A seeded-error study comparing a persona panel against repeated reviews from one persona, on the same model and the same budget

Status: protocol, pre-registered in this repository before any study run · Version 1.0 · 5 November 2026
Author: Raphael Malikian · ORCID 0009-0008-4326-4205

---

## 1. The challenge this study answers

The claim at the centre of this system is that a panel of reviewers with different personas and experience buckets catches problems that repeated reviews from a single persona miss, because different reviewers have different blind spots.

That claim is currently **untested**. The system launched with a worked example from real use, and real use shows the panel produces different, non-overlapping comments. It does not show that the difference comes from persona diversity rather than from simply running more reviews. Any panel of six runs will catch more than one run, whatever the personas say. A fair test has to separate those two explanations:

- **Ensemble effect:** more independent runs catch more errors, personas irrelevant.
- **Diversity effect:** at the same number of runs, the same model and the same total budget, varied personas catch errors that a repeated single persona systematically misses, and the misses that remain are less shared.

This protocol is written so the diversity claim can fail. If the repeated single persona matches the panel, the honest conclusion is that persona selection adds cost and ceremony without detection benefit, and the protocol in this repository should be revised to say so.

The challenge was put to the author in a public comment on the launch post on 5 November 2026. This study exists because that comment was right.

## 2. Study question and hypotheses

**Question.** In pre-submission peer review of clinical AI and medical research papers, does a 6-reviewer persona panel detect more seeded errors, and leave fewer shared blind spots, than 6 repeated independent reviews from one persona, holding model, manuscript set and total token budget constant?

**H1 (primary).** The persona panel has higher seeded-error recall than the repeated single persona arm, paired by manuscript.

**H2 (blind spots).** The proportion of seeded errors missed by every review in an arm (shared blind spots) is lower in the persona panel arm.

**H3 (where diversity should show up).** The panel advantage, if any, concentrates in cross-domain errors (ethics and governance, patient impact, literature position, reporting standards) rather than in-domain errors for a strong single persona (for example, statistical errors when the repeated persona is a statistician). A panel win driven entirely by one domain still counts, but it will be reported by domain, not pooled into a headline.

**H0, stated plainly.** At matched budget, persona diversity adds nothing over repeated review. This is a live outcome, not a rhetorical one.

## 3. Design

### Arms (all runs: same model, same version, same temperature, independent sessions, no shared context)

| Arm | Reviewers per paper | Persona |
|---|---|---|
| A. Persona panel | 6 | The panel the Persona Selector assigns for that paper, per `PERSONA_SELECTION.md` |
| B. Repeated single persona (generic) | 6 | One generic "experienced peer reviewer" prompt, repeated in 6 independent sessions |
| C. Repeated single persona (strongest specialist) | 6 | The single bucket best matched to each paper's main method, repeated 6 times. Included so a panel win cannot rest on Arm B being weak by construction |

### Budget matching
- Total token budget per paper is fixed in advance and identical across arms: the panel's measured spend on the first paper sets the cap, stated in the study log before Arm B and C runs begin.
- Review length is capped by the same report template in all arms.
- Any run that hits the cap is filed as-is. No arm gets a second attempt.

### Manuscripts
- 12 papers: a mix of the author's own published papers (used with seeded changes, so the seeded version never replaces the published record), open-access clinical AI and health research papers under licences that allow derivative study use, and synthetic papers written for this study.
- Papers span at least four article types from the panel matrix: systematic review or meta-analysis, clinical AI model paper, open-source or software analysis, commentary.
- Reviewers in every arm are blind to which errors were seeded, how many, and to the other arms' results.

### Seeded errors
Each paper receives 10 seeded errors, 120 in total, drawn from a fixed taxonomy tied to the protocol's twelve review domains (`PROTOCOL.md` Section 2). The seeding catalogue is written and committed to this repository **before** any review run, and held by a study member who does not review.

Taxonomy (at least one per paper from each of the first six, the rest rotating):
1. Number inconsistency: a figure in the abstract or text that disagrees with the table or dataset.
2. Statistical error: wrong denominator, interval that cannot follow from the stated numbers, or an estimator named in methods and a different one reported in results.
3. Citation error: a fabricated reference, or a real reference cited for a claim it does not support.
4. Claim past the evidence: causal language on observational data, or a conclusion stronger than the results section supports.
5. Spin: a null or mixed primary result framed as positive in the abstract.
6. Methods drift: a post hoc analysis presented as pre-specified, or an eligibility change between methods and results.
7. Missing limitation: removal of a limitation the design plainly carries, replaced with a generic one.
8. Ethics or governance gap: patient-level data with the governance statement removed or contradicted.
9. Reporting gap: a required checklist item claimed in text and absent in the paper (for example, no flow diagram numbers that reconcile).
10. Literature gap: removal of the strongest disagreeing prior paper, with the gap claim left standing.
11. Figure error: a mislabelled axis, swapped group labels, or a forest plot without a summary diamond where one is claimed.
12. Patient-impact gap: a downstream harm or burden the intervention plainly carries, absent from the discussion.

Severity is assigned at seeding time (Blocker, Major, Minor, per `PROTOCOL.md` Section 3) by the seeder, before reviews, and is part of the ground truth.

### Scoring
- Two human scorers, blind to arm, match every review comment against the ground-truth catalogue. A seeded error counts as detected if a comment identifies the problem and its location, at any severity. Severity grading is scored separately.
- Disagreements between scorers are settled by reading the comment and the paper, and logged. Inter-scorer agreement is reported.
- Comments that flag no seeded error and no genuine problem in the paper count as false positives. Scorers also record genuine unseeded problems a review found, because a system that only finds what was planted is not the goal.

## 4. Outcomes

**Primary:** seeded-error recall per arm (detected / 120), compared paired by manuscript.

**Secondary:**
- Shared blind spot rate per arm: errors missed by all 6 reviews in that arm.
- Per-domain recall (the twelve domains), reported in full, not cherry-picked.
- Unique detections: errors found by exactly one reviewer, by arm and by persona bucket. This is the direct read on whether personas partition the error space.
- Reviewer overlap: pairwise agreement between reviewers in an arm on which errors they found. The diversity hypothesis predicts lower overlap in Arm A at equal or higher recall.
- False positive rate per arm, and severity-grading accuracy against the seeded severity.
- Cost per detected error, and cost per unique detection, at the matched budget.

## 5. Analysis

- Primary comparison is paired by manuscript: per-paper recall in Arm A vs Arm B, and Arm A vs Arm C, reported as differences with 95% confidence intervals, with a paired test named in the study log before unblinding.
- Per-domain results are descriptive with intervals. No pooled headline is published without the domain table beside it.
- All 120 seeded errors are accounted for in the report, detected or not, by arm. There is no excluded-error category created after the runs.

## 6. Threats to validity, named in advance

- **Same-model correlation.** All personas run on one model, so shared blind spots may reflect the model's limits rather than the personas'. That is the point of H2: the study measures how much persona variation reduces shared misses *within* one model, and says nothing about cross-model panels. A follow-up with mixed models is out of scope here and will not be smuggled into the conclusions.
- **Seeded errors are cleaner than real errors.** Real flaws are ambiguous in a way planted ones are not. Detection rates here are an upper bound on real-world performance, and the report will say so.
- **The author's own papers are in the set.** Scorers are blind to arm, seeders do not review, and synthetic and external papers are included so the set is not all home ground.
- **Persona prompts could win by length, not content.** The matched token cap and shared report template exist to block that route.

## 7. Reporting and openness

- This protocol, the seeding catalogue (published after the runs, so reviewers stay blind during them), the scoring sheets, and the full results, including a null result if that is what comes out, will be published in this repository and deposited on Zenodo with a DOI.
- If the result is null or negative for the panel, `README.md` and `PROTOCOL.md` will be amended in the same release to state the finding where the diversity claim is made. A test the system can fail, whose failure changes the system's own documentation, is the only kind worth running.
- No part of this study is described as journal peer review. It is a methods evaluation of a pre-submission tool.

## 8. Status

Protocol committed 5 November 2026. Seeding catalogue and manuscript set are the next step. Progress is tracked in the repository issue: "Validation study: persona panel vs repeated single persona on seeded errors".
