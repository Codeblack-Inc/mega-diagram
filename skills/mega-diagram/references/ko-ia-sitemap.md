# IA Sitemap / 정보구조도

**Best for:** the 누리집·포털 구축 사업 figure (제안서, 설계 산출물) that shows the menu structure from 홈 through 1depth menus to 2depth pages, and marks which pages are 신규 and which are 개선 in this project. The reader checks scope: how many pages, where the new ones sit, and how deep the menu goes.

This is a Korean report pattern, not a new visual type. It inherits **Tree** ([type-tree.md](type-tree.md)): root at the top, orthogonal bus connectors, no arrowheads, one accent node.

## When to use / not

Use **IA sitemap** when the nodes are pages or menus and the only relation is "contains".

Don't use it for:

- User paths through pages (click flow) → **Flowchart** or **User journey**.
- Screen wireframes → a mockup, not a diagram.
- More than 2 depths below 홈, or >20 pages → split by 1depth menu (one figure per menu), or use a table sitemap in the appendix.
- An organisation's departments → **Org chart**.

## Layout conventions

Canvas `viewBox="0 0 1000 484"`, all geometry on the 4px grid.

| Element | Geometry |
|---|---|
| 홈 (root) | x=420, y=40, 160 × 48, centred on x=500 |
| 1depth menus | 5 columns × 168, gap 20, x = 40 + 188i; y=136, h=48 |
| 2depth pages | x = column + 24, w=144, h=40; first y=204, step 52 (12px gap) |
| Legend | Hairline y=436, row baseline y=464 |

- **홈 → 1depth**: a 48px stem from the root bottom (x=500, 88 → 136), one bus at y=112 drawn as a single path with `r=8` outer corners, and short drops (112 → 136) into columns 2 and 4. One bus path, not one path per child, so no segments overlap (§6 rule 3).
- **1depth → 2depth**: a left spine at column + 12 from the menu bottom (y=184) down to the last child's centre, turning into it with `r=8`; the other children get 12px horizontal branches. This file-tree spine reads faster than a centred bus when pages stack vertically.
- Lines are `muted`, 1px, no markers. Containment is implied.
- **Menu node**: Geist Mono 9px `soft` index (`01`–`05`) at x+12, Korean name 12px/600 centred. `backend` treatment.
- **Page node**: Korean name 12px left-aligned at x+12, baseline y+24. A status chip (32 × 16, `rx=2`, fully inside the node) right-aligned at x+w−40, y+12.
- Paint order: lines → root → menus → pages → chips.

### Status chips

| Status | Chip | Page node |
|---|---|---|
| 신규 | solid `ink`, text `paper` 12px/500 `신규` | paper / `muted` stroke, name 600 `ink` |
| 개선 | paper, `muted` 0.8 stroke, text `muted` `개선` | paper / `muted` stroke, name 600 `ink` |
| 유지 | no chip | paper / `rule` stroke, name 500 `muted` |
| 핵심 신규 (1 only) | solid `accent`, text `paper` | `accent-tint` / `accent` |

Changed pages are darker and carry a chip; unchanged pages recede. That contrast, not colour, is the signal — the accent goes to one flagship page only.

## Korean wording

- Menu and page names are the actual menu labels, 명사형, ≤7자 when the page carries a chip (the chip takes 40px), ≤10자 without.
- Use the site's own terms: `민원 서비스`, `정보 공개`, `참여·소통`, `분야별 정보`, `시청 안내`.
- `1depth`/`2depth` stay as written in Korean IT documents; don't translate to `1단계 메뉴`.
- Page counts (신규 n · 개선 n · 유지 n) and rationale go in `-full` cards.

## Complexity budget

- 1depth menus: 4–6 (5 fills the canvas). 2depth pages: 2–4 per menu, ≤20 total.
- Depth: 홈 + 2. A 3depth goes in a per-menu detail figure.
- Accent: 1 page (+ its chip).

## Anti-patterns

- Colour-coding every status (blue 신규, green 개선, orange 삭제). Use chips; keep one accent.
- One path per child from the root bus — overlapping strokes.
- Diagonal fan-out lines.
- Page names shrunk below 12px to fit; shorten the label instead.
- Mixing user flow arrows into the tree.

## Checklist

- [ ] 홈 → 1depth → 2depth only; ≤6 menus, ≤4 pages each, ≤20 pages.
- [ ] One bus path with `r=8` corners; spines with 12px branches; no markers.
- [ ] Chips fully inside their node; counts in the card match the figure.
- [ ] Exactly one accent page.
- [ ] Korean ≥12px, Pretendard stack.
- [ ] `self_check.py`, `lint-skin.py`, `verify-geometry.py`, `lint-render.py` pass; light and dark PNG checked.

## Examples

- `assets/example-ia-sitemap.html` — minimal light
- `assets/example-ia-sitemap-dark.html` — minimal dark
- `assets/example-ia-sitemap-full.html` — full editorial
