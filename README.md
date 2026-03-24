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

| 시간 | 단계 | 전원 |
|------|------|------|
| 0~10분 | **브리프** | brief.md 함께 작성 |
| 10~80분 | **각자 작성** | 각자 `versions/X/drafts/`에 전체 사업계획서 독립 작성 |
| 80~100분 | **비교 선정** | PM이 4개 버전 비교 요청 → plan-selector가 베스트 조합 |
| 100~110분 | **통합** | integrator가 `final/사업계획서.md` 생성 |
| 110~115분 | **검토** | document-reviewer로 최종 체크 |
| 115~120분 | **변환** | hwpx-converter로 제출 파일 생성 |

## 사용법

### 전원 (0~10분): 브리프 작성

```
brief.md를 열고 아이템 정보, 팀 정보를 함께 채운다
```

### 각자 (10~80분): 전체 사업계획서 작성

각 팀원이 자기 버전 폴더에서 **전체 5개 섹션**을 작성합니다.

```
# 팀원 A의 경우
"brief.md 읽고 versions/A/drafts/ 에 전체 사업계획서 작성해줘"

# 또는 섹션별로
"brief.md 기반으로 versions/A/drafts/00-아이템개요.md 작성해줘"
"시장조사해줘" → market-researcher 동작
"versions/A/drafts/02-문제인식.md 작성해줘"
...
```

> 같은 brief에서 출발하지만, 각자의 AI가 다른 관점/데이터를 제공합니다.

### PM (80~120분): 비교 → 통합 → 변환

```
# 1. 4개 버전 비교 (스토리 중심)
"versions/ 의 4개 버전 비교해서 최종 조합 만들어줘"
→ plan-selector가 스토리 일관성 기준으로 베스트 조합 선정

# 2. 선정 결과를 drafts/에 반영 후 통합
"최종 통합해줘"
→ integrator가 final/사업계획서.md 생성

# 3. 검토
"검토해줘"
→ document-reviewer가 피드백

# 4. hwpx 변환
"hwpx로 변환해줘"
→ hwpx-converter가 final/사업계획서.hwpx 생성
```

## 핵심 파일

| 파일 | 역할 |
|------|------|
| `brief.md` | 모든 작업의 출발점. 아이템/팀 정보 (가장 먼저 작성) |
| `versions/X/drafts/` | 각 팀원의 독립 버전 (A, B, C, D) |
| `drafts/` | plan-selector가 선정한 최종 조합 |
| `research/` | 시장조사, 경쟁분석 결과 |
| `final/사업계획서.md` | integrator가 통합한 최종본 |
| `final/사업계획서.hwpx` | 제출용 한글 파일 |

## 에이전트

| 에이전트 | 역할 | 언제 동작 |
|---------|------|----------|
| market-researcher | TAM/SAM/SOM, 시장 트렌드 | 시장조사 요청 시 |
| strategy-advisor | 경쟁사, 차별화, 로드맵 | 경쟁분석/전략 요청 시 |
| financial-analyst | 예산 검증, 규정 체크 | 예산 관련 요청 시 |
| plan-selector | 4개 버전 스토리 비교, 베스트 조합 | 버전 비교 요청 시 |
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
