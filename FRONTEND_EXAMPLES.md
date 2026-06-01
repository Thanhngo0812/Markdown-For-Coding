# EXAMPLES.md

Real-world code examples demonstrating the five frontend principles. Each example shows what AI commonly generates and what it should generate instead.

---

## 1. Commit to an Aesthetic Direction

### Example: Landing Page for a Coffee Brand

**User Request:** "Build a landing page for a specialty coffee brand"

**❌ What AI Does (No Direction)**

```html
<!-- Picks "clean and modern" silently. Safe. Forgettable. -->
<section class="hero" style="background: #fff; text-align: center; padding: 80px;">
  <h1 style="font-family: Inter, sans-serif; font-size: 48px; color: #111;">
    Premium Coffee, Delivered.
  </h1>
  <p style="color: #666; font-size: 18px;">
    Freshly roasted, straight to your door.
  </p>
  <button style="background: #3B82F6; color: #fff; padding: 12px 24px; border-radius: 8px;">
    Shop Now
  </button>
</section>
```

**Problems:**
- No aesthetic direction — could be any SaaS product
- Default blue button, white background, centered layout
- Nothing connects to coffee, warmth, craft, or origin

**✅ What Should Happen (Direction First)**

```
Before implementing, I'll commit to a direction:

Direction: Dark editorial — rich espresso tones, tactile texture,
heavy serif typography. Feels like a curated print magazine.
The one thing someone will remember: the grain overlay + warm amber
accent against a near-black background.

--color-bg:      #0E0B09;
--color-surface: #1A1410;
--color-accent:  #C97B3A;
--color-text:    #F0E8DC;
--font-display:  'Fraunces', serif;       /* optical, nostalgic */
--font-body:     'Switzer', sans-serif;   /* clean contrast */
```

```html
<section class="hero">
  <div class="hero__eyebrow">Single Origin · Small Batch</div>
  <h1 class="hero__title">Coffee worth<br><em>slowing down for.</em></h1>
  <a href="/shop" class="hero__cta">Explore the roasts →</a>
  <div class="grain-overlay"></div>
</section>
```

```css
.hero {
  background: var(--color-bg);
  min-height: 100vh;
  display: grid;
  place-items: start;
  padding: clamp(3rem, 8vw, 7rem);
  position: relative;
}

.hero__title {
  font-family: var(--font-display);
  font-size: clamp(3rem, 8vw, 7rem);
  color: var(--color-text);
  line-height: 1.05;
  max-width: 12ch;
}

.hero__title em {
  color: var(--color-accent);
  font-style: italic;
}

.grain-overlay {
  position: fixed;
  inset: 0;
  background-image: url("data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' width='200' height='200'><filter id='n'><feTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4'/><feColorMatrix type='saturate' values='0'/></filter><rect width='200' height='200' filter='url(%23n)' opacity='1'/></svg>");
  opacity: 0.035;
  pointer-events: none;
  z-index: 100;
}
```

---

## 2. Typography

### Example: Dashboard Header

**User Request:** "Add a page title and subtitle to the dashboard"

**❌ What AI Does (Default Font)**

```css
.page-title {
  font-family: Inter, -apple-system, BlinkMacSystemFont, sans-serif;
  font-size: 24px;
  font-weight: 600;
  color: #111827;
}

.page-subtitle {
  font-family: Inter, -apple-system, BlinkMacSystemFont, sans-serif;
  font-size: 14px;
  color: #6B7280;
}
```

**Problems:**
- Inter is the new Arial — default, invisible, forgettable
- Same font family for both title and subtitle — no contrast, no hierarchy
- Could be any dashboard from any company

**✅ What Should Happen (Intentional Pairing)**

```css
/* Import at top of stylesheet */
@import url('https://fonts.googleapis.com/css2?family=Instrument+Serif:ital@0;1&family=DM+Sans:wght@400;500&display=swap');

:root {
  --font-display: 'Instrument Serif', serif;
  --font-body: 'DM Sans', sans-serif;
}

.page-title {
  font-family: var(--font-display);
  font-size: clamp(1.75rem, 3vw, 2.5rem);
  font-weight: 400; /* serifs read well at regular weight */
  color: var(--color-text);
  letter-spacing: -0.02em;
  line-height: 1.1;
}

.page-subtitle {
  font-family: var(--font-body);
  font-size: 0.9rem;
  font-weight: 400;
  color: var(--color-text-secondary);
  letter-spacing: 0.01em;
  margin-top: 0.35rem;
}
```

**Why this works:** Serif display + sans body creates contrast. The pairing feels deliberate, not assembled.

---

## 3. Color

### Example: Pricing Card

**User Request:** "Build a pricing card with a highlighted 'Pro' tier"

**❌ What AI Does (Default Palette)**

```css
.card { background: #fff; border: 1px solid #E5E7EB; border-radius: 12px; }
.card--featured { border-color: #3B82F6; }
.badge { background: #3B82F6; color: #fff; border-radius: 999px; }
.price { color: #111827; font-size: 48px; }
.btn { background: #3B82F6; color: #fff; border-radius: 8px; }
```

**Problems:**
- `#3B82F6` appears four times — the palette has one note
- White card on white page — no depth
- Could be Stripe, Linear, Vercel, or any SaaS built in 2021

**✅ What Should Happen (Defined Palette)**

```css
:root {
  --color-bg:       #0A0A0F;
  --color-surface:  #13131A;
  --color-border:   #2A2A35;
  --color-primary:  #A78BFA;   /* violet — one accent, used sparingly */
  --color-text:     #F4F4F6;
  --color-muted:    #6B6B80;
}

.card {
  background: var(--color-surface);
  border: 1px solid var(--color-border);
  border-radius: 4px; /* sharp — intentional, not rounded by default */
}

.card--featured {
  border-color: var(--color-primary);
  box-shadow: 0 0 0 1px var(--color-primary),
              0 20px 60px -10px rgba(167, 139, 250, 0.15);
}

.badge {
  background: transparent;
  border: 1px solid var(--color-primary);
  color: var(--color-primary);
  border-radius: 2px;
  font-size: 0.7rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

.btn--primary {
  background: var(--color-primary);
  color: #0A0A0F;
  border-radius: 2px;
  font-weight: 600;
}
```

**If the palette could belong to any app, it's wrong.**

---

## 4. Layout

### Example: Feature Section

**User Request:** "Add a features section with 3 key product features"

**❌ What AI Does (Template Layout)**

```html
<section style="padding: 80px 0; text-align: center;">
  <h2>Everything you need</h2>
  <p>Powerful tools to grow your business</p>
  <div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 24px; margin-top: 48px;">
    <div class="card">
      <div class="icon">⚡</div>
      <h3>Fast</h3>
      <p>Lightning fast performance</p>
    </div>
    <div class="card">
      <div class="icon">🔒</div>
      <h3>Secure</h3>
      <p>Enterprise-grade security</p>
    </div>
    <div class="card">
      <div class="icon">📊</div>
      <h3>Analytics</h3>
      <p>Real-time insights</p>
    </div>
  </div>
</section>
```

**Problems:**
- Centered title + 3-column cards is the most overused layout on the web
- Emoji icons — no design decision made
- Uniform card size, equal weight — no visual hierarchy

**✅ What Should Happen (Break the Template)**

```html
<!-- Asymmetric: one large featured item, two secondary -->
<section class="features">
  <div class="features__header">
    <span class="features__label">Why it works</span>
    <h2 class="features__title">Built different,<br>by design.</h2>
  </div>

  <div class="features__grid">
    <!-- Primary feature — large, left-aligned -->
    <article class="feature feature--primary">
      <div class="feature__number">01</div>
      <h3 class="feature__name">Sub-10ms response</h3>
      <p class="feature__desc">
        Processed at the edge, not a datacenter three states away.
        Every interaction feels immediate.
      </p>
    </article>

    <!-- Two secondary features — compact, right column -->
    <article class="feature feature--secondary">
      <div class="feature__number">02</div>
      <h3 class="feature__name">Zero-config security</h3>
      <p class="feature__desc">Encrypted by default. No settings to misconfigure.</p>
    </article>

    <article class="feature feature--secondary">
      <div class="feature__number">03</div>
      <h3 class="feature__name">Live analytics</h3>
      <p class="feature__desc">See what's happening as it happens.</p>
    </article>
  </div>
</section>
```

```css
.features__grid {
  display: grid;
  grid-template-columns: 1.6fr 1fr;
  grid-template-rows: auto auto;
  gap: 2px; /* tight gap — industrial feel */
}

.feature--primary {
  grid-row: 1 / 3; /* spans both rows */
  padding: clamp(2rem, 5vw, 4rem);
  background: var(--color-surface);
}

.feature--secondary {
  padding: clamp(1.5rem, 3vw, 2.5rem);
  background: var(--color-surface);
}

.feature__number {
  font-family: var(--font-display);
  font-size: 4rem;
  color: var(--color-border); /* faint — structural, not decorative */
  line-height: 1;
  margin-bottom: 1.5rem;
}
```

---

## 5. Motion

### Example: Page Load Animation

**User Request:** "Add entrance animations to the homepage"

**❌ What AI Does (Decoration)**

```css
/* Fades everything in uniformly — adds nothing */
.hero, .features, .footer, .nav, .card, h1, p, button {
  animation: fadeIn 0.5s ease forwards;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to   { opacity: 1; }
}
```

**Problems:**
- Fading everything creates visual noise, not hierarchy
- 0.5s on every element — nothing feels considered
- No relationship between animation and meaning

**✅ What Should Happen (Purpose-Driven)**

```css
/* Only animate the hero — it's the first thing seen */
/* Staggered to guide the eye: eyebrow → title → subtitle → CTA */

.hero__eyebrow,
.hero__title,
.hero__subtitle,
.hero__cta {
  opacity: 0;
  transform: translateY(16px);
  animation: reveal 0.6s cubic-bezier(0.16, 1, 0.3, 1) forwards;
}

.hero__eyebrow  { animation-delay: 100ms; }
.hero__title    { animation-delay: 220ms; }
.hero__subtitle { animation-delay: 340ms; }
.hero__cta      { animation-delay: 460ms; }

@keyframes reveal {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Below the fold: only animate when scrolled into view */
@media (prefers-reduced-motion: no-preference) {
  .feature[data-visible="false"] {
    opacity: 0;
    transform: translateY(24px);
    transition: opacity 0.5s ease, transform 0.5s ease;
  }
  .feature[data-visible="true"] {
    opacity: 1;
    transform: translateY(0);
  }
}
```

```js
// Trigger scroll animations only when element enters viewport
const observer = new IntersectionObserver(
  (entries) => entries.forEach(e => {
    e.target.dataset.visible = e.isIntersecting;
  }),
  { threshold: 0.15 }
);

document.querySelectorAll('.feature').forEach(el => {
  el.dataset.visible = 'false';
  observer.observe(el);
});
```

**Why this works:** The hero stagger guides the eye top-to-bottom. Features only animate when visible. Nothing below the fold loads animation upfront.

---

## Anti-Patterns Summary

| Principle | Anti-Pattern | Fix |
|-----------|-------------|-----|
| Aesthetic Direction | Silently picks "clean and modern" | State direction explicitly before any code |
| Typography | Inter everywhere, same family for all text | Display + body pairing, chosen for context |
| Color | `#3B82F6` blue, white cards, gray text `#6B7280` | One dominant + 1–2 accents, defined as CSS variables |
| Layout | Centered title → 3-column cards → CTA | Asymmetry, hierarchy, grid-breaking |
| Motion | Fade-in every element at 0.5s | Stagger only meaningful elements, animate on scroll |

## Key Insight

The bad examples aren't ugly — they're **invisible**. They pass a basic quality bar but leave no impression. That's the failure mode for AI-generated UI: technically correct, aesthetically absent.

The fix isn't more decoration. It's more **intention**.

**Good UI has a point of view. Every decision — font, color, layout, motion — should be traceable to that point of view.**
