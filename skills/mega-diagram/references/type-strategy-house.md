# Strategy House (전략 체계도)

**Best for:** the Korean 보고서 / 사업계획서 / 중장기 계획 figure that reads top-down from one 비전 to measurable 목표, the 추진 전략 that carry them, the 추진 과제 under each strategy, and the shared 기반 everything stands on. Public-sector 5-year plans, enterprise 중기 경영전략, digital transformation roadmaps at the "what", not the "when", level.

A strategy house is a **tiered census, not a flow**: it has **no connectors**. Vertical order carries the hierarchy (위가 목적, 아래가 수단). If the figure needs arrows between pillars, it is a dependency or process diagram; if it needs dates, it is a Gantt or timeline.

## When not to use

- **Schedules or phases** (`1단계 2026`, `2단계 2027`): use timeline or Gantt. A strategy house has no time axis beyond the one plan period on the vision banner.
- **Cause and effect between tasks**: use dependency or flowchart.
- **Unequal nesting**, where one strategy has 6 tasks and another has 1: use tree or org chart. The house works only when the pillars are balanced.
- **Goals without numbers**: if no 목표 carries a KPI, cut the goal tier or write it as a paragraph. A goal tier that restates the vision in three boxes adds nothing.

## Layout conventions

All geometry sits on the 4px grid inside a `0 0 1000 520` viewBox. The house spans x = 120–960 (width 840). The left margin (x = 32) carries the tier labels.

| Tier | y | Height | Geometry |
|---|---|---|---|
| 비전 | 40 | 56 | One banner, full width 840, `rx=6` |
| 목표 | 120 | 64 | 3 cards × 264, gap 24 (2 cards: 408 each) |
| 추진 전략 (header) | 208 | 48 | 4 columns × 192, gap 24 (3 columns: 264 each) |
| 추진 과제 (rows) | 256 | 3 × 36 | Rows inside each column. Column rect runs 208–364 |
| 기반 (optional) | 388 | 48 | One bar, full width 840 |
| Legend strip | 468 | — | Hairline at 468, items at baseline 496 |

- **Tier gap is 24** everywhere (96→120, 184→208, 364→388). Without a 기반 bar, the legend hairline moves up to 396 and the viewBox shrinks to 448.
- **Tier labels**: `비전` · `목표` · `추진 전략` · `추진 과제` · `기반` at x = 32, Korean 12px weight 500 `muted`, no tracking, baseline at the tier's vertical center + 4. They are the 보고서 index column, so don't box or number them.
- **Vision banner**: the vision sentence centered, Geist/Pretendard 16px 600. The plan period sits right-aligned inside the banner as a Geist Mono 9px sublabel (`2026~2030`).
- **Goal card**: the KPI number on the left at x + 16 (28px 600, `−30%`, `85%`). The goal name at x + 112 (14px 600) and one baseline/target line under it (Korean 12px 500 `muted`: `현재 20일, 목표 14일`).
- **Strategy column**: one rect holds the header and its tasks, so each pillar reads as a single object. The header holds a type tag (`S1`, 20×12, `rx=2`, Geist Mono 7px) at x + 12 and the strategy name at x + 40 (14px 600). A full-width hairline sits at y = 256 under the header.
- **Task rows**: a Geist Mono 9px `soft` number (`1-1`) at x + 16 and the task name at x + 40 (12px 600). Rows are divided by `rule` hairlines inset 12px from the column edges, not boxed. Twelve boxes would out-shout four pillars.
- **Foundation bar**: 2–4 items centered in equal segments. With 4 pillars, the dividers sit at the pillar gutters (x + 216k − 12), so each foundation item centers under a pillar. The bar spans all pillars on purpose: it supports every strategy, not one.
- **Drawing order**: tier labels → vision → goals → columns (rect, tag, name, header rule, task rows) → foundation → legend.

## Node treatments by semantic role

| Role | Fill | Stroke | Notes |
|---|---|---|---|
| 비전 (focal 1) | `accent-tint` | `accent` | Plan period in `accent` mono |
| 목표 | `paper` (white) | `ink` | Number and name in `ink`. Don't color KPIs |
| 추진 전략 column | `ink @ 0.03` | `ink @ 0.30` | Header rule `rule` |
| Core strategy (focal 2) | `accent-tint` | `accent` | Tag and header rule in `accent` |
| 추진 과제 row | none (column fill) | `rule` hairline between rows | Number `soft` mono |
| 기반 | `ink @ 0.05` | `muted` | `store` treatment. Dividers `rule` |

**Focal rule**: at most 2 accents, normally the vision banner plus **one** core strategy (the one the other strategies depend on). You may also accent the vision alone. Never accent a goal *and* a strategy, and never accent a single task: the reader should see which pillar carries the plan, not which line item is urgent.

## Korean wording

- **Vision**: one line, noun phrase, ≤ 20자, no period (`데이터로 여는 모두의 공공서비스`). It is a slogan, not a sentence.
- **Goals**: `지표명` + number with its unit. Name ≤ 9자 (`민원 처리 기간`, `공공데이터 개방률`). Direction lives in the sign (`−30%`), not in a verb. The sublabel gives baseline and target (`현재 62%, 2030년`, `2025년 대비`). Use one number style per figure: `%` throughout, or `억 원` throughout.
- **Strategies**: 명사형 ≤ 8자 (`민원 서비스 혁신`, `데이터 개방·활용`). Pair two nouns with `·`, never `/` or `및`.
- **Tasks**: 명사형 ≤ 10자, numbered `전략-과제` (`2-1`, `2-2`) so the text can cite them. No 문장형 (`개방합니다` → `전면 개방`).
- **Foundation**: 2–4 items ≤ 8자 (`추진 거버넌스`, `데이터 품질 관리`, `정보보호 체계`, `디지털 전문 인력`).
- **Width budget** (style-guide § Korean labels): Hangul = 1em, other characters 0.60em. A 10자 task name with 3 spaces at 12px is 10×12 + 3×7.2 ≈ 142px, which is the most a 192 column holds after the 40px number gutter and 12px right padding. Over budget → shorten the wording. Don't shrink below 12px and don't wrap a task into two lines.

## Complexity budget

- 1 vision · ≤ 3 goals · ≤ 4 strategies · ≤ 3 tasks per strategy (≤ 12 tasks) · ≤ 4 foundation items.
- Pillars must be balanced: every strategy gets the same number of tasks (±1). Pad with nothing. If one pillar has 1 task and another has 3, the 1-task pillar is probably a task of another pillar.
- Max 2 accent elements.
- Over budget (5 strategies, 4+ tasks each) → split: one house with strategies only (tasks cut), then one detail figure per strategy (tree or table).

## Anti-patterns

- **Arrows between tiers or pillars.** Order already says "supports". An arrow from each task to its strategy is 12 redundant connectors.
- **A literal house**: triangle roofs, drop shadows, 3D pillars. The metaphor is structural; draw it with flat bands.
- **Each pillar in a different color.** It erases the focal strategy and turns the figure into a rainbow legend.
- **Goals with no numbers** (`국민 만족도 향상`). If it can't be measured, it belongs in the vision.
- **Sentence labels** (`민원 처리 기간을 30% 단축한다`). Split them into name + number.
- **Tasks as 12 separate boxed cards.** Use rows inside the column. The column is the object.
- **Foundation drawn as a fifth pillar.** 기반 spans the full width because it underlies all strategies.
- **Figure number or caption inside the SVG** (`[그림 3] 추진 체계`). The document tool numbers figures (mega.md).

## Pre-output checklist

- [ ] One vision line, ≤ 20자, noun phrase?
- [ ] Every goal has a number, a unit, and a baseline or target line?
- [ ] ≤ 4 strategies, ≤ 3 tasks each, pillars balanced?
- [ ] Tasks numbered `n-m` and named ≤ 10자, 명사형?
- [ ] Column x = 120 + 216k (4 pillars) or 120 + 288k (3 pillars), all on the 4px grid?
- [ ] Zero connectors?
- [ ] ≤ 2 accents: vision and/or one core strategy?
- [ ] Every Korean `<text>` uses `'Geist', 'Pretendard', 'Noto Sans KR', sans-serif` at ≥ 12px? Numbers (`1-1`, `2026~2030`) in Geist Mono?
- [ ] Font sizes on the ramp: 12 (names/tasks), 14 (goal and strategy headings), 16 (vision), 28 (KPI)?
- [ ] Legend strip at the bottom names the accent meaning (`비전·핵심 전략`) and the foundation treatment?
- [ ] Light, dark, and full variants carry identical labels?

## Examples

- `assets/example-strategy-house.html`: minimal light. 2030 공공서비스 디지털 전략: vision, 3 KPI goals, 4 strategies × 3 tasks, 4-item foundation. The vision and `S2 데이터 개방·활용` are accented.
- `assets/example-strategy-house-dark.html`: minimal dark, same labels.
- `assets/example-strategy-house-full.html`: full editorial. Korean header, 3 summary cards of varied widths, and a footer.
