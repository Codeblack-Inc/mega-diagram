# Security Framework / 보안 체계도

**Best for:** the 사업계획서·ISMS-P 준비 문서 figure that lays out an organisation's 정보보호 체계 in one page: one 보안 목표 at the top, three 보안 영역 (관리적 · 물리적 · 기술적 보안) with their 통제 항목, and the 법·제도 준거 every control answers to at the bottom.

This is a Korean report pattern, not a new visual type. It inherits the tiered, connector-free grammar of **Strategy house** ([type-strategy-house.md](type-strategy-house.md)): vertical order carries the hierarchy (위가 목적, 아래가 근거). The full-width bottom band borrows the **Layer stack** idea ([type-layers.md](type-layers.md)) that the base supports everything above it.

## When to use / not

Use **Security framework** when the reader needs the *scope* of the security programme: every control in its domain, with the laws that require it.

Don't use it for:

- Where servers and firewalls sit → [ko-network-zones.md](ko-network-zones.md).
- Control-by-system coverage (which control applies to which system) → **DP security matrix** ([type-dp-security-matrix.md](type-dp-security-matrix.md)) or a table.
- An incident-response process → **Flowchart** or **Swimlane**.
- 5-year strategy with KPIs → **Strategy house**.

## Layout conventions

Canvas `viewBox="0 0 1000 484"`. The house spans x = 120–960 (width 840); the left margin (x = 32) carries the tier labels.

| Tier | y | Height | Geometry |
|---|---|---|---|
| 보안 목표 banner | 40 | 56 | Full width 840, `rx=6` |
| 보안 영역 header | 120 | 48 | 3 columns × 264, gap 24 |
| 통제 항목 rows | 168 | 4 × 36 | Inside each column; column rect runs 120–312 |
| 법·제도 준거 band | 336 | 64 | Full width 840, two lines per law |
| Legend | 432 | — | Hairline at 432, row baseline 460 |

- **Tier gap is 24** (96→120, 312→336).
- **Tier labels**: `보안 목표` · `보안 영역` · `통제 항목` · `법·제도 준거` at x=32, 12px/500 `muted`, baseline at the tier's vertical centre + 4.
- **Banner**: the goal sentence centred, 16px/600; the certification or plan year right-aligned in Geist Mono 9px `accent` (`ISMS-P 2026`).
- **Domain column**: Geist Mono 7px tag (`ADM` / `PHY` / `TEC`, 28×12) at x+12, domain name 14px/600 at x+48, a Geist Mono 9px `soft` count right-aligned (`4 controls`), header hairline at y=168.
- **Control rows**: Geist Mono 9px `soft` number (`3-2`) at x+16, control name 12px/600 at x+48; rows divided by `rule` hairlines inset 12px. Not boxed.
- **준거 band**: `store` treatment; dividers sit in the column gutters (x + 288k − 12) so each law centres under a domain column. Law name 12px/600 `ink` at y+28, the article or scope 12px/500 `muted` at y+48 (`제29조 안전조치의무`).
- The law under a column does not mean "this law governs only this domain" — the band spans every column on purpose. Say so in a card if the reader might misread it.

## Node treatments

| Role | Fill | Stroke |
|---|---|---|
| 보안 목표 (focal 1) | `accent-tint` | `accent` |
| 중점 보안 영역 (focal 2, optional) | `accent-tint` | `accent`, header rule `accent` |
| Other 보안 영역 | `ink @ 0.03` | `ink @ 0.30` |
| 법·제도 준거 band | `ink @ 0.05` | `muted` |

Accent budget: the banner plus at most one domain — the one this project invests in. With no project focus, leave all three domains neutral.

## Korean wording

- Domain names are fixed: `관리적 보안`, `물리적 보안`, `기술적 보안`. Keep this order.
- Control names 명사형, ≤12자: `망분리·접근 통제`, `개인정보 암호화`, `저장매체 반출입 통제`. Not `접근을 통제함`.
- Laws by their official short names: `개인정보 보호법`, `전자정부법`, `정보통신망법`, `ISMS-P 인증 기준`. Cite the article only when it is correct; otherwise use a scope line (`관리체계·보호대책 요구사항`).
- Inspection cycles, audit dates, and counts go in `-full` cards.

## Complexity budget

- Domains: exactly 3. Controls: 3–4 per domain, same count in every column.
- Laws: 2–4 in the band. Accent: ≤2 (banner + 1 domain).
- More than 4 controls per domain → group them, or split into one figure per domain.

## Anti-patterns

- Arrows between domains. The framework is a census, not a flow.
- Unequal columns (6 technical controls, 1 physical). Balance or group them.
- Product names as controls (`○○ 방화벽 도입`). Name the control, not the purchase.
- Laws floating as tags inside columns; the 준거 band is the foundation for all.
- Accent on every domain.
- A figure number or caption inside the SVG ([mega.md](mega.md)).

## Checklist

- [ ] Banner → 3 domains → controls → 준거 band, top to bottom; no connectors.
- [ ] 3–4 controls per domain, equal count, ≤12자 each.
- [ ] Law names and article numbers verified.
- [ ] Accent on ≤2 elements.
- [ ] All Korean text ≥12px with the Pretendard stack; sizes on the ramp (7/9 mono, 12/14/16 sans).
- [ ] `self_check.py`, `lint-skin.py`, `verify-geometry.py`, `lint-render.py` pass; light and dark PNG checked.

## Examples

- `assets/example-security-framework.html` — minimal light
- `assets/example-security-framework-dark.html` — minimal dark
- `assets/example-security-framework-full.html` — full editorial
