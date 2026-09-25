# 이슈 트리 / Issue Tree (로직 트리)

**Best for:** the 문제 해결 보고서 figure that splits one 핵심 질문 into MECE 하위 이슈 and then into testable 가설, each paired with the 분석 항목 that will confirm or reject it. One branch is marked as the 우선 검증 이슈.

Korean report figure, not a new visual type. It inherits **Tree** ([type-tree.md](type-tree.md)) — orthogonal stem + bus + branch connectors, two node widths, accent on one node — rotated to run left to right so the Korean hypothesis lines have room.

## 쓰는 곳 / 쓰지 않는 곳

Use it when the reader must check that the breakdown is complete (MECE) and see which hypothesis gets analysed first.

Use instead:

- Causes grouped by category around one effect, no hypothesis/analysis pairing → **Fishbone** ([type-fishbone.md](type-fishbone.md)).
- Goal → pillar → task decomposition of a strategy → **Strategy house** ([type-strategy-house.md](type-strategy-house.md)).
- An organisation's reporting lines → **Org chart** ([type-org-chart.md](type-org-chart.md)).
- A yes/no decision path → **Flowchart** ([type-flowchart.md](type-flowchart.md)).

## Layout

Canvas `viewBox="0 0 1000 624"`, 40px side margins, all geometry on the 4px grid.

| Column | Role | Geometry (x, w × h) |
|---|---|---|
| 1 | 핵심 질문 (root) | x=40, 200 × 96, vertically centred on the middle group (cy=296) |
| 2 | 하위 이슈 ×3 | x=320, 200 × 56, each centred on its leaf group |
| 3 | 가설 ×3 per issue | x=600, 360 × 40, 12px gap inside a group, 24px between groups |
| Captions | 핵심 질문 · 하위 이슈 · MECE · 가설 · 분석 항목 | baseline y=36 |
| Legend | hairline y=568, row baseline y=600 |

- Leaf height 40 and the 12px sibling gap follow type-tree.md (node height 40–52), not the SKILL.md §7 node/gap tables; 48/20 would push the canvas past 640.
- Leaf groups start at y=56: group height 3 × 40 + 2 × 12 = 144; group centres y=128 / 296 / 464.
- **Connectors** (paint first, no arrowheads, `fill="none"`): root right edge → x=280 bus → each issue's left edge; issue right edge → x=560 bus → each leaf's left edge. The middle child gets a straight `H` segment; the others branch off the bus with `r=8` quarter-arcs (`M 280,296 V 136 Q 280,128 288,128 H 320`). No connector crosses a box.
- **Root:** two lines of 14px/600 `ink` at `y + 42` and `y + 64` — the question itself, ending in a question form (`…떨어졌나`).
- **Issue box:** tag `이슈 A · 유입` 12px/500 `soft` at `y + 22`, name 12px/600 `ink` at `y + 42`.
- **Leaf:** 가설 12px/500 `ink` left at `x + 16`; 분석 항목 12px/400 `soft` right-aligned at `x + w − 16`, baseline `y + 25`.

## Treatments

| Role | Fill / stroke |
|---|---|
| 핵심 질문 | `ink @ 0.04` / `ink` 1.2 |
| 하위 이슈 | `backend` / `ink` 1 |
| 우선 검증 이슈 (1 only) | `accent-tint` / `accent` 1; tag in `accent` |
| 가설 leaf | `paper` / `ink @ 0.30` 0.8 |
| Connector | `muted` 1; the focal branch (root → issue → its leaves) `accent` 1.4 |

Accent budget: the focal issue box plus its connector branch. Leaves under it stay neutral.

## Korean wording

- 하위 이슈: 명사형 ≤10자 (`무료 체험 경험 악화`), tag `이슈 A · 유입` names the MECE axis in one word.
- 가설: a falsifiable statement ≤16자 with the number when there is one (`연간권 9.9만→12.9만 원 인상`). No `~일 것이다`.
- 분석 항목: the data or method, ≤8자 (`온보딩 퍼널`, `가격 탄력성`).
- Width rule: `tw(가설) + tw(분석 항목) + 48 ≤ 360` (Hangul 1em, other 0.60em). Shorten before widening.

## Complexity budget

- 3 하위 이슈 × ≤3 가설 = ≤13 nodes. This exceeds the universal 9-node budget on purpose, like Governance's 7 organisations; beyond it, split into an overview tree and one detail tree per issue.
- Depth 3 (question → issue → hypothesis). A fourth level goes in a detail tree.
- Exactly one focal issue.

## Anti-patterns

- Overlapping issues (`가격 문제` and `결제 불편` as siblings) — not MECE; merge or re-cut the axis.
- Hypotheses without an 분석 항목 — the tree stops being a work plan.
- Accent on the root or on a single leaf as well as the focal branch.
- Diagonal fan-out lines or arrowheads on tree connectors.
- Paragraph leaves (`광고 채널이 바뀌어 유입된 고객의 의향이 낮아졌을 가능성`).

## Checklist

- [ ] One question, 2–3 MECE issues, ≤3 hypotheses each, every hypothesis paired with an 분석 항목.
- [ ] Connectors orthogonal with r=8, drawn before boxes, none behind a box.
- [ ] One focal issue; accent only on it and its branch.
- [ ] Korean text 12px (root 14px) with the Pretendard stack; widths pass the budget.
- [ ] `self_check.py`, `lint-skin.py`, `verify-geometry.py`, `lint-render.py` pass; light and dark PNGs checked.

## Examples

- `assets/example-issue-tree.html` — minimal light
- `assets/example-issue-tree-dark.html` — minimal dark
- `assets/example-issue-tree-full.html` — full editorial
