---
name: hwpx-export
description: 최종 마크다운 사업계획서를 hwpx(한글) 파일로 변환하는 워크플로우. hwpx, 한글, 변환, export, 제출 파일, 최종 문서 키워드에 반응.
argument-hint: "[마크다운 파일 경로] (기본: final/사업계획서.md)"
---

# hwpx 변환 워크플로우

## 개요
`final/사업계획서.md` → 한글변환기 서브에이전트 호출 → `final/사업계획서.hwpx` 생성

## 사전 조건
- `final/사업계획서.md`가 존재해야 함 (문서통합자 에이전트로 먼저 통합)
- hwpx MCP 서버가 동작 중이어야 함 (`.claude/settings.json`에 등록됨)
- `pip install hwpx-mcp-server` 또는 `uvx hwpx-mcp-server` 사전 설치

## 워크플로우

### Step 1: 소스 확인
`final/사업계획서.md` 파일을 읽어 내용과 구조를 파악한다.

### Step 2: 한글변환기 에이전트 호출
한글변환기 서브에이전트를 실행한다. 에이전트에게 전달할 정보:
- 마크다운 전체 내용
- 포맷 규격: project.yaml의 document.format 참조
- 출력 경로: `final/사업계획서.hwpx`

### Step 3: 검증
생성된 hwpx 파일을:
1. `get_document_info`로 메타데이터 확인
2. `get_document_outline`로 섹션 구조 확인
3. `get_document_text`로 내용 누락 여부 확인

### Step 4: 완료
- 결과 파일 경로 안내
- 수동 확인 사항 안내 (한글 프로그램에서 최종 서체/줄간격 확인)

## 포맷 규격 참조
project.yaml의 document.format 참조

| 항목 | 값 |
|------|-----|
| 서체 | project.yaml의 document.format.font_hwpx |
| 크기 | project.yaml의 document.format.font_size |
| 줄간격 | project.yaml의 document.format.line_height |
| 여백 | project.yaml의 document.format.margin |
| 요약서 | 1페이지 (페이지 나누기 후 본문) |

## hwpx MCP 도구 매핑

### 문서 생성 순서
1. `copy_document` — 빈 템플릿에서 시작 (또는 새 문서)
2. `create_custom_style` — 본문/제목 스타일 생성 (project.yaml의 document.format 기준)
3. `add_heading` — 섹션 제목 추가
4. `add_paragraph` — 본문 텍스트 추가 (style 지정)
5. `add_table` — 테이블 추가
6. `set_table_cell_text` — 테이블 셀 내용 채우기
7. `format_table` — 테이블 서식
8. `add_page_break` — 요약서/본문 사이 페이지 나누기

### 마크다운 → hwpx 요소 매핑
| 마크다운 | hwpx 도구 |
|---------|----------|
| `# 제목` | `add_heading` (level=1) |
| `## 소제목` | `add_heading` (level=2) |
| 일반 텍스트 | `add_paragraph` |
| `\| 테이블 \|` | `add_table` + `set_table_cell_text` |
| `---` (구분선) | `add_page_break` (요약서/본문 구분) |
| **굵은 텍스트** | `format_text` (bold) |

## 주의사항
- hwpx MCP는 stateless — 모든 도구 호출에 `filename` 명시 필요
- 한 번에 많은 내용을 추가하면 타임아웃 가능 — 섹션 단위로 나눠서 추가
- 서체 이름이 시스템에 설치된 정확한 이름과 일치해야 함
- 최종 확인은 반드시 한글 프로그램에서 열어서 육안 검증
