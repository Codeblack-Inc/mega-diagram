# Network Zones / 망 구성도 (공공기관 망분리)

**Best for:** the 사업계획서·보안 설계서 figure that shows how a public-sector system is split into 외부망(인터넷) · DMZ · 내부 업무망, where the 방화벽 sit, which ports each zone boundary opens, and that data reaches the 업무망 **only** through the 망연계 솔루션. The reviewer's question is "is there any direct path from the internet into the 업무망?", and the figure must answer "no" at a glance.

This is a Korean report pattern, not a new visual type. It inherits the zone → node → path grammar of **Deployment** ([type-deployment.md](type-deployment.md)) and the elbow and port rules of **Architecture** ([type-architecture.md](type-architecture.md)).

## When to use / not

Use **Network zones** when the content is a network-boundary decision: which zone a server sits in, which firewall a path crosses, and which protocol and port it uses.

Don't use it for:

- Replica counts, versions, and hosts inside one environment, with no 망분리 story → **Deployment**.
- Logical services and who calls whom → **Architecture**.
- A security control catalogue (관리적·물리적·기술적) → [ko-security-framework.md](ko-security-framework.md).
- Firewall rule tables → a table in the document body, not a figure.

## Layout conventions

Canvas `viewBox="0 0 1000 520"`, 40px side margins, all geometry on the 4px grid.

| Element | Geometry |
|---|---|
| Zones, left → right (trust grows rightward) | 외부망 x=40 w=176 · DMZ x=256 w=224 · 내부 업무망 x=520 w=440; all y=40 h=408, `rx=8` |
| Firewall walls | 8px-wide rect centred in each 40px zone gutter (x=232, x=496), y=72 → 448; `FW-1`/`FW-2` Geist Mono 8px tag centred above at y=60 |
| Nodes | 144–160 × 56, `rx=6`; main row cy=160, second row cy=272 (망연계), third row cy=392 |
| 망연계 솔루션 | Straddles the FW-2 wall (x=420, w=160), so it visibly *is* the only gap in the boundary |
| Legend | Hairline y=472, row baseline y=500 |

- **Zone label**: Korean name 12px/600 `ink` at (x+16, y+28); the subnet in Geist Mono 9px `soft` under it at y+44 (`172.16.10.0/24`). The name is inside the zone, so it needs no mask.
- **Firewalls are walls, not nodes.** Draw them after the zones and before paths, filled `ink @ 0.05`, stroked `muted`. A path that crosses a wall *is* the firewall rule; don't draw a firewall box in the flow with arrows into and out of it.
- **Paint order**: zones → firewall walls → paths → labels → nodes.

### Paths and labels

| Path | Stroke | Label |
|---|---|---|
| Crosses a zone boundary through a firewall | `link`, 1.2, `arrow-link` | Geist Mono 8px `HTTPS:443`, `link` |
| Stays inside one zone | `muted`, 1.2, `arrow` | Geist Mono 8px `TCP:5432` |
| 망연계 → 업무망 hand-off (1 only) | `accent`, 1.4, `arrow-accent` | Korean 12px/500 `검사 후 전달`, `accent` |

- Protocol:port labels stay Latin in Geist Mono (12px mask, text + 8 rounded to 4). The one Korean label follows the Korean rule: 16px mask, width text + 8 rounded to 4, 8px clear of its stroke.
- Every path is labelled. A path without protocol and port is decoration.
- **No path may cross FW-2 except through the 망연계 node.** If the design really allows a direct DMZ → WAS API call, draw it with its port and say so in a card; the figure must not hide it.
- A label between two nodes may sit over a firewall wall (walls are not nodes), but must end ≥4px short of the next node (§6 rule 6).

## Node treatments

| Role | Treatment | Fill / stroke |
|---|---|---|
| 민원인 · 외부 사용자 | `input` | `muted @ 0.10` / `soft` |
| 웹서버 · WAS · 업무 PC | `backend` | paper / `ink` |
| DB · 파일 저장소 | `store` | `ink @ 0.05` / `muted` |
| 망연계 솔루션 (focal) | `focal` | `accent-tint` / `accent`, 1.2 |
| Zones | boundary | `ink @ 0.02` / `ink @ 0.20` dashed `4,4` |

Node anatomy: Geist Mono 7px type tag (`WEB`, `WAS`, `DB`, `CDS`) at (x+12, y+12), Korean name 12px/600 right of the tag at baseline y+23, sublabel at baseline y+43 — Geist Mono 9px for technical values (`nginx 1.26 · x2`, `PostgreSQL 16`), or Korean 12px/500 when it is prose (`단방향 자료 전송`). Hangul never goes into a mono sublabel; write `VDI · x320`, not `VDI · 320대`.

Accent budget: the 망연계 node + its one hand-off arrow.

## Korean wording

- Zone names: `외부망 (인터넷)`, `DMZ`, `내부 업무망` (or `업무망`, `인터넷망`); keep the agency's own terms if the RFP uses them.
- Node names ≤8자, noun style: `업무 WAS`, `민원 DB`, `망연계 솔루션`.
- Legend entries describe meaning, not colour: `경계 통과`, `구간 내부`, `망간 전달`, `방화벽`.
- Allowed ports, device counts, and daily transfer volumes go in `-full` cards.

## Complexity budget

- Zones: 3 (add a 4th, e.g. 관리망, only by splitting into two figures).
- Firewalls: ≤3. Nodes: ≤6 (Deployment budget). Paths: ≤8. Accent: 2.

## Anti-patterns

- A firewall drawn as a box in the data path with arrows entering and leaving — it reads as a hop, not a boundary.
- A direct path from DMZ to the 업무망 that silently bypasses the 망연계 node.
- Korean text in mono sublabels, or ports translated into Korean (`포트 443`).
- Accent on the firewalls or the DB. The focal element is the controlled crossing.
- Cloud / vendor icon soup instead of named nodes.
- Subnets or ports left out. They are the content.

## Checklist

- [ ] Three zones left → right in increasing trust; walls in the gutters with `FW-n` tags.
- [ ] Every path labelled with protocol:port; zone-crossing paths are `link`.
- [ ] Nothing crosses into the 업무망 except via the 망연계 node.
- [ ] ≤6 nodes, ≤8 paths, accent = 망연계 + 1 arrow.
- [ ] Korean 12px with the Pretendard stack; no Hangul in mono.
- [ ] `self_check.py`, `lint-skin.py`, `verify-geometry.py`, `lint-render.py` pass; light and dark PNG checked.

## Examples

- `assets/example-network-zones.html` — minimal light
- `assets/example-network-zones-dark.html` — minimal dark
- `assets/example-network-zones-full.html` — full editorial
