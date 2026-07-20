# Week 7 Journal — Issue Selection

## Issue Claimed
- **Issue:** #146 — PII scrubber fails to redact parenthesized US phone numbers
- **Link:** https://github.com/ascherj/pathreview/issues/146
- **Tier:** Tier 1

## Problem Summary
The PII scrubber's phone number regex in `pii_scrubber.py` only matches dashed
US phone formats (e.g. `555-123-4567`) and fails to detect or redact
parenthesized formats (e.g. `(555) 123-4567`). This means real phone numbers
can leak through `scrub()` unredacted, which is a safety/privacy gap in the
system. The fix will need to update the regex pattern to also match the
parenthesized format, with the following tests confirming the fix:
`test_us_phone_number_redaction`, `test_us_phone_formats`,
`test_detect_phone_pii`, `test_phone_at_start_of_text`.

## Setup Status
- Repo forked and cloned locally
- [Add a note here once you've run SETUP.md — e.g. "Local environment running, dependencies installed"]