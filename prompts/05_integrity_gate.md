# Prompt 05. Final Integrity Gate: verify, do not review

You are a fresh agent who did not review this paper. Your task is verification, not opinion, under Gate 6 of PROTOCOL.md.

Inputs: the revised manuscript, the rendered PDF, the dataset snapshot, analysis outputs, the reporting checklist for the study type, and the submission metadata.

Check, item by item, and record Pass or Fail with evidence for each Fail:
1. References. Every citation resolves to a real source (authors, year, title, venue). Spot-check that sources support the claims they are cited for, and check every citation attached to a headline claim in full.
2. Numbers. Every number in the title, abstract and conclusions traces to the dataset snapshot or an analysis output. Percentages carry denominators. Text, tables and figures agree.
3. Consistency. Abstract matches results. Conclusions stay inside the results. Title matches content.
4. Reporting checklist. The checklist for this study type is complete, and each item's claim matches the manuscript.
5. Figures and tables. Open the rendered PDF and inspect every figure and table page visually. Forest plots, if any, show summary diamonds. Nothing is cut off, overlapping or unreadable.
6. Declarations. Funding, conflicts, contributions, data availability, the AI-assistance note, and the pre-submission peer review statement (Rule 1 wording) are present and accurate. No passage presents the author as currently licensed or practising, and none uses a retired-status label.
7. Safety and authority. No individual clinical advice, no medication recommendation, no patient identifier, no governance gap for the data used.
8. Metadata. Preprint and journal submission metadata (title, abstract, keywords, licence, ORCID 0009-0008-4326-4205 where the author is Raphael Malikian) match the manuscript word for word where they should.
9. Public text. Any abstract, cover letter or post shipping with the paper has passed the author's de-AI copy audit: no em dashes, no banned vocabulary, no claim stronger than the paper.

Output: the Gate 6 entry for peer-review/gate-log.md. Any Fail returns the paper to revision (Gate 4) with the failed items listed. There is no partial pass.
