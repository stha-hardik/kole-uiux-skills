# Sources — what this skill is built from

Every criterion traces to a source below. Nothing is invented.

Allowed sources (only these were used):
1. The `Kole UI-UX Resources Form Website/` folder — 20 `.fig` files (his real design work).
2. https://www.kolejain.com/resources
3. https://www.youtube.com/@KoleJain — including transcripts of his top 24 videos
   (`Kole Youtube Trasncript Extract.txt`, supplied by the user).
4. https://www.instagram.com/uiuxdailytips

---

## A. The 20 `.fig` files (read-only, decompressed in a temp folder)
`.fig` = ZIP → kiwi binary (deflate schema block + **zstd** data block). Tokens read directly:
- **Fonts:** DM Sans, Geist, Inter, Manrope, Space Grotesk, SF Pro (modern geometric/neo-grotesque
  sans; no serifs/decorative). Roboto appears mainly as a Figma fallback.
- **Type:** semantic iOS-style scale (Large Title → Caption), Regular + Bold.
- **Color:** systematic tokens (System colours, Label/Primary, Background, Accents) with **Light
  and Dark** sets.
- **Construction:** component sets with variants, auto-layout, one icon library (outline/bold/duotone).
- **Ethos in demo copy:** "do less, better… no bloated dashboards… just the clarity you need."

## B. kolejain.com/resources
"A growing collection of Figma components from my design videos and builds." Resource list = his
curriculum (4 Levels of SaaS, Mobile App UI, Every UI Concept, Software colors, Kill boring designs,
Colors That Ruin, Dashboard UI, Captivating Sections, Microanimations, SaaS Sections, UI Elements, …).

## C. YouTube @KoleJain — transcripts of 24 videos
Bio: "web designer and developer from Canada with 6 years of experience." The transcripts are the
backbone of the rubric and supply the **specific** rules (numbers, do/don'ts, frameworks). Key videos:
- **Every UI/UX Concept Explained in Under 10 Minutes** → the 11-dimension taxonomy + per-concept rules.
- **Why the 60-30-10 Rule is RUINING Your UI Designs** → the **4-layer product colour system**.
- **The 4 Levels of Landing Page UI/UX Design** → the **maturity ladder** (real L1-L4 definitions,
  value/score anchors).
- **The 7 Color Mistakes that RUIN your UI Designs** → neutral balance, semantic colour, grey-over-black.
- **7 UI/UX mistakes that SCREAM you're a beginner** → the beginner-tells checklist.
- **5 SaaS UI/UX mistakes that SCREAM you Vibe Code** → the **AI / vibe-code tells**.
- **How to think like a GENIUS UI/UX designer** → user-intent-first, conventions, content structure,
  progressive disclosure, design systems.
- **Mathematically Perfect Typography** → font pairing limits, ratio scales, line-height rules.
- **The 8 UI/UX Cheat Codes**, **8 Web Design Hacks** → hierarchy via weight+colour, rounded-corner
  math, HSB palette trick, shadow x/y/blur rule, lose-the-lines.
- **11 Micro Animations**, **3 Types of Mobile Swipe Interactions** → easing, micro-interaction patterns.
- **Mobile App UIs**, **Dashboard UI**, **Finance Dashboard redesign**, **macOS like Apple** →
  mobile/dashboard/native specifics, chart rules, optimistic UI.
- **4 UI Hacks to KILL boring designs**, **Truly Captivating UI Sections** → context-not-clutter,
  structure + motion + surprise.
- **Present UIs like a pro**, **Modern UI Layouts from 50 companies**, **Trending sections**,
  **Slept-on trends** → presentation, layout patterns, trends.

## D. Instagram @uiuxdailytips
Confirmed account; post captions weren't machine-readable, so nothing is attributed to Instagram.

## E. Companion: the user's `i-animate` skill (for `references/animation.md` only)
The animation **principles and patterns** in `animation.md` come from Kole's transcripts (11 Micro
Animations, 3 Types of Swipe Interactions, Captivating Sections, Kill boring designs, Think like a
genius). The **executable layer** (duration bands, easing curves, GPU/perf, `prefers-reduced-motion`)
is informed by the user's own `i-animate` skill at `~/.claude/skills/i-animate/`, used at the user's
request. Where the two conflicted (i-animate "avoid bounce" vs Kole's deliberate spring/bounce), the
reference reconciles them rather than overriding Kole.

---

## Honesty note
The earlier version of this eval was limited to video *titles* (transcripts wouldn't extract from the
browser). With the user-supplied transcripts of 24 videos, the rubric now rests on his **actual
spoken rules** plus his real `.fig` tokens — the two strongest possible sources.
