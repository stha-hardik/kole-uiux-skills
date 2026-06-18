# Animation & motion — detailed reference

Kole has no still-image references for motion, so this file is the animation bar. It combines **Kole's
animation philosophy** (from his "11 Micro Animations", "3 Types of Mobile Swipe Interactions",
"Captivating Sections", "Kill boring designs", "Think like a genius" transcripts — see `../SOURCES.md`)
with an **executable implementation layer**. For deep implementation, the user's **`i-animate`** skill
is a companion (durations, easing, performance, accessibility) — invoke it when building complex motion.

## Kole's motion philosophy (the principles)
- **Purpose over decoration.** Animation must *confirm an action, smooth a transition, guide attention,
  or reveal progressively.* "Motion should support clarity, not distract from it." If motion is the
  first thing you notice, it's too much.
- **Don't animate everything.** Over-animation feels slow and unserious. Pick **one hero/signature
  moment**; everything else is quiet micro-feedback.
- **Easing is almost never linear.** Real things accelerate and decelerate. The curve sets the tone
  (snappy, springy, smooth). Kole *deliberately uses spring/bounce* for natural mobile motion (his
  example: smart-animate, ~500ms, **stiffness 636 / damping 24**).
- **Functional motion** (from "genius"): a nav that consolidates into an animated menu, a search bar
  that expands on click, progressive disclosure (load-more > infinite scroll). Buttons should almost
  always have a small animation; **scroll-jacking sparingly, if ever.**
- **Delight, not utility** (from "kill boring"): entrances with personality (rotate+pop, fly-in, gentle
  bob), parallax on scroll, **animated narratives** (e.g. the word "deadlines" morphs into a filling
  progress bar) — while keeping spacing intact so elements stay context, not clutter.
- **Captivating = structure + motion + one surprise.** Motion introduces the product; break the
  pattern *once* (an unexpected hover/reveal), not constantly.
- **Optimistic UI.** Update instantly on action (then reconcile) so nothing feels laggy.

## Kole's specific micro-interaction patterns (from "11 Micro Animations")
Button hover (text slides up / scale-down on press) · toast that slides up to confirm (loading →
celebratory success) · name tag pop on avatar hover · shimmer/gradient stroke · **tooltips after a
~1000ms hover delay** · text hover pop-out (preview image) · progress bars that draw in · stacked
card swipe (cards behind scale up + shift as the top one leaves) · search-bar expansion from the
magnifying-glass icon · hover-to-reveal upgrade details.

## Kole's swipe/gesture patterns (mobile, from "3 Types of Swipe Interactions")
- **Within-page:** scrolling cards with bounce; skew them into a 3D ring; circular swipe; fluid
  "magnetic" page indicators.
- **Between-page:** the tapped card expands to fill the screen while the new content fades up, finished
  with an **elastic snap** — motion follows the swipe direction.
- **Gestures:** swipe-back moves the background ~35%; long-press blurs the rest + slight zoom on the
  element; swipe-down to dismiss sheets (background zooms out then back); **slide-to-confirm** for
  high-impact/irreversible actions (buy, send) — harder to trigger by accident than a button.

## Executable layer (implementation)
**Durations by purpose:** 100-150ms instant feedback (press/toggle) · 200-300ms state change
(hover/menu) · 300-500ms layout (accordion/modal) · 500-800ms entrance (page load). **Exit ≈ 75% of
enter.**

**Easing — default to smooth deceleration:**
```css
--ease-out-quart: cubic-bezier(0.25, 1, 0.5, 1);
--ease-out-quint: cubic-bezier(0.22, 1, 0.36, 1);
--ease-out-expo:  cubic-bezier(0.16, 1, 0.3, 1);
```
**Spring/bounce — reconciling Kole with the i-animate "avoid bounce" rule:** use a *measured* spring
(Kole's ~stiffness 636 / damping 24, or Framer Motion `type:"spring"`) for **mobile gestures, draggable
/ stacked cards, and signature delight moments** — that's the "natural bounce" Kole wants. **Do not**
put spring on routine state changes, and never use cheesy over-shoot *elastic* easing — that's the
dated look i-animate warns against. So: smooth ease-out is the default; spring is a deliberate tool for
gesture-driven and playful moments, not everywhere.

**Tech:** CSS `transition`/`@keyframes` for simple, **`transform` + `opacity` only** (GPU); Web
Animations API or **Framer Motion** (React) / **GSAP** for complex sequences. `will-change` sparingly.
Target **60fps**.

**Accessibility (mandatory):** honour `prefers-reduced-motion` — provide a reduced/!important-off path.
```css
@media (prefers-reduced-motion: reduce){ *{animation-duration:.01ms!important;transition-duration:.01ms!important} }
```

## Never
Animate layout props (width/height/top/left) — use transform · durations >500ms for feedback ·
motion with no purpose · animate everything · block interaction during animation (unless intentional) ·
ignore reduced-motion · let an entrance/elastic effect become the thing you notice.
