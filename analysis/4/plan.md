# Plan: QoQ-Med3: a multimodal reasoning foundation model for clinical analysis

- Issue: https://github.com/itsjiyunbro/medical-practice/issues/4
- Paper: `recommended/2026-08-19/qoq-med3-multimodal-reasoning-foundation-model/paper.json`
- DOI: https://doi.org/10.1038/s41746-026-02945-3
- Physician focus: the issue body did not specify a distinct focus beyond the
  paper path itself, so this plan follows the axes recorded in `paper.json`:
  **기관 간 일반화 (inter-institution generalization)** and
  **설명 가능성 (explainability)**.

## Proposed presentation

Dashboard entry: "Cross-institution transfer risk in our chest X-ray cohort"

1. **Stacked bar chart — institution × department case counts (x-axis:
   INST01–INST05, y-axis: case count, stacked by department).** This is the
   structural precondition for the paper's core claim: transferability only
   matters if sites differ in composition. A stacked bar directly shows
   whether department mix is balanced or skewed per institution, which a
   table would make harder to scan at a glance.
2. **Grouped bar chart — "No Finding" vs "Finding" rate by department (x-axis:
   department, y-axis: % no-finding, grouped bars for emergency vs
   radiology).** Chosen because the paper's transferability axis implies
   performance may degrade when the label distribution a model was tuned on
   (e.g., radiology-read images) differs from a deployment site's actual
   distribution (e.g., emergency triage images). A rate/percentage encoding
   normalizes for the different case counts per department.
3. **Pie or donut chart — view position (PA vs AP) split.** AP films are
   typically portable/bedside (sicker, less standardized), while PA is
   standard upright. Since the paper flags robustness to real-world
   heterogeneity, this single proportion is a fast visual for "how much of
   our cohort deviates from the standard-view assumption most models are
   validated on."
4. **Text section — "What this cohort can and cannot test."** Explicitly states
   we are single-modality (chest X-ray only), so QoQ-Med3's headline
   multimodal transfer gains (ultrasound, mammography) are not reproducible
   here; only the narrower institution/department heterogeneity question is
   in scope.
5. **Layout order:** abstract/relevance blurb → institution×department bar →
   finding-rate-by-department bar → view-position donut → caveats/text
   section → open questions. Structural composition is shown first because
   it is the precondition readers need before interpreting the rate
   comparison.

## Open questions

- Should "transferability" be operationalized as held-out-institution
  performance drop (train on 4, test on 1, rotate), or as department-only
  splits (train on radiology-read reports, test on emergency-read reports)
  as the paper's `check` field suggests?
- Is explainability in scope for this deep dive at all, given we have no
  model to audit yet — or should this analysis be purely descriptive of
  cohort heterogeneity as a prerequisite study?
- Do we have (or need) ground-truth outcome labels beyond the free-text
  `findings_label` field to define a transfer-performance metric, or is
  label agreement/consistency across institutions itself the deliverable?
- Should INST04's noticeably lower internal_medicine count (6 vs 10-16
  elsewhere) be treated as a known site-mix imbalance to control for, or
  investigated as a data-quality flag first?
