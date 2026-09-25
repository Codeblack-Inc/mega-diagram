# 위험 관리 매트릭스 / Risk Matrix

**Best for:** the 사업·전환 계획서 figure that scores each 위험 on 발생 가능성 × 영향도 (5단계씩), plots numbered risks R1–R6 on a 5×5 grid whose cells darken with the score, and lists each risk's 대응 방안 in a side table.

Korean report figure, not a new visual type. It inherits **Heatmap** ([type-heatmap.md](type-heatmap.md)) — one monotone ink ramp, paper underlay per cell, one accent — with the fill driven by the score band instead of a measured value, and adds marker chips and a table.

## 쓰는 곳 / 쓰지 않는 곳

Use it when a reviewer must see which risks are serious *and* that each has a response.

Use instead:

- A measured value per row × column (failure rate, volume) → **Heatmap** ([type-heatmap.md](type-heatmap.md)).
- Items positioned by two continuous scores → **Quadrant** ([type-quadrant.md](type-quadrant.md)).
- Causes of one incident → **Fishbone** ([type-fishbone.md](type-fishbone.md)).
- Only a risk register with no scoring → a table.

## Layout

Canvas `viewBox="0 0 1000 496"`, all structural geometry on the 4px grid.

| Element | Geometry |
|---|---|
| Grid | columns 발생 가능성 1→5 at x = 120 + 72·(L−1); rows 영향도 5→1 at y = 48 + 64·(5−I); cell 68 × 60, rx=2, 4px gaps |
| Tick numbers | Geist Mono 9 `soft`: below each column (y=380), left of each row (x=108, end) |
| Axis names | `발생 가능성` centred under the grid (y=404); `영향도` at x=40 beside the grid middle — horizontal, never rotated |
| Risk chip | circle r=12 at the cell centre; two risks in one cell → x ±16 |
| Table | x 544–960; header band 32px (`ink @ 0.04`, rx=6); 6 rows × 48 → ends at y=368, level with the grid |
| Table columns | 번호 chip cx=568 · 위험 x=596 · 점수 swatch x=724 + number x=744 · 대응 방안 x=776 |
| Legend | hairline y=432, row baseline y=464: five bands + 최우선 대응 |

### Score bands (score = L × I)

| Band | Score | Ink opacity |
|---|---|---|
| 낮음 | 1–4 | 0.05 |
| 보통 | 5–9 | 0.14 |
| 높음 | 10–14 | 0.28 |
| 매우 높음 | 15–19 | 0.44 |
| 심각 | 20–25 | 0.60 |

Monotone, lowest ≥ 0.05, highest ≤ 0.70 (Heatmap ramp bounds). Each cell is a `paper` underlay plus the tinted rect carrying `data-score`.

## Treatments

| Role | Treatment |
|---|---|
| Risk chip | `paper` fill, `ink` 1 stroke, `R1` 12px/600 `ink` — readable on every band |
| 최우선 대응 chip (1 only) | `accent` fill, `paper` text — same chip in grid and table |
| Table risk name | 12px/600 `ink`; score 12px/500 `muted`; 대응 방안 12px/400 `muted` |
| Score swatch | 12 × 12 of the band tint, `ink @ 0.20` 0.8 stroke |

Accent budget: the one focal risk (its two chips are one element). No red/amber/green ramp.

## Korean wording

- 위험: 명사형 ≤9자, the event not the cause (`전환 중 결제 중단`, not `DB 이관 절차 미흡`).
- 대응 방안: ≤14자 action (`이중 운영·단계 전환`, `수수료 3개월 면제`).
- Owners, deadlines, thresholds go in the `-full` cards.

## Complexity budget

- Risks: ≤6 on one figure (the table height matches the grid). More → split by category.
- ≤2 risks per cell; a third means the scoring is too coarse.
- Exactly one focal risk.

## Anti-patterns

- Red–yellow–green cell colours; the ink ramp already carries severity.
- Rotated `영향도` axis text.
- Risk names inside the grid cells — only the R-number goes there; names live in the table.
- Chips with coloured fills that change per band (unreadable on dark cells).
- A focal risk chosen by score alone when the figure's argument is elsewhere — pick the one the title is about.

## Checklist

- [ ] Rows 영향도 5→1 top to bottom, columns 발생 가능성 1→5 left to right; tick numbers on both.
- [ ] Band opacities monotone, 0.05–0.60; legend states each band's score range.
- [ ] Each plotted risk appears in the table with score = L × I and a 대응 방안.
- [ ] One accent risk; all Korean text 12px with the Pretendard stack.
- [ ] `self_check.py`, `lint-skin.py`, `verify-geometry.py`, `lint-render.py` pass; light and dark PNGs checked.

## Examples

- `assets/example-risk-matrix.html` — minimal light
- `assets/example-risk-matrix-dark.html` — minimal dark
- `assets/example-risk-matrix-full.html` — full editorial
