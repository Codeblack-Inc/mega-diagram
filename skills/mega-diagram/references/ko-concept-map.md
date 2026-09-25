# 서비스 개념도 (Service concept map)

**Best for:** the 사업계획서·서비스 기획서 page that shows *what the service is and who gets what from it*: one central service/platform, the actors around it (국민·이용자, 기관, 운영사, 외부 시스템), and the labelled value that flows each way — 예약·결제, 보조금, 정산금, 이용 통계, API 연계.

This is a catalogued Korean report pattern, not a new visual type. It inherits from **Architecture** ([type-architecture.md](type-architecture.md)) — components plus labelled connections, orthogonal routing — but its nodes are stakeholders, not software components, and its hub is the one focal object.

## 쓰는 곳 / 쓰지 않는 곳

Use it when one service sits at the centre and every relation of interest runs between it and an actor.

Don't use it for:

- Organisations bound by agreements, funding and reports on a project → **Governance** ([type-governance.md](type-governance.md)).
- Software components, ports and protocols → **Architecture** ([type-architecture.md](type-architecture.md)).
- The step-by-step order in which actors act → **Swimlane** or **Sequence**.
- Actor-to-actor relations that bypass the hub. Those belong in a card, or the hub isn't the centre.

## Layout grammar

Canvas `viewBox="0 0 1000 640"`, 40px margins, 4px grid. A plus-shaped radial layout: each actor sits on one of the hub's axes, so **every flow is a straight orthogonal line** — no elbows, no crossings.

| Element | Geometry (x, y, w × h) |
|---|---|
| Hub (focal) | 360, 216, 280 × 168 — centre (500, 300) |
| Top actor (기관) | 380, 40, 240 × 80 |
| Left actor (국민) | 40, 260, 200 × 80 — centred on y=300 |
| Right actor (운영사) | 760, 260, 200 × 80 |
| Bottom actor (외부 시스템) | 380, 480, 240 × 80 |
| Legend | hairline y=584, items baseline 616 |

- **One flow per direction.** Each actor pair gets two parallel one-way lines 32px apart (≥12 per SKILL.md §6 rule 3), never a double-headed arrow: horizontal pairs at y=284 (→) and y=316 (←); vertical pairs at x=476 (↓) and x=524 (↑).
- **Labels** (12px 500, 16px mask, width = text + 8 rounded to 4): horizontal pairs put the upper label above the upper line (mask top = line − 24) and the lower label below the lower line (mask top = line + 8); vertical pairs put labels outside the pair (mask edge 8px from the stroke, x=468 right edge / x=532 left edge), vertically centred in the gap. All masks stay in the 96–120px gap, clear of every box (§6 rule 6).
- **Hub anatomy:** caption `서비스 플랫폼` 12px 500 `accent` at y+22; service name 16px 600 at y+46; `rule` hairline at y+60; 3–4 function bullets 12px at y+84, 20px pitch (1.5px dot at x+20, text at x+28).
- **Actor anatomy:** role caption 12px 500 `soft` (`국민`, `기관`, `운영사`, `외부 시스템`) at y+22; name 14px 600 at y+44; one detail line at y+66 — a scale number (`등록 전기차 42,000대`) or, for systems, a Geist Mono 9px tech sublabel (`PG · MAP · OEM API`).
- **Paint order:** flows → labels → actors → hub → legend.

## Node treatments and flow strokes

| Role | Treatment | Fill / stroke |
|---|---|---|
| Service hub (focal, 1) | `focal` | `accent-tint` / `accent`, 1.2 |
| 국민·이용자 | `input` | `muted @ 0.10` / `soft` |
| 운영사 (operates the service) | `backend` | white (dark `#24223a`) / `ink` |
| 기관 · 외부 시스템 | `external` | `ink @ 0.03` / `ink @ 0.30` |

| Flow | Stroke | Marker |
|---|---|---|
| Headline value (1 max) | `accent` 1.4 | `arrow-accent` |
| Service, money | `muted` 1.2 | `arrow` |
| Information returned (통계, 상태) | `muted` 1 dashed `4,3` | `arrow` |
| System/API calls | `link` 1.2 (return dashed) | `arrow-link` |

Accent budget: hub + one headline flow (usually what the citizen gets or does).

## Korean wording

- Flow labels 2–6자, 명사형, naming the *thing* that moves (`예약·결제`, `정산금`, `충전기 상태`), not the verb (`결제한다`).
- Actor names ≤ 10자; group many into one with a count (`충전 사업자 12개사`).
- Hub name ≤ 12자; bullets ≤ 10자.
- Width: `결제 승인 요청` = 6×12 + 2×7.2 = 86.4 → mask 96.

## Complexity budget

- 1 hub, 4 actors (max 6 — add diagonal-corner actors only with elbow routing and r=8 corners).
- ≤ 10 flows, 2 per actor. ≤ 4 hub bullets. 2 accents.

## Anti-patterns

- Diagonal spokes from the hub to actors placed on a circle. Put actors on the hub's axes.
- One double-headed arrow for a two-way relation.
- Unlabelled flows. A concept map's lines carry different values; each one is labelled.
- Actor-to-actor lines around the hub — they cross or pass behind boxes.
- Icons or pictograms instead of names; keep the icon set for architecture diagrams.

## Pre-output checklist

- [ ] One focal hub; every flow starts or ends on it?
- [ ] Actors on the hub's axes; all flows straight, paired lines 32px apart?
- [ ] Every flow labelled, masks 8px from the stroke and clear of every box?
- [ ] Stroke kinds match meaning (value / return / API); ≤ 2 accents?
- [ ] Korean text ≥12px, Pretendard stack, sizes 12 / 14 / 16 (mono 9 tech sublabel)?
- [ ] Legend covers the four actor treatments and three flow strokes; light/dark/full identical; verifiers pass?

## Examples

- `assets/example-concept-map.html` — minimal light. 가온 통합 충전 플랫폼: 전기차 이용자 (예약·결제 / 빈 충전기 안내), 가온시·환경공단 (보조금·정책 / 이용 통계), 충전 사업자 12개사 (정산금 / 충전기 상태), 결제·지도·차량 연계 (결제 승인 요청 / 지도·차량 정보).
- `assets/example-concept-map-dark.html` — minimal dark, same labels.
- `assets/example-concept-map-full.html` — full editorial.
