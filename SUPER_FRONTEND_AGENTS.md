# AGENTS.md — Frontend Design Guidelines

Guidelines to build interfaces that feel intentional, product-specific, and visually distinctive.
Merge with project-specific instructions as needed.

**Tradeoff:** These guidelines bias toward quality and distinctiveness over speed.
For trivial UI tasks, use judgment.

---

## 0. Study Before You Design

**Do not invent a visual language before understanding the existing one.**

Before writing any code:
- Inspect nearby screens, shared components, design tokens, and styling conventions.
- Identify the existing spacing scale, typography, colors, radii, shadows, and breakpoints.
- Reuse established components and patterns whenever they fit.
- State assumptions when requirements or intended behavior are unclear.
- If no design system exists, derive a small, consistent set of rules from the current product.

The new work should feel native to the surrounding interface — not imported from a different template.

---

## 1. Commit to an Aesthetic Direction

**Don't default. Don't play it safe. Pick a direction and execute it fully.**

Before designing anything:
- State the aesthetic direction explicitly: editorial, brutalist, luxury, playful, retro-futuristic, etc.
- If the brief is vague, ask. Don't silently pick "clean and modern."
- Every design decision should trace back to that direction.
- Name the subject, its audience, and the page's single job before starting.

The subject's own world — its materials, artifacts, and vernacular — is where distinctive choices come from.

> Ask: *"If someone saw this without context, would they remember it?"* If no, reconsider.

---

## 2. Typography

**No default fonts. Ever.**

- Never default to: Inter, Roboto, Arial, system-ui.
- Always pair: one display font with personality + one refined body font.
- Set a clear type scale with intentional weights, widths, and spacing.
- The font choice should feel deliberate, not like a placeholder.
- Make the type treatment itself a memorable part of the design.

---

## 3. Color

**No default palettes. No purple gradients on white.**

- Never default to: `#3B82F6` blue, `#F3F4F6` gray cards, purple-to-white gradients.
- Always define: one dominant color + 1–2 sharp accents via CSS variables.
- If the palette could belong to any app, it's wrong.
- Contrast and cohesion matter — maintain sufficient contrast for readability.

---

## 4. Layout

**Break the template.**

- Never default to: centered hero → 3-column cards → CTA section → footer.
- Asymmetry, overlap, and intentional negative space are valid choices.
- Match layout complexity to the aesthetic direction.
- Prefer whitespace and alignment over extra containers and borders.
- Group related controls; separate unrelated content.

---

## 5. Motion

**Animate with purpose, not decoration.**

- Every animation should signal, guide, or create emotion.
- Never: fade-in everything uniformly, default spinner loaders.
- One well-timed staggered reveal > ten scattered micro-interactions.
- Respect `prefers-reduced-motion` — users who opt out must still have a functional experience.
- Sometimes less is more: extra animation contributes to the "AI-generated" feeling.

---

## 6. Copy & Content

**Words are design material, not decoration.**

- Write from the end user's side of the screen — name things by what people control, not how the system is built.
- Use active voice: "Save changes," not "Submit."
- Keep labels specific, concise, and consistent throughout the flow.
- Treat empty states and errors as moments for direction, not mood: explain what happened and how to fix it.
- Use realistic content when creating examples — not Lorem Ipsum.

---

## 7. Design Real States

**A polished interface handles more than the ideal screenshot.**

Account for:
- Loading
- Empty
- Error
- Disabled
- Success
- Partial or long content
- Permission-restricted

Do not add states that cannot occur. When a state can occur, make it understandable and actionable.

---

## 8. Responsive by Intent

**Do not treat mobile as a compressed desktop layout.**

- Decide what information and actions matter most at each viewport.
- Let layouts reflow naturally before adding many breakpoints.
- Avoid hiding essential actions on smaller screens.
- Ensure text, tables, forms, and controls remain usable with long content.
- Prefer responsive CSS over JavaScript viewport checks.

---

## 9. Accessibility Is Part of the UI

**Accessible behavior is a baseline, not a later enhancement.**

- Use semantic HTML before adding ARIA.
- Ensure all interactive elements work with a keyboard.
- Provide visible focus states.
- Use proper labels for inputs and controls.
- Do not communicate meaning through color alone.
- Use buttons for actions and links for navigation.

---

## 10. Use Components With Restraint

**Create the minimum structure needed.**

- Reuse existing components before creating new ones.
- Do not add abstractions for a single use unless they remove meaningful complexity.
- Keep component APIs narrow and driven by actual use cases.
- Do not add a new UI library when the current stack can handle the task.
- Match the project's existing component and styling patterns.

Every new component should have a clear reason to exist.

---

## 11. Keep Changes Surgical

**Touch only what the task requires.**

- Do not restyle unrelated screens or shared components.
- Preserve existing behavior unless the request changes it.
- Remove only the unused code introduced by your changes.
- Mention unrelated issues instead of fixing them silently.

Every changed line should trace back to the requested outcome.

---

## 12. Verify the Result

**Do not consider frontend work complete because it compiles.**

For each task:
1. Define the intended user flow and visible success criteria.
2. Implement the smallest complete change.
3. Open the interface and inspect it visually.
4. Test the interaction, responsive layout, and all relevant states.
5. Compare with nearby product screens for consistency.

Before finishing, ask:
- Does this look like it belongs to this product?
- Is the primary action obvious?
- Is any visual element present only for decoration?
- Does the layout still work with real, long, or missing content?
- Could this be simpler without losing clarity?
- Would someone remember this UI for the right reasons?

---

**These guidelines are working if:** the UI feels specific to the product, has a recognizable point of view,
font/color choices feel intentional, no two outputs look like the same template, and the diff stays focused.
