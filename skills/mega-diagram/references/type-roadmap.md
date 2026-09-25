# Roadmap (추진 로드맵)

**Best for:** the classic Korean 사업계획서·과제 제안서 figure. It shows a multi-year plan as **phases × workstreams, with outcomes**. Columns are 3–4 phases (`1단계 기반 구축 · 2026` → `2단계 확산 · 2027` → `3단계 고도화 · 2028`). Rows are bands such as 핵심 과제 / 주요 산출물 / 성과 지표. A dated milestone rail runs through the phases, and a target arrow points at the final goal on the right (`2028 전국 확산`). It answers "what do we do in each stage, what comes out of it, how do we measure it, and where does it all lead?"

This is none of **Gantt**, **Timeline** or **Story map**, and the distinction is load-bearing:

- **Gantt** shows *tasks with start and end dates* as bars on a continuous time axis. Use it when overlap and duration at week or month grain matter. A roadmap has no bars: each cell is a phase-level bucket of work.
- **Timeline** shows *single events* positioned in time on one baseline. A roadmap's milestones are a timeline, but the bands of tasks, outputs and KPIs are what make it a roadmap. If you only have dates, draw a timeline.
- **Story map** slices *user stories into releases* along narrative order. Its columns are user activities, not phases, and its cut is scope, not calendar. If the columns are the user's steps, use a story map.

If there is no end goal and no outcome row (KPI or deliverable), you have a phase table, and a table does the job better.

## Layout conventions

Canvas `viewBox="0 0 1112 536"` for 3 phases × 3 bands. Everything structural sits on the 4px grid, and all y values below are absolute.

1. **Row-header column:** x=32, 112 wide (to x=144). There is one `ink @ 0.05` rect (`rx=6`, no stroke) per row, aligned to that row's y and height. Each rect holds the band name in Korean at 12px Geist sans 600, centered at x=88 with its baseline at `row_y + 42`. A Latin Geist Mono 8px tracked eyebrow sits below at `row_y + 58` (`TASKS`, `OUTPUTS`, `KPI`, `MILESTONE`). The header-row cell holds a muted `구분`.
2. **Phase columns:** the first starts at x=160. Each column is 232 wide with a 16px gutter (x=160 / 408 / 656 for 3 phases). For 4 phases, use 172-wide columns at x=160 / 348 / 536 / 724 (16 gutter). The goal box then starts at x=944 (x1 + 48) and the canvas stays 1112 wide.
3. **Phase header (chevron):** y=24, 56 tall, at the column's x0..x1. Phase 1 is flat on the left: `x0,24 x1,24 x1+16,52 x1,80 x0,80`. Later phases add a notch: `… x0,80 x0+16,52`. The tip protrudes 16px into the gutter and stops 16px short of the next notch, so the steps read as one sequence. Non-focal headers use `ink @ 0.05` fill and a `muted` 1px stroke. Each header has two lines, centered on the visible body (column center, +8 when notched). The first line is `N단계 · YYYY` at 12px sans 500 `muted` with baseline y=46. The second is the phase name at 14px sans 600 `ink` with baseline y=68 (the group-heading size).
4. **Milestone lane:** y=96–160. The rail is a horizontal `muted` 1.2px line at y=112. It runs from x=160 to the goal box's left edge minus 4, with `marker-end="url(#arrow)"`. This rail is the **target arrow**: the plan moves toward the goal. Each milestone is a ◆ polygon (half-diagonal 6) on the rail with an `ink` fill. Its x is honest to the date: `col_x + col_w × (month − 0.5) / 12`, which is data-derived, so off-grid positions are allowed. Below each diamond, the Korean name sits at 12px sans 500 (baseline y=138, centered) and the date in Geist Mono 9px `muted` (`2027.03`, baseline y=152). Keep adjacent label centers ≥ label width apart. Measure with the per-character budget: `통합 플랫폼 오픈` at 12px = 7×12 + 2×7.2 = 98px.
5. **Bands:** start at y=168 with a height of 88 and an 8px gap between bands (y=168 / 264 / 360). Each phase × band intersection is a **cell**: rect `rx=6`, `paper` fill, `ink @ 0.12` 1px stroke, the column's width.
   - *List cell* (과제, 산출물): ≤3 items, with baselines at `band_y + 28`, `+48` and `+68` (20px pitch). Each item has a 4×4 `muted` square bullet at `x0+12, baseline−7` and its text at `x0+24`, 12px sans 400 `ink`. Items are 명사형 and ≤14 characters, so they fit 196px at 12px.
   - *KPI cell* (성과 지표): the same three baselines. The metric name sits left at `x0+12`, 12px sans 400 `muted`. The value sits right at `x1−12` with `text-anchor="end"`, 12px sans 600 `ink` (`30%`, `5분`, `243곳`). **Repeat the same metrics in every phase** so the row reads as a trend.
6. **Goal column:** x = last phase x1 + 48 (936 for 3 phases), 144 wide, full height from y=24 to the last band's bottom (y=448). It uses `paper` fill, an `ink` 1.2px stroke and `rx=6`. The top holds `최종 목표` at 12px sans 500 `muted` (y=48), then the goal headline at 14px sans 600 (`2028 전국 확산`, y=70). Dashed `ink @ 0.12` hairlines (0.8, `4,4`) at each band boundary divide the rest. In each band's slot, one 12px sans 500 line states that workstream's end state (`24시간 민원 상담`, `전국 단일 창구`, `상담 비용 30% 절감`), centered at `band_y + 48`. The goal box must not repeat the last phase's KPI values. It states the end state, not the last target.
7. **Legend:** a horizontal strip per the global rule. It has a hairline at y=472, a `LEGEND` eyebrow (mono 8) at y=490, and items at y=508 spaced 200px apart: 중점 단계 (mini accent chevron), 마일스톤 (◆ ink), 핵심 마일스톤 (◆ accent), 최종 목표 (16×12 ink-stroked rect), and 추진 방향 (short rail arrow). The Korean legend text is 12px sans 500 with no tracking.

Paint order: row-header rects → chevrons → cells and their text → milestone rail (a connector, so before the goal box) → diamonds and labels → goal box → legend.

## Focal rule

There are at most 2 accent elements, and both mark the same decision:

1. **The focal phase header.** This is the chevron of the phase the plan hinges on, usually the scale-up phase. It gets `accent-tint` fill, an `accent` stroke, and the `N단계 · YYYY` line in `accent`. Its name stays `ink`.
2. **The focal milestone** in that phase. This is the one date the whole schedule turns on. It gets an `accent`-filled ◆ and its name label in `accent`.

Cells, KPI values, the rail and the goal box stay neutral. Do not add an accent wash behind the focal column, because that makes a third element and fills the page with blue.

## Complexity budget

- Max 4 phases, max 4 bands, max 3 items per cell, max 4 milestones, 1 goal box.
- Max 2 accent elements (the focal phase header and the focal milestone).
- A cell with more than 3 items gets merged into a parent item or moved into a detail diagram for that phase. More than 4 phases means the horizon is too long: group the years into stages.
- Over budget overall → split into an overview roadmap plus a per-phase Gantt.

## Anti-patterns

- **Day- or week-level bars inside cells.** That is a Gantt. A roadmap cell is a bucket of work for the whole phase.
- **No goal on the right, or a goal that just repeats the last phase's KPIs.** Without a destination, the target arrow has nothing to point at, and the figure becomes a phase table.
- **KPI rows with different metrics per phase.** `응답률 30%` then `만족도 80점` then `기관 243곳` cannot be compared. Keep the same metrics in every column and change only the values.
- **Evenly spaced milestones regardless of date.** Place each ◆ by month inside its phase column, the same honesty rule as Timeline.
- **Sentence labels.** `상담 데이터를 표준화합니다` → `상담 데이터 표준화`. Cells are 개조식.
- **Arrows between cells.** The chevrons and the rail already carry the sequence. Arrows from task to output to KPI add noise, not information.
- **Every phase in accent, or rainbow phase colors.** Phases are a sequence, not categories. One focal phase only.
- **Chevrons drawn as arrows with markers or skewed text.** Build them as flat polygons with horizontal text, and give the notch and tip the same 16px depth on every header.

## Checklist

- [ ] Phases × bands with an outcome row and a goal: not a Gantt, a timeline or a story map?
- [ ] ≤4 phases, ≤4 bands, ≤3 items per cell, ≤4 milestones?
- [ ] Chevron tips and notches 16px deep, with tips stopping 16px short of the next notch?
- [ ] Milestones placed by month, with labels that don't collide at 12px (per-character width budget)?
- [ ] The rail ends in an arrowhead at the goal box's left edge, and the goal box states an end state per band?
- [ ] Same KPI metrics in every phase, with values right-aligned?
- [ ] Accent only on the focal phase header and its focal milestone?
- [ ] Korean text ≥12px in the `'Geist', 'Pretendard', 'Noto Sans KR', sans-serif` stack, with dates in Geist Mono 9px?
- [ ] Legend strip at the bottom, and structural geometry on the 4px grid?

## Examples

- `assets/example-roadmap.html`: minimal light. *AI 민원 상담 서비스 3개년 추진 로드맵*: 1단계 기반 구축 (2026) → 2단계 확산 (2027) → 3단계 고도화 (2028) across 핵심 과제 / 주요 산출물 / 성과 지표. It has four milestones and the goal `2028 전국 확산`. 2단계 and `2027.03 광역 확대 착수` are the focal pair.
- `assets/example-roadmap-dark.html`: minimal dark, same data.
- `assets/example-roadmap-full.html`: full editorial, with a framed container, 3 summary cards of varied widths and a footer.
