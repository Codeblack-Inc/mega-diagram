# Cycle / PDCA 순환

**Best for:** the 품질 관리 체계·운영 계획 figure that shows a management cycle — PDCA (계획 · 실행 · 점검 · 개선) or any 4-step 순환 — around one shared goal, with two short activities per step, where the last step feeds the next cycle's first. Public-sector 품질 관리, 정보보호 관리체계 운영, 성과 관리, 내부 감사 cycles.

This is a Korean report pattern, not a new visual type. It inherits the ring geometry of **Loop** ([type-loop.md](type-loop.md)): stations on one circle, clockwise circular arcs between them, a hub at the centre. It differs in two ways: it has **4 stations** (Loop requires 5–8), and it has **no write-back spokes**, because the centre is a goal the cycle serves, not shared state it writes to — exactly the case type-loop.md calls a Cycle.

## When to use / not

Use **Cycle** when the steps repeat on a fixed period and the reader needs each step's activities.

Don't use it for:

- A cycle whose steps write to a shared record every pass → **Loop** (with spokes).
- A process that ends → **Process** or **Flowchart**.
- Phases with dates → **Roadmap** or **Timeline**.
- More than 4 steps with bullets → **Loop** (5–8 stations, sublabels only).

## Layout conventions

Canvas `viewBox="0 0 1000 628"`. Ring centre C = (500, 288), radius R = 216.

| Element | Geometry |
|---|---|
| Stations (4) | 224 × 80, `rx=6`, centred on the circle at −90° / 0° / 90° / 180°: 계획 (388, 32), 실행 (604, 248), 점검 (388, 464), 개선 (172, 248) |
| Hub (goal) | 176 × 96, `rx=8`, centred on C: (412, 240) |
| Return label | `다음 주기` on the 개선 → 계획 arc, outside the ring (mask 280, 108, 64 × 16) |
| Legend | Hairline y=576, row baseline y=604 |

- **Station order is semantic**: station 0 at the top, then clockwise. PDCA always starts with 계획 at the top.
- **Ring arcs**: one SVG arc per step, `A R R 0 0 1`, from the circle's clockwise exit of the source box to its entry into the next box, pulled back 1.2px (marker overhang / R) so the tip lands on the stroke. Compute the circle/box intersections as in type-loop.md §2.2 — never eyeball them. `muted`, 1.2, `arrow`. The arcs are Loop's documented exception to §6 rule 1.
- **Hub clearance**: with these sizes the hub sits 16px inside the side stations; the arcs pass outside the hub. If you widen stations, grow R, not the hub.
- **Station anatomy** (left-aligned): Geist Mono 7px tag (`PLAN`, `DO`, `CHECK`, `ACT`) at (x+16, y+12); Korean step name 14px/600 right of the tag, baseline y+23; two bullets 12px/400 `muted` at baselines y+50 and y+68, 1.5px dot at x+20, text at x+28.
- **Hub anatomy** (centred): caption `품질 목표` 12px/500 `accent` at y+28; goal 14px/600 `ink` at y+52; KPI line 12px/500 `muted` at y+74.
- **Return label** (optional, one only): the 12px Korean mask rule, placed outside the circle with its nearest corner ≥ R + 6 from C.

## Node treatments

| Role | Fill / stroke |
|---|---|
| Hub / goal (focal) | `accent-tint` / `accent`, 1.2 |
| Stations | paper / `ink` |

Accent budget: the hub only. If one step is this year's improvement focus, you may give that station `accent` stroke as the second accent — then the hub goes neutral `external`.

## Korean wording

- Step names are the standard pair: `계획 · 실행 · 점검 · 개선` with Latin tags `PLAN · DO · CHECK · ACT`. Don't write `Plan(계획)` in the name.
- Bullets 명사형, ≤14자, exactly 2 per step: `품질 목표·지표 설정`, `내부 품질 감사`.
- The hub goal is one noun phrase (≤10자) plus one KPI line.
- The cycle period (분기, 반기), owners, and baseline→target numbers go in `-full` cards.

## Complexity budget

- Stations: exactly 4. Bullets: 2 per station, ≤14자.
- Hub: 1. Arc labels: ≤1. Accent: ≤2.

## Anti-patterns

- Straight or elbowed connectors between stations; the ring must read as one circle.
- Four boxes in a square with corner arrows — loses the cycle.
- Spokes from stations to the hub when the hub is only a goal.
- Labels on every arc (`→ 실행`). The order is already clockwise.
- Three or more bullets per station; move detail into cards.

## Checklist

- [ ] 4 stations clockwise from the top, on one circle; arcs computed from intersections.
- [ ] Hub clear of every arc; no spokes.
- [ ] 2 bullets per station, ≤14자.
- [ ] Accent on the hub (or hub + 1 station, as above).
- [ ] Korean ≥12px, Pretendard stack; sizes on the ramp.
- [ ] `self_check.py`, `lint-skin.py`, `verify-geometry.py`, `lint-render.py` pass; light and dark PNG checked.

## Examples

- `assets/example-cycle.html` — minimal light
- `assets/example-cycle-dark.html` — minimal dark
- `assets/example-cycle-full.html` — full editorial
