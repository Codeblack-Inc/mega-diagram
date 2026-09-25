# SWOT 분석 / SWOT Analysis

**Best for:** the 사업계획서·전략 보고서 figure that lays out 강점·약점·기회·위협 on a 내부/외부 × 긍정/부정 2×2, with 3–4 bullets each, and an optional strip of SO·ST·WO·WT 교차 전략 below that names the one to pursue first.

Korean report figure, not a new visual type. It inherits the **Quadrant** consultant variant ([type-quadrant.md](type-quadrant.md)) — four named cells on two axes, one focal element — but the axes are categorical labels, not arrows, and each cell carries a bullet list.

## 쓰는 곳 / 쓰지 않는 곳

Use it when the reader needs the situation *and* the strategic response on one page.

Use instead:

- Items positioned by two measured scores → **Quadrant** ([type-quadrant.md](type-quadrant.md)).
- Stakeholders by 영향력 × 관심도 → **Stakeholder map** ([ko-stakeholder-map.md](ko-stakeholder-map.md)).
- Vision → strategy → tasks → **Strategy house** ([type-strategy-house.md](type-strategy-house.md)).
- Likelihood × impact of risks → **Risk matrix** ([ko-risk-matrix.md](ko-risk-matrix.md)).

## Layout

Canvas `viewBox="0 0 1000 576"`, all geometry on the 4px grid.

| Element | Geometry |
|---|---|
| Column captions `긍정 요인` / `부정 요인` | centred over each column, baseline y=48 |
| Row captions `내부 환경` / `외부 환경` / `교차 전략` | right-aligned at x=104, vertically centred on the row |
| SWOT cells | x = 120 / 548, y = 64 / 220, 412 × 140 (16px gaps) |
| Separator | hairline y=376, x 120–960 |
| Strategy strip | x = 120 / 332 / 544 / 756, y=392, 204 × 88 (8px gaps) |
| Legend | hairline y=512, row baseline y=544 |

- **Fixed order:** S top-left, W top-right, O bottom-left, T bottom-right. Rows are 내부/외부, columns 긍정/부정 — never swap them.
- **Cell anatomy:** heading `강점 (S)` 14px/600 `ink` at `y + 28`; hairline at `y + 40`; bullets 12px/400 `muted` at `y + 62` + 20·k, 1.5px dot at `x + 20`, text at `x + 28`.
- **Strategy cell:** tag `SO 전략` 12px/600 at `y + 24`, two lines 12px/400 `muted` at `y + 52` / `y + 70`.
- Axis captions are horizontal text only — no `writing-mode`, no arrows.

## Treatments

| Role | Fill / stroke |
|---|---|
| SWOT cell | `ink @ 0.03` / `ink @ 0.20` |
| 교차 전략 | `backend` / `ink @ 0.30` |
| 우선 추진 전략 (1 only) | `accent-tint` / `accent`; tag in `accent` |

No hue per quadrant (no green 강점 / red 위협). Accent budget: the one priority strategy cell. The four SWOT cells stay neutral because they are evidence, not decisions.

## Korean wording

- Bullets 명사형·개조식, ≤16자, one fact each, numbers where they exist (`기업 고객 재구독률 92%`, `식자재 물가 전년 대비 7% 상승`).
- Each strategy cell: two lines ≤12자 that read as *which strength/weakness × which opportunity/threat → action* (`바우처 대상 중소기업` / `재구독 사례로 공략`).
- Targets, dates, owners go in the `-full` cards.

## Complexity budget

- 4 cells × 3–4 bullets. A fifth bullet means the cell holds two ideas; merge or move one to the cards.
- Strategy strip: 0 or 4 cells (all four combinations), exactly one focal.

## Anti-patterns

- Traffic-light colours per quadrant.
- Internal facts in 기회/위협 (`영업 인력 부족` is a 약점, not a 위협).
- Strategies that do not trace to a bullet above.
- Accent on a SWOT cell *and* a strategy — pick the decision.
- Sentence bullets (`원가율이 높아 수익성이 떨어지고 있음`).

## Checklist

- [ ] S/W/O/T in fixed positions with 내부/외부 × 긍정/부정 captions.
- [ ] 3–4 bullets per cell, ≤16자, `tw + 44 ≤ 412`.
- [ ] Strategy strip absent or complete (SO/ST/WO/WT), one focal.
- [ ] All Korean text 12px (headings 14px) with the Pretendard stack.
- [ ] `self_check.py`, `lint-skin.py`, `verify-geometry.py`, `lint-render.py` pass; light and dark PNGs checked.

## Examples

- `assets/example-swot.html` — minimal light
- `assets/example-swot-dark.html` — minimal dark
- `assets/example-swot-full.html` — full editorial
