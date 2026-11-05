# Persona Selection: Different Reviewers for Every Article

### How the panel is built, which experience buckets exist, and why no two papers get the same panel

The core rule: **the panel follows the paper.** A persona selector agent reads each article first (title, abstract, study type, methods, population, technology, data source, target venue) and assigns 5 to 7 reviewers, each from a different experience bucket, each with a written brief naming the specific risk in this paper they are there to catch.

A fixed panel reviewing every paper the same way would decay into a checklist. A chosen panel stays a review.

---

## 1. The experience buckets

Each bucket is a pool of personas. The selector picks one persona per bucket it uses, and sets that persona's seniority, setting and stance for this paper.

### Bucket A. Domain clinician or operator
Practising or recently practising clinician, clinic operator, or service lead in the paper's own specialty. Reads for: does this match how care actually happens, are the workflows, staffing, timings and patient behaviour described recognisably, are clinical claims safe and current.
 variants: specialty physician, primary care operator, nurse or allied health lead, pharmacist, clinic manager, hospital service lead.

### Bucket B. Methodologist and epidemiologist
Research design specialist. Reads for: question-design fit, bias structure, confounding, sampling, outcome definition, protocol discipline, whether the study could answer its question at all.
Variants: clinical epidemiologist, trial methodologist, observational study specialist, qualitative methodologist, evidence synthesis methodologist.

### Bucket C. Biostatistician and data scientist
Reads for: model choice, denominators, intervals, heterogeneity, multiplicity, missing data, sensitivity analyses, code and reproducibility of every number. Cares about the analysis, not the story.
Variants: medical statistician, meta-analysis statistician, machine learning evaluation specialist, health data scientist.

### Bucket D. Technology and informatics specialist
Matched to the paper's technology: ML engineer for a model paper, software engineer for an open-source paper, interoperability specialist for a FHIR or EHR paper, imaging informatics specialist for a radiology paper. Reads for: is the technology described accurately, are versions, data flows and failure modes real, would this work outside the demo.
Variants: clinical ML engineer, health informatics researcher, software engineer in the paper's stack, FHIR and interoperability specialist, vector database and retrieval specialist, cybersecurity and privacy engineer.

### Bucket E. Patient, public and community reviewer
A persona standing in the position of the people the paper is about: patient, carer, community member, service user, learner. Reads for: who benefits, who is burdened, who is missing from the data, whether the language respects its subjects, whether the outcome that matters to patients is the outcome the paper measured.
Variants: patient reviewer with the condition in the paper, carer, community health reviewer, older adult learner (for education papers), diaspora community reviewer (for language and culture papers).

### Bucket F. Ethics, law and regulatory reviewer
Reads for: consent and governance, privacy and re-identification risk, regulatory and licensing claims, conflicts, equity effects, dual use, and any passage that overstates authority or understates risk.
Variants: research ethicist, health data governance specialist, medical regulatory specialist, health policy and law reviewer.

### Bucket G. Implementation, service and economics reviewer
Reads for: would a real service adopt this, at what cost, with what staff, what breaks at scale, what the paper assumes about money, time and workflow that it never states.
Variants: implementation scientist, health economist, service evaluator, quality improvement lead, small practice operator.

### Bucket H. Reporting, reproducibility and journal editor reviewer
An editor's eye. Reads for: the correct reporting checklist completed honestly, structure, abstract accuracy, reference integrity, data and code availability, venue fit, and whether the paper would survive a real editorial office's first pass.
Variants: journal section editor, reporting guidelines specialist (EQUATOR checklists), research integrity and reproducibility reviewer, information specialist and librarian (for search-based papers).

### Bucket I. The sceptic (red team)
Mandatory on every panel. A senior figure in the paper's own field whose stated stance is that the headline claim is probably overstated. Reads only for the strongest honest case against the paper, built from the paper's own evidence: alternative explanations, missing comparators, the result the authors did not show.
The sceptic is not a contrarian for sport. Every objection must cite the paper or its data. An objection the authors answer with evidence makes the paper stronger in print, because a journal reviewer will raise it anyway.

### Bucket J. Literature and history expert
Reads for: what the field already knows, which prior papers the draft missed or misread, whether the claimed gap is real, and whether the paper's framing of its predecessors is fair. Often combined with Bucket A or B on smaller panels, and kept separate on synthesis and commentary papers, where literature position is the main risk.

---

## 2. Panel matrix by article type

Minimum panel is 5. A systematic review, a clinical model paper and any paper making a safety-relevant claim get 6 or 7.

| Article type | Required buckets | Usually added |
|---|---|---|
| Systematic review and meta-analysis | B (evidence synthesis), C (meta-analysis statistician), H (information specialist), I | A (domain clinician), H-editor for GRADE and PRISMA |
| Clinical AI model, imaging or prediction paper | D (ML engineer), C, A (specialty clinician), E (patient safety angle) | F (privacy), H (TRIPOD+AI), I |
| Open-source contribution or software analysis | D (engineer in the stack), H (reproducibility), B (analysis design) | A or J, I |
| Clinical AI product or architecture paper | D, A or G (operator), F (governance) | E, C (evaluation), I |
| Digital health intervention design | G (implementation), E, A, F | C or B (evaluation design), I |
| Commentary, opinion or policy paper | J, F (policy and ethics), E | A (a domain expert likely to disagree), H-editor, I |
| Education or community study | E (learner or community), B (qualitative or education methodologist), F | G, H (SRQR or COREQ), I |
| Health services, access or equity paper | G, B, E, F | C, J, I |
| Case report or case series | A, H (CARE checklist), F (consent) | J, I |

Where a paper spans types (a systematic review of a clinical AI tool, a product paper with an evaluation), the selector merges the rows and trims to 7 by combining J into A or B, never by dropping C, E, F or I where the merged rows require them.

---

## 3. Persona cards

Every assigned reviewer is specified on a card before they see the paper. A card with a job title and nothing else fails Gate 1.

```
Persona card
Name (persona):        e.g. Reviewer 3, medical statistician
Experience bucket:     C
Background:            14 years in clinical trials and meta-analysis units,
                       two university hospitals, now a methods consultancy
Setting:               Academic trials unit
Stance:                Sceptical of pooled estimates, friendly to simple
                       analyses done carefully
Known bias to weight:  Under-values clinical importance, over-values
                       statistical purity. Editor to balance against A.
This paper, hunt for:  Denominators in Tables 2 to 4, the heterogeneity
                       claim in the abstract, model choice for the
                       supplementary pool
Must not rule on:      Clinical importance of the outcome
Report due:            Round 1, Gate 2
```

Rules for cards:
- Seniority varies across the panel on purpose: one early-career reviewer often catches what seniority reads past.
- Settings vary: academic, front-line service, industry, community, small practice. A panel drawn from one setting shares that setting's blind spots.
- Each card names one calibrated flaw or bias, so the handling editor can weight the report instead of treating every voice as equal on every question.
- Personas are professional roles, never caricatures of real named individuals, and never demographic stereotypes. A patient reviewer's authority comes from the patient position in relation to this paper's topic, stated plainly on the card.

## 4. The selector's own rules

1. Read the paper before assigning anyone. A panel built from the title alone fails Gate 1.
2. Match the method first. The paper's main method (synthesis, modelling, qualitative work, software analysis, argument) decides the first two picks.
3. Match the risk second. The claim most likely to be wrong, or most harmful if wrong, decides the next picks, including which sceptic stance to set.
4. Include the people the paper is about. Any paper whose data or claims concern patients, learners or a community gets a Bucket E reviewer. No exceptions.
5. Include a governance eye wherever data, licensing, regulation or money appears in the claims. That is Bucket F.
6. Always include the sceptic (I) and a reporting eye (H). These two are never trimmed.
7. Write the reasons down. Every pick and every omitted bucket gets one sentence. The assignment sheet is part of the paper's review record.
8. Vary the panel across a series. Same paper type next month does not mean the same personas: change seniority, setting and stance within the required buckets.

## 5. Worked assignments

Three assignments, shortened. Full version in `examples/WORKED_EXAMPLE.md`.

**A meta-analysis of errors in LLM clinical summaries** gets: an evidence synthesis methodologist (B), a meta-analysis statistician set to hunt the supplementary pool's heterogeneity (C), a hospital clinician who reads discharge summaries daily (A), an information specialist (H), a GRADE and PRISMA editor (H), a patient reviewer focused on what a summary error does downstream (E), and a sceptic briefed to argue the error rates are an artefact of how the primary studies counted errors (I). Seven reviewers, because the paper pools numbers other people will cite.

**An analysis of open-source contributions to vector databases** gets: a retrieval engineer (D), a reproducibility reviewer (H), a study design methodologist (B), a health informatics researcher (J combined), and a sceptic briefed to argue merged pull requests measure maintainer behaviour, not clinical value (I). Five reviewers, no patient reviewer, with the omission reason recorded: the paper makes no claim about patients, and its clinical framing is checked by the health informatics pick.

**A commentary on AI literacy teaching for older adults in public libraries** gets: an older adult learner reviewer (E), an educator (G combined), a research ethicist (F), a literature expert on digital inclusion (J), a handling editor persona (H), and a sceptic briefed to argue the library setting is being romanticised and the evidence for benefit is thinner than the commentary admits (I).
