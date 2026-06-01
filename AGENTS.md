# AGENTS.md — Frontend Design Rules

This document instructs AI agents (Claude, Cursor, Copilot, etc.) when generating frontend code.
Goal: avoid interfaces that look "AI-made" — generic, industrial, soulless.

---

## Core Principle

Before writing a single line of code, commit to a **clear aesthetic direction**.
Do not play it safe. Pick a direction and push it all the way.

Ask yourself first:
- Who is this interface for? What is the emotional tone?
- What makes this UI **unforgettable**?
- If you remove the logo, would someone still recognize the brand?

---

## Typography

- **NEVER** use: Inter, Roboto, Arial, system-ui, or default sans-serif
- **DO** use fonts with distinct personality suited to the context
- Pair fonts intentionally: one strong display font + one refined body font
- Consider: DM Serif Display, Playfair Display, Syne, Instrument Serif, Cabinet Grotesk, Chillax, Unbounded, Fraunces, Switzer

```css
/* Example — editorial feel */
--font-display: 'Fraunces', serif;
--font-body: 'Switzer', sans-serif;

/* Example — tech with soul */
--font-display: 'Syne', sans-serif;
--font-body: 'DM Sans', sans-serif;
```

---

## Color

- **NEVER** use: purple gradient on white, default blue #3B82F6, light gray cards #F3F4F6
- **DO** choose an intentional palette: one dominant color + 1–2 sharp accents
- Use CSS variables for consistency across the entire project

```css
/* Example — dark editorial */
--color-bg:      #0E0E0E;
--color-surface: #1A1A1A;
--color-primary: #E8D5B0;
--color-accent:  #C94A2B;
--color-text:    #F0EDE6;

/* Example — light luxury */
--color-bg:      #FAF7F2;
--color-surface: #FFFFFF;
--color-primary: #1C1C1C;
--color-accent:  #B5936A;
--color-text:    #2E2E2E;
```

---

## Layout & Spatial Composition

- **NEVER** use: three equal-width cards, centered hero + sections + footer pattern
- **DO** try: asymmetry, overlapping elements, grid-breaking, diagonal flow, intentional white space
- Negative space is design — not leftover emptiness
- One unexpected layout beats ten safe, pretty ones

---

## Motion & Interaction

- Every animation must have **purpose**: signal, guide, or create emotion
- Prefer CSS-only for plain HTML; use Motion/Framer Motion for React
- Focus on: staggered page load reveals, surprising hover states, smooth transitions
- **NEVER** do: fade-in everything the same way, default spinner loaders

```css
/* Staggered reveal example */
.item:nth-child(1) { animation-delay: 0ms; }
.item:nth-child(2) { animation-delay: 80ms; }
.item:nth-child(3) { animation-delay: 160ms; }
```

---

## Visual Details & Atmosphere

Build depth and atmosphere instead of flat backgrounds:

- Gradient mesh, noise texture, grain overlay
- Layered transparency, colored shadows (not just black)
- Decorative borders, subtle geometric patterns
- Custom cursors where contextually appropriate

```css
/* Noise texture overlay */
.bg::after {
  content: '';
  position: fixed;
  inset: 0;
  background-image: url("data:image/svg+xml,..."); /* noise SVG */
  opacity: 0.04;
  pointer-events: none;
}
```

---

## Hard Rules — Never Do These

| Avoid | Replace with |
|-------|--------------|
| Purple gradient on white | An intentional palette — see color section |
| Uniform `box-shadow: 0 2px 8px rgba(0,0,0,0.1)` on every card | Colored, directional shadows with personality |
| Every button at `border-radius: 8px` | A deliberate decision: sharp / pill / mixed — pick one and commit |
| Unstyled Heroicons / Lucide icons | Icons as part of the design language, styled consistently |
| Centered section title + gray subtitle + blue CTA | Break this pattern entirely |
| Every component with border + shadow + white background | Use space and typography for hierarchy, not boxes |

---

## Pre-Submit Checklist

- [ ] Is the font Inter, Roboto, or Arial? If yes → change it
- [ ] Is the color scheme a purple gradient or default blue? If yes → change it
- [ ] Does the layout look like a Bootstrap or default Tailwind template? If yes → break it
- [ ] Is there at least one surprising, memorable detail?
- [ ] If all text is removed, does the layout and color palette still communicate a recognizable style?

---

## In Short

> A good interface is not one that looks safely pretty.
> A good interface is one that has **a point of view** — and executes it without compromise.

Every time you generate frontend code, make **one clear aesthetic choice** and commit to it.
Do not choose average. Do not choose "good enough."
