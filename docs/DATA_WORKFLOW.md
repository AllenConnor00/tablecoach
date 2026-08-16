# Data & Decision Workflow

TableCoach is designed around the idea that operational data has to pass through several different states before it should influence a management decision.

This public overview describes those states without exposing internal company data or proprietary implementation.

## 1. Import

A recurring PDF or CSV scorecard enters the system as **source material**, not as unquestioned truth.

The application parses expected fields and associates the source with a reporting period while preserving enough context for later review.

## 2. Normalize

Values from different reports are converted into consistent application representations so historical comparisons are possible.

Normalization may include formatting, metric representation, reporting-period alignment, and employee identity resolution.

## 3. Review

Questionable information is surfaced instead of silently accepted.

Review concerns can include:

- missing expected fields;
- suspicious values;
- low-confidence parsing;
- duplicate imports;
- ambiguous employee identity;
- unexpected report structure.

The objective is not to pretend automated parsing is infallible. The objective is to make uncertainty visible and inexpensive to resolve.

## 4. Approve

Once reviewed, an import becomes part of the trusted operational history used by downstream analytics.

Keeping this transition explicit prevents provisional data from quietly influencing rankings, trends, or coaching recommendations.

## 5. Analyze

Approved data can be compared across reporting periods to identify patterns at both employee and team levels.

Analysis is used to support questions such as:

- What changed?
- Is the change persistent or isolated?
- Where is performance consistently strong?
- Where may follow-up be useful?
- Which apparent opportunities are supported by enough history to warrant attention?

## 6. Act

A finding can be converted into a coaching or management workflow rather than disappearing when the dashboard closes.

This creates continuity between analytics and the actual operational work that follows.

## 7. Validate Outcomes

TableCoach distinguishes **modeled opportunity** from **confirmed outcome**.

An analytical model can estimate where an intervention may have value. That estimate should not later be presented as realized business impact without supporting operational/POS evidence.

This distinction is important both analytically and ethically: recommendations should be measurable, and estimates should remain identifiable as estimates.

## Why This Matters

A large portion of practical data work is not choosing a chart type or calculating a score. It is establishing whether the data is trustworthy, whether two records refer to the same thing, whether a trend has enough context to matter, and whether a recommendation actually produced the result attributed to it.

TableCoach is designed around that full lifecycle.
