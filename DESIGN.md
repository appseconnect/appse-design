---
version: alpha
name: appse ai
description: >
  Product UI design system for appse ai — the AI & Automation Orchestration platform.
  Brand values come from the appse ai Brand Guidelines (brand-guideline skill, source of truth).
  Values marked "proposed" in the prose are product-UI additions the brand guide does not define;
  they need Designer sign-off before they are treated as final.
colors:
  # Brand core (from brand guidelines — do not change)
  neon-mint: "#00F6A2"
  blue-tint: "#00BAFF"
  electric-blue: "#0100FF"
  bright-purple: "#8951FF"
  deep-violet: "#7A3EF0"
  white: "#FFFFFF"
  # Roles
  primary: "{colors.electric-blue}"
  primary-hover: "#0000CC"
  accent: "{colors.neon-mint}"
  secondary: "{colors.deep-violet}"
  # Neutrals (proposed)
  ink: "#0B0B1F"
  ink-muted: "#4A4A63"
  border: "#E3E3EE"
  surface: "#FFFFFF"
  surface-subtle: "#F6F6FB"
  surface-dark: "#0B0B1F"
  surface-dark-raised: "#16163A"
  # Semantic (proposed)
  success: "#008F5D"
  warning: "#B25E00"
  danger: "#D92D3A"
  info: "{colors.electric-blue}"
  ai: "{colors.deep-violet}"
typography:
  display:
    fontFamily: Funnel Display
    fontSize: 3rem
    fontWeight: 800
    lineHeight: 1.1
    letterSpacing: -0.02em
  h1:
    fontFamily: Funnel Display
    fontSize: 2rem
    fontWeight: 700
    lineHeight: 1.2
  h2:
    fontFamily: Plus Jakarta Sans
    fontSize: 1.5rem
    fontWeight: 700
    lineHeight: 1.3
  h3:
    fontFamily: Plus Jakarta Sans
    fontSize: 1.125rem
    fontWeight: 600
    lineHeight: 1.4
  body-md:
    fontFamily: Plus Jakarta Sans
    fontSize: 0.875rem
    fontWeight: 400
    lineHeight: 1.5
  body-sm:
    fontFamily: Plus Jakarta Sans
    fontSize: 0.8125rem
    fontWeight: 400
    lineHeight: 1.5
  label:
    fontFamily: Plus Jakarta Sans
    fontSize: 0.8125rem
    fontWeight: 600
    lineHeight: 1.2
  code:
    fontFamily: JetBrains Mono
    fontSize: 0.8125rem
    fontWeight: 400
    lineHeight: 1.5
rounded:
  sm: 4px
  md: 8px
  lg: 12px
  pill: 999px
spacing:
  xs: 4px
  sm: 8px
  md: 16px
  lg: 24px
  xl: 32px
  2xl: 48px
components:
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.white}"
    typography: "{typography.label}"
    rounded: "{rounded.md}"
    padding: 8px 16px
    height: 36px
  button-primary-hover:
    backgroundColor: "{colors.primary-hover}"
    textColor: "{colors.white}"
  button-secondary:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.ink}"
    typography: "{typography.label}"
    rounded: "{rounded.md}"
    padding: 8px 16px
    height: 36px
  button-ai:
    backgroundColor: "{colors.ai}"
    textColor: "{colors.white}"
    typography: "{typography.label}"
    rounded: "{rounded.pill}"
    padding: 8px 16px
    height: 36px
  input:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.ink}"
    typography: "{typography.body-md}"
    rounded: "{rounded.md}"
    padding: 8px 12px
    height: 36px
  card:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.ink}"
    rounded: "{rounded.lg}"
    padding: 24px
  badge-status:
    typography: "{typography.label}"
    rounded: "{rounded.pill}"
    padding: 2px 8px
  workflow-node:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.ink}"
    typography: "{typography.body-md}"
    rounded: "{rounded.lg}"
    padding: 12px
    width: 240px
  workflow-node-active:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.ink}"
---

# appse ai — Product Design System

Machine-readable layer of the appse ai brand for **product UI**. Coding and design agents
(Claude Code, Claude Design, Google Stitch, Figma MCP) read this file instead of guessing.
The **brand-guideline** skill stays the source of truth; when the two disagree, the brand
guideline wins and this file is fixed.

Lint before you commit: `npx -p @google/design.md designmd lint DESIGN.md`

## Overview

Enterprise-grade, AI-native, calm. Brand marketing is loud — vibrant gradients, starbursts,
white display type. The **product** is where people spend eight hours building and debugging
workflows, so the product uses brand energy as **accent, not wallpaper**.

- **Strategy & Stability** → predictable layouts, dense but legible data, no surprise motion.
- **Innovation & Creativity** → AI moments get the brand's violet and the 4-point sparkle.
- **Quality & Perseverance** → every screen designs its empty, loading, error and partial states.

Always write **appse ai** — lowercase, with a space — in UI copy, titles and alt text.

## Colors

- **Primary — Electric Blue `#0100FF`**: primary buttons, links, focus rings, selected nav.
  Passes WCAG AA as text on white.
- **Accent — Neon Mint `#00F6A2`**: active and live states, run-in-progress pulse, highlights.
  **Never use it as text on white, and never put white text on it.** Fails contrast. On mint, use
  `ink` text; on dark surfaces mint can be text.
- **AI — Deep Violet `#7A3EF0`**: anything the AI generated or is doing — agent steps,
  suggestions, the "Generate with AI" action. The user must always be able to tell AI output from
  their own input.
- **Bright Purple, Blue Tint**: gradients and illustrations only, never UI controls.
- **Gradients**: use the brand gradients only on hero, onboarding, empty-state illustration and
  marketing surfaces. **No gradients on data tables, forms or the workflow canvas.**
- **Neutrals and semantic colors are proposed**, not from the brand guide. Success, warning
  and danger are picked for AA contrast as text on white. Never signal status by color alone. Add
  an icon and a label.
- Dark theme uses `surface-dark` / `surface-dark-raised`. Brand colors keep their values, and
  text becomes `white`.

## Typography

- **Funnel Display** for `display` and `h1` only: page titles, onboarding and empty-state
  headlines. Bold or ExtraBold. ALL CAPS only for taglines and brand pillars, never for UI.
- **Plus Jakarta Sans** for everything else: 400 body, 600 labels and emphasis, 700 hierarchy.
- **JetBrains Mono** (proposed) for code, JSON payloads, expressions and IDs in run logs.
- Base product size is 14px (`body-md`). Enterprise screens are dense, so keep body text at 13px
  or larger.

## Layout

- 4px base grid. Use `spacing` tokens only, with no one-off values.
- App shell: left nav at 240px (64px when collapsed), top bar at 56px, content at max width
  1440px with `lg` gutters.
- Workflow builder: full-bleed canvas, a 360px properties panel on the right and a run log at the
  bottom that can be resized.
- Must work from 1280px desktop down to 1024px laptop. Mobile is read-only (run status, approvals).

## Elevation & Depth

- Flat by default. Separate with 1px `border` and `surface-subtle`, not shadows.
- Shadows only for overlays: menus and popovers (small), dialogs and drawers (large).
- The brand's "glow" is reserved for the live or running state on workflow nodes, as a soft Neon
  Mint outer glow.

## Shapes

- Radius: `md` on controls, `lg` on cards, panels and workflow nodes, `pill` on status badges and
  AI actions.
- **4-point sparkle** is the only icon for AI actions and AI-generated content.
- Starbursts, semicircle patterns and waves are for empty states and onboarding illustration
  only. Never put them behind data.

## Components

Build on shadcn/ui primitives, styled with these tokens. Don't fork components.

- **Buttons**: one primary per view. `button-ai` (violet pill + sparkle) for AI actions only.
- **Status badge**: Running uses the mint pulse, Succeeded uses `success`, Failed uses `danger`,
  Waiting for approval uses `warning`, Queued uses `ink-muted`. Each always has an icon and a
  label.
- **Workflow node**: app icon (partner logo unaltered), operation name and a status dot. Active
  adds the mint glow, and an error adds a `danger` border plus an inline reason.
- **Tables**: sticky header, row hover is `surface-subtle`, numbers are right-aligned, IDs use
  mono.
- **Partner marks** (SAP, Microsoft, Google, AWS and others): use the official asset unaltered.
  Never recolor or tint them.

## AI & Agent Patterns

appse ai is AI-native, so these states are part of every AI feature:

- **Thinking / working**: show which step the AI is on. Don't use a bare spinner.
- **Tool calls**: show which app and operation is being called, with collapsible input and
  output.
- **Human approval**: a clear approve or reject card with what will happen, and who and when.
- **Explain**: every AI-generated workflow or field mapping has a "why" the user can open.
- **Undo**: a user can revert any AI change in one step.
- **Confidence and limits**: say when the AI is unsure. Never present a guess as fact.

## Accessibility

- WCAG 2.2 AA minimum: 4.5:1 for text, 3:1 for UI and focus indicators.
- Visible 2px `primary` focus ring on every interactive element.
- Everything works by keyboard, including adding nodes and moving through the workflow canvas.
- Respect `prefers-reduced-motion`, so the mint pulse becomes a static dot.

## Do's and Don'ts

**Do**
- Use Electric Blue for primary action and Deep Violet for AI.
- Design empty, loading, error, partial and no-permission states for every screen.
- Write **appse ai** lowercase with a space.

**Don't**
- Put white text on Neon Mint, or mint text on white.
- Put gradients or brand shapes behind tables, forms or the canvas.
- Alter partner logos.
- Show PII in mockups. Use synthetic data.
- Promise roadmap features in UI copy.
