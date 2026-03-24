# zerocrew

zeroone 팀의 **zerothon** — AI 도구를 활용한 2시간 사업계획서 스프린트

## 퀵스타트

```bash
# 1. 클론
git clone <repo-url>
cd zerocrew

# 2. hwpx MCP 서버 설치 (최종 변환용)
pip install hwpx-mcp-server

# 3. Claude Code 실행
claude
```

## 2시간 타임라인

| 시간 | 전체 | PM | 시장분석 | 사업전략 | 재무 |
|------|------|----|---------|---------|------|
| 0~10분 | **브리프** | brief.md 작성 (전원 함께) | ← | ← | ← |
| 10~40분 | **리서치** | 00-아이템개요 + 01-팀구성 | 시장조사 요청 | 경쟁분석 요청 | 예산 검증 요청 |
| 40~80분 | **초안** | 00, 01 완성 | 02-문제인식 작성 | 03-실현가능성 작성 | 04-사업비편성 작성 |
| 80~100분 | **검토** | 전체 수합 + 검토 요청 | 피드백 반영 | 피드백 반영 | 피드백 반영 |
| 100~115분 | **통합** | 통합 요청 (integrator) | 교차 확인 | 교차 확인 | 숫자 확인 |
| 115~120분 | **변환** | hwpx 변환 | 최종 확인 | 최종 확인 | 최종 확인 |

## 역할별 가이드

### PM (00-아이템개요 + 01-팀구성)

```
1. brief.md를 열고 아이템 정보, 팀 정보를 채운다 (전원 함께)
2. Claude에게:
   "brief.md 기반으로 drafts/00-아이템개요.md 작성해줘"
   "brief.md 기반으로 drafts/01-팀구성.md 작성해줘"
3. 다른 팀원 작업이 끝나면 전체 drafts/ 모아서:
   "전체 초안 검토해줘" → document-reviewer 동작
   "최종 통합해줘" → integrator 동작
   "hwpx로 변환해줘" → hwpx-converter 동작
```

### 시장분석 (02-문제인식)

```
1. Claude에게:
   "brief.md 읽고 시장조사해줘" → market-researcher 동작
   → research/market/에 결과 저장됨
2. 리서치 결과 확인 후:
   "research 결과 기반으로 drafts/02-문제인식.md 작성해줘"
3. 검토 피드백 받으면 수정
```

### 사업전략 (03-실현가능성)

```
1. Claude에게:
   "brief.md 읽고 경쟁사 분석해줘" → strategy-advisor 동작
   → research/competitors/에 결과 저장됨
2. 리서치 결과 확인 후:
   "research 결과 기반으로 drafts/03-실현가능성.md 작성해줘"
3. 검토 피드백 받으면 수정
```

### 재무 (04-사업비편성)

```
1. Claude에게:
   "예산 편성안 검증해줘" → financial-analyst 동작
2. 검증 결과 반영해서:
   "drafts/04-사업비편성.md 완성해줘"
3. 외주 항목 구체화 확인 (세금계산서 요건)
```

## 핵심 파일

| 파일 | 역할 |
|------|------|
| `brief.md` | 모든 작업의 출발점. 아이템/팀 정보 (가장 먼저 작성) |
| `drafts/00~04` | 섹션별 초안 |
| `research/` | 시장조사, 경쟁분석 결과 |
| `final/사업계획서.md` | 통합 최종본 |
| `final/사업계획서.hwpx` | 제출용 한글 파일 |

## 에이전트

| 에이전트 | 역할 | 언제 동작 |
|---------|------|----------|
| market-researcher | TAM/SAM/SOM, 시장 트렌드 | 시장조사 요청 시 |
| strategy-advisor | 경쟁사, 차별화, 로드맵 | 경쟁분석/전략 요청 시 |
| financial-analyst | 예산 검증, 규정 체크 | 예산 관련 요청 시 |
| document-reviewer | 품질/일관성 검토, 피드백 | 검토 요청 시 |
| integrator | 전체 통합, 톤/용어 통일 | 통합 요청 시 |
| hwpx-converter | md → hwpx 변환 | hwpx 변환 요청 시 |

## 스킬 (자동 트리거)

| 스킬 | 역할 |
|------|------|
| market-research | TAM/SAM/SOM 추정 프레임워크, 통계 출처 |
| competitive-analysis | 경쟁사 비교, 포지셔닝 맵 가이드 |
| financial-planning | 300만원 집행 규정, 금지 항목 |
| document-quality | 필수항목 체크리스트, 분량/포맷 기준 |
| hwpx-export | md → hwpx 변환 워크플로우 |

## 제약 조건

- 분량: 요약서 1p + 본문 5p 이내
- 서체: 중고딕 12pt, 줄간격 160%
- 마감: 2026-04-02 (목)
- 예산: 총 300만원 (회식비30 + 사무비30 + 홍보비50 + 마케팅대행110 + 디자인대행80)
- 제출: JBNU 인터네셔널센터 3층 303호 방문 제출
