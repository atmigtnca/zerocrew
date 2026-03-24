# zerocrew

zeroone 팀의 **zerothon** — AI 도구를 활용한 2시간 사업계획서 스프린트

## 퀵스타트

```bash
# 1. 클론
git clone <repo-url>
cd zerocrew

# 2. hwpx MCP 서버 설치 (최종 변환용)
pip install hwpx-mcp-server
# 또는
uvx hwpx-mcp-server

# 3. Claude Code 실행
claude
```

## 구조

```
drafts/          섹션별 초안 (여기에 내용을 채웁니다)
research/        리서치 산출물 (시장조사, 경쟁분석)
final/           최종 통합 문서
assets/          이미지, 도표
.claude/agents/  전문 서브에이전트 5종
.claude/skills/  도메인 지식 스킬 4종
```

## 워크플로우

1. **리서치** — 시장조사, 경쟁분석 요청 → `research/`에 저장
2. **초안 작성** — `drafts/` 각 파일에 내용 채우기
3. **검토** — 검토 요청 → document-reviewer가 피드백
4. **통합** — 통합 요청 → integrator가 `final/사업계획서.md` 생성
5. **변환** — hwpx MCP로 최종 한글 파일 생성

## 에이전트

| 에이전트 | 역할 |
|---------|------|
| market-researcher | 시장 규모 추정, TAM/SAM/SOM, 트렌드 |
| strategy-advisor | 경쟁사 분석, 차별화, 로드맵 |
| financial-analyst | 예산 검증, 자금조달 계획 |
| document-reviewer | 품질 검토, 필수항목 체크, 피드백 |
| integrator | 최종 통합, 톤/문체 통일 |

## 스킬

| 스킬 | 역할 |
|------|------|
| market-research | TAM/SAM/SOM 추정 프레임워크, 통계 출처 |
| competitive-analysis | 경쟁사 비교, 포지셔닝 맵 가이드 |
| financial-planning | 300만원 집행 규정, 금지 항목 |
| document-quality | 필수항목 체크리스트, 분량/포맷 기준 |

## 제약 조건

- 분량: 요약서 1p + 본문 5p 이내
- 서체: 중고딕 12pt, 줄간격 160%
- 마감: 2026-04-02 (목)
- 예산: 총 300만원
