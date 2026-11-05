# Multi-Agent Peer Review System for Clinical AI, Medical Research and Health Technology Papers

### Persona-based AI peer reviewers. Looped editorial gates. No paper reaches a preprint server until it has survived review.

[![Licence: Attribution, Non-Commercial](https://img.shields.io/badge/Licence-Attribution--NonCommercial-orange)](LICENSE.md)
[![Process: Looped gates, not a single pass](https://img.shields.io/badge/Process-Looped%20gates-brightgreen)](#the-looped-gates)
[![Companion: Cochrane-level review process](https://img.shields.io/badge/Companion-Cochrane--level%20review%20process-blue)](https://github.com/rtmalikian/multi-agent-cochrane-level-review-process)

**By Raphael Malikian**, independent researcher, healthcare founder and operator who bootstrapped and ran a direct primary care clinic as CEO, now building clinical AI. ORCID [0009-0008-4326-4205](https://orcid.org/0009-0008-4326-4205) · rtmalikian@gmail.com · GitHub [@rtmalikian](https://github.com/rtmalikian) · X [@rtmalikian](https://x.com/rtmalikian)

---

## What this is

A complete, reusable **multi-agent peer review system** for research papers, systematic reviews, meta-analyses, clinical AI papers, digital health studies, health technology assessments and scholarly commentaries.

Before any article is submitted for preprint posting (Zenodo, arXiv or any other server) or sent to a journal, a panel of AI sub-agents reviews it. Each agent carries a **different critical persona and a different experience bucket**, chosen for that specific article. A clinician does not review a statistics problem the way a biostatistician does, and a patient reviewer does not read a workflow claim the way an implementation scientist does. This system builds that difference in on purpose, then forces the paper through **looped editorial gates** until every major criticism has been answered in the text, fixed in the data, or recorded as an honest limitation.

It is the pre-submission peer review layer for a weekly research publication series in clinical AI, and a companion to the open [Multi-Agent Cochrane-Level Review Process](https://github.com/rtmalikian/multi-agent-cochrane-level-review-process), which covers how a review is *produced*. This repository covers how a finished draft is *challenged* before anyone else sees it.

> Honesty note, built into the protocol itself: this is **pre-submission peer review**. It improves a paper before submission. It is never described, in any manuscript, post or cover letter, as journal peer review, and a paper that passes these gates is "internally peer reviewed before submission", nothing more. See Rule 1 in [`PROTOCOL.md`](PROTOCOL.md).

## Why a panel, and why personas

A single reviewer, human or AI, has a single blind spot pattern. Real journal peer review works, when it works, because editors send a paper to people who disagree about different things:

- The **domain expert** knows the literature cold and spots a missing citation, an outdated comparator or a claim the field settled two years ago.
- The **methodologist** reads the design before the results and asks whether the study could answer its own question at all.
- The **biostatistician** checks the numbers, the denominators, the model choice and the intervals, and does not care how good the story sounds.
- The **clinician or operator** asks whether the workflow described exists in a real clinic, at a real staffing level, on a real Tuesday.
- The **patient and public reviewer** asks who this helps, who it might harm, and whether the language respects the people in the data.
- The **ethics and regulatory reviewer** checks consent, privacy, data governance, conflicts and claims that go past the evidence.
- The **reporting and reproducibility reviewer** checks the checklist (PRISMA 2020, CONSORT, STROBE, STARD, TRIPOD+AI, CARE, as the study type requires), the data and code links, and whether a stranger could rebuild the result.
- The **sceptic** has one job: argue the strongest case against the paper's own headline claim, using only the paper's own evidence.

Give all of those jobs to one generic "peer reviewer" prompt and you get one mild, averaged review. Give each job to a separate agent, in a separate session, with no sight of the other reviews, and you get the friction that makes peer review useful. That friction is the product.

## Persona selection is per article, never fixed

There is no standing panel. For every paper, a **Persona Selector** agent reads the title, abstract, study type, methods, population, technology and target venue, then assigns 5 to 7 reviewers from the experience buckets in [`PERSONA_SELECTION.md`](PERSONA_SELECTION.md), with a written reason for each pick and a written reason for any bucket it leaves out.

Examples the protocol works through in full:

| Article type | Panel it gets |
|---|---|
| Systematic review and meta-analysis | Evidence synthesis methodologist, biostatistician, domain clinician, information specialist, GRADE and reporting reviewer, sceptic |
| Clinical AI model or imaging paper | ML engineer, biostatistician, practising clinician in the specialty, patient safety reviewer, TRIPOD+AI reporting reviewer, sceptic |
| Open-source contribution analysis | Software engineer in the stack, health informatics researcher, reproducibility reviewer, domain clinician, sceptic |
| Digital health intervention design | Implementation scientist, clinician or operator, patient and public reviewer, ethics and privacy reviewer, health economist or service evaluator, sceptic |
| Commentary or opinion | Domain expert who is likely to disagree, policy or ethics reviewer, literature expert, patient and public reviewer, handling editor |
| Education or community study | Educator, community representative reviewer, methodologist, ethics reviewer, reporting reviewer |

Full matrix, persona cards and the selector prompt: [`PERSONA_SELECTION.md`](PERSONA_SELECTION.md) and [`prompts/01_persona_selector.md`](prompts/01_persona_selector.md).

## The looped gates

A paper cannot be submitted until it clears every gate, in order. A failed gate loops back. Nothing is waived by deadline pressure.

| Gate | Name | What happens | Fail means |
|---|---|---|---|
| 0 | Editorial triage | Scope, venue fit, ethics flags, article type confirmed, materials complete (manuscript, dataset, figures, references) | Paper returned before review starts |
| 1 | Persona assignment | Selector builds the panel for this article and records its reasoning | Panel rebuilt, no review starts on a generic panel |
| 2 | Independent review | Each reviewer works alone, in a separate session, no sight of other reviews, structured report with severity-graded comments | Any Blocker or unanswered Major stops the paper here |
| 3 | Editorial synthesis | A handling-editor agent merges the reviews, preserves disagreements, issues a decision: Accept, Minor revision, Major revision, or Reject and resubmit | Decision is Major revision or worse: loop to Gate 4 |
| 4 | Revision | Author agent (or human author) answers every comment in a response matrix, changes the manuscript, the tables or the analysis, and logs every change | A comment answered with words alone, where the text did not change, counts as unanswered |
| 5 | Re-review | The original reviewers who raised Major comments re-check only their own points against the revised draft | Any Major still open loops back to Gate 4 |
| 6 | Final integrity gate | Citations verified against sources, every number traced to the dataset snapshot, figures inspected page by page, declarations, conflicts and AI-assistance note checked, peer review statement worded honestly | Any failed check loops back to Gate 4, however late it is found |

**Loop rule:** Gates 3 to 5 repeat until no Blocker and no Major remains open. If a paper reaches a third loop with a Major still unresolved, the system stops and escalates to the human author with the unresolved point stated plainly. It never passes a paper silently, and it never averages a Blocker away because the other reviewers were happy.

Full gate definitions, severity taxonomy, decision rules and stop conditions: [`PROTOCOL.md`](PROTOCOL.md).

## What a comprehensive peer review has to cover

The protocol's review checklist, applied in full by the panel between them, covers:

1. **Question and originality.** Is the question worth asking, is it stated plainly, and what does this paper add to what is already published?
2. **Literature position.** Are the key prior papers cited, represented fairly, and engaged with, including papers that disagree?
3. **Design and methods.** Could this design answer this question? Are eligibility, sampling, comparators, outcomes and denominators fixed and reported?
4. **Statistics and numbers.** Model choice, intervals, heterogeneity, multiplicity, missing data, sensitivity analyses, and whether every number in the text matches the tables and the dataset.
5. **Results and claims.** Does every claim sit in the same paragraph as the evidence for it? Do the abstract and conclusions stay inside what the results support?
6. **Bias and limitations.** Selection, measurement, confounding, publication and author bias named specifically, with the direction each bias would push the result.
7. **Ethics, privacy and safety.** Consent and governance where people or patient data are involved, no individual clinical recommendations in a research paper, no claim of a licence or authority the author does not hold.
8. **Reporting standards.** The correct checklist for the study type, completed and checked against the manuscript, item by item.
9. **Reproducibility.** Data snapshot, code or extraction files, search strings, prompts and versions recorded well enough for a stranger to check the work.
10. **Clarity and structure.** A reader outside the specialty can follow the argument. Jargon explained. Tables and figures readable on their own.
11. **Declarations.** Funding, conflicts, contributions and a factual AI-assistance note present and accurate.
12. **Venue fit.** The paper matches the target journal or server in scope, format and audience, and the cover letter says nothing the paper does not support.

## Start here

1. Read [`PROTOCOL.md`](PROTOCOL.md), the full system.
2. Run [`prompts/00_orchestrator.md`](prompts/00_orchestrator.md) on a finished draft. It walks the gates in order and refuses to skip one.
3. Let [`prompts/01_persona_selector.md`](prompts/01_persona_selector.md) build the panel for that paper.
4. Give each reviewer [`prompts/02_independent_reviewer.md`](prompts/02_independent_reviewer.md) with their persona card filled in.
5. Synthesise with [`prompts/03_handling_editor.md`](prompts/03_handling_editor.md), revise, re-review with [`prompts/04_rereview.md`](prompts/04_rereview.md), and close with [`prompts/05_integrity_gate.md`](prompts/05_integrity_gate.md).
6. Keep the paperwork: blank forms are in [`templates/`](templates/), and a filled-in worked example is in [`examples/WORKED_EXAMPLE.md`](examples/WORKED_EXAMPLE.md).

## How this is used in practice

In the weekly research publication series this system was built for, the gates sit **between the finished draft and every external step**. No Zenodo deposit, no journal submission, no arXiv posting and no conference abstract leaves until the Gate 6 sign-off is logged in the paper's own folder, alongside the reviews, the response matrix and the panel assignment sheet. The peer review record for each paper is kept with the paper, and the manuscript's declarations carry a short, honest statement that the draft received multi-agent pre-submission peer review under this protocol, with the human author accountable for the final text.

## Is persona diversity actually better? The test

Honest answer: not yet tested. The claim that varied personas beat repeated reviews from one persona is this system's central hypothesis, and a public comment on launch day put the right challenge: papers with seeded errors, the same model, the same budget, a persona panel against one persona repeated. [`EVALUATION.md`](EVALUATION.md) is the pre-registered protocol for that study: 12 papers, 120 seeded errors across the twelve review domains, three arms (persona panel, repeated generic reviewer, repeated strongest specialist), blind scoring, shared blind spot rate and per-domain recall as named outcomes. It is written so the diversity claim can fail, and a null result will amend this README where the claim is made.

## Repository map

```
README.md                    This file
PROTOCOL.md                  The full multi-agent peer review protocol, gates 0 to 6
EVALUATION.md                Seeded-error study protocol: persona panel vs repeated single persona, matched model and budget
PERSONA_SELECTION.md         Experience buckets, persona cards, per-article panel matrix
prompts/                     Orchestrator, selector, reviewer, editor, re-review, integrity prompts
templates/                   Reviewer report, editorial decision, response matrix, gate log, panel sheet
examples/WORKED_EXAMPLE.md   One paper taken through every gate, with its panel and its loops
docs/                        GitHub Pages landing page
CITATION.cff                 Cite this system
LICENSE.md                   Malikian Attribution, Non-Commercial Licence v1.0
```

## Licence

Free for non-profit, academic, personal and other non-commercial use, with prominent acknowledgement and a link back to this repository. Commercial use requires a licence by email. Full terms: [`LICENSE.md`](LICENSE.md).

Suggested acknowledgement:

> Pre-submission peer review process: Malikian R. Multi-Agent Peer Review System for Clinical AI, Medical Research and Health Technology Papers. 2026. https://github.com/rtmalikian/multi-agent-peer-review-system-clinical-ai-medical-research

## How to cite

Malikian R. Multi-Agent Peer Review System for Clinical AI, Medical Research and Health Technology Papers: persona-based AI reviewers and looped editorial gates before preprint submission. 2026. GitHub: https://github.com/rtmalikian/multi-agent-peer-review-system-clinical-ai-medical-research · ORCID: 0009-0008-4326-4205

## Author and collaboration

Raphael Malikian · rtmalikian@gmail.com · [GitHub](https://github.com/rtmalikian) · [LinkedIn](https://www.linkedin.com/in/raphael-t-malikian-mbbs-bsc-hons-71075436a/) · [X](https://x.com/rtmalikian)

Open to collaboration on clinical AI research, evidence synthesis and research publishing infrastructure. Open an issue to discuss a paper type the panel matrix does not cover yet, or a reporting checklist that should be added to Gate 6.

## Keywords

multi-agent peer review, AI peer review, automated peer review, LLM peer reviewers, pre-submission peer review, manuscript peer review system, clinical AI research, medical research publishing, systematic review peer review, meta-analysis quality, persona-based AI agents, editorial gates, research integrity, reproducibility, PRISMA 2020, TRIPOD+AI, GRADE, preprint submission, Zenodo, scholarly publishing
