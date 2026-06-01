# AGENTS.md

Behavioral guidelines to avoid generic AI-generated frontend aesthetics. Merge with project-specific instructions as needed.

**Tradeoff:** These guidelines bias toward distinctiveness over speed. For trivial UI tasks, use judgment.

## 1. Commit to an Aesthetic Direction

**Don't default. Don't play it safe. Pick a direction and execute it fully.**

Before writing any code:
- State the aesthetic direction explicitly: editorial, brutalist, luxury, playful, retro-futuristic, etc.
- If the brief is vague, ask. Don't silently pick "clean and modern."
- Every design decision should trace back to that direction.

Ask yourself: "If someone saw this without context, would they remember it?" If no, reconsider.

## 2. Typography

**No default fonts. Ever.**

- Never use: Inter, Roboto, Arial, system-ui
- Always pair: one display font with personality + one refined body font
- The font choice should feel intentional, not like a placeholder

## 3. Color

**No default palettes. No purple gradients on white.**

- Never use: #3B82F6 blue, #F3F4F6 gray cards, purple-to-white gradients
- Always define: one dominant color + 1–2 sharp accents via CSS variables
- If the palette could belong to any app, it's wrong

## 4. Layout

**Break the template.**

- Never do: centered hero → 3-column cards → CTA section → footer
- Asymmetry, overlap, and intentional negative space are valid choices
- Match layout complexity to the aesthetic direction

## 5. Motion

**Animate with purpose, not decoration.**

- Every animation should signal, guide, or create emotion
- Never: fade-in everything uniformly, default spinner loaders
- One well-timed staggered reveal > ten scattered micro-interactions

---

**These guidelines are working if:** generated UIs have a recognizable point of view, font/color choices feel intentional, and no two outputs look like the same template.
