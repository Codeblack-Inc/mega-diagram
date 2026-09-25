# 추진 배경·필요성 (Problem → Cause → Solution)

**Best for:** the opening figure of a 사업계획서·과제 제안서·정책 보고서 — *why this project must exist*. Three evidence-backed 현황 문제 on the left, the 원인 behind each in the middle, and one strong conclusion box on the right that turns the causes into 해결 방향 and states the 사업 목적. The reviewer reads it left to right as one argument: 문제 → 원인 → 그래서 이 사업.

This is a catalogued Korean report pattern, not a new visual type. It inherits its layout grammar from **Process** ([type-process.md](type-process.md)) — ordered columns read left to right — and its banded rows from **Layer stack** ([type-layers.md](type-layers.md)).

## 쓰는 곳 / 쓰지 않는 곳

Use it when every problem carries a number (건, 곳, 분, %, 억 원) and each problem has one identifiable cause the project addresses.

Don't use it for:

- Many causes of **one** observed effect, grouped by category → **Fishbone** ([type-fishbone.md](type-fishbone.md)).
- A before/after comparison of the same process step → **AS-IS / TO-BE** ([ko-as-is-to-be.md](ko-as-is-to-be.md)).
- Vision → goals → strategies → tasks → **Strategy house** ([type-strategy-house.md](type-strategy-house.md)).
- Problems without numbers. If you can't cite 142건 or 47분, write a paragraph; the figure's authority is the evidence column.

## Layout grammar

Canvas `viewBox="0 0 1000 568"`, 40px side margins, everything structural on the 4px grid.

| Element | Geometry (x, y, w × h) |
|---|---|
| Column header strip ×3 | y=40, h=32, `ink @ 0.05` fill, no stroke, `rx=6`. Mono 9px `01`/`02`/`03` at x+12, Korean 12px 600 name centred |
| 현황 문제 cards | x=40, w=280; rows y = 96 / 192 / 288, h=80 (16px gap) |
| 원인 cards | x=368, w=240, same rows (48px gutter) |
| 해결 방향·사업 목적 box (focal) | x=656, w=304, y=96 → 472 (one box, not three) |
| Source line | x=40, baseline 456, Korean 12px `soft`: `자료: …(2023~2025)` |
| Legend | hairline y=504, items baseline 536 |

- **Rows are the argument.** Problem *i*, cause *i* and 해결 방향 *i* share a row, so the connectors are straight horizontal `<line>`s at the row centre (y + 40). No elbows are needed; if a cause serves two problems, the layout is wrong — merge the problems.
- **Connectors** run 320→368 and 608→656, `muted` 1.2 with `arrow`. They are unlabelled: the column headers already say what each hop means.
- **Problem card anatomy:** the evidence number at x+16, baseline y+50, 28px 600 `ink` (`142건`, `47분`); name at x+112, baseline y+34, 14px 600; basis line at x+112, baseline y+56, 12px 400 `muted` (`최근 3년, 연 18% 증가`). The number column is 88px wide.
- **Cause card anatomy:** name 14px 600 at x+16, baseline y+34; detail 12px `muted` at y+56 — a second number here strengthens the causal claim (`센서 설치율 12%`).
- **Conclusion box anatomy:** three 해결 방향 rows aligned with the cause rows (mono 9px `accent` index `01` at x+16, name 14px 600 at x+40, detail 12px `muted`), `rule` hairlines at y−8 between them; then an `accent` hairline at y=384, `사업 목적` caption (12px 500 `accent`, baseline 408), the purpose statement (14px 600, baseline 432) and the target (12px 500 `muted`, baseline 456).
- **Paint order:** headers → connectors → problem cards → cause cards → conclusion box → source line → legend.

## Node treatments by semantic role

| Role | Treatment | Fill / stroke |
|---|---|---|
| 현황 문제 | `backend` | white (dark `#24223a`) / `ink` |
| 원인 | `store` | `ink @ 0.05` / `muted` |
| 해결 방향·사업 목적 (focal, 1) | `focal` | `accent-tint` / `accent`, 1.2 |
| Column header strip | none | `ink @ 0.05`, no stroke |

Accent budget: the conclusion box only. Don't accent a problem number — red-alert styling reads as alarmism, and the palette has no red on purpose.

## Korean wording

- 문제 이름 ≤ 7자, 명사형 (`안전사고 증가`, `초동 대응 지연`). The number carries the severity; don't write `심각한`.
- 근거 줄 ≤ 14자 and states the base of the number (`감독관 1인당 담당 사업장`, `사고 인지부터 출동까지`).
- 원인 ≤ 10자, a structural cause, not a restated symptom (`수기 점검·서면 보고`, not `점검이 느림`).
- 해결 방향 ≤ 12자, each answering its row's cause. 사업 목적 is one noun phrase ≤ 18자; the target line carries a year and a number (`2028년 중대사고 50% 감축`).
- Width budget (style-guide § Korean labels): at 14px a Hangul syllable is 14px, other characters 8.4px. `IoT 실시간 감지·경보` = 7×14 + 5×8.4 = 140px → fits the 248px text run of the conclusion box.

## Complexity budget

- Exactly 3 rows (2 allowed). Four problems means two of them share a cause — merge.
- 1 focal box. 6 connectors. No arrow labels.
- 1 source line. Budget figures and schedules go in the `-full` cards.

## Anti-patterns

- Problems without numbers (`관리 체계 미흡`). The left column is evidence.
- Three separate solution boxes on the right. The conclusion is one object; that's what makes it read as the answer.
- Crossing connectors (problem 1 → cause 3). Re-order rows instead.
- An arrow from the conclusion box back to the problems. The figure ends at the purpose.
- Figure number or caption inside the SVG (`[그림 1] 추진 배경`); the document tool adds it ([mega.md](mega.md)).

## Pre-output checklist

- [ ] Every problem has a number with a unit and a basis line?
- [ ] Rows aligned: problem *i* → cause *i* → 해결 방향 *i*, straight connectors at the row centre?
- [ ] One focal conclusion box with the 사업 목적 and a dated target?
- [ ] Source line cites the data period?
- [ ] Korean text ≥12px in `'Geist', 'Pretendard', 'Noto Sans KR', sans-serif`; sizes on the ramp (12, 14, 28; mono 9)?
- [ ] Legend strip at the bottom; light, dark and full carry identical labels?
- [ ] `self_check.py`, `lint-skin.py`, `verify-geometry.py`, `lint-render.py` pass; light and dark PNG checked by eye?

## Examples

- `assets/example-problem-solution.html` — minimal light. 가온 국가산업단지 통합 안전관리: 안전사고 142건·감독관 1인당 310곳·초동 대응 47분 → 개별 관리·수기 점검·감지 부재 → 데이터 허브·스마트 점검·IoT 감지, 사업 목적 `데이터 기반 산단 안전관리 체계 구축`.
- `assets/example-problem-solution-dark.html` — minimal dark, same labels.
- `assets/example-problem-solution-full.html` — full editorial with Korean header, 3 cards of varied widths and footer.
