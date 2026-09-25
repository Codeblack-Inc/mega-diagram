# 성과지표 체계 (KPI tree)

**Best for:** the 성과계획서·사업계획서 figure that decomposes one 최종 목표 into 2–3 성과 목표 and, under each, the 성과 지표 with 현재값 → 목표값 and 측정 방법. It answers "how will we know it worked?" and is the figure 평가위원 check targets against.

This is a catalogued Korean report pattern, not a new visual type. It inherits from **Tree** ([type-tree.md](type-tree.md)) — root at left, children to the right, orthogonal bus connectors, 3 levels — and adds a value column to the leaves.

## 쓰는 곳 / 쓰지 않는 곳

Use it when every leaf is measurable with a baseline, a target and a data source.

Don't use it for:

- Vision → strategies → tasks (the *means*, not the *measures*) → **Strategy house** ([type-strategy-house.md](type-strategy-house.md)).
- How inputs become outcomes → **로직 모델** ([ko-logic-model.md](ko-logic-model.md)).
- Indicator values across phases → the KPI band of a **Roadmap**.
- A flat list of 5 indicators with no goals above them → a table.

## Layout grammar

Canvas `viewBox="0 0 1000 616"` for 3 goals × 2 indicators, 40px margins, 4px grid.

| Column | Geometry |
|---|---|
| Column headings | baseline y=64, 12px 500 `muted`: `최종 목표` (x=40), `성과 목표` (x=296), `성과 지표 · 측정 방법` (x=568), `현재` (right-aligned x=820), `목표` (x=868) |
| 최종 목표 (focal) | x=40, w=200, h=128, vertically centred on the leaf span |
| 성과 목표 | x=296, w=200, h=72, each centred on its two leaves |
| 성과 지표 | x=552, w=408, h=56; 16px between leaves of one goal, 32px between goals; first at y=80 |
| Legend | hairline 32px below the last leaf, items +32 |

- **Connectors** (type-tree bus): a stem from the parent's right-edge centre to the mid-gutter bus (x=268 / x=524), then per child a vertical run and an `r=8` quarter-curve into a horizontal that ends at the child's left edge. `muted` 1px, **no arrowheads** — hierarchy, not flow. The middle child's horizontal starts at the bus, not at the parent, so no two strokes overlap.
- **Root anatomy:** plan period mono 9px `accent` at y+24; goal 16px 600 on two lines (y+50, y+72); `rule` hairline at y+88; headline target 12px 500 `muted` at y+110.
- **Goal anatomy:** `성과 목표 n` 12px 500 `soft` at y+26 and `가중치 40%` right-aligned; name 14px 600 at y+52.
- **Indicator anatomy:** name 12px 600 at x+16, y+24; 측정 방법 12px `soft` at y+44; current value 14px 600 `muted` (14 is a heading size, so it must be 600 — the ramp has no 14px regular) right-aligned at x=820 (row centre +5); a 24px `muted` arrow 832→856; target 16px 600 `ink` left-aligned at x=868.
- **Paint order:** headings → connectors → root → goals → indicators → legend.

## Node treatments by semantic role

| Role | Treatment | Fill / stroke |
|---|---|---|
| 최종 목표 (focal, 1) | `focal` | `accent-tint` / `accent`, 1.2 |
| 성과 목표 | `backend` | white (dark `#24223a`) / `ink` |
| 성과 지표 | `backend` light | white / `ink @ 0.30` |

Accent on the root only (type-tree: root *or* one critical leaf, never both). Don't colour targets — the bold target column already stands out.

## Korean wording

- 최종 목표 ≤ 12자 noun phrase; its target line names the one headline indicator (`수단분담률 35% 달성`).
- 성과 목표 ≤ 9자 with a direction noun (`단축`, `향상`, `제고`) and a 가중치; weights sum to 100%.
- 성과 지표 ≤ 9자, a measurable quantity (`도착 정보 정확도`), never a goal (`정확도 향상`).
- 측정 방법 ≤ 14자, naming the data source (`BIS 운행 기록 분석`, `연 1회 설문 (n=2,000)`).
- Values: same unit on both sides (`12분` / `8분`, `월 420건` / `월 250건`). Baseline year and measurement cycle go in the `-full` cards.

## Complexity budget

- 1 root, 2–3 goals, 2 indicators per goal (max 3; ≤ 8 leaves total). Depth exactly 3.
- 1 accent. Connectors: 1 + goals + leaves paths, none crossing.

## Anti-patterns

- Indicators without a baseline (`목표 95%` alone). The pair is the content.
- 측정 방법 omitted; a reviewer's first question is "where does this number come from?"
- Arrowheads on tree connectors, or diagonal spokes from root to goals.
- Mixed units in one row (`82%` → `0.95`).
- Activity indicators (`교육 12회`) in an outcome tree.

## Pre-output checklist

- [ ] Root → goals → indicators, left to right, bus connectors with r=8, no arrowheads?
- [ ] Every indicator has name, 측정 방법, current and target in the same unit?
- [ ] Goal weights present and sum to 100%?
- [ ] Only the root accented?
- [ ] Korean ≥12px, Pretendard stack, sizes 12 / 14 / 16 (mono 9 period)?
- [ ] Legend strip; light/dark/full identical; verifiers pass; PNGs checked?

## Examples

- `assets/example-kpi-tree.html` — minimal light. 가온시 스마트 대중교통 혁신: 대중교통 이용 편의 향상 → 이동 시간 단축 40% (배차 간격 12분 → 8분, 환승 대기 9분 → 5분), 서비스 신뢰도 향상 35% (도착 정보 82% → 95%, 정시 운행 76% → 90%), 이용 만족도 제고 25% (만족도 68점 → 80점, 민원 월 420건 → 월 250건).
- `assets/example-kpi-tree-dark.html` — minimal dark, same labels.
- `assets/example-kpi-tree-full.html` — full editorial.
