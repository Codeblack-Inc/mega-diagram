# mega — 한국어 문서용 규칙

mega-diagram은 [diagram-design](https://github.com/cathrynlavery/diagram-design)(Cathryn Lavery, MIT)의 편집 원칙과 41종 레이아웃을 그대로 쓰고, 한국 보고서 형식 3종을 더해 44종이 되었다. 원본에서 바꾼 것은 세 가지다.

1. **색** — [mega BI](https://github.com/Codeblack-Inc/mega-bi) 팔레트. 강조색은 mega-diagram 블루 `#2F6FDB` 하나.
2. **한글** — 사용자가 한국어로 요청하면 라벨도 한국어가 기본이다. Hangul은 Pretendard로 그린다.
3. **배경** — SVG에 배경 사각형을 그리지 않는다. 내보낸 SVG/PNG는 투명해서 HWP·Word·PPT 본문에 그대로 얹힌다.

### 한국 보고서 전용 형식

원본에 없는 형식 세 가지를 더했다. 사업계획서·연구과제 계획서·공공 보고서에서 가장 자주 쓰는 도식이다.

| 형식 | 쓰는 곳 | 참조 |
|---|---|---|
| **전략 체계도** (Strategy house) | 비전 → 목표 → 추진 전략 → 추진 과제, 하단 기반 | [type-strategy-house.md](type-strategy-house.md) |
| **추진 체계도** (Governance) | 발주·전담기관, 주관기관, 참여·수요기관의 역할과 관계 | [type-governance.md](type-governance.md) |
| **추진 로드맵** (Roadmap) | 단계(연차) × 추진 과제·산출물·성과 지표, 마일스톤 | [type-roadmap.md](type-roadmap.md) |

"보고서에 넣을 그림"을 요청받으면 이 세 가지와 조직도·간트·타임라인을 먼저 후보로 둔다.

이 문서는 SKILL.md와 [style-guide.md](style-guide.md)를 덮어쓰지 않고 보탠다. 충돌하면 연결선 규칙(SKILL.md §6)과 복잡도 예산(§7)이 이긴다.

---

## Korean labels

폭 계산, 12px 하한, 레지스터 전환 같은 기본 규칙은 [style-guide.md § Korean labels](style-guide.md#korean-labels)에 있다. 여기서는 문서에 들어갈 글을 어떻게 쓰는지를 정한다.

| 슬롯 | 한글 처리 | 예 |
|---|---|---|
| 노드 이름 | Pretendard 12–13px, 600. **명사형**, 10자 이내 | `결제 승인`, `주문 DB` |
| 기술 부제 | 영문 `Geist Mono` 유지. 번역하지 않는다 | `POST /v1/pay`, `:8443` |
| 화살표 라벨 | 12px, 500, 대문자·자간 없음. 6자 이내 동사 명사형 | `승인 요청`, `결과 저장` |
| 범례·축 이름 | 12px, 500 | `외부 시스템`, `처리 시간(초)` |
| 영문 eyebrow·태그 | 원본 규칙 그대로(7–8px mono, 대문자) | `API`, `DB` |
| 제목(`<title>`) | 한 줄 명사구, 30자 이내 | `주문 결제 처리 흐름` |

글쓰기 규칙:

- **개조식·명사형으로 끝낸다.** `결제를 승인합니다` → `결제 승인`. 노드 안에 문장을 넣지 않는다.
- **한 노드 한 줄이 기본.** 두 줄이 필요하면 `<tspan x="CX" dy="16">`으로 나누고 박스 높이를 16px 늘린다. SVG는 자동 줄바꿈이 없으므로 넘친 글은 잘리지 않고 박스 밖으로 샌다.
- **폭은 글자마다 센다.** 한글·전각 문자는 1em, 나머지는 해당 서체의 라틴 폭(sans 0.60em, mono 0.62em). `주문 v2.1` at 12px = 2×12 + 5×7.2 = 60px + 좌우 패딩 → 4의 배수로 올림.
- **숫자와 단위.** 천 단위 쉼표(`12,400`), 금액은 `억 원`·`만 원`, 비율은 `%`, 기간은 `2026.09` 또는 `2026년 3분기`. 한 그림 안에서 한 가지 표기만 쓴다.
- **구분자.** 나열은 가운뎃점 `·`, 범위는 물결 `~`(`3~5일`), 화살표 글자(`→`)는 라벨 안에 쓰지 않는다 — 화살표는 선이 그린다.
- **외래어·약어.** 문서 독자가 쓰는 말을 쓴다. 개발 문서는 `API 게이트웨이`, 경영 보고는 `외부 연동 창구`. 청중 다이얼(`engineer`·`mixed`·`executive`, [output-spec.md §4](output-spec.md))이 결정한다.
- **한자·일본어 슬롯 금지.** 한국 문서에 `詳細`/`簡略` 같은 표기를 쓰지 않는다.

---

## Document presets

목적지에 맞춰 크기·스킨·배율을 고른다. 크기 이름은 [output-spec.md §2](output-spec.md)의 프리셋이다.

| 목적지 | 크기 | 스킨 | 내보내기 |
|---|---|---|---|
| HWP·Word A4 본문(세로) | `doc-inline` (960×600) | `mega` | PNG @2 → 1920px ≈ 본문 폭 16cm에서 300dpi |
| A4 가로 부록·도면 | `print-a4-landscape` | `mega` | PNG @3 |
| 흑백 인쇄 보고서 | `doc-inline` | `mono` | PNG @3 |
| mega-ppt 장표 패널 | 패널 비율에 가까운 프리셋 (`slide-16x9`, `doc-inline`) | `mega-ppt` | PNG @2, `fit: contain` |
| 어두운 슬라이드 | `slide-16x9` | 다크 변형 (`template-dark.html`) | PNG @2 |
| 위키·README | `doc-wide` | `mega` | SVG 또는 PNG @2 |

### 스킨 프리셋

기본 `mega` 스킨은 [style-guide.md](style-guide.md)의 값이다. 나머지 둘은 **바뀌는 줄만** 적는다. 쓰려면 style-guide.md를 복사해 아래 값을 바꾼 뒤 [profiles.md](profiles.md)의 `save`로 프로필(`mega-ppt`, `mono`)을 만들고, 프로젝트 루트의 `.mega-diagram` 마커(`profile: mega-ppt`)로 묶는다.

| 역할 | `mega` (기본) | `mega-ppt` | `mono` |
|---|---|---|---|
| `accent` | `#2f6fdb` | `#b5452d` (mega-ppt 진한 coral) | `#17152b` (ink) |
| `accent-tint` | `rgba(47,111,219,0.08)` | `rgba(181,69,45,0.08)` | `rgba(23,21,43,0.08)` |
| `link` | `#6043d5` | `#6043d5` | `#68657b` + 점선 `4,3` |

- **`mega-ppt`** — mega-ppt 기본 테마(잉크·페이퍼·coral)와 같은 강조색. 작은 글자와 색면 대비를 위해 공식 coral `#F37055` 대신 `#B5452D`를 쓴다(mega-ppt와 같은 선택).
- **`mono`** — 흑백 인쇄에서 색이 사라져도 초점이 남도록 강조 노드는 테두리 `stroke-width="2"`로 굵게 그린다. 색만으로 구분하던 범례 항목은 점선·실선으로 바꾼다.

### 배경과 마스크

화살표 라벨과 노드 뒤의 불투명 마스크는 `paper`로 칠한다. 기본 `paper`가 흰색이라 흰 문서에서는 보이지 않는다. 목적지가 흰색이 아니면(예: 회색 박스 안, 색 슬라이드) `paper`를 그 색으로 바꾼 스킨으로 다시 그린다 — 투명 PNG 위의 흰 칩이 문제의 신호다.

---

## Export to documents

내보내기 절차는 [export.md](export.md)를 따른다. 문서에 넣을 때 추가로 지킬 것:

- **HWP·Word·PPT에는 PNG가 기본이다.** SVG의 웹 폰트(Pretendard, Geist)는 오피스 프로그램이 불러오지 않아 다른 서체로 바뀐다. PNG는 브라우저가 그린 글자를 그대로 굽는다.
- **SVG가 꼭 필요하면** (편집 가능한 벡터, 위키) 받는 쪽에 Pretendard가 설치돼 있어야 같은 모양이 나온다. PowerPoint는 export.md의 `rgba` → `fill-opacity` 변환을 거친 SVG만 제대로 읽는다.
- **투명 확인.** PNG를 흰 배경과 `#F6F5FA` 배경 위에 한 번씩 얹어 본다. 가장자리에 흰 사각형이 보이면 배경 사각형이 남은 것이다.
- **파일 이름**은 영문 슬러그(`order-payment-flow.png`). 한글 파일 이름은 HWP 링크·Git·CI에서 깨지기 쉽다. 그림 안의 글은 한국어여도 된다.

---

## Hand-off to other mega tools

| 도구 | 넘기는 방법 |
|---|---|
| [mega-ppt](https://github.com/Codeblack-Inc/mega-ppt) | PNG를 deck.json 옆에 두고 `image` 패널로 넣는다: `{"type": "image", "src": "diagrams/order-flow.png", "alt": "주문 결제 처리 흐름", "fit": "contain", "border": false, "caption": "주문 결제 처리 흐름"}`. `alt`는 SVG `<title>`을 그대로 쓴다. 다이어그램은 자르지 않으므로 `focus`·`crop`을 쓰지 않는다. 스킨은 `mega-ppt`. |
| mega-hwp (준비 중) | PNG @2 또는 @3. HWP 그림 넣기는 투명 PNG를 지원한다. |
| Word (`.docx`) · PowerPoint (`.pptx`) 스킬 | PNG를 그림으로 삽입하고, 대체 텍스트에 SVG `<desc>` 문장을 넣는다. |
| [mega-ui](https://github.com/Codeblack-Inc/mega-ui) | 인라인 SVG를 그대로 쓴다. 색은 mega-ui/mega-bi 토큰(`--mega-ink` 등)과 같은 값이다. |

그림 번호(`[그림 1]`)와 캡션은 다이어그램에 그리지 않는다. 문서 도구(mega-ppt `caption`, HWP 캡션)가 번호를 매긴다 — 그림 안에 넣으면 번호가 이중으로 붙는다.

---

## Korean pre-output check

SKILL.md §9 체크리스트에 더해:

- [ ] 한국어 요청이면 노드·화살표·범례 라벨이 한국어인가? 기술 부제만 영문인가?
- [ ] 모든 한글 글자가 12px 이상인가?
- [ ] 한글 라벨이 박스 폭을 넘지 않는가? (글자별 폭 계산 후 브라우저에서 PNG로 확인)
- [ ] 문장형 라벨(`~합니다`, `~한다`)이 없는가?
- [ ] SVG 안에 전면 배경 사각형이 없는가?
- [ ] 목적지에 맞는 크기·스킨·배율을 골랐는가? (§ Document presets)
