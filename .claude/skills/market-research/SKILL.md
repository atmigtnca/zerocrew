---
name: market-research
description: Auto-triggers on market research — TAM/SAM/SOM estimation framework, domestic market methodology, source verification guidelines. Responds to: 시장규모, 시장분석, TAM, SAM, SOM, 산업분석.
---

# Market Research Framework

## TAM/SAM/SOM Concepts
- **TAM** (Total Addressable Market): Total market size for the industry our product belongs to.
- **SAM** (Serviceable Addressable Market): Portion of TAM we can actually reach.
- **SOM** (Serviceable Obtainable Market): Portion of SAM we can realistically capture in 1-2 years.

## Estimation Formulas

### Top-down
```
TAM = Total industry market size (official statistics)
SAM = TAM × regional ratio × target age ratio × channel ratio
SOM = SAM × initial market share (0.1~1%)
```

### Bottom-up (more persuasive)
```
SOM = Target users × conversion rate × ARPU × 12 months
SAM = Total potential users × ARPU × 12 months
TAM = Parent market containing SAM
```

### Example (university student target)
```
National university students: ~1.9M (2024 education statistics)
Regional students: ~80K
Target ratio: 30% (interested students)
Conversion: 5% (actual users)
Monthly ARPU: 5,000 KRW

SOM = 80K × 30% × 5% × 5,000 × 12 = 72M KRW
```

## Domestic Statistics Sources (Priority Order)

### Tier 1: Government/Public Statistics
- **KOSIS (National Statistics Portal)**: https://kosis.kr — demographics, industry, economy
- **Statistics Korea e-Indicators**: https://www.index.go.kr — key national indicators
- **MSIT (Ministry of Science and ICT)**: https://www.msit.go.kr — IT/SW industry
- **Education Statistics**: https://kess.kedi.re.kr — student counts, university data

### Tier 2: Industry Research Institutions
- **KISA (Korea Internet & Security Agency)**: Internet/mobile usage surveys
- **KISDI (ICT Policy Research)**: ICT industry statistics
- **KEIT (Korea Evaluation Institute)**: Industry technology trends
- **MSS (Ministry of SMEs and Startups)**: Startup/SME statistics

### Tier 3: Private Research (free public data)
- **Statista**: Global + domestic market sizes
- **IGAWorks Mobile Index**: App market data
- **WiseApp**: App user statistics

## Source Citation Format
```
(Source: [Institution], "[Report/Data Name]", YYYY, URL)
```
Example: (Source: KISA, "2024 Internet Usage Survey", 2024, https://www.kisa.or.kr/...)

## Rules
- No figures without sources
- Data older than 2 years must note "[as of YYYY]"
- Estimates must show full calculation process
- No AI-fabricated statistics — mark as "verification needed" if unverifiable
