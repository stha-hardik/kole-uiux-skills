# Kole's principles — detailed reference

Specific, sourced rules behind each rubric dimension. Drawn from 24 transcripts (see
`../SOURCES.md`). Quotes are paraphrased unless in "quotes". Use these to make reviews
concrete instead of generic. Color and the 4 maturity levels have their own file:
`color-and-levels.md`.

---

## 1. Affordances & Signifiers
- The UI should explain itself with **no instructions**. A container around items signifies
  grouping or selection; greyed-out signifies inactive/disabled.
- "Good UI has many signifiers": button press states, highlighted active nav items, hover
  states, tooltips. If a user can't tell what's clickable or what state something is in, it fails.
- **Mutually-exclusive options = ONE container (a segmented control), not detached pills.** A
  single-select filter/toggle (e.g. All / 1 month / 3 months / 6 months / 1 year) belongs inside one
  track, with the active option as a pill *inside* it — this is exactly Kole's Drinks/Food/Dessert
  toggle. Separate free-floating pills with gaps between them ("gap holes") lose the signified meaning
  that these are one control and one is selected, and look unanchored. Wrap the set in a single
  rounded container with a subtle background; the selected segment gets the solid pill.
  (Multi-select *tags* can stay as separate chips — the container rule is for pick-one sets.)
- **Group related controls; don't leave islands.** When related items sit as separate elements with
  random gaps, either group them in one container (like the segmented control above) or tighten them
  with proximity. Gaps should read as deliberate grouping, not leftover space. (Balance with "fewer
  containers" — group pick-one/related controls, but don't double-nest or box everything.)

## 2. Visual Hierarchy
- Three tools: **size, position, color**. Hierarchy comes from *contrast* (big vs small,
  colorful vs not), not size alone.
- Most important = larger, bolder, nearer the top. Images add a colour pop and make scanning
  easy. Price often top-right and coloured so it stands out.
- Convey meaning without words: icons + alignment (e.g. "from → to") instead of labels.
- Hack: use **font weight and font colour** for hierarchy, not just size. Max **two weights**
  (separated by at least one step) and **two colours** (primary + the same colour at 40-70%
  opacity). Avoid ultra-bold/ultra-thin for regular text.

## 3. Grids, Layouts & Spacing
- Grids are **guidelines, not law**. 12-col isn't mandatory; landing pages often don't align.
  Grids matter most for repeating content (galleries, blogs) and for responsive behaviour
  (≈12 / 8 / 4 columns on desktop / tablet / mobile).
- **White space beats excessive grids** — "let things breathe."
- **4-point (or 8-point) base grid**: everything a multiple, so you can always split in half →
  consistency. Set Figma's nudge to 8. For large sizes round to nearest 5/10 (120 vs 128
  doesn't matter); keep small elements strictly on the grid.
- Default rhythm ~**32px between items**; group related items closer (proximity = relationship).
- "Fewer containers and fewer lines." Don't **double-nest cards** (padding-on-padding cramps
  content) — group with white space instead. Removing dividers/cards lets layouts breathe.
- **Consistency:** pick one corner radius and reuse it (e.g. 10px for small elements); two controls
  that do the same thing must look identical. Use styles for colours, variables for measurements,
  components for repeated elements.
- **Nested corners:** when a rounded element sits inside another, **inner radius = outer radius − gap**
  (outer 30px, gap 10px → inner 20px). Don't make both equal — it looks off. Pill shapes need no fix.

## 4. Typography & Font Sizing
- "You'll never need more than **one** font." Pick a good sans-serif and stick to it. Two is
  fine (display+sans, or serif+sans); three is pushing it; four "is asking for problems."
- **Design sin:** a display or handwritten font used for paragraph/small text.
- Large text (>~70-80px): tighten letter-spacing to **−2% to −4%** and line-height to
  **110-120%** — instantly looks pro.
- Line-height rule of thumb: **body ~150%, headings ~110-130%.**
- Size counts: landing pages **≤6 font sizes** with a large range; dashboards a much smaller
  range, **rarely >24px** (higher information density).
- Type scale by ratio off a 16px base: golden ratio **1.618** (simple heading/body),
  **1.27** (√golden, full scale), or cube-root (dense UIs / mobile).
- Mobile text is **similar or larger** than desktop, not smaller (iOS base 17px, macOS 13px).
- Display fonts can be a *visual element* (giant text) but only **once or twice per page**.

## 5. Color Theory
See `color-and-levels.md` for the full 4-layer product color system. Headlines:
- **Less is more.** Reducing the palette creates clarity; multiple accent colours compete.
- "Use colour for **purpose, not decoration**." Icons mostly need **no colour** — reserve
  colour for status/meaning (active tab, etc.).
- Semantic colours: **blue = trust, red = danger/urgency, yellow = warning, green = success.**
  Destructive actions are **red, never the brand colour** (a "design sin"), which is why red/green
  live in palettes even when off-brand.
- **Neutral balance:** backgrounds stay in the background — almost never bright. Start neutral
  grey bg + light/white foreground; add a *hint* of brand hue into the neutral. Define edges with
  ~85% white borders, **not thin black borders**. Sometimes the best background is none (a border).
- **Muted/off colours are your friend** (baby blue, beige, lavender). Off-whites in light mode and
  bluish-blacks in dark mode signal experience. Prefer **grey over pure black/white** for most text.
- 60-30-10 is fine for beginners/landing pages but doesn't cover product design — use the
  4-layer system instead.

## 6. Dark Mode
- **Not the inverse of light mode** — inverting makes contrast too high and looks off.
- No shadows in dark mode → create depth with **surfaces that get lighter as they elevate**
  (lighter cards than background), or borders.
- Dark colours need **more distance** to read as different — roughly **double** the gap between
  neutrals (light ~2% steps → dark ~4-6%).
- Light greys are easier on the eyes than pure white; reserve pure white for the most important
  text/actions. Dim/desaturate bright chips and logos.
- Plenty of room for deep purples/reds/greens, not just navy/grey.

## 7. Shadows
- **"If the shadow is the first thing you notice, you're not using it right."**
- Figma default shadows are too harsh. Fix: drop opacity (25% → **15-20%**) **and** raise blur;
  often change the shadow **colour to a light grey**; or remove it entirely.
- Strength scales with elevation: cards need less, popovers/overlays need more; darker
  backgrounds need stronger shadows.
- Rule of thumb: **x ≤ y**, and **blur = 1.3-2× y**. Inner+outer shadows make raised tactile buttons.
- If a gradient or shadow isn't working, **just remove it** — often looks more professional.
- **Gradients:** keep to one colour family (a lighter/darker shade of the same hue), never two
  unrelated hues (e.g. blue→green); most of the time none at all is cleaner.

## 8. Icons & Buttons
- Icons are usually **too large**: match icon size to the font's line-height (e.g. 24px), then
  tighten the text.
- **One icon library**, consistent fill / stroke-width / style (Feather, Phosphor, Lucide,
  Flaticon sorted by stroke+corner; grab SVG). Simpler is better; bigger icon → more detail.
  Mixing icon styles is OK **only** if they're in visually separate areas/functions.
- Icon-only is fine for well-known icons (house, bookmark, user); otherwise add a tooltip.
- **Buttons:** ghost buttons have no background until hover. Padding guideline: **width = 2× height.**
  Only **one primary CTA per header section**; secondary = outline / no background / reduced opacity.
- **Chips ≠ buttons:** chips are never the primary-CTA colour and are always thinner vertically;
  use auto-layout with vertical padding = **¼ to ½** of horizontal padding.
- **Button states:** at least four — default, hover, active/pressed, disabled (+ loading).
  Hover = lighter/brighter base; active = darker; disabled = desaturate. Mobile has no hover —
  use a slightly darker press state.

### Sourcing one free icon family (executable — fixes mismatched icons)
The reliable way to guarantee same-family icons (no mismatched arrow vs gear): standardise on **one
free, open-source icon package** and pull *every* icon from it — never hand-code an inline SVG or grab
one icon from a different set. All of these are free (MIT) and have the icons a dashboard needs:
- **Best default for code (React): Lucide** — `npm i lucide-react`, ~1500 icons, uniform 24px / 2px
  stroke. `import { Send, ArrowRight, Settings, MoreVertical } from "lucide-react"`.
- **Alternatives (free):** Phosphor (`@phosphor-icons/react` — pick ONE weight), Heroicons
  (`@heroicons/react` — outline *or* solid, not both), Tabler (`@tabler/icons-react`), Feather.
- **Figma / no-code:** the Lucide or Phosphor Figma plugin; export **SVG**. (Flaticon works too —
  sort by stroke + corner so the set matches.)
- **Rule:** one package, one weight/style, one default size (≈ the text line-height) and one stroke
  width across the whole app. If the Send arrow and the Settings gear don't visually match, they're
  from different sources — swap **both** to the same package (`Send`/`ArrowRight` + `Settings`).
- **Prompt cue to give an AI build:** *"Use lucide-react for ALL icons — no emojis, no inline
  hand-drawn SVGs, no other icon sets; import each icon by name from lucide-react."*

## 9. Feedback & States
- **"When a user does anything, there should be a response."**
- Inputs need a **focus** state, **error** (red border + message), sometimes **warning**.
  Provide **loading** spinners, **success** messages, and **empty** states everywhere.
- Acknowledge instantly: grey out a button on click while the next screen loads (a split-second
  delay otherwise feels like the click didn't register); fill a save icon + add a red dot to the
  save tab.
- **Optimistic UI:** assume the server request succeeds and update immediately (Gmail delete,
  Apple Mail) so there are no awkward pauses.

## 10. Micro Interactions
- A form of feedback that "steps it up" — confirm an action (copy → a chip slides up). Range from
  practical to playful.
- **Easing matters most:** "almost never want a linear ease." Real things speed up and slow down;
  bounce/curve gives tone (snappy, springy, smooth). Example settings: 500ms, stiffness 636,
  damping 24; tooltips reveal after a **1000ms** hover delay.
- Buttons should almost always have a small animation; **scroll-jacking sparingly, if ever.**
- **Don't animate everything** — it feels slow and unserious. Motion supports clarity, not distraction.

## 11. Overlays
- **Popover:** simple, non-blocking context (click away freely). **Modal:** complex but stays on
  page, blocking (must confirm/cancel) → pair with a **toast** to confirm the change. **Toast:**
  notify/prompt without taking over the screen — great for warnings/errors. **New page:** large or
  permanent context → must have back button / breadcrumb. **Bottom sheet** (mobile): keeps context,
  gesture-friendly.
- **Image overlays:** don't dump a full-screen scrim — use a **linear gradient** from the image
  into a readable background, optionally a **progressive blur** on top for a modern look.

---

## Cross-cutting principles (recur across many videos)

- **User-intent first ("think like a genius"):** start from what the user is trying to do, not
  aesthetics. Web design is "a story, not art." Fonts/colours/icons change the look but not the
  function — only expand functionality as user intent expands. If the goal is to guide to an
  action, flair just gets in the way.
- **Leverage conventions:** after 30+ years of the web, users expect nav at top, flow top→bottom
  and left→right, eye-catching CTAs. Respect expectations, then make it uniquely yours with one
  considered micro-interaction or feature — that's what separates good from genius.
- **Content structure & edge cases:** decide *what* content to show (driven by how the user
  interacts), then structure it. Test with **real/edge content** — long names (truncate), bright
  images (add a circle behind icons for contrast). "Perfect content" hides problems.
- **Progressive disclosure:** show only what's needed, reveal more on demand. Collapse advanced
  options by default. **Load-more beats infinite scroll** (user control + reachable footer).
- **Design systems:** styles for colours, variables for measurements, components for elements.
  Match the team's needs (lean startup = lightweight; Material = massive). A shared language —
  break rules with intention, not by accident.
- **Context, not clutter / kill boring:** elements that add *context* (meaningful imagery, data)
  are good; elements that just decorate are clutter. Removing things can make a page feel empty
  rather than clearer. Captivating = Structure (effortless, guides the eye in a 5-sec scan) +
  Motion (the right kind, introduces the product) + **Surprise (break the pattern once)**.
  Captivating ≠ chaotic. Prefer friendly, natural copy over corporate jargon.

## Charts (a recurring Kole pet-peeve)
Charts must be **simple, informative, and aesthetic**. Always include axis labels, gridlines, and
a time/range selector. **Never:** curve the data line, fade out the data line, round bar tops (you
can't tell where the bar ends), add decorative bars with no meaning, or show more bars than data
points. For multi-series colour, use an **OKLCH** palette for equal perceived brightness. Include a
brief title/summary and favicons/labels per series when comparing items. For income vs expenses use a
**two-sided bar chart** (bars up = income, down = expenses).

## Mobile specifics
Bottom bar 3-4 links ideal (5 max); **44px** minimum touch target. One direction of content flow
per section. Four building blocks: cards, text/links, images, inputs (don't double-nest cards).
**One screen, one job** — new need → new page, not a busier layout. Bottom sheets keep context.
Gestures: swipe-back (move bg ~35%), long-press = right-click (blur + slight zoom), swipe to
dismiss. Actions appear/disappear contextually. Design **empty states** (first-run *and* no-results).
**Bottom navbar:** the active icon must clearly stand out (brand colour / stronger fill) while
inactive icons stay visible but de-prioritised — never make them so low-contrast you can't tell them
apart. Labels optional for well-known icons; spread icons slightly apart to enlarge the tap area.

## Dashboard specifics
Sidebar = the "spine": group nav links, push settings/help to the bottom, give an active-state
indicator, make it collapsible. Dashboards use smaller fonts, tighter spacing, and **stricter
grids** than landing pages. The main area reflects what's most important to the user; keep data
simple. List separation, best→worst: **space > dividers > colour**. Tables need search/filter/sort.
Four reusable components: lists/tables, cards, inputs, tabs. Use bulk actions on multi-select and
**optimistic UI** for a snappy feel. (Plus the chart rules above.)
**Widget priority = a tier list:** arrange by importance, **high → top-left, mid → middle, low →
bottom-right** (priority flows top-to-bottom, left-to-right). The most important widget is the first
thing seen without scrolling; don't mix priority levels randomly.

## Dense rows & list items (the "breathe + ⋯ menu" recipe)
When a row or card crams in too much — a truncated title, wrapping subtext, a date, chips, and 2+
buttons all on one line (a very common AI output) — apply Kole's de-clutter recipe:
- **Let it breathe:** add vertical padding, give the title room (don't crush it to "Member v80…"),
  let content set the height instead of squeezing one line.
- **One primary action visible** (e.g. *Send*); **collapse the secondary actions into a ⋯ (kebab /
  triple-dot) overflow menu** ("Mark reached out", etc.). Align the primary action to the right.
- **Turn wordy secondary controls into icons or chips**, and group the meta (date, tier chip) so it
  reads as one cluster, not four competing items.
This is the same move Kole makes on cramped cards: "collapse these buttons into a triple-dot menu,
move the date to the centre, collapse chips to icons, move the primary to the right."
*Implementation:* the ⋯ menu must render **above** the row/card (portal / z-index) — don't let
`overflow: hidden` clip it, or you've hidden the action you just moved there.

## Expected structure by surface type (use in the Step 0 architecture pass)
Before scoring, check whether the screen *contains and is organised into* the structure Kole uses for
its type. Missing structure is a finding — recommend adding/splitting it, don't just restyle.

**Host context first:** if the app is *embedded in a host* (a Whop app, a Shopify app, a browser-
extension panel, an iframe widget), the host already provides the outer nav/sidebar — **do not
recommend adding one.** Judge it as the embedded-utility type below.

- **Landing page** — hero (stacked, real product visual, punchy headline) → logos / social proof →
  feature sections (clickable multi-section, bento, or straight-line grid) → CTA → a small footer
  (3-5 links centred; not a giant 23-link footer). Flow should pull you to keep scrolling.
- **Dashboard** — sidebar spine (grouped nav, settings/help at bottom, active state, collapsible) +
  top bar for page actions + a main area showing what matters most to the user. Built from the 4
  components (lists/tables, cards, inputs, tabs). Include empty states, bulk actions, toasts.
- **Settings** — **never one flat list.** Decompose into grouped sections, and use **tabs or panels**
  to split categories ("tabs add pages without cluttering the sidebar"); rarely-used items to the
  bottom. Notion-style settings = lists + inputs + cards, often inside a modal or its own section.
  *If a settings screen is an undifferentiated list, the fix is to split it into grouped panels/tabs.*
- **Mobile app** — bottom bar (3-4, 44px) or nav-as-home-page; **one screen, one job**; bottom sheets
  for in-context actions; gestures; empty states (first-run *and* no-results).
- **Pricing** — 3-4 plans (not 5+); each with a name + short description; monthly cost prominent;
  checkmarks; show what the *next* plan adds; separate price from the feature list.
- **Form / signup modal** — labels **above** inputs (always visible), real placeholder examples, a
  subheading, a link to the alternate action (e.g. log in), 4px grid, off-white input bg + reduced-
  opacity stroke.
- **Native desktop (macOS) app** — "an app is a system": top global actions / sidebar nav / centre
  content; respect OS light+dark; prominent search; keyboard-first with visible feedback; drag-and-
  drop; onboarding; progressive disclosure via empty states.
- **Navigation menus** — when link names aren't self-explanatory (product/service/feature
  categories), add a small **thumbnail/image beside each link** (mega-menu) so users see what
  they're clicking before they click.
- **Embedded / single-purpose utility app** (e.g. a Whop app) — **one job, done well.** The host
  frame supplies global nav, so there's no app sidebar. Lead with the single primary action and the
  core list; **resist padding the top with a row of mostly-zero KPIs** (an AI reflex — keep only the
  1-2 stats that matter); design empty / first-run / no-results states; add **bulk actions**
  (multi-select) as the list grows. Settings sit behind one button and open grouped sections.

## AI / "vibe-code" tells — high-value for reviewing AI-generated designs
Things that instantly reveal an AI/vibe-coded UI, and the fixes:
- **Emojis** as icons → swap to a real interface icon set (Phosphor/Lucide).
- **AI-chosen colours** ("never let an AI choose your colours") — always too bright and clashing →
  refine toward neutrals + one disciplined accent; nudge hues (e.g. purple→more blue), darken bg.
- **Repeated KPI rows** (same four KPIs appearing 2-3×) → consolidate; show data via charts/icons.
- **Same colour for every status** (e.g. Gantt bars / task lists all rendered in the "completed"
  colour) → colour must encode state (completed vs in-progress); prefer a % number over a vague label.
- **Chips/badges that fail contrast** (bright pill + white text) → audit every small coloured
  element; darken the fill or use dark text so it passes WCAG.
- **Gradient circle avatars with initials** → real account card.
- **Sparse modals/flyouts** with lots of wasted space → use a proper modal, add the missing fields.
- **Cards/elements that do nothing** → delete them.
- **Too many pricing plans** (5+) → cut to 3-4; emphasise monthly cost, show what the next plan adds.
- **Generic AI layouts** — AI is good at logic/setup when instructed but bad at complex layouts and
  cards, so that's where a human adds the most value (tighten spacing, collapse to popovers/menus).

When **generating** a UI with AI (Co-build): reference a **clean real-product screenshot** (e.g.
Linear, siteinspire.com), not a busy Dribbble shot the model can't parse; and tell it to use a real
icon library, no emojis. After generating/importing, the three things to fix first are **fonts,
alignment, and colour**. Finally, **review at the real size on the target device** (mirror on mobile,
100% on desktop; the browser bar eats space) — don't judge a design zoomed out.
