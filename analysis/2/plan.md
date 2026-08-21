# Plan: CLEAR: an auditable foundation model for radiology grounded in clinical concepts

- Issue: https://github.com/itsjiyunbro/medical-practice/issues/2
- Paper path: `recommended/2026-08-19/clear-auditable-foundation-model-radiology-concepts/paper.json`
- DOI: https://doi.org/10.1038/s41551-026-01741-4
- Physician's focus: the issue names only the paper file (no additional free-text focus was
  provided). We therefore adopt the axes already assigned to this paper in the daily
  recommendation README — **institution-to-institution generalization** and **explainability
  of concept-level predictions** — as the working focus, pending physician confirmation.

## Proposed presentation

Dashboard entry: "CLEAR — institutional finding-label heterogeneity & auditability"

1. **Stacked bar chart: finding-label distribution by institution** (x-axis = `INST01`–`INST05`,
   y-axis = record count, stacked segments = `No Finding` vs. abnormal). This is the primary
   visual because the paper's central claim (auditable, generalizable concept model across
   sites) is only interesting to us if our own sites show heterogeneous label mixes — a stacked
   bar directly encodes "how much does the No-Finding/abnormal balance shift per site,"
   which is the exact confounder the physician (via the `check` field in `paper.json`) asked
   about.
2. **Grouped bar chart: view position (PA/AP) by institution** (x-axis = institution, bars =
   PA vs AP counts). AP vs. PA framing differs systematically and is a known confounder for
   chest X-ray classifiers; showing it site-by-site next to the label chart lets the physician
   see in one glance whether a site's finding pattern could be explained by projection mix
   rather than true prevalence — directly supporting "auditing for confounders," the paper's
   core selling point.
3. **Table: cohort summary** (total records, unique patients, age mean/range, sex split,
   department split) — compact text/number reference so readers can judge external-validity
   distance from CLEAR's ~0.87M-pair training set without re-deriving it from charts.
4. **Text block: relevance & caveat** — short prose (reusing/expanding the paper's own
   `relevance`/`caveat`/`check` fields) stating what a deep dive could realistically show
   (site-level label-mix and projection-mix differences) versus what it cannot (no external
   validation of CLEAR's actual classification accuracy, since we hold no model weights or
   predictions to audit).

Layout order: title/abstract-source link → cohort summary table → finding-label-by-institution
chart → view-position-by-institution chart → relevance/caveat text. Numeric summary first
grounds the reader before the two site-comparison charts, which are the analytical payload;
the text block closes with interpretation and limits.

## Open questions

- The issue body did not include a specific physician focus beyond the paper path — please
  confirm whether "institutional generalization / explainability" (the paper's pre-assigned
  axes) is the intended angle, or specify a different one (e.g., a particular finding label,
  age/sex subgroup, or department).
- Is there a specific institution or subgroup (e.g., pediatric age range, a single department)
  the physician wants highlighted, given none was named in the issue?
- Should the deep dive attempt any concept-bottleneck-style analysis (e.g., grouping finding
  labels into concept clusters), or stay at the descriptive/confounder-audit level proposed here?
