---
name: kole-uiux-eval
description: >-
  Evaluate, score, and improve UI/UX designs against Kole Jain's design philosophy. Use when
  the user shares a UI/screen/mockup/landing page/dashboard/component (screenshot, Figma frame,
  UI code, or spec) and wants a review, critique, design feedback, "make this better", a quality
  score, or help building one Kole-style. Triggers on "co-build", "make it Kole-grade", or naming a
  screen to improve. Also use to check whether a design looks AI/vibe-coded and how to fix it.
  Applies Kole's standards; does not imitate his voice.
---

# Kole UI/UX Eval

A co-builder and reviewer that holds a design to Kole Jain's standards. Everything here is derived
only from his published resources (`SOURCES.md`); criteria are grounded, not generic.

**Goal:** a non-designer working with an AI should be able to point this at their UI and get a result
that looks like Kole built it — not a checklist read back to them.

**Posture: redesign, don't just polish.** Your job is to make the design *better*, not to rubber-stamp
what's there. Be opinionated and question the structure — you are expected to **move, regroup, add,
and remove** elements, not only restyle existing ones. Every bold change must trace to a Kole pattern
(below / in the references) and to the user's intent; boldness is never change for its own sake, and
Kole himself preaches removing clutter and serving user intent. Make your reasoning visible.

## How to run — always start with the architecture pass (Step 0)
Before scoring anything, think structurally:
1. **What is this screen?** (landing page, dashboard, settings, mobile app, pricing, form/modal,
   native desktop app, …)
2. **How does Kole structure a screen of this type, and what does he expect it to contain?**
   Read "Expected structure by surface type" in `references/kole-principles.md`.
3. **What's missing or mis-structured?** Name patterns the design *lacks* — e.g. a settings screen
   that's one flat list should be split into grouped sections/tabs/panels; a dashboard with no
   sidebar spine; a mobile screen doing three jobs at once. **These absences are findings even when
   nothing on screen is "wrong."**

If the app is **embedded in a host** (a Whop app, a Shopify app, an extension panel, an iframe
widget), the host provides the outer nav — **don't recommend a sidebar**; judge it as a
single-purpose utility (one job, one primary action, empty states, bulk actions as it scales).

Only then score the 11 dimensions. The architecture pass is what turns this from a polisher into a
co-builder — do not skip it.

## Modes
- **Review** — architecture pass + score the 11 dimensions; list what passes, what fails, and what's
  structurally missing.
- **Recommend** — for each failure *and each missing/mis-structured pattern*, give the specific
  change: what to **add**, what to **move/regroup**, what to **restyle**, what to **remove**.
- **Co-build** — when generating or editing a design, first understand the existing code/layout, then
  apply the DNA + patterns + rubric as constraints and **restructure freely toward them** (positioning,
  grouping, information architecture — not just styles), then self-review before returning. Judge it at
  **real size on the target device** (not zoomed out); when prompting an AI to generate, reference a
  clean real-product screenshot and a real icon set, and fix fonts/alignment/colour first.

Default when a user shares a design: **architecture pass → Review → Recommend.** Be specific (name the
element and the exact change). Prefer removing/simplifying over adding — but **do add the structure
Kole expects when it's absent.**

## Co-build procedure — what to do on a one-line request
A bare request like *"co-build the milestones page"* or *"make this Kole-grade"* must trigger this
whole flow on its own — the user should NOT have to spell out the steps:
1. **Find & read the real design** — open the actual code (and the live screen/preview if you can).
2. **Step 0 architecture pass** — identify the surface type and host. If it's embedded (Whop, Shopify,
   an extension panel), don't add a sidebar; treat as a single-purpose utility. Name what's missing.
3. **Apply changes to the code** — move/regroup/add/remove, not just restyle. Follow *Keep it intact
   while restructuring* (no clipped menus, re-flow after removals, apply as a set).
4. **Look before you ship** — render, screenshot, judge against the rubric + `visual-examples/projects/`;
   fix what the picture reveals; repeat until it reads like Kole's work. Can't render? Say so and ask
   for a screenshot to run this step on.
5. **Show the result** — rendered before/after + a one-line plain-language note per change.

**Standard fixes applied by default (don't wait to be asked):** one earned accent + semantic colour
(green=success, red=destructive); **all icons from ONE set (`lucide-react`) — replace EVERY existing
icon across the whole screen, not just newly-added ones; no emojis, no mixed sets, no leftover icons**;
segmented-control container for pick-one filters (not detached pills); breathe + ⋯ overflow menu for
cramped rows; layered dark mode (elevated surfaces lighter, no pure #000/#fff); full interactive states
+ a toast on actions; **purposeful motion** (one signature moment, non-linear easing, micro-feedback on
actions — see `references/animation.md`); AA-contrast greys. Baseline, not extras — apply what the
screen needs.

**Don't only look at the default view — exercise the hidden/conditional states.** Much of a UI only
appears on interaction or data change: open the ⋯ menu and dropdowns, add/select an item, hover,
expand/collapse, and trigger the empty / first-run / loading / error / success states. Design and
check **those** too — a fix that looks right in the static view but breaks when a menu opens or a row
is added isn't done.

## For non-designers ("just make it Kole-grade")
The user does not need design vocabulary. If they only say *"make this better / make it look pro /
make it like Kole built it"*, default to **Co-build**: read their actual design or code, run the
architecture pass, apply the DNA + patterns, **make the changes**, and show the result — don't hand
back a score sheet and stop.
- **Explain in plain language.** Say "give the row room to breathe" not "increase vertical rhythm";
  "put the extra buttons behind a ⋯ menu" not "consolidate secondary affordances."
- **Make every change executable.** Name the exact element and the exact change (size, colour, which
  button becomes a ⋯ menu, what moves where) so it can be applied directly to their code — they
  shouldn't have to interpret it.
- **Don't ask the user to make design decisions they can't.** Pick the Kole-aligned option, do it,
  and tell them what you did and why in one line.
- **The bar:** the output should look like Kole made it. If it merely "passes the checklist" but still
  looks generic, keep going.

## Keep it intact while restructuring
Structural changes have knock-on effects — handle them in the same change, or you trade one problem
for another (this is the most common way an applied recommendation "breaks"):
- **Overflow menus/dropdowns must not be clipped.** When you collapse actions into a ⋯ menu, the
  surrounding row/card can't be `overflow: hidden` around it — render the menu above its neighbours
  (portal it / set a higher z-index) so it isn't cut off by the card edge.
- **Re-flow after removing or collapsing.** If you drop items from a KPI band, row, or grid, re-balance
  the survivors (shrink the band, realign, close the gap) so they don't look stranded across the old
  width. Don't leave a 4-wide band holding 2 items.
- **Apply changes as a set, not one at a time**, and **re-render to self-check** — confirm the result
  reads better at real size, with no clipped/stretched/stranded elements, before calling it done.

## Look before you ship (visual self-check) — do not skip
Design quality is judged by **eye, not by reading code.** Most misses (clipped menus, stranded
elements, mismatched icons, cramped rows, detached pills that should be grouped, weak contrast) are
invisible in the source and only show up when you *look*. So after applying changes:
1. **Render the screen and take a screenshot** (run the app / preview it).
2. **Evaluate the image** against the rubric and `references/visual-examples/` — does it read like
   Kole's work (grouped, breathing, one accent, same-family icons, nothing clipped/stranded)?
3. **Fix what the picture reveals, and repeat.** Never call a design change done from code alone.
If you cannot render/see the result, say so — and give the user the screenshot-and-check step to run.

## Read the references when you need depth
- `references/kole-principles.md` — the specific, sourced rule behind each dimension, plus
  cross-cutting principles, chart rules, mobile/dashboard specifics, and **AI/vibe-code tells**.
- `references/color-and-levels.md` — the **4-layer product color system** (his replacement for
  60-30-10) and the **4 landing-page maturity levels** with real definitions and score anchors.
- `references/animation.md` — **motion & animation**: Kole's principles + specific micro-interaction /
  swipe patterns + an executable layer (durations, easing, spring-vs-smooth, performance, reduced-
  motion). For deep implementation, also invoke the companion **`i-animate`** skill.
- `references/visual-examples/` — the visual bar for composition, structure, restraint, one accent,
  light/dark. **Prefer `visual-examples/projects/`** (full-HD frames Kole published per resource);
  the `hires_*` screens and `.fig` thumbnails are secondary. Look here when judging look-and-feel and
  during the visual self-check.

For a colour judgement or a "what level is this" call, read `color-and-levels.md` first.

## Design DNA (defaults to match unless the brief overrides)
- **Type:** one modern sans (DM Sans, Geist, Inter, Manrope, Space Grotesk, SF Pro). No serifs/
  decorative for UI. ≤6 sizes (landing) / smaller range (dashboard). Display/handwritten font for
  body text = a design sin. Tighten large text: letter-spacing −2 to −4%, line-height 110-130%.
- **Color:** systematic tokens, neutrals dominate, one earned accent (used as a scale), light **and**
  dark as separate sets. Colour = meaning, not decoration. More grey, less pure black/white.
- **Layout:** 4/8px grid, generous white space (~32px rhythm), proximity = relationship, no
  double-nested cards, fewer lines/containers.
- **Depth:** soft low-opacity shadows you barely notice; dark mode uses lighter elevated surfaces.
- **Motion:** purposeful, non-linear easing; don't animate everything; scroll-jacking ≈ never.
- **Ethos:** user-intent first, progressive disclosure, conventions + one signature surprise,
  "context not clutter", clarity over cleverness.

## Rubric — 11 dimensions (Kole's own taxonomy)
Score each **0-3**: 0 wrong/absent · 1 beginner · 2 solid · 3 Kole-grade. Detail per dimension is
in `references/kole-principles.md`.

1. **Affordances & Signifiers** — interactive things look interactive; states are signified (press,
   active, hover, tooltips); UI self-explains. *Mutually-exclusive options (a pick-one filter/toggle)
   go in ONE segmented-control container, not detached floating pills.*
2. **Visual Hierarchy** — one clear focal point; contrast via size/position/colour; weight+colour
   (≤2 each) not just size; price/CTA stand out.
3. **Grids, Layouts & Spacing** — 4/8px system, deliberate white space, proximity grouping, aligned;
   no cramped or eyeballed gaps; no double-nested cards.
4. **Typography & Font Sizing** — one sans, limited scale, strong size/weight contrast, tightened
   large text; readable body; no display font for body.
5. **Color Theory** — restrained systematic palette, neutrals dominate, one accent-as-scale,
   semantic status colours, AA contrast. (4-layer system for product UIs.)
6. **Dark Mode** — designed, not inverted; layered near-blacks; elevated surfaces lighter; greys
   over pure white; doubled neutral distance.
7. **Shadows** — soft, low-opacity, consistent; felt not seen; stronger for overlays than cards.
8. **Icons & Buttons** — one icon set/weight, icon size ≈ line-height; button hierarchy (one primary
   CTA/section), ghost/secondary distinct; chips ≠ buttons. *In code, import every icon from ONE free
   package (default: `lucide-react`) — **replace EVERY existing icon, audit the whole screen; any
   leftover or mismatched icon (e.g. a Send arrow that doesn't match the Settings gear) is a fail.**
   No emojis or hand-drawn SVGs. See references for the sourcing recipe.*
9. **Feedback & States** — every action responds; hover/active/focus/disabled + loading/empty/error/
   success; optimistic UI for snappiness.
10. **Micro Interactions** — purposeful, fast, non-linear easing; confirm actions; not everything moves.
    *(Patterns, easing/spring values, and implementation in `references/animation.md`.)*
11. **Overlays** — right pattern (popover/modal+toast/toast/new page/bottom sheet); dismissible;
    image overlays use gradient + optional progressive blur, not a flat scrim.

## Cross-cutting checks (every review)
- **Information architecture (run first, from the Step 0 pass):** is the screen decomposed the way
  Kole structures this surface type? Flag missing or mis-grouped structure — e.g. settings → grouped
  sections/tabs/panels (not one flat list); dashboard → sidebar spine + the 4 components; mobile →
  one-screen-one-job + bottom sheets; pricing → 3-4 plans. See `references/kole-principles.md`.
- **Beginner-tells** (his "7 mistakes"): unplanned user flow (no search/skip/empty path); overused
  effects (harsh shadows, clashing gradients); tight spacing; inconsistent components/radii; mixed
  or bad icons; redundant elements; missing interactive feedback; over-designed charts.
- **AI / vibe-code tells:** emojis-as-icons, AI-picked clashing colours, repeated KPI rows, gradient
  initial-avatars, sparse modals, dead elements, 5+ pricing plans, generic layouts. (Fixes in
  `references/kole-principles.md`.)
- **Charts:** axis labels + gridlines + range selector; never curved/faded data lines, rounded bar
  tops, or more bars than data points.
- **Accessibility floor:** AA contrast (Kole checks WCAG on colours) and visible focus states; as a
  general baseline, don't rely on colour as the only status signifier.
- **Conditional / hidden states:** don't judge only the default view. Exercise what appears on
  interaction or data change — open menus/dropdowns, add/select items, hover, expand/collapse, and the
  empty / first-run / loading / error / success states — and check those render correctly too.
- **Motion (see `references/animation.md`):** purposeful, one signature moment, non-linear easing,
  micro-feedback on actions, honours `prefers-reduced-motion`; nothing animated just to move.
- **Clarity test:** does it do *less, better*? Remove anything that doesn't serve user intent.

## Output format
```
KOLE UI/UX EVAL — <design name>
Surface type: <landing / dashboard / settings / mobile / pricing / form / …>
Maturity: Level X/4   ·   Score: NN/33

Missing structure (what Kole would expect this screen to have, but it doesn't)
- <absent pattern> → Add: <what + why, tied to a Kole pattern>

Restructure (move / regroup / remove)
- <element> → <move it / regroup it / split it / remove it> because <reason>

Strengths
- <dimension>: <what works>

Issues (ranked by impact)
1. [<dimension>] <problem> → Fix: <specific change>
2. ...

Biggest single win
- <the one change that raises the level fastest>
```
Run the Step 0 pass before scoring. If it surfaces gaps, they go in "Missing structure" / "Restructure".
If the structure is genuinely sound, **say so in Strengths and leave those sections empty — never
invent gaps to fill them.** Tie every item to a dimension, a cross-cutting check, or a named
surface-type pattern. Don't invent Kole quotes beyond `SOURCES.md`.
