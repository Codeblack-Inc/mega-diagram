# 이해관계자 맵 / Stakeholder Map

**Best for:** the 사업계획서·추진계획 figure that answers *whom do we manage how* — 8–10 이해관계자 placed on 영향력 × 관심도, with one 관리 전략 per quadrant (적극 관리 · 만족 유지 · 정보 제공 · 모니터링) and one 핵심 협상 대상 marked.

Korean report figure, not a new visual type. It inherits every rule of **Quadrant** ([type-quadrant.md](type-quadrant.md)) — axis cross, dots with labels, one accent item — and fixes the axes, the quadrant names, and the corner wording.

## 쓰는 곳 / 쓰지 않는 곳

Use it when each stakeholder's *position* is the argument: a reviewer should see at a glance who must be consulted before a decision and who only needs a newsletter.

Use instead:

- Organisations bound by agreements, funding, and reports → **Governance** ([type-governance.md](type-governance.md)).
- Who does which task (실행·승인·협의·공유) → **RACI** ([ko-raci-matrix.md](ko-raci-matrix.md)).
- Four named scenarios, not positioned items → Quadrant § Consultant special.
- Fewer than 6 stakeholders → a table says it with less ink.

## Layout

Canvas `viewBox="0 0 1000 520"`. Every origin and gap is on the 4px grid.

| Element | Geometry |
|---|---|
| Plot area | x 120–880, y 48–432 |
| Axis cross | `ink @ 0.45`, 1px: horizontal y=240, vertical x=500 |
| Focal quadrant tint (적극 관리, top-right) | rect 500, 48, 380 × 192, `accent @ 0.04`, no stroke |
| Corner block (title + action) | 16px inside the outer corner: top baselines y=72 / 90, bottom y=398 / 416; `text-anchor="end"` on the right side |
| Axis end labels | `영향력 높음` (512, 60), `영향력 낮음` (512, 428), `관심도 낮음` (120, 260), `관심도 높음` (880, 260, end) |
| Stakeholder | dot at (cx, cy), name at (cx + 12, cy + 4), always to the right of the dot |
| Legend | hairline y=464, row baseline y=496 |

- **Axes are fixed:** y = 영향력 (위가 높음), x = 관심도 (오른쪽이 높음). Swapping them breaks the reader's memory of the standard Mendelow grid.
- **Quadrant names are fixed:** TR 적극 관리, TL 만족 유지, BR 정보 제공, BL 모니터링. Under each, one action line in 명사형 (`정기 협의·의사결정 참여`, `주요 결정 사전 보고`, `설명회·소식지 정기 공유`, `동향 점검·최소 대응`).
- **Label box rule:** treat each name as the box (cx + 12, cy − 8, tw(name), 16). It must not cross x=500 or y=240, must stay inside the plot, and must not overlap another name, a corner block, or an axis label. The generator asserts this; do the same.

## Treatments

| Role | Dot | Name |
|---|---|---|
| 핵심 협상 대상 (1 only) | r=6, `accent` | 12px 600 `ink` |
| 이해관계자 | r=4, `ink` | 12px 500 `muted` |
| Corner title | — | 12px 600 `ink` (`accent` on 적극 관리) |
| Corner action | — | 12px 400 `soft` |
| Axis end label | — | 12px 500 `muted` |

Accent budget: the focal dot plus the 적극 관리 tint and title (one zone). No quadrant fills other than the focal tint.

## Korean wording

- Stakeholder names ≤10자, the organisation or group itself: `버스운송사업조합`, `시의회 교통위원회`, `장애인 이동권 연대`. No role verbs (`예산 승인하는 예산담당관`).
- Use fictional local names (`가온시`); ministries may appear as generic roles (`국토교통부`).
- 관리 방법·빈도·금액 (`월 1회 실무 협의`, `국비 24억 원`) go in the `-full` cards, never on the map.
- Korean text is 12px (`'Geist', 'Pretendard', 'Noto Sans KR', sans-serif`), no tracking, no uppercase.

## Complexity budget

- Stakeholders: 8–10 (the Quadrant cap is 12; above 10 the names collide). Group the rest (`주민자치회 5곳`).
- Focal: exactly 1 dot.
- Every quadrant holds at least one stakeholder; an empty quadrant usually means an axis is mis-scored.

## Anti-patterns

- Four differently coloured quadrants. Position already carries the category.
- A name straddling an axis — the quadrant, and therefore the strategy, becomes ambiguous.
- Accent on the most powerful actor by default. Mark the one the figure is about (usually the key negotiation).
- Arrows showing "moving" a stakeholder between quadrants on the same map. Draw a second map or a note in the cards.
- The 사업 주관 부서 plotted as its own stakeholder.
- Legend swatch for the quadrant tint — the accent corner title already names it.

## Checklist

- [ ] y = 영향력, x = 관심도; four fixed quadrant names with one action line each.
- [ ] 8–10 stakeholders, one focal dot, every quadrant populated.
- [ ] No label crosses an axis or overlaps a corner block, axis label, or another name.
- [ ] All Korean text 12px with the Pretendard stack; sizes on the type ramp.
- [ ] Legend strip below the plot (핵심 협상 대상 · 이해관계자).
- [ ] `self_check.py`, `lint-skin.py`, `verify-geometry.py`, `lint-render.py` pass; light and dark PNGs checked.

## Examples

- `assets/example-stakeholder-map.html` — minimal light
- `assets/example-stakeholder-map-dark.html` — minimal dark
- `assets/example-stakeholder-map-full.html` — full editorial
