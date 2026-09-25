# mega-diagram cookbook

Operator recipes for this repository. The design system still lives in [`skills/mega-diagram/SKILL.md`](../skills/mega-diagram/SKILL.md); this file is the runbook: what to say, which files to load, and which commands to run.

Use it from an **editable clone** (this checkout). Managed marketplace installs can still follow the recipes, but do not edit `references/style-guide.md` inside a package that updates will replace — save a [client profile](../skills/mega-diagram/references/profiles.md) instead.

---

## Map

| I want to… | Jump |
|---|---|
| Wire this clone into Claude, Codex, Cursor, Cline, Kiro, OpenCode, or Copilot | [R0](#r0-editable-install) |
| Confirm Python, Playwright, PNG export | [R1](#r1-doctor) |
| Draw the first diagram in a real project | [R2](#r2-first-diagram-in-a-project) |
| Match a brand | [R3](#r3-onboard-a-skin) |
| Choose type / pattern / size without rereading the whole skill | [R4](#r4-selection-cheat-sheet) |
| Browse shipped examples | [R5](#r5-gallery-and-templates) |
| Redraw draw.io or Mermaid | [R6](#r6-import) |
| Hand off SVG or PNG | [R7](#r7-export) |
| Check a generated HTML file | [R8](#r8-taste-and-geometry-gates) |
| Paste a request to an agent | [R9](#r9-prompt-pack) |

---

## R0. Editable install

The canonical skill root is `skills/mega-diagram/` (`SKILL.md` + `references/` + `assets/`). Point skill hosts at that inner directory. Pi and the repository's native marketplace packages are the exceptions because they already resolve the `skills/` directory from the repository root.

This repository does not duplicate `SKILL.md` into host-specific loader stubs. For an editable install, symlink or junction the canonical inner directory into one discovery root used by your host.

### Host matrix

| Host | How it finds the skill | What you do |
|---|---|---|
| **Claude Code** | Marketplace plugin, `~/.claude/skills/`, or project `.claude/skills/` | Use `/plugin install` for managed updates or link the inner skill for editable work. |
| **Codex** | Marketplace plugin or `~/.agents/skills/` | Use the marketplace for managed updates or link the inner skill for editable work. |
| **Cursor** | `~/.cursor/skills/`, `~/.agents/skills/`, project `.cursor/skills/`, or project `.agents/skills/` | Link the inner skill, then ask in Agent chat. |
| **Cline CLI / VS Code** | `~/.cline/skills/`, `~/.agents/skills/`, workspace `.cline/skills/`, or workspace `.agents/skills/` | Link the inner skill and enable it from the Skills view when needed. |
| **Kiro** | Workspace `.kiro/skills/` or global `~/.kiro/skills/` | Link the inner skill, or import its GitHub subdirectory URL; imported skills are copied and must be re-imported to update. |
| **OpenCode** | Project `.opencode/skills/` or global `~/.config/opencode/skills/` | Link or copy the inner skill; copied installs must be replaced to update. |
| **GitHub Copilot** | Marketplace plugin; project `.github/skills/`, `.agents/skills/`, or `.claude/skills/`; user `~/.copilot/skills/`, `~/.agents/skills/`, or `~/.claude/skills/` | Use the marketplace for managed updates or link the inner skill for editable work. |

Marketplace installs (Claude `/plugin`, `copilot plugin install`, `codex plugin add`, `droid plugin install`) stay the right path if you do **not** need to edit `style-guide.md` in-tree. Use profiles instead.

### Unix (user-global inner skill)

```bash
git clone https://github.com/Codeblack-Inc/mega-diagram.git ~/code/mega-diagram
DIAGRAM_SKILL=~/code/mega-diagram/skills/mega-diagram
mkdir -p ~/.claude/skills ~/.cursor/skills ~/.agents/skills ~/.cline/skills \
  ~/.kiro/skills ~/.config/opencode/skills ~/.copilot/skills
ln -s "$DIAGRAM_SKILL" ~/.claude/skills/mega-diagram
ln -s "$DIAGRAM_SKILL" ~/.cursor/skills/mega-diagram
ln -s "$DIAGRAM_SKILL" ~/.agents/skills/mega-diagram
ln -s "$DIAGRAM_SKILL" ~/.cline/skills/mega-diagram
ln -s "$DIAGRAM_SKILL" ~/.kiro/skills/mega-diagram
ln -s "$DIAGRAM_SKILL" ~/.config/opencode/skills/mega-diagram
ln -s "$DIAGRAM_SKILL" ~/.copilot/skills/mega-diagram
```

Create only the destinations for the hosts you use. When a host scans both its native root and `.agents/skills/`, choose one so it does not discover the same skill twice.

### Windows (directory junction — not a file symlink)

```powershell
$src = "E:\mega-diagram\skills\mega-diagram"
foreach ($t in @(
  "$env:USERPROFILE\.claude\skills\mega-diagram",
  "$env:USERPROFILE\.cursor\skills\mega-diagram",
  "$env:USERPROFILE\.agents\skills\mega-diagram",
  "$env:USERPROFILE\.cline\skills\mega-diagram",
  "$env:USERPROFILE\.kiro\skills\mega-diagram",
  "$env:USERPROFILE\.config\opencode\skills\mega-diagram",
  "$env:USERPROFILE\.copilot\skills\mega-diagram"
)) {
  $parent = Split-Path $t -Parent
  if (-not (Test-Path $parent)) { New-Item -ItemType Directory -Path $parent -Force | Out-Null }
  if (-not (Test-Path $t)) { cmd /c mklink /J "$t" "$src" }
}
```

Replace `E:\mega-diagram` with your clone path. If a junction already exists, leave it; do not copy the skill over a managed plugin folder.

Pi still registers the **repo root**: `pi install <clone-path>`.

---

## R1. Doctor

Ask in any host: `run mega-diagram doctor` or `/mega-diagram:doctor` / `/doctor`.

The procedure is [`references/doctor.md`](../skills/mega-diagram/references/doctor.md). It must not install packages. Typical local setup for PNG export:

```bash
python -m pip install playwright
python -m playwright install chromium
```

On Windows, `python` is the usual interpreter; the skill also accepts `python3` when that is what the host has.

---

## R2. First diagram in a project

Work in the **project that will own the HTML**, not inside `skills/mega-diagram/assets/` unless you are contributing an example.

1. **Style-guide gate** ([SKILL.md §0](../skills/mega-diagram/SKILL.md)). If the working copy is still shipped defaults (paper `#ffffff`, ink `#17152b`, accent `#2f6fdb`), the agent must pause and offer onboarding, a profile, or an explicit default. Skip the gate when a valid `.mega-diagram` marker selects a profile (including `profile: default`).
2. **Confirm before drawing** ([SKILL.md §3](../skills/mega-diagram/SKILL.md)): visual type, optional semantic pattern, size preset, and what the complexity budget will cut.
3. **Load** the matching `references/type-*.md` before writing SVG. If a semantic pattern applies, load [`semantic-patterns.md`](../skills/mega-diagram/references/semantic-patterns.md) first.
4. **Write** a self-contained HTML file in the project (for example `docs/diagrams/<name>.html`). Do not silently overwrite gallery examples.
5. **Run** the pre-output checklist ([SKILL.md §9](../skills/mega-diagram/SKILL.md)). Orthogonal connectors, 4px grid, ≤9 nodes unless you split, accent on ≤2 focals.

Marker file at the project root, entire file:

```text
profile: <slug>
```

See [`profiles.md`](../skills/mega-diagram/references/profiles.md). Profiles live in `~/.mega-diagram/profiles/`, not in this clone.

---

## R3. Onboard a skin

Full flow: [`onboarding.md`](../skills/mega-diagram/references/onboarding.md).

Say one of:

- `Onboard mega-diagram to https://example.com`
- `Extract mega-diagram tokens from the local design-system folder <path>`
- `Use these tokens: paper … ink … accent …` (manual)
- `Proceed with the default skin` (optionally write `profile: default` with consent)

Then: propose the style-guide diff, wait for approval, write `references/style-guide.md` **or** save a named profile and point the project marker at it. Prefer profiles when this clone is shared or when plugin updates would clobber a customized working copy.

---

## R4. Selection cheat sheet

Do not duplicate the 40-type table here. Open [SKILL.md §3](../skills/mega-diagram/SKILL.md) and pick one layout grammar.

**Behavior first** (then nearest type):

| If the story is… | Pattern → type |
|---|---|
| Fan-in, queues, bottlenecks | Fan-in queue → Data flow |
| Repeated stage slots | Stage framework → Process |
| Messy input becomes a durable artifact | Unstructured → structured → Data flow |
| Two policy traces, first divergence | Paired traces → Flowchart |
| Trust boundaries / paved road | Secure paved road → Architecture |
| Controls by enforcement layer | Governance catalog → Layer stack |
| Compensating defenses, residual risk | Compensating layers → Layer stack |

**Hard stops:** if a table or paragraph is clearer, do not draw. If you are over the [complexity budget](../skills/mega-diagram/SKILL.md) (9 nodes / 12 arrows as the default ceiling), split overview + detail.

**Size** ([output-spec.md](../skills/mega-diagram/references/output-spec.md)): `doc-inline` for docs, `slide-16x9` for decks, `social-og` for cards, `fit` for Figma SVG. Size changes type ramp, not just viewBox.

**Motion:** default is static. Load [`animation.md`](../skills/mega-diagram/references/animation.md) only when the user asked for motion or ordered change is otherwise unclear.

---

## R5. Gallery and templates

From the clone root:

```bash
# macOS / Linux
open skills/mega-diagram/assets/index.html
xdg-open skills/mega-diagram/assets/index.html

# Windows
start skills/mega-diagram/assets/index.html
```

Copy a scaffold, then replace the SVG:

```bash
cp skills/mega-diagram/assets/template.html my-diagram.html
cp skills/mega-diagram/assets/template-full.html my-diagram.html
cp skills/mega-diagram/assets/template-motion.html my-diagram.html
```

Shipped examples are `assets/example-<type>.html` plus `-dark` and `-full` variants. Treat them as specimens, not scratch files.

---

## R6. Import

Load [`import-drawio.md`](../skills/mega-diagram/references/import-drawio.md), [`import-mermaid.md`](../skills/mega-diagram/references/import-mermaid.md), or [`import-excalidraw.md`](../skills/mega-diagram/references/import-excalidraw.md) and set the four dials **before** redrawing ([output-spec.md](../skills/mega-diagram/references/output-spec.md)):

| Dial | Typical values |
|---|---|
| Format | `html` · `svg` · `png` · `html+png` |
| Size | `doc-inline` · `slide-16x9` · `social-og` · `fit` · … |
| Detail | `faithful` · `balanced` · `simplified` |
| Audience | `engineer` · `mixed` · `executive` |

Slash forms (Claude): `/mega-diagram:import-drawio <file>`, `/mega-diagram:import-mermaid <file-or-md>`, and `/mega-diagram:import-excalidraw <file>`. Always report a **fidelity ledger** (merged, collapsed, dropped). Source coordinates, source palette, Mermaid auto-layout, and Excalidraw hand-drawn geometry do not carry over.

Extractors in this checkout: `skills/mega-diagram/scripts/drawio_extract.py`, `mermaid_extract.py`, `excalidraw_extract.py`.

---

## R7. Export

**Never export unprompted.** Procedure: [`export.md`](../skills/mega-diagram/references/export.md).

- SVG: first `<svg>` only, XML-escaped Google Fonts `@import`, diagram-only (no full-page cards).
- PNG: Playwright screenshot of that SVG box, transparent background. Motion HTML: `?motion=static`, wait for `document.fonts.ready`, `data-frame="static"`.

```
/mega-diagram:export-diagram path/to/diagram.html
/mega-diagram:export-diagram path/to/diagram.html --png-only --scale=2
```

---

## R8. Taste and geometry gates

After generating HTML in this clone (examples or a file you are contributing):

```bash
python skills/mega-diagram/scripts/self_check.py path/to/diagram.html
python scripts/lint-skin.py path/to/diagram.html
python scripts/verify-geometry.py path/to/diagram.html
```

Full contributor gates: [CONTRIBUTING.md](../CONTRIBUTING.md). Docs/routing: `python scripts/verify-docs-sync.py`.

---

## R9. Prompt pack

Copy and fill. Keep one type, one size, one destination.

**Architecture (docs):**

> Draw an architecture diagram of [system]. Nodes: [list ≤9]. Focal: [1–2]. Size `doc-inline`, format HTML. Use the mega-diagram skill. Confirm type and cuts before drawing. Save to `[path].html`.

**Deck:**

> Redraw `[file].drawio` for a 16:9 slide, detail `simplified`, audience `executive`, format PNG.

**Mermaid in a README:**

> Import every Mermaid block in `[file].md`, size `doc-wide`, detail `balanced`, audience `mixed`. Report the fidelity ledger.

**Brand, then diagram:**

> Onboard mega-diagram from `https://[site]`. If I approve the tokens, save profile `[slug]` and write `.mega-diagram` with `profile: [slug]`. Then draw [type] of [topic].

**Do not:**

> Make it look like Mermaid / add shadows / coral every box / diagonal connectors / more than nine nodes in one figure.

---

## Pointers

| Topic | File |
|---|---|
| Philosophy, types, checklist | [`SKILL.md`](../skills/mega-diagram/SKILL.md) |
| Tokens | [`style-guide.md`](../skills/mega-diagram/references/style-guide.md) |
| Settled design decisions | [`docs/adr/`](adr/) |
| Maintainer validation | [`CONTRIBUTING.md`](../CONTRIBUTING.md) |
