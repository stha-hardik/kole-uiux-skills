# Color system & maturity levels — detailed reference

The two most distinctive frameworks in Kole's work, with his actual numbers. Sourced from
"Why the 60-30-10 Rule is RUINING Your UI Designs" and "The 4 Levels of Landing Page UI/UX
Design" (+ the colour and software-colour videos). See `../SOURCES.md`.

---

## The 4-layer product color system (Kole's replacement for 60-30-10)

> 60-30-10 is fine for beginners and landing pages, but product design needs more. Reference
> point: Vercel is ~90% black, ~8% white, ~2% red (sometimes 0%).

Notation: "% white" = position on a black (0%) → white (100%) scale. So a heading at "11% white"
is very dark (≈#1a1a1a, not pure black) and a background at "99% white" is near-white.

### Layer 1 — Neutral foundation
- A product UI generally needs **~4 background layers, 1-2 strokes, ~3 text variants** (before
  hover/interactive states).
- **Backgrounds:** mostly near-white (Linear ~99%, Notion 100%, Vercel ~98%); pure white is fine.
  Light mode is flexible — dark bg + light cards (Vercel), light bg + dark cards (Notion), or
  monochromatic layers (Supabase). The app frame/sidebar is a **slightly darker anchor** (Mercury
  adds ~2% blue); large elements only need to be very slightly darker.
- **Don't** define a card edge with a thin black border or rely on a drop shadow — use **~85% white**
  to suggest the edge without overpowering it.
- **Buttons:** the more important the button, the darker it is (ghost → … → black w/ white text);
  most multi-purpose buttons sit around **90-95% white**.
- **Text:** important headings ~**11% white** (i.e. very dark, not pure black); the majority of text
  ~**15-20% white**; subtext ~**30-40% white**.

### Layer 2 — Functional accent
- Treat the accent as a **scale**, not one colour: main = **500/600**, hover = **700**, link = **400/500**.
  (Generate a ramp with a tool like UI Colors.) Some products stay neutral (Vercel); others are
  identity-defining (Linear blue/purple, Supabase green).
- **Dark mode:** primary = **300/400**, hover = **400/500**. Dim text, brighten borders.
  Neutrals need **double the distance** vs light mode (light ~2% steps → dark ~4-6%).
  **Surfaces always get lighter as they elevate** (raised cards lighter, or a border).

### Layer 3 — Semantic communication
- Break the neutral system where colour carries meaning: success/fail/in-progress, destructive = red
  even if the brand is purple/black (Vercel manages this with a black-and-white brand).
- **Charts** need a full spectrum. A neutral chart is "super lame"; a brand-ramp chart is too similar.
  Use **OKLCH** (oklch.com) for equal *perceived* brightness across hues — set lightness + chroma,
  then increment hue by **~25-30** per series.

### Layer 4 — Theming
- To re-theme a design, for every neutral: drop **lightness by 0.03**, raise **chroma by 0.02**, then
  adjust the **hue**. Works especially well for dark mode and lets you theme to any colour reliably.

### Quick HSB palette trick (from the cheat-codes video)
From a base colour, step each shade by **+20 saturation / −10 brightness**; adjust hue so cooler
colours (blues/purples) are darker and warmer (yellows/reds) are lighter. For dark-mode depth: take
the dark background and raise brightness ~4-6 / lower saturation 10-20 per layer.
Tailwind shortcut: light bg = the `50` value + accent `500`; dark mode primary = `300`, bg = `950`.

---

## The 4 levels of landing-page UI (maturity ladder — real definitions)

Use as the overall maturity score. Kole's own value/score anchors:

### Level 1 — Template (~$500, ~2/10)
Functionally works but **no design decisions made.** Tells: generic alternating text-left/image-right
all the way down; **stock images** unrelated to the product; mismatch between sharp image edges and
rounded buttons; flat menu with no hierarchy; colour applied haphazardly to anything that will take
it; **no animation** (maybe a bare hover).

### Level 2 — Visual identity forming (~$2,000, ~6/10)
Knows *what* but not yet *why*. **Stacked hero** instead of side-by-side; a **real product
dashboard** instead of stock imagery; colour pops come **from the dashboard**; white buttons;
tightened type with some hierarchy; **punchier copy**; menu hierarchy (outline on important links);
**matching CTAs** (same label ⇒ same destination); simple load animations; logical top-to-bottom flow.

### Level 3 — Craft (~$6-10k, ~8/10)
Good instincts meet real craft. **Zoom into** the important parts of the dashboard; vertical framing
lines (also aids responsiveness on large screens); **Bento grid**; multi-select / click-through
interactivity; clear hierarchy via colour + size; shorter punchier copy. Designer becomes a
**product designer** — badges, logos, social proof. **Mega menu** for key links; the brand accent
woven back in as the primary CTA with an icon; smoother animations + hover; better page flow.

### Level 4 — Attention to detail (>$10k, ~10/10)
"The difference between good and great is almost never one big thing." Visuals are **crafted** (not
just zoomed) to show exactly what the product does; layout molded into a more interesting shape;
looser type with leading lines into content; copy shifts from **"what it does" → "how it helps"**;
colour threaded throughout. The standout is **motion and detail**: blur effects, a mega menu that
stays open and bumps content left/right, CTAs that appear only on hover, immaculate page flow that
pulls you to keep scrolling. Crucially — **no 3D or custom illustrations needed**, just craft.

### Scoring map
Use these to place a design and name the **next** level's fixes (the point of the ladder is "what to
fix next"). When scoring the 11-dimension rubric (0-3 each, 33 max), map: ≤16 → L1 · 17-24 → L2 ·
25-30 → L3 · 31-33 → L4.

**Scope note:** Kole defined these levels for **landing pages**. For dashboards, mobile apps, or
single components, treat the 33-point rubric score as the primary measure and the level as
indicative — the level *language* (template → identity → craft → detail) still maps cleanly, but the
specific tells (hero layout, mega menu, etc.) are landing-page-flavoured.
