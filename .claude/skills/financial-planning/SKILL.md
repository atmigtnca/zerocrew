---
name: financial-planning
description: Auto-triggers on budget planning — spending rule verification, item limits, prohibited items, funding plan framework. Responds to: 예산, 사업비, 자금조달, 비용, 정산.
---

# Budget Planning Guide

> Specific amounts and rules are defined in `project.yaml` budget section.

## Total Budget
Refer to project.yaml `budget.total_display` (must not exceed)

## Current Budget Plan
Refer to project.yaml `budget.items`

## Spending Rules per Item
Refer to project.yaml `budget.items[].rules`

### Outsourcing Specificity Guide
Outsourcing items must be described concretely:

| Vague | Specific |
|-------|----------|
| Marketing outsourcing | SNS content creation (20 Instagram feeds + 5 reels) |
| Design outsourcing | Brand design (1 logo + business cards + 5 app UI screens) |
| Video production | Service intro video filming/editing (2 videos, 1 min each) |

- **Key**: Electronic tax invoice (전자세금계산서) required
- **Evidence**: Tax invoice + service contract + deliverables

## Prohibited Items
Refer to project.yaml `budget.prohibited`

## Funding Plan Framework

### 3-Timepoint Structure
| Timepoint | Description | Example |
|-----------|-------------|---------|
| **Past** | Previous investments/grants | New teams: 0 is normal |
| **Present** | This grant + self-funding | Grant amount + team contributions |
| **Future 1yr** | Follow-up funding plans | Competitions, additional grants |

### Follow-up Funding Sources (Examples)
| Source | Amount Range | Timing | Note |
|--------|-------------|--------|------|
| University startup competition | 1~5M KRW | Rolling | Varies by university |
| KISED Early Startup Package | Up to 100M KRW | H1 annually | Pre/early-stage startups |
| Regional startup support center | 1~10M KRW | Rolling | Local innovation centers |
| TIPS (Private-led) | Up to 500M KRW | Rolling | Tech-based startups |
| University incubation center | Office space + mentoring | Rolling | Indirect support |

## Settlement Notes
- Only expenditures within project period (ref: project.yaml `program.period`) are valid
- Corporate card or bank transfer preferred (avoid cash)
- Keep per-transaction evidence (card receipts, tax invoices, quotes)
- Write expenditure reports (budget management forms)
- Comply with settlement deadline (typically 1 month after project end)
