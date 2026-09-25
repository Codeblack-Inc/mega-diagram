# AS-IS / TO-BE (현황·개선 비교)

**Best for:** the 정보화 전략계획(ISP)·업무 재설계(BPR)·사업계획서 figure that compares the current way of working with the target way, step by step: left 현행 with its problem number, right 개선 with the improved number, and a central band naming the 핵심 전환 that gets you from one to the other.

This is a catalogued Korean report pattern, not a new visual type. It inherits from **IT current-state** ([type-it-state.md](type-it-state.md)) — which draws only the *before* state — and adds the paired *after* column and the transition band.

## 쓰는 곳 / 쓰지 않는 곳

Use it when the same 3–4 business steps exist before and after, and each step has one metric you can measure in both states.

Don't use it for:

- The before-state system landscape (servers, legacy apps, interfaces) → **IT current-state** ([type-it-state.md](type-it-state.md)).
- A single before/after number pair → a sentence or a table (SKILL.md §2).
- The 원인 → 해결 argument for why the project exists → **추진 배경** ([ko-problem-solution.md](ko-problem-solution.md)).
- Change over several time points → **Line chart** (slopegraph) or **Roadmap**.

## Layout grammar

Canvas `viewBox="0 0 1000 520"` for 4 pairs, 40px side margins, 4px grid.

| Element | Geometry (x, y, w × h) |
|---|---|
| AS-IS header | 40, 40, 320 × 40, `ink @ 0.05`, no stroke. Mono 8px tracked `AS-IS` at x+16, `현행 업무` 14px 600 at x+72, `문제 수치` 12px 500 `soft` right-aligned at x+w−16 |
| 핵심 전환 header | 12px 600 `muted` centred at x=500, no box |
| TO-BE header (focal 1) | 640, 40, 320 × 40, `accent-tint` / `accent`. `TO-BE`, `개선 업무`, `개선 효과` (in `accent`) |
| Paired rows | y = 96 / 184 / 272 / 360, h=72 (16 gap). AS-IS at x=40, TO-BE at x=640, both w=320 |
| Transition chevron | per row, x 376 → 624, y+12 → y+60; points `376,y+12 600,y+12 624,y+36 600,y+60 376,y+60 392,y+36` |
| Legend | hairline y=456, items baseline 488 |

- **Card anatomy** (both sides identical so the eye compares like with like): step caption 12px 500 `soft` at x+16, baseline y+26; approach 14px 600 at y+52; metric name 12px 500 `soft` right-aligned at x+w−16, y+26; value 16px 600 right-aligned at y+52.
- **The value column is the comparison.** Same metric name on both sides, same unit, same position. The AS-IS value is `muted`; the TO-BE value is `ink`.
- **Transition chevron:** notched on the left, 24px tip on the right, 16px clear of both cards. Name 12px 600 centred at y+33, detail 12px 400 `muted` at y+51. The chevron *is* the connector — do not add arrows between cards.
- **Paint order:** headers → chevrons → AS-IS cards → TO-BE cards → legend.

## Node treatments by semantic role

| Role | Treatment | Fill / stroke |
|---|---|---|
| 현행 card (문제점) | `optional` | `ink @ 0.02` / `ink @ 0.30` dashed `4,3`; text `muted` |
| 개선 card | `backend` | white (dark `#24223a`) / `ink` |
| 핵심 전환 chevron | none | `ink @ 0.05`, no stroke |
| 중점 전환 (focal 2) | `focal` | `accent-tint` / `accent`; name in `accent` |
| TO-BE header (focal 1) | `focal` | `accent-tint` / `accent` |

The dashed, muted AS-IS column is the 문제점 표시: it reads as provisional, being replaced. Accent budget: TO-BE header + the one transition the plan hinges on (usually the biggest value change).

## Korean wording

- Step caption ≤ 6자 (`신청 채널`, `자격 확인`, `심사`, `결과 안내`) — the same on both sides.
- Approach ≤ 10자, 명사형 (`담당자 수기 심사` → `규칙 기반 자동 심사`).
- Metric ≤ 6자; values short with unit (`14일`, `평균 2회`, `6.2%`). Never write `14일→3일` in one label — the layout carries the arrow (mega.md: no `→` in labels).
- Transition name ≤ 7자 (`심사 자동화`), detail ≤ 10자 naming the enabler (`심사 규칙 엔진 도입`).
- Width budget: approach at 14px + value at 16px must fit 320 − 32; `기관별 서류 발급·제출` = 9×14 + 2×8.4 = 143px.

## Complexity budget

- 3–4 pairs (max 5). More steps → split by phase.
- 1 metric per pair. 2 accents. 0 connectors.

## Anti-patterns

- Different metrics on each side (`처리 기간` vs `만족도`). The pair can't be compared.
- A TO-BE column without numbers. The effect is the point of the figure.
- Arrows from each AS-IS card to its TO-BE card crossing the band. The chevron already says it.
- Red/green good-bad colouring. Use dashed-muted vs solid-ink; the palette has no traffic-light colours.
- Rows in a different order on the two sides.

## Pre-output checklist

- [ ] Same step caption and metric name on both sides of every row?
- [ ] AS-IS dashed and muted, TO-BE solid with `ink` values?
- [ ] One chevron per row naming the 핵심 전환; no extra connectors?
- [ ] ≤ 2 accents: TO-BE header + one focal transition?
- [ ] Korean text ≥12px, Pretendard stack, sizes 12 / 14 / 16 (mono 8 eyebrows)?
- [ ] Legend strip; light, dark and full carry identical labels; all four verifiers pass?

## Examples

- `assets/example-as-is-to-be.html` — minimal light. 가온시 복지급여 신청: 방문·서면 → 온라인·모바일 (평균 2회 → 0회), 서류 7종 → 0종, 수기 심사 14일 → 자동 심사 3일 (중점 전환), 우편 통지 6.2% → 알림톡 0.4%.
- `assets/example-as-is-to-be-dark.html` — minimal dark, same labels.
- `assets/example-as-is-to-be-full.html` — full editorial.
