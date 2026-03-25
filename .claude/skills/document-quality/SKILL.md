---
name: document-quality
description: 사업계획서 작성/검토 시 자동 트리거 — 필수항목 체크리스트, 분량 기준, 포맷 규격, 제출 요건. 체크리스트, 검토, 제출, 포맷 키워드에 반응.
---

# 사업계획서 품질 기준

> 문서 규격, 분량, 필수항목, 심사 기준은 `project.yaml`에 정의되어 있습니다.

## 포맷 규격
project.yaml의 document.format 참조

## 분량 배분 가이드
project.yaml의 document.sections[].pages 참조

## 필수항목 체크리스트
project.yaml의 document.sections[].required_items 참조

### 공통
- [ ] "작성방법" 안내 표 삭제
- [ ] 아이템명 전 섹션 통일
- [ ] 팀명 전 섹션 통일
- [ ] 숫자/통계 출처 표기

## 심사 기준
project.yaml의 scoring 참조

> 문제인식 + 실현가능성 = 50%. 이 두 섹션에 가장 공을 들여야 합니다.

## 제출 요건
project.yaml의 program 참조 (마감일, 제출처, 서류 목록)

## 사업비 항목
- 합계 = project.yaml의 budget.total_display
- 항목별 세부 내용 및 외주 항목 구체적 산출물 명시

## 감점 주의사항
- "작성방법" 설명 표 미삭제 → 감점
- 분량 초과 → 감점 가능
- 필수항목 누락 → 감점
- 예산 합계 불일치 → 감점
- 팀원 3인 미만 → 자격 미달

## 검토 방법론
1. 포맷 규격 준수 확인 (project.yaml의 document.format 대조)
2. 섹션별 분량 확인 (project.yaml의 document.sections[].pages 대조)
3. 필수항목 체크리스트 순서대로 확인
4. 심사 기준 배점 기준으로 섹션별 완성도 평가
5. 감점 주의사항 최종 점검
