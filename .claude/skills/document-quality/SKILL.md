---
name: document-quality
description: Auto-triggers on business plan writing/review — required-item checklist, page limits, format specs, submission requirements. Responds to: 체크리스트, 검토, 제출, 포맷.
---

# Business Plan Quality Standards

> Document specs, page limits, required items, and scoring criteria are defined in `project.yaml`.

## Format Specs
Refer to project.yaml `document.format`

## Page Allocation
Refer to project.yaml `document.sections[].pages`

## Required Items Checklist
Refer to project.yaml `document.sections[].required_items`

### Common Checks
- [ ] "작성방법" instruction tables removed
- [ ] Item name consistent across all sections
- [ ] Team name consistent across all sections
- [ ] All statistics/numbers have sources cited

### Writing Style
- [ ] First-person team perspective ("본 팀"/[team name]) — no third-person observer voice
- [ ] Formal style (~합니다/~입니다) only — no report style (~임/~함), academic (~이다), or casual (~해요)

## Scoring Criteria
Refer to project.yaml `scoring`

> 문제인식 + 실현가능성 = 50%. These two sections deserve the most effort.

## Submission Requirements
Refer to project.yaml `program` (deadline, location, document list)

## Budget Items
- Total must equal project.yaml `budget.total_display`
- Each item needs detailed description; outsourcing items need specific deliverables

## Deduction Warnings
- "작성방법" instruction tables not removed → deduction
- Exceeding page limit → possible deduction
- Missing required items → deduction
- Budget total mismatch → deduction
- Fewer than minimum team members → disqualification

## Review Methodology
1. Verify format compliance (compare against project.yaml `document.format`)
2. Check section page lengths (compare against project.yaml `document.sections[].pages`)
3. Walk through required items checklist in order
4. Evaluate section completeness by scoring criteria weights
5. Final check on deduction warnings
6. Writing style review (first-person team perspective, formal endings consistency)
