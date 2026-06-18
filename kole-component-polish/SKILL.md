---
name: kole-component-polish
description: >-
  Surgical component-level polish using Kole Jain's standards. Use when the user wants to refine,
  tighten, fix, or "nitpick" one or a few small parts — a button, card, row, chip, filter, modal,
  input, icon, badge, tab — rather than redesign a whole screen. Works on several at once, including
  components the user CIRCLES / annotates on a screenshot or lists in a message ("check these",
  "look at the circled bits"). It proactively points out the small things that are off (the details a
  non-designer wouldn't catch) and fixes just those components, consistently with the rest of the UI.
  Triggers on "polish", "tighten this up", "clean up this", "what's off with this", "check these",
  "fix this component/button/card", "nitpick this", or pointing at parts of a screenshot.
---

# Kole Component Polish

The **surgical companion** to the `kole-uiux-eval` co-build skill. That skill redesigns whole screens;
**this one refines the specific components you point at** (circle them on a screenshot or name them)
and surfaces the small flaws so the user doesn't have to know what Kole would do — you do.

## Shared eval (same brain, one source of truth)
This skill uses the **same references** as the eval skill in the parent folder. Read them from
`../references/` (this skill sits inside the eval skill's folder):
- `kole-principles.md` — the per-detail rules (spacing, corners, type, icons, buttons/chips, states).
- `color-and-levels.md` — the 4-layer colour system.
- `animation.md` — micro-interaction / easing rules.
- `visual-examples/projects/` — the visual bar to match.

Don't restate or fork those rules here — read them. This file only changes the **scope** (a few
components) and the **posture** (surgical + proactive nit-spotting).

## Targets — figure out what to work on
Work on the specific parts the user points to. Determine the target set from any of these:
- **Circled / annotated screenshot** — the user marks regions (red circle, box, arrow, scribble,
  highlight). Treat **each marked region as one target**; identify the component under each mark and
  ignore the rest of the screen. If a mark is ambiguous, say what you think it's pointing at and ask.
- **Named in the message** — "the filter chips and the Send button", "check these two cards". Each
  named item is a target.
- **Both** — they often circle *and* describe ("check these, the spacing feels off"). Use the
  description as the hint for what to look for on the circled items.

Handle **2-3 (or more) targets in one run** — scan and fix each, report per component. If no target is
given at all, ask which component(s) to polish (don't silently polish the whole screen — that's the
main skill).

## Scope — surgical, not structural
- Touch **only the targeted component(s)** and what's strictly inside them. **Do not** restructure the
  page, move other sections, or add new patterns elsewhere — that's the main co-build skill's job.
- **Match the existing system.** Reuse the screen's tokens, spacing scale, accent, icon set, and
  component styles. The fixed component must look like it belongs, not like a new style.
- **Smallest correct change.** Prefer adjusting a value/token over rebuilding. If the component is
  fundamentally wrong-pattern (e.g. detached pills that should be a segmented control), say so and fix
  the pattern — but still only within that component.

## Procedure — run per target (repeat for each circled / named component)
1. **Resolve the targets** (see "Targets" above): list the component(s) you're about to polish so the
   user can confirm you read the marks/message right. Then for each:
2. **Look at it** — render/inspect it, **including its hidden states**: hover, active, focus, disabled,
   the open ⋯ menu/dropdown, expanded, empty, loading, error. Many flaws only appear on interaction.
3. **Micro-flaw scan** — proactively list what's off by Kole's detail standards (checklist below).
   Catch the subtle stuff; this is the whole point.
4. **Fix surgically** — smallest set of consistent changes; replace ALL icons in it with the screen's
   one set (`lucide-react`); honour `prefers-reduced-motion`.
5. **Self-check** — re-render and look (incl. states) against `visual-examples/projects/`. Nothing
   clipped/stranded/mismatched. Then show before/after + one plain-language line per change.

## Micro-flaw checklist (what to proactively catch — detail in `kole-principles.md`)
- **Spacing/grid:** off the 4/8 grid · inconsistent or eyeballed padding · cramped (needs to breathe).
- **Corners:** mismatched radii · nested corner wrong (`inner = outer − gap`) · pill needs no fix.
- **Type:** large text not tightened (−2 to −4% letter-spacing, 110-130% line-height) · >2 weights or
  >2 colours · display font used on small text.
- **Colour:** accent used decoratively / not the one accent-as-scale · destructive not red · pure
  black/white where grey belongs · contrast below AA.
- **Shadow:** too strong → 15-20% opacity, higher blur, light-grey; `x ≤ y`, blur 1.3-2× y.
- **Icons:** not from the one set · wrong size (≈ line-height) · mixed weight · a leftover/mismatched
  icon (e.g. Send arrow vs Settings gear).
- **Buttons/chips:** more than one primary · secondary not ghost/outline · padding ≠ ~width 2× height ·
  chip coloured like the primary CTA or too tall.
- **States & feedback:** missing hover/active/focus/disabled (mobile: press) · no loading/empty/error/
  success · no micro-feedback or toast on action · linear easing.
- **Grouping:** detached pills that should be ONE segmented control · dividers that should be space ·
  double-nested cards.
- **Alignment:** off-grid or optically misaligned edges/icons.

## Output format
Confirm the target set first, then one block per component:
```
KOLE POLISH — targets: <component A>, <component B>, <component C>

▸ <component A>
  Nits (Kole would fix these)
  - <small flaw> → <precise fix: exact value / token / pattern>
  Applied
  - <what changed, in plain language>

▸ <component B>
  Nits
  - ...
  Applied
  - ...

(if you couldn't render it) Show me a screenshot of the targets incl. their hover/open states so I can self-check.
```
Lead with the **Nits** — surfacing the small bad things is the job. Keep it to this component; if you
notice a whole-screen problem, name it in one line and point to the `kole-uiux-eval` skill instead of
fixing it here. Don't invent Kole quotes beyond what's in the shared sources (`../SOURCES.md`).
