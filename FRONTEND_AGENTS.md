# AGENTS.md

Behavioral guidelines to avoid generic AI-generated frontend aesthetics.
Merge with project-specific instructions as needed.

**Tradeoff:** These guidelines bias toward distinctiveness over speed. For trivial UI tasks, use judgment.

---

## Core principle

The goal isn't to avoid specific fonts or layouts — it's to avoid **choosing by default**. Any element is acceptable if you can answer "why this, for this project." An element is wrong if the honest answer is "it's what I reach for when I'm not thinking."

---

## 1. Commit to an Aesthetic Direction

**Don't default. Don't play it safe. Pick a direction and execute it fully.**

Before writing any code:

- State the aesthetic direction explicitly: editorial, brutalist, luxury, playful, retro-futuristic, etc.
- If the brief is vague, ask. Don't silently pick "clean and modern."
- Every design decision should trace back to that direction.

Ask yourself: *"If someone saw this without context, would they remember it?"* If no, reconsider.

---

## 2. Typography

**No default fonts without a reason.**

Common defaults to think twice about: `Inter`, `Roboto`, `Arial`, `system-ui`. These aren't banned — but if you reach for them, name why they serve *this* project's aesthetic.

- Always pair: one display font with personality + one refined body font
- The font choice should feel intentional, not like a placeholder
- If Inter is right for the direction (e.g., a devtools product, a data dashboard), use it — and say so

---

## 3. Color

**No default palettes without a reason.**

Common defaults to think twice about: `#3B82F6` blue, `#F3F4F6` gray cards, purple-to-white gradients. If you use them, explain why they fit — don't let them slip in because they were nearby.

- Always define: one dominant color + 1–2 sharp accents via CSS variables
- Test the palette against the brief: could this exact palette belong to a different app in a different category? If yes, push further.

---

## 4. Layout

**Break the template — unless the template is the right answer.**

Common default to think twice about: centered hero → 3-column cards → CTA section → footer. This structure isn't forbidden, but it's the layout equivalent of a system font: it signals no decision was made.

- Asymmetry, overlap, and intentional negative space are valid choices
- Match layout complexity to the aesthetic direction
- If a conventional layout is right for the project, call it out: "this is a structured, content-first layout — intentional"

---

## 5. Motion

**Animate with purpose, not decoration.**

- Every animation should signal, guide, or create emotion
- Don't default to: fading in everything uniformly, stock spinner loaders
- One well-timed staggered reveal > ten scattered micro-interactions
- Sometimes no animation is the right answer — especially for dense data UIs or serious content

---

## Self-check before shipping

Before finalizing any UI, run through:

1. **Direction** — Can I name the aesthetic in one word?
2. **Typography** — Did I pick these fonts, or did I just not change the default?
3. **Color** — Would this palette work for a different app in a different category? (If yes: rethink)
4. **Layout** — Does the structure reflect the content, or is it a template with content dropped in?
5. **Motion** — Does every animation have a job? Can I remove any without losing meaning?

If all five have real answers, ship it.

---

**These guidelines are working if:** generated UIs have a recognizable point of view, font/color choices feel intentional, and no two outputs look like the same template.
