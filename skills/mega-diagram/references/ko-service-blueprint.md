# Service Blueprint / 서비스 블루프린트

**Best for:** the 공공서비스 디자인·서비스 개선 사업 figure that lays one service out by stage and by layer: what the 고객 does, which 접점 they meet (front-stage), what 후방 업무 happens behind it (back-stage), and which 지원 시스템 supports it — separated by the 상호작용선 and the 가시선, with the one 불편 지점 that the project will fix.

This is a Korean report pattern, not a new visual type. It inherits the stage-column grid and pain-marker rule of **User journey** ([type-journey.md](type-journey.md)) and the labelled-lane grammar of **Swimlane** ([type-swimlane.md](type-swimlane.md)), with rows fixed to the four blueprint layers.

## When to use / not

Use **Service blueprint** when the argument is "the problem the citizen feels is caused by something they can't see" — the rows below the 가시선 are the point.

Don't use it for:

- How the user *feels* per stage (sentiment) → **User journey**.
- Hand-offs between departments with decisions and branches → **Swimlane** or **Flowchart**.
- System components and APIs → **Architecture**.

## Layout conventions

Canvas `viewBox="0 0 1000 520"`. The left margin (x = 40–144) holds row and line labels; stage columns start at x=160.

| Element | Geometry |
|---|---|
| Stage columns | 5 × 136, gap 24, x = 160 + 160i (to 936) |
| Stage headers | y=40, h=32, `rx=4`, `external`; Geist Mono 9px index `01` at x+12, name 12px/600 centred (+8) |
| 고객 행동 row | cards y=88, h=48 |
| 불편 지점 tag | under its customer card: y=148, 104 × 20, centred in the column |
| 상호작용선 | y=184, solid `ink @ 0.30`, 1px, x 40 → 936 |
| 접점 row | cards y=200 |
| 가시선 | y=276, dashed `6,4`, `muted`, 1.2 |
| 후방 업무 row | cards y=292 |
| 내부 상호작용선 | y=368, `rule` hairline (unlabelled) |
| 지원 시스템 row | cards y=384 |
| Legend | Hairline y=464, row baseline y=492 |

- **Row labels** at x=40: Korean 12px/600 at card y+22, Latin Geist Mono 8px `soft` role under it at y+38 (`CUSTOMER`, `FRONT-STAGE`, `BACK-STAGE`, `SUPPORT`).
- **Line labels** (`상호작용선`, `가시선`) at x=40, 8px above their line, 12px/500 `soft`. They sit in the margin, never on the cards.
- **Cards**: one line, 12px/600 centred at y+28; text + 24 ≤ 136, so ≤9자. A stage with no back-stage work leaves the cell empty — don't invent a card.
- **Connectors** (drawn before cards):
  - Customer flow: short `muted` arrows in the 24px gutters of the 고객 행동 row.
  - 접점 → 후방 업무: vertical `muted` 1.2 at the column centre, crossing the 가시선.
  - 후방 업무 → 지원 시스템: vertical `muted` 1, dashed `4,3` (a query, not a hand-off).
  - No arrows across the 상호작용선: the column alignment already pairs an action with its touchpoint.

## Node treatments

| Role | Fill / stroke |
|---|---|
| 고객 행동 | `input`: `muted @ 0.10` / `soft` |
| 접점 · 후방 업무 | `backend`: paper / `ink` |
| 지원 시스템 | `store`: `ink @ 0.05` / `muted` |
| 문제 접점 (focal 1) | `accent-tint` / `accent`, 1.2 |
| 불편 지점 tag (focal 2) | paper / `accent @ 0.50` dashed `3,3`, text 12px/500 `accent` |
| Stage headers | `external`: `ink @ 0.03` / `ink @ 0.30` |

Accent budget: the one problem touchpoint and its pain tag. Nothing else.

## Korean wording

- Stage names 명사형 ≤6자: `정보 탐색`, `온라인 신청`, `서류 보완`, `심사·결정`, `지원금 지급`.
- Card text 명사형 ≤9자: `보완 서류 재제출`, `보완 요청 문자`, `자격 심사·결정`.
- The pain tag states the measurable symptom (`평균 5일 지연`), not an adjective (`불편함`).
- System names are generic (`민원 접수 시스템`, `행정정보 조회`); real product names go in cards if needed.
- Volumes, rates, and the improvement plan go in `-full` cards.

## Complexity budget

- Stages: ≤6 (5 fills the canvas). Rows: exactly 4.
- Connectors: ≤12. Pain markers: 1 (2 only if both are on the same stage).
- Accent: 2.

## Anti-patterns

- Omitting the 가시선. Without it, it is a swimlane.
- A sentiment curve on top; that is a journey map — pick one.
- Pain markers on every stage.
- Arrows zig-zagging between rows and stages; keep verticals inside their column.
- Paragraph text in cards (`신청인이 서류를 다시 제출합니다`).
- Row labels rotated with `writing-mode`.

## Checklist

- [ ] Four rows in blueprint order, 상호작용선 solid, 가시선 dashed, both labelled in the margin.
- [ ] ≤6 stages, card text ≤9자, empty cells left empty.
- [ ] One pain tag + one accent touchpoint in the same stage.
- [ ] ≤12 connectors, all vertical in-column or in the customer gutters.
- [ ] Korean ≥12px, Pretendard stack; mono only for Latin roles and indices.
- [ ] `self_check.py`, `lint-skin.py`, `verify-geometry.py`, `lint-render.py` pass; light and dark PNG checked.

## Examples

- `assets/example-service-blueprint.html` — minimal light
- `assets/example-service-blueprint-dark.html` — minimal dark
- `assets/example-service-blueprint-full.html` — full editorial
