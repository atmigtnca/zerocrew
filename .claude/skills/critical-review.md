---
name: critical-review
description: Devil's advocate review of business plans — maximum criticism from opposing stance. Responds to: 반론, 비판, 약점찾기, 독설리뷰, 악마의변호인.
user_invocable: true
---

# Devil's Advocate Review

Performs a critical review opposing every claim in the business plan.

## Procedure

1. Identify review target:
   - If a file path is given as argument, review that file
   - If no argument, auto-search: `final/사업계획서.md` → `drafts/` → `versions/`

2. Invoke the `악마의변호인` sub-agent for critical review.

3. Deliver review results to the user.

## Notes
- This review is **intentionally negative**. The goal is to find weaknesses so the team can strengthen them before submission.
- No alternatives are provided — only problem discovery.
- For alternatives and fixes, use `품질검토관` agent or the commands below.

## Related Workflows
- `/고도화` — Critique → select → fix loop (max 3 rounds)
- `/수정 [section] "instruction"` — Quick fix for specific section + auto-verification
- `/재검토` — Full re-review by 품질검토관 + 악마의변호인
