# Governance Chart / 추진 체계도

**Best for:** the 연구과제·사업계획서 figure that answers *who does what, and what passes between them* — a 발주·전담기관 at top, the 주관기관 in the centre, 참여기관·공동연구기관 around it with their 역할, 수요·실증기관 on the side, and labelled relations (협약, 연구비, 성과 보고, 기술 이전, 실증 데이터).

## When to use / not

Use **Governance** when the nodes are *separate organisations* bound by agreements, money, and deliverables, and each box must carry its own 역할 list. The labelled relation is the content: a reviewer checks that funding flows down, reports flow up, and 실증 data comes back.

Use **Org chart** ([type-org-chart.md](type-org-chart.md)) instead when the nodes are people, teams, or agents *inside one organisation* and the only relation is reporting. An org chart's connectors are unlabelled because the line always means "reports to"; a governance chart's lines carry different meanings, so each one is labelled.

Don't use it for:

- A task-by-organisation schedule → **Gantt**.
- A process in which organisations hand work to each other step by step → **Swimlane**.
- A plain list of 참여기관 and their shares → a table.

## Layout conventions

Canvas `viewBox="0 0 1000 672"` (the template width; the height holds three bands and the legend strip), 40px side margins. Every origin, size, and gap below is on the 4px grid.

| Band | Role | Geometry (x, y, w × h) |
|---|---|---|
| Top | 발주기관 | 400, 40, 200 × 56 — centred on x=500 |
| Top | 전담기관 | 400, 136, 200 × 56 — 40px below 발주 |
| Centre | 주관기관 (focal) | 360, 248, 280 × 128 — centred on x=500, 56px below 전담 |
| Centre-left | 자문위원회 (optional) | 40, 284, 200 × 56 — vertically centred on 주관 (y=312) |
| Centre-right | 수요·실증기관 | 760, 248, 200 × 128 — same row as 주관, 120px gap |
| Bottom | 참여·공동연구기관 ×3 | x = 40 / 360 / 680, y=456, 280 × 112 — 40px gaps, middle one under 주관 |
| Legend | Separator line + one row | line y=608, swatches y=628, text baseline y=640 |

- **The 주관기관 is the hub.** Every relation starts or ends on it, except 발주 → 전담. If a line connects two peripheral organisations, that relation belongs in a card below the figure, not in the chart.
- **Authority runs top-down, execution runs outward.** 발주·전담 sit above 주관; 참여 sit below it; 수요·실증 and 자문 sit level with it on the right and left. Keep 수요·실증 on the 주관 row, so its relations are plain horizontal `<line>`s and never pass behind a 참여 box (SKILL.md §6 rule 5).
- **Box anatomy** (left-aligned at `x + 16`):
  1. Role caption: 12px, weight 500, `soft` (the `accent` on the focal box), baseline `y + 22`: `주관기관`, `참여기관`, `공동연구기관`, `수요·실증기관`, `자문위원회`.
  2. Organisation name: 12px, weight 600, `ink`, baseline `y + 42`.
  3. Hairline divider at `y + 56` (`rule`, 0.8), only when bullets follow.
  4. Role bullets: 12px, weight 400, `muted`, baselines `y + 78`, `+ 96`, `+ 114`; a 1.5px dot at `x + 20`, text at `x + 28`.
  Height: 56 with no bullets, 112 with two, 128 with three. Every box in one row has the same height.
- **Font stack** on every Korean `<text>`: `'Geist', 'Pretendard', 'Noto Sans KR', sans-serif`. No Korean text below 12px. 13px is off the type ramp, so names stay at 12px/600.

### Role bullets

- ≤3 bullets per box, ≤14자 each, 명사형·개조식: `과제 총괄·성과 관리`, not `과제를 총괄합니다`.
- Size the box from the longest line: the text width (Hangul 1em, other characters 0.60em) + 32px padding must fit `w`. `한빛대학교 산학협력단` = 10×12 + 7.2 = 127px, so it fits any box ≥160px. If a line does not fit, shorten the wording before you widen the box.
- 발주·전담기관 and 자문위원회 carry no bullets. Their role is implied by the caption.
- Budget amounts, headcounts, and dates go in the `-full` cards, not in the bullets.

### Relationship labels

- Every relation connector has a label, because the lines carry different meanings. Labels are 2–6자 명사형: `협약·연구비`, `성과 보고`, `기술 이전`, `실증 데이터`, `기술 자문`, `연구비 배분`, `사업 위탁`.
- Label format: 12px, weight 500, no tracking or uppercase. The mask is 16px tall and its width is the text width + 8, rounded up to a multiple of 4 (`성과 보고` → 64, `협약·연구비` → 76). Fill the mask with `paper`.
- Horizontal segment: put the mask above the line, with its bottom edge 8px above the stroke. Vertical segment: put it beside the line, 8px away. Keep the mask on open canvas, clear of every box (§6 rule 6). `verify-geometry.py` does not measure 16px masks, so check this in the PNG.
- **A pair of organisations with flows in both directions gets two parallel lines**, never one double-headed arrow. For example, 전담 ↔ 주관 uses x=476 for `협약·연구비` (down) and x=524 for `성과 보고` (up), 48px apart. Put the labels on opposite outer sides. 주관 ↔ 수요 uses y=288 for `기술 이전` and y=336 for `실증 데이터`.
- **One-to-many funding uses a bus**: a stem from the bottom-centre of 주관 (x=500, y=376 → 456), a bus at y=416, and a drop to each 참여 box with `r=8` corners. The single label (`연구비 배분`) goes beside the stem, not on the bus.
- Stroke by meaning:

| Relation | Stroke | Marker |
|---|---|---|
| Headline funding / agreement (1 max) | `accent`, 1.4 | `arrow-accent` |
| Commission, transfer, allocation | `muted`, 1.2 | `arrow` |
| Report, feedback, advice (return or passive) | `muted`, 1, dashed `4,3` | `arrow` |

## Node treatments

| Role | Treatment | Fill / stroke |
|---|---|---|
| 발주기관 · 전담기관 | `external` | `ink @ 0.03` / `ink @ 0.30` |
| 주관기관 (1 only) | `focal` | `accent-tint` / `accent` |
| 참여기관 · 공동연구기관 | `backend` | white (dark: `#24223a`) / `ink` |
| 수요기관 · 실증기관 | `input` | `muted @ 0.10` / `soft` |
| 자문위원회 (optional) | `optional` | `ink @ 0.02` / `ink @ 0.20` dashed `4,3` |

Draw a `paper` mask rect before every styled box, as in the SKILL.md §6 node pattern. Accent budget: the 주관 box plus the one headline funding arrow.

Use fictional names for companies, universities, and institutes (`(주)메가데이터`, `한빛대학교 산학협력단`). Ministry and agency names such as 과학기술정보통신부 may appear as generic roles.

## Complexity budget

- Organisations: ≤7, not counting the 자문위원회: 1 발주, ≤1 전담, 1 주관, ≤3 참여, ≤1 수요·실증. With more than three 참여기관, group them (`참여기관 5곳`) and list them in a card.
- 자문위원회: ≤1, dashed.
- Labelled relations: ≤10. A bus counts as one relation.
- Role bullets: ≤3 per box, ≤14자 each.
- Accent: 주관 box + 1 arrow.
- Max depth: 3 bands (발주·전담 / 주관 / 참여). A 위탁기관 under a 참여기관 goes into a detail diagram.

## Anti-patterns

- Drawing it as an org chart with unlabelled lines. A reviewer cannot tell funding from reporting.
- One double-headed arrow for `협약 / 성과 보고`. Draw two parallel lines 48px apart, one per direction.
- Accent on the ministry. The ministry holds authority, but the figure is about the 주관기관.
- Paragraph bullets (`본 과제의 총괄 관리를 수행함`), or more than three bullets. Move the detail into cards.
- Routing 수요·실증 relations behind a 참여 box. Keep 수요·실증 on the 주관 row.
- Peer-to-peer lines between 참여기관. Collaboration among them is implied by the shared bus.
- Budget figures in node names (`(주)누리소프트 3.2억`). Put money in the full-variant cards.
- A figure number or caption (`[그림 3]`) inside the SVG. The document tool adds it ([mega.md](mega.md)).

## Checklist

- [ ] Nodes are organisations and relations are labelled. Otherwise this is an org chart.
- [ ] ≤7 organisations (+1 자문), ≤10 relations, ≤3 bullets of ≤14자.
- [ ] Exactly one focal box (주관) and at most one accent arrow.
- [ ] Two-way pairs use two parallel lines ≥12px apart (48 by default), with labels on opposite sides.
- [ ] 수요·실증 on the 주관 row. No connector passes behind a non-endpoint box.
- [ ] All Korean text is 12px, with the Pretendard stack. Masks are 16px tall, their widths a multiple of 4, and 8px from their stroke.
- [ ] Legend strip below all boxes, covering the five box roles and three stroke kinds.
- [ ] `self_check.py`, `lint-skin.py`, `verify-geometry.py`, and `lint-render.py` pass. Light and dark PNGs checked by eye.

## Examples

- `assets/example-governance.html` — minimal light
- `assets/example-governance-dark.html` — minimal dark
- `assets/example-governance-full.html` — full editorial
