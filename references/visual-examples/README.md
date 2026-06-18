# Visual examples — what "Kole-grade" looks like

These are the **embedded Figma thumbnails** extracted from Kole's own `.fig` files (real renders, one
cover per file). They are **low-resolution** — good for judging *composition, structure, restraint,
colour balance, light/dark feel*, not pixel-level detail. Use them as the visual bar during the
**self-check** (see `SKILL.md` → "Look before you ship"): does my screen feel like these?

> Fidelity note: I cannot *render* the vector canvas to a PNG (only Figma can). But the `.fig` files
> also embed **full-resolution raster images** that Kole dropped in, and some are crisp UI screens —
> those are the best references. They're hit-or-miss per file (redesign/mockup files have them;
> pure-vector files don't), and mixed with photos/logos/illustrations, so they need curating by eye.

## Project preview frames — PRIMARY references (full HD, from kolejain.com/resources)
`projects/<Project>/` holds the 1920×1080 preview slides Kole publishes for each resource — composed
by him, crisp, each illustrating a pattern. **Prefer these over everything below.** Retire the
matching low-res `.fig` thumbnail once a project's frames are here.

10 projects (61 frames):
- **`projects/4 Level of SaaS/`** — the L1→L4 landing maturity ladder (Linkd): dark hero, one blue
  accent, floating analytics cards, donut + funnel charts with context.
- **`projects/AI Startup/`** — AI product UI: dark dashboards, modals, pricing/usage breakdowns, code blocks.
- **`projects/Captivating Sections/`** — landing section patterns: clean hero, component cards, restraint.
- **`projects/Every UI Concept/`** — the 11 concepts: hierarchy, the **Drinks/Food/Dessert segmented
  control**, colour theming (one product card in multiple hues w/ matching accent CTA), animated narrative.
- **`projects/Mobile App UI/`** — mobile: dashboards, calendar/tasks, **long-press menu w/ blur +
  semantic red Delete**, bottom sheets, dark surfaces.
- **`projects/Sidebar Tutorial/`** — sidebar spine + command-palette/quick-actions modal (icon grid),
  integration connect cards, settings page.
- **`projects/Skill For 2026/`** — outreach app: dashboards, template-picker modal, create/recipient forms.
- **`projects/Software Colour/`** — the **4-layer colour system**: the same dashboard in light / dark /
  themed variants, charts.
- **`projects/UI Elements/`** — component library: pricing cards, stickers, signup forms, navbars,
  footers, carousels, chart cards.
- **`projects/Vibe Coded SaaS/`** — AI/vibe-coded UI cleaned up: dashboards with charts, maps, tables, sidebar.

*To add a new project: drop a `projects/<Project>/` folder of frames in — it slots straight in.*

## High-res UI references (curated from embedded `.fig` assets) — secondary set
Crisp, full-resolution screens Kole embedded in his files. Curated from 287 embedded images (137
were ≥500px wide); the rest were brand logos (Figma, Notion, Stripe, Deel, Slack…), stock photos,
and decorative illustrations — all discarded. This set is deliberately tight and non-redundant,
covering light/dark × dashboard/table/notes/modal:

| File | Shows | Use it to judge |
|---|---|---|
| `hires_pm-app-light.png` | Linear-style project app, light: sidebar spine (grouped nav + cycles), issue list, right detail panel with a progress chart, green accent, tabs. | Dashboard structure, sidebar spine, restraint, one accent |
| `hires_financial-dashboard.png` | Full finance dashboard, light: card grid, ONE coral accent, charts with context. | Dashboard density, charts done right, single accent |
| `hires_link-modal-darkmode.png` | Dark form modal: breathing room, labeled inputs w/ help icons, **ghost** secondary buttons vs ONE primary "Create Link", one green accent, same-family icons. | Forms/modals, button hierarchy, dark mode, breathing room |
| `hires_expense-tracker-dark.png` | Dark data table / expense tracker. | Tables, dark-mode surfaces, data density |
| `hires_notes-dark.png` | Dark content/notes screen: clear hierarchy, semantic link colour, highlighted field, tabbed footer. | Content layout, hierarchy, dark mode, one-screen-one-job |

*To add more later: harvest embedded assets from any `.fig` (`unzip "<file>.fig" "images/*"`), but
expect ~half to be logos/photos/illustrations — keep only composed UI screens/components.*

## Reference thumbnails (Kole's real work)
| File | Best shows |
|---|---|
| `4 levels.png` | The 4 maturity levels (template → crafted) on one landing page |
| `Beginner UI.png` | Before/after of beginner fixes: user flow, spacing, icons, states |
| `Colors That Ruin.png` | Colour discipline — neutral balance, restrained palette |
| `Dashboard UI.png` | Dashboard structure: sidebar spine + the 4 components |
| `Financial Dashboard.png` | Dashboard redesign: sidebar, card grid, ONE accent, charts with context |
| `Micro Dashboard.png` | Compact dashboard density |
| `Software Sections.png` | SaaS landing sections (logos, bento, multi-section) |
| `Software colors.png` | The 4-layer product colour system in practice |
| `Mobile App UI.png` | Mobile patterns: bottom bar, one-screen-one-job, bottom sheets |
| `Swipe Anims.png` | Mobile swipe interactions / easing |
| `Micro-Animations.png` | Micro-interactions & feedback |
| `UI Elements.png` | Component upgrades: navbar, cards, pricing, chips, footers |
| `Sidebar Tutorial.png` | The sidebar-spine pattern |
| `Skincare Redesign.png` | Redesign method; light, restrained, one accent |
| `Kill boring designs.png` | Context-not-clutter / captivating sections |
| `Every UI Concept-1.png` | The 11 core concepts illustrated |
| `Present like a pro.png` | Presentation / showcase techniques |
| `Design 2025.png` | Current trend aesthetic |
| `Vibe Coded SaaS.png` | Fixing an AI/vibe-coded SaaS UI |
| `Vibe Coding Results.png` | AI-generated UI cleaned up in Figma |

## Annotated good/bad pairs (add images here)
The highest-value teaching images are *side-by-side good vs bad* for the patterns text struggles with.
Drop images in this folder and caption them here as we collect them:
- `segmented-control_good-vs-bad.png` — one grouped track (good) vs detached floating pills (bad).
- `icon-family_good-vs-bad.png` — all icons from one set/weight (good) vs mismatched arrow + gear (bad).
- `row-density_good-vs-bad.png` — breathing row with one primary + ⋯ menu (good) vs cramped row (bad).

*(Pending: user-supplied reference shots — e.g. Kole's Drinks/Food/Dessert segmented toggle, and the
Milestones filter before/after.)*
