# 로직 모델 (Logic model)

**Best for:** the 성과관리·재정사업 평가·사업계획서 figure that states the programme theory: 투입 → 활동 → 산출 → 성과(단기·중기) → 영향, with the 전제·외부요인 the chain depends on. Reviewers of 재정사업 자율평가 and R&D 성과계획서 expect exactly this five-stage frame.

This is a catalogued Korean report pattern, not a new visual type. It inherits from **Process** ([type-process.md](type-process.md)) — ordered stages left to right — and borrows the chevron stage header and bucket cells of **Roadmap** ([type-roadmap.md](type-roadmap.md)).

## 쓰는 곳 / 쓰지 않는 곳

Use it when the audience asks "how does money become impact?" and you can fill every stage with measurable bullets.

Don't use it for:

- Phases over time with milestones → **Roadmap** ([type-roadmap.md](type-roadmap.md)). A logic model has no calendar; stages are causal, not chronological.
- The KPI hierarchy and target values → **성과지표 체계** ([ko-kpi-tree.md](ko-kpi-tree.md)).
- Who executes each activity → **Swimlane** or **Governance**.

## Layout grammar

Canvas `viewBox="0 0 1000 472"`. Five columns, w=168, gutter 16: x = 48 / 232 / 416 / 600 / 784 (ends 952). 4px grid throughout.

| Element | Geometry |
|---|---|
| Stage chevron | y 40 → 96. First flat-left; later ones notched 16px; tip protrudes 16px into the gutter (roadmap geometry). Mono 8px tracked Latin eyebrow (`INPUTS`, `ACTIVITIES`, `OUTPUTS`, `OUTCOMES`, `IMPACT`) at baseline 62, Korean stage name 14px 600 at baseline 82, centred (+8 when notched) |
| Body cells | y 112 → 280 (h=168), `rx=6`, `ink @ 0.12` stroke. Bullets: 4×4 `muted` square at x+12, text at x+24, baselines y+36 + 32k (≤4 items) |
| 성과 split | two stacked cells h=76 at y=112 and y=204 (16 gap): caption `단기 · 1년` / `중기 · 3년` 12px 500 `accent` at y+24, two bullets 12px **600** at y+46, y+66 |
| 전제·외부요인 band | 48, 304, 904 × 64, dashed; `rule` divider at x=500; captions 12px 600 at x+16, text 12px `muted` at x+88, baseline 341 |
| Legend | hairline y=400, items baseline 432 |

- **The chevrons carry the causality.** No arrows between cells (roadmap anti-pattern): five chevrons already read as "leads to".
- **Outcome bullets are bold** because they are what the model is judged on; everything else is 400.
- **Paint order:** chevrons → cells → band → legend.

## Node treatments by semantic role

| Role | Treatment | Fill / stroke |
|---|---|---|
| Stage chevron | — | `ink @ 0.05` / `muted` |
| 성과 chevron (focal, 1) | `focal` | `accent-tint` / `accent`; eyebrow in `accent` |
| 투입·활동·산출 cells | `backend` | white (dark `#24223a`) / `ink @ 0.12` |
| 성과 cells | `backend` strong | white / `ink` 1 |
| 영향 cell | `external` | `ink @ 0.03` / `ink @ 0.12` — long-term, outside direct control |
| 전제·외부요인 band | `optional` | `ink @ 0.02` / `ink @ 0.30` dashed `4,3` |

Accent budget: the 성과 chevron (+ its captions). Don't accent 영향 — it is the aspiration, not the accountable result.

## Korean wording

- Every bullet is 명사형 and quantified where the stage allows: 투입 in 억 원·명·곳; 산출 in counts (`수료생 300명`); 성과 in rates (`취업률 70%`); 영향 in population-level change (`청년 고용률 +2.1%p`).
- ≤ 11자 per bullet: the 132px text run holds 11 Hangul at 12px. `현장 프로젝트 60건` = 7×12 + 4×7.2 = 113px.
- 산출 ≠ 성과: `수료생 300명` is an output (what the programme produced); `취업률 70%` is an outcome (what changed for people). Mixing them is the most common review comment.
- 전제 states conditions that must hold (`협력 기업 채용 수요 유지`); 외부요인 states forces outside the programme (`지역 경기 둔화`).

## Complexity budget

- 5 stages exactly. ≤ 4 bullets per cell; 성과 2 + 2. ≤ 2 items each in 전제 and 외부요인.
- 1 accent (2 max). 0 connectors.

## Anti-patterns

- Outputs in the 성과 column (`교육 12회 실시`).
- Arrows from each bullet to the next column — a spaghetti of 16 lines.
- A calendar in the headers (`2026`, `2027`): that's a roadmap.
- Omitting the 전제·외부요인 band; reviewers read an unconditional chain as over-claiming.
- 영향 with a precise attributable number the programme can't own (`GDP 0.3% 증가`).

## Pre-output checklist

- [ ] Five chevrons in order 투입 → 활동 → 산출 → 성과 → 영향?
- [ ] 성과 split into 단기·중기 with rates, not counts?
- [ ] Bullets ≤ 11자, quantified, 명사형?
- [ ] 전제·외부요인 band present and dashed?
- [ ] Korean ≥12px, Pretendard stack, sizes 12 / 14 (mono 8 eyebrows)?
- [ ] Legend strip; light/dark/full identical; verifiers pass; PNGs checked?

## Examples

- `assets/example-logic-model.html` — minimal light. 가온시 청년 AI 인재 양성: 사업비 24억 원·전담 12명·협력 기업 40곳 → AI 실무 교육·기업 연계 프로젝트 → 수료생 300명·프로젝트 60건 → 단기 역량 +25%·자격 180명 / 중기 취업률 70%·고용 유지 85% → 청년 고용률 +2.1%p.
- `assets/example-logic-model-dark.html` — minimal dark, same labels.
- `assets/example-logic-model-full.html` — full editorial.
