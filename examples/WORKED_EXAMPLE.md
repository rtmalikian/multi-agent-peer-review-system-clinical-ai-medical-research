# Worked example: one paper through every gate

A shortened, realistic run. The paper is a meta-analysis of clinically significant errors in LLM-generated clinical summaries, the third review in a Cochrane-level series. Numbers in this example are the paper's real headline results, included so the review points read concretely.

## Gate 0. Triage
Article type: systematic review and meta-analysis. Materials complete: manuscript, extraction sheets, dataset snapshot, forest plots, reference list. Venue note: journal of clinical epidemiology, subscription route, free. Pass.

## Gate 1. The panel the selector built
1. **B, evidence synthesis methodologist**, 16 years, Cochrane-trained, now in a university evidence unit. Hunt for: whether the supplementary pools were defined after seeing the data, and whether the paper says so plainly.
2. **C, meta-analysis statistician**, 12 years, trials unit. Hunt for: the supplementary any-error pool (60.6%, I-squared 98.6% on the fabrication pool in particular) and whether the text warns a reader off treating it as a stable estimate.
3. **A, hospital clinician**, acute medicine, reads discharge summaries daily. Hunt for: whether "clinically significant error" matches what would matter at the bedside.
4. **H, information specialist**, health sciences librarian. Hunt for: search currency, and whether the near-identical PROSPERO-registered review limited to discharge summaries is cited and the scope difference explained.
5. **H, GRADE and PRISMA editor persona**, journal section editor. Hunt for: GRADE ratings (very low throughout) stated in the abstract, not buried.
6. **E, patient reviewer**, persona standing for patients who receive these summaries. Hunt for: what an error rate means for a person acting on a summary, and whether the discussion says it.
7. **I, the sceptic**, senior clinical informatician. Brief: argue the error rates are an artefact of inconsistent error counting across 11 primary studies, and that the honest headline is the reporting gap, not any pooled number.

Buckets F omitted with reason recorded: no patient-level data, no licensing or regulatory claim in the draft. Bucket G omitted: no service adoption claim.

## Gate 2. What came back (extracts)
- **Statistician, Major:** the fabrication pool (17.6%, 95% CI 2.9 to 60.0, I-squared 98.6%) is described in the discussion with the same confidence as the omission pool. Text must label it near-uninterpretable wherever it appears, including the abstract.
- **Methodologist, Major:** the supplementary pools rest on a post hoc amendment. The amendment is logged in the supplement but the main text introduces the pools as if pre-specified. Move the post hoc status into the main text.
- **Clinician, Minor:** the definition of clinically significant error is sound but appears on page 9. Move it into the abstract's methods line.
- **Information specialist, Major:** the competing discharge-summary-only review is cited once and the scope difference (all summary types vs discharge only) is never stated. State it in the introduction and the discussion.
- **GRADE editor, Minor:** abstract gives pooled figures without the very low certainty rating. Add it.
- **Patient reviewer, Major:** the discussion never says what a 21.0% clinically significant error rate in the one reporting study means for a patient who acts on a summary. Add a plain paragraph, no clinical advice, consequences at population level only.
- **Sceptic, Major, the strongest report:** with only 1 of 11 studies reporting the primary outcome, the pooled supplementary figures risk becoming the cited headline while the real finding, a reporting gap across the field, sits in the middle of the paper. Recommendation: restructure so the reporting gap leads the abstract's conclusions.

No Blockers. Five Majors, two Minors.

## Gate 3. Editorial decision
Major revision. The editor names the central problem in one line: the paper's framing promotes its weakest numbers over its strongest finding. Revision brief orders the sceptic's restructure first, then the amendment disclosure, the heterogeneity labelling, the competing review scope statement, and the patient consequence paragraph.

## Gate 4 and 5. One loop
The author restructures the abstract and conclusions around the reporting gap, moves the post hoc amendment into the methods, labels the fabrication pool near-uninterpretable in three places, states the scope difference against the discharge-only review, adds the patient consequence paragraph, and moves the error definition forward.
Re-review: statistician, methodologist, information specialist, patient reviewer and sceptic each mark their Majors Resolved. The sceptic adds one sentence, kept in the record: "The restructure answers my point. The fabrication pool label should survive any journal edit." Loop count: 1.

## Gate 6. Integrity gate
All references verified. Headline numbers traced to the snapshot: primary outcome 13 of 62 (21.0%), supplementary any-error pool 60.6%, omission 20.7%, fabrication 17.6%, inaccuracy 27.9%. GRADE very low confirmed in abstract, summary of findings and discussion. Forest plot pages inspected. Declarations, AI-assistance note and the Rule 1 peer review statement present. Pass.

The paper was then deposited as a preprint (Zenodo DOI 10.5281/zenodo.23847500) with its review record saved in its folder. The journal submission followed. At no point was the internal review described as journal peer review.
