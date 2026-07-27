## Week 7 — Issue selection

**Issue link:** https://github.com/ascherj/pathreview/issues/146

**Issue title:** PII scrubber fails to redact parenthesized US phone numbers

**Tier:** [x] Tier 1  [ ] Tier 2  [ ] Tier 3

**Problem summary:**
The PII scrubber in `safety/pii_scrubber.py` is supposed to detect and redact
US phone numbers from text before it's processed further. Its current regex
only matches dashed formats like `555-123-4567`, so parenthesized formats like
`(555) 123-4567` pass through both `scrub()` and `detect()` without being
flagged or redacted. This is a real safety/privacy gap since parenthesized
format is one of the most common ways US phone numbers are written. A
successful fix will update the phone number pattern so both formats are
correctly detected and redacted, confirmed by the related unit tests in
`tests/unit/test_pii_scrubber.py`.

**Checklist reasoning:**
I used the "Is this right for me?" checklist before committing to this issue.
It's scoped to a single file (`pii_scrubber.py`), the bug is reproducible with
a short code snippet included in the issue itself, and the exact failing
tests are already named, so I have a clear definition of "done." As someone
newer to navigating large codebases, this made it a good, well-bounded first
issue.

**Branch name:** fix/146-phone-regex-parenthesized

**Setup confirmation:** [ ] App runs locally at localhost:5173

**Cohort ledger:** [ ] Issue added to cohort ledger

## Week 8 — Reproduction & solution planning

**Reproduction commit link:** [we'll fill this in after you commit]

**Reproduction summary:**
Ran the repro script from the issue locally. The dashed phone number
(`555-123-4567`) was correctly redacted to `[REDACTED]`, but the
parenthesized format (`(555) 123-4567`) was left completely untouched in
the output. `detect()` also returned zero PII matches (`count=0, types=0`,
`[]`) for text containing only the parenthesized number, confirming it
isn't being flagged at all.

**PLAN.md link:** [we'll fill this in once PLAN.md is created]

**Walkthrough video (recommended):** [optional — skip if not recording one]

**Blockers or open questions:**
[leave blank or add anything you're unsure about]