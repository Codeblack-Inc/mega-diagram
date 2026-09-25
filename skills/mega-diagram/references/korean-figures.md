# 한국 보고서 도식 (Korean report figures)

사업계획서·제안서·공공 보고서·회사소개서에서 반복해서 쓰는 도식 30가지. 원본 diagram-design의 44가지 형식(SKILL.md §3)을 **늘리지 않고**, 가장 가까운 형식의 레이아웃 규칙을 물려받는 한국형 패턴으로 정리했다(ADR 0002와 같은 방식). 연결선 규칙(SKILL.md §6), 4px 격자와 복잡도 예산(§7), 한글 규칙([mega.md](mega.md))은 그대로 적용된다.

## 고르는 법

1. 사용자가 아래 이름(또는 비슷한 말: "추진 배경", "SWOT", "망 구성도", "도넛 차트" …)을 말하면 해당 도식의 참조 문서를 읽고 그린다.
2. 이름이 없으면 SKILL.md §3에서 형식을 먼저 고른다. 결과가 보고서 도식에 가까우면 이 표에서 더 구체적인 도식을 고른다.
3. 참조 문서의 **기본 형식** 줄에 적힌 `type-*.md`도 함께 읽는다 — 도식은 그 형식의 규칙 위에 한국 보고서 관례를 더한 것이다.

## 목록

### 기획·보고

| 도식 | 쓰는 곳 | 참조 |
|---|---|---|
| 추진 배경·필요성 | 문제 → 원인 → 해결 방향 | [ko-problem-solution.md](ko-problem-solution.md) |
| AS-IS / TO-BE | 현행 문제와 개선 후 모습 비교 | [ko-as-is-to-be.md](ko-as-is-to-be.md) |
| 서비스 개념도 | 중심 서비스와 이용 주체, 가치 흐름 | [ko-concept-map.md](ko-concept-map.md) |
| 로직 모델 | 투입 → 활동 → 산출 → 성과 → 영향 | [ko-logic-model.md](ko-logic-model.md) |
| 성과지표 체계 | 최종 목표 → 성과 목표 → 지표(현재→목표) | [ko-kpi-tree.md](ko-kpi-tree.md) |
| 이슈 트리 | 핵심 질문을 MECE로 분해 | [ko-issue-tree.md](ko-issue-tree.md) |
| SWOT 분석 | 강점·약점·기회·위협과 대응 전략 | [ko-swot.md](ko-swot.md) |
| 이해관계자 맵 | 영향력 × 관심도, 관리 전략 | [ko-stakeholder-map.md](ko-stakeholder-map.md) |
| 위험 관리 매트릭스 | 발생 가능성 × 영향도, 대응 방안 | [ko-risk-matrix.md](ko-risk-matrix.md) |
| 역할 분담표 (RACI) | 과업 × 기관의 R·A·C·I | [ko-raci-matrix.md](ko-raci-matrix.md) |
| 기대효과 | 정량·정성 효과와 파급 효과 | [ko-expected-effects.md](ko-expected-effects.md) |
| 인력 투입 계획 | 역할 × 월, M/M 합계 | [ko-staffing-plan.md](ko-staffing-plan.md) |
| 세부 추진 일정표 | 추진 내용 × 1~12월, 산출물 | [ko-schedule-table.md](ko-schedule-table.md) |
| 추진 절차 | 단계별 주체·내용·기간 | [ko-procedure-steps.md](ko-procedure-steps.md) |
| 연혁 | 연도별 주요 이력 | [ko-company-history.md](ko-company-history.md) |

### 사업·시장

| 도식 | 쓰는 곳 | 참조 |
|---|---|---|
| 시장 규모 (TAM·SAM·SOM) | 목표 시장 크기와 산출 근거 | [ko-tam-sam-som.md](ko-tam-sam-som.md) |
| 경쟁사 비교표 | 경쟁사 × 기준, ●◐○ | [ko-competitor-matrix.md](ko-competitor-matrix.md) |
| 비즈니스 모델 | 서비스 흐름과 돈의 흐름 | [ko-business-model.md](ko-business-model.md) |
| 5 Forces | 산업 구조 분석 | [ko-five-forces.md](ko-five-forces.md) |
| 가치사슬 | 본원·지원 활동과 강점 | [ko-value-chain.md](ko-value-chain.md) |

### 시스템·공공 SI

| 도식 | 쓰는 곳 | 참조 |
|---|---|---|
| 망 구성도 | 외부망·DMZ·업무망, 망연계 | [ko-network-zones.md](ko-network-zones.md) |
| 보안 체계도 | 관리적·물리적·기술적 보안, 준거 법령 | [ko-security-framework.md](ko-security-framework.md) |
| 정보구조도 (IA) | 메뉴 depth와 신규·개선 화면 | [ko-ia-sitemap.md](ko-ia-sitemap.md) |
| 서비스 블루프린트 | 고객 행동·접점·후방 업무·지원 시스템 | [ko-service-blueprint.md](ko-service-blueprint.md) |
| PDCA 순환 | 계획·실행·점검·개선 체계 | [ko-cycle.md](ko-cycle.md) |

### 차트

| 도식 | 쓰는 곳 | 참조 |
|---|---|---|
| 도넛 차트 | 예산·구성비 | [ko-donut.md](ko-donut.md) |
| 누적 막대 | 연도별 구성 변화와 합계 | [ko-stacked-bar.md](ko-stacked-bar.md) |
| 콤보 차트 | 금액 막대 + 증가율 선 | [ko-combo.md](ko-combo.md) |
| 목표 달성률 (불릿) | 지표별 실적·목표·달성률 | [ko-bullet.md](ko-bullet.md) |
| 양방향 막대 | 두 집단·전후 비교 | [ko-butterfly.md](ko-butterfly.md) |

각 도식은 `assets/example-<slug>.html`(밝게), `-dark`, `-full` 예시를 가진다. 갤러리의 "보고서 도식" 분류에서 볼 수 있다.
