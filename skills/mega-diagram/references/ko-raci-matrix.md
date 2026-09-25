# 역할 분담표 / RACI Matrix

**Best for:** the 사업 수행계획서 figure that answers *who executes, who is accountable, who is consulted, who is informed* for each 업무 — 6–8 task rows × 4–5 organisation/role columns, one R/A/C/I chip per cell, with the one accountability hand-over marked.

Korean report figure, not a new visual type. It inherits **DP security matrix** ([type-dp-security-matrix.md](type-dp-security-matrix.md)) — row-label column, role header band, closed-vocabulary cell values styled by level, one focal cell — with the RACI vocabulary in place of access levels.

## 쓰는 곳 / 쓰지 않는 곳

Use it when the reader must audit responsibility per task: every row has exactly one A and at least one R.

Use instead:

- Relations *between* organisations (협약, 연구비, 보고) → **Governance** ([type-governance.md](type-governance.md)).
- Who can read/write which system → **DP security matrix** ([type-dp-security-matrix.md](type-dp-security-matrix.md)).
- When each task happens → **Gantt** ([type-gantt.md](type-gantt.md)).
- A hand-off sequence between parties → **Swimlane** ([type-swimlane.md](type-swimlane.md)).

## Layout

Canvas `viewBox="0 0 1000 H"`, H = 104 + 40·rows + 96 (7 rows → 480). All geometry on the 4px grid.

| Element | Geometry |
|---|---|
| Header band | 40, 40, 920 × 56, rx=6, `ink @ 0.04` |
| Role column | x = 320 + 128·i, w 128 (5 columns end at 960) |
| Role header | caption (`발주 부서`) 12px/500 `soft` at y=62, organisation 12px/600 `ink` at y=82, centred |
| Task column | `단계별 업무` caption at (56, 72); rows: number Geist Mono 9 `soft` at x=56, task 12px/600 `ink` at x=80 |
| Rows | from y=104, h 40; hairline under each row, column dividers `rule` 0.8 |
| Chip | 28 × 20, rx=2, centred in the cell at `row y + 10`; letter 12px/600 centred at `y + 24` |
| Legend | hairline at rows bottom + 32, baseline +32 below it; note `업무마다 A는 한 곳` right-aligned |

## Chip treatments (tonal, no hue)

| Letter | Meaning | Fill / stroke / text |
|---|---|---|
| R | 실행 담당 | `ink @ 0.12` / `ink @ 0.60` / `ink` |
| A | 최종 책임·승인 | `ink` / — / `paper` |
| C | 사전 협의 | `paper` / `ink @ 0.30` / `muted` |
| I | 결과 공유 | none / `ink @ 0.30` dashed `3,2` / `soft` |
| A (focal, 1 only) | 책임 이관 | `accent` / — / `paper` |
| (blank) | 해당 없음 | empty cell |

Weight descends A → R → C → I, so a row scans by darkness. Accent budget: one chip — usually where accountability passes to another organisation.

## Korean wording

- Tasks: 명사형 ≤12자, a deliverable-bearing step (`개인정보 영향평가`, `운영 이관·사용자 교육`).
- Role header: role caption + organisation name ≤9자 (`(주)누리소프트`, `민원여권과`). Use fictional company names.
- Letters stay Latin R/A/C/I; the legend carries the Korean meaning. Don't write `실행` inside cells — the chip must stay 28px wide.

## Complexity budget

- Tasks 6–8, roles 4–5.
- Exactly one A per row (asserted in the generator), at least one R per row.
- One focal chip.

## Anti-patterns

- Two A's in one row — accountability is split and nobody owns it.
- A row with no R.
- Colour per letter (green R, red A) — tone already ranks them.
- Full Korean words in cells instead of chips.
- Every cell filled; blanks (해당 없음) are information.

## Checklist

- [ ] One A and ≥1 R per task row; blanks allowed.
- [ ] Chips 28 × 20 centred; tone order A > R > C > I.
- [ ] Header shows role caption + organisation; legend explains R/A/C/I in Korean.
- [ ] One accent chip; all Korean text 12px with the Pretendard stack.
- [ ] `self_check.py`, `lint-skin.py`, `verify-geometry.py`, `lint-render.py` pass; light and dark PNGs checked.

## Examples

- `assets/example-raci-matrix.html` — minimal light
- `assets/example-raci-matrix-dark.html` — minimal dark
- `assets/example-raci-matrix-full.html` — full editorial
