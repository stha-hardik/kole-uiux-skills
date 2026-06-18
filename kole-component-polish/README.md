# Kole Component Polish — a Claude skill

The **surgical companion** to `Kole UI/UX Eval`. The main skill redesigns whole screens; this one
**refines the specific components you point at** and proactively flags the small Kole-level flaws —
so you don't have to spot them yourself.

## When to use which
- **Kole UI/UX Eval** → "co-build / make this screen Kole-grade" (big, structural).
- **Kole Component Polish** → "tighten just these bits" (small, surgical, one or a few components).

## How to use
Point it at the components — either way works:
- **Circle them on a screenshot** and say *"check these"* — it treats each mark as a target.
- **Name them** — *"polish the filter chips and the Send button."*

It lists what's off on each (with the exact fix), applies the smallest consistent change, and shows
before/after. It will **not** restructure the screen — if it spots a bigger problem it points you to
the main skill.

## Shared brain
This skill lives inside the eval skill's folder and reads the **same references** via `../references/`
(principles, colour, animation, visual-examples), so its judgments stay consistent. One eval, two
postures. Keep this folder nested where it is so the `../references/` path resolves.

## Files
- **`SKILL.md`** — the skill (targets, surgical scope, micro-flaw checklist, output).
- **`README.md`** — this file.

## Example trigger
> Use the kole-component-polish skill — check the circled parts in this screenshot and tighten them.
> (attach your annotated screenshot)
