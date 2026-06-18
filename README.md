# Kole UI/UX Eval — a Claude skill

A skill that reviews, scores, and improves UI/UX designs against **Kole Jain's** design
philosophy — built only from his own resources (his `.fig` files + his links + transcripts of
his top 24 videos). No app, no code, nothing to install or run; it's instructions an AI loads.

## Files
- **`SKILL.md`** — the skill. Frontmatter + modes + the 11-dimension rubric + cross-cutting checks
  + output format. *This is the product.*
- **`references/kole-principles.md`** — the specific, sourced rule behind each dimension, plus
  cross-cutting principles, chart rules, mobile/dashboard specifics, and AI/vibe-code tells.
- **`references/color-and-levels.md`** — the 4-layer product colour system and the 4 maturity levels.
- **`references/animation.md`** — motion/animation: Kole's principles + patterns + an executable layer
  (durations, easing, performance, reduced-motion); pairs with the `i-animate` companion skill.
- **`references/visual-examples/`** — the visual bar: 61 full-HD frames from Kole's published projects
  (`projects/<Project>/`, primary), plus crisp `hires_*` screens and low-res `.fig` thumbnails
  (secondary/fallback). Indexed in its own `README.md`. Used during the visual self-check.
- **`SOURCES.md`** — every criterion traced to its source.
- **`README.md`** — this file.

## Install as a skill
Copy this whole folder into your skills directory so the folder contains `SKILL.md`:
- Claude Code / Agent SDK: `~/.claude/skills/kole-uiux-eval/` (or a project `.claude/skills/`).
- Or just paste `SKILL.md` into any AI chat as context.

It triggers when you share a UI/screen/mockup/landing page/dashboard/component and ask for a
review, critique, score, "make this better", help building one Kole-style, or an AI-vibe-code check.

## Modes
**Review** (score + pass/fail) · **Recommend** (specific fixes) · **Co-build** (generate to the
rubric, then self-review). Default when you just share a design: Review → Recommend.

## Scope
Applies Kole's *standards*; does not mimic his voice. Honest about sources — see `SOURCES.md`.

---

## Worked example (sanity check)

**Input:** "A SaaS billing dashboard, vibe-coded. Pure-black background, white text. A row of four
KPI cards repeated under two different charts. Sidebar with a gradient circle avatar showing 'JD'.
Emojis used as the nav icons. One line chart with curved, faded data lines and no axis labels.
Three bright button colours (blue/green/purple). Poppins + a script logo font. Hard grey offset
shadows. No hover/focus states."

**Output:**
```
KOLE UI/UX EVAL — SaaS billing dashboard
Surface type: dashboard (billing)
Maturity: Level 1/4   ·   Score: 7/33

Missing structure (what Kole would expect this screen to have, but it doesn't)
- Billing is one flat scroll → split it into tabs/panels (Plan · Payment method · Invoices · Usage),
  the way Kole decomposes settings so categories don't pile into one list.
- No empty/loading/error states for the charts or invoice list → add them (his recurring miss).
- No bulk actions on the invoice list → add multi-select + a contextual bulk-action bar.

Restructure (move / regroup / remove)
- The two duplicate KPI rows → keep one, move it directly above the chart it explains.
- Sidebar gradient "JD" avatar → replace with an account card; push settings/help to the bottom.
- Charts and KPIs that repeat the same numbers → remove the redundant one (don't show data twice).

Strengths
- Layout: a sidebar + main-content split is the right dashboard skeleton.

Issues (ranked by impact)
1. [AI/vibe-code tells] Emojis-as-icons, AI-clashing colours, repeated KPIs, gradient initial-avatar.
   → Fix: real icon set (Phosphor/Lucide); one disciplined accent; consolidate; account card.
2. [Color Theory] Three bright button colours compete and the accent loses meaning.
   → Fix: one accent as a scale (500 main / 700 hover); secondary actions = outline/ghost.
3. [Dark Mode] Pure #000 + #fff with no elevation system.
   → Fix: layered near-blacks; elevated cards slightly lighter; light-grey text over pure white.
4. [Charts] Curved + faded data lines, no axis labels — unreadable.
   → Fix: straight lines, gridlines + numbers, a range selector.
5. [Typography] Poppins + a script logo font; build hierarchy with size + weight (≤2 weights).
6. [Shadows] Hard offset grey shadows → soft, 15-20% opacity, higher blur.
7. [Feedback & States] No hover/active/focus → add the four button states + visible focus.

Biggest single win
- Restructure billing into tabbed panels and kill the AI tells — that reorganisation plus real icons /
  one accent / layered dark surfaces lifts it from L1 toward L2.
```

Expected behaviour: the **architecture pass runs first**, so the design's *missing* structure (tabbed
billing panels, states, bulk actions) and what to *restructure* (dedupe KPIs, fix the sidebar) are
surfaced — not just restyled-what's-there. Every item ties to a dimension, a cross-cutting check, or a
surface-type pattern.
