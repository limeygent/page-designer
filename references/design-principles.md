# Design Principles Toolkit

These 13 principles represent how experienced designers think about layout. They are not a sequential checklist. For any given page, some principles will matter more than others.

**Before designing, consider: which 3-4 of these principles are most important for the page I'm building?** Those should guide your decisions. The rest are still good design thinking, but they're background awareness, not primary drivers.

A few examples of how context shapes which principles matter:

- **Fear-driven emergency page?** Visual hierarchy and Fitts's Law matter enormously. The visitor needs to find the phone number instantly. Gestalt consistency matters less because the page is short and action-oriented.
- **Aspirational cosmetic/luxury page?** Spatial awareness and symmetry/asymmetry are critical for creating that premium feel. Progressive disclosure handles the educational depth gracefully.
- **Research-heavy comparison page?** Reading patterns and typography rhythm keep dense content scannable. Color as information helps structure complex data without overwhelming.
- **Short trust-building page?** Section rhythm and attention anchoring do the heavy lifting. Every section needs to earn its place visually.

---

## 1. Visual Hierarchy

**What:** Size, contrast, and position control what gets read first. The largest, boldest element on screen is read first regardless of where it sits. A huge heading in the middle of the page beats a small one at the top.

**Why it matters:** Without deliberate hierarchy, every section looks equally important, which means nothing stands out. The visitor's eye has nowhere to land, so they bounce.

**Design intuition:** A well-designed section has a clear focal point. When you look at a section, your eye should know where to land. Ask yourself: what is the one thing I want the visitor to notice first here? Then make that element visually heavier than its surroundings.

Sometimes the heading is the focal point. Sometimes a stat dominates. Sometimes a quote in large italic text anchors the section. The choice depends on what the section is trying to accomplish.

**CSS patterns:**

```html
<!-- Level 1: Page-level (hero only) -->
<h1 class="display-4 fw-bold mb-3">...</h1>

<!-- Level 2: Section anchor (section headings) -->
<h2 class="fw-bold mb-2">...</h2>
<p class="text-muted mb-4">One-line section subtitle</p>

<!-- Level 3: Sub-section / card titles -->
<h3 class="h5 fw-semibold mb-2">...</h3>

<!-- Level 4: Supporting text -->
<p class="text-muted">...</p>

<!-- Level 5: De-emphasized -->
<p class="small text-muted">...</p>

<!-- Stat as anchor (reads first due to size) -->
<div class="display-6 fw-bold" style="color: var(--pd-primary);">97%</div>
<p class="text-muted mb-0">Customer satisfaction rate</p>
```

**Variation technique:** Not every section heading needs to be the dominant element. In a testimonial section, the quote itself (larger font, italicized) can be the anchor. In a stats section, the numbers dominate. In a process section, the step numbers lead. Varying what anchors each section prevents the "H2 parade."

---

## 2. Section Rhythm

**What:** Adjacent sections should feel visually distinct. The eye needs contrast between sections to register that a new topic has begun.

**Why it matters:** This principle prevents the #1 AI page problem: every section looking identical. When backgrounds, layouts, and spacing vary, the page feels hand-designed.

**Design intuition:** When you scroll through your page, each section should feel like a new moment. If two adjacent sections share the same background, the same layout, and the same visual structure, they blur together and the visitor can't tell where one topic ends and the next begins. This doesn't mean you need to mechanically alternate treatment IDs. It means you should notice when the page starts to feel monotonous and introduce a shift. The goal is contrast between sections, not strict non-repetition.

A good page typically draws from at least 3-4 different visual treatments, but this emerges naturally from thinking about what each section needs, not from counting.

**Pattern example (good):**
```
Section 1: Hero         → T4 Split Panel (gradient bg)
Section 2: Trust bar    → T5 Accent Band (brand color)
Section 3: Services     → T3 Card Grid (white bg)
Section 4: Why choose   → T2 Tinted Band (gray bg)
Section 5: Process      → T1 Open Canvas (white bg)
Section 6: Mid CTA      → T5 Accent Band (brand color)
Section 7: Testimonials  → T6 Boxed Container (white bg)
Section 8: FAQ          → T2 Tinted Band (gray bg)
Section 9: Final CTA    → T4 Split Panel (white bg)
```

No two adjacent items share the same treatment — but this emerged from choosing what each section needed, not from mechanically cycling through a list.

---

## 3. Spatial Awareness (Negative Space)

**What:** Negative space (white space) is an active design element, not leftover emptiness. The amount of space between elements communicates how they relate. Tight spacing = grouped/related. Wide spacing = separate topics. Empty space around a key element isolates it, making it more prominent and easier to process.

**Why it matters:** Without deliberate spacing, content feels like a wall of text. With it, the page "breathes" and information is naturally chunked into digestible pieces.

**Design intuition:** Spacing communicates relationships. A major topic shift deserves generous breathing room. A compact utility section (trust bar, CTA band) can be tighter. Text-heavy reading sections benefit from narrower containers that keep line length comfortable. The specific Bootstrap classes are tools for expressing these relationships:

**Common spacing patterns:**
- Major topic transitions: `py-5` (3rem vertical padding)
- Related sequential content: `py-4` (1.5rem)
- Compact utility sections (trust bar, CTA band): `py-3` (1rem)
- Text-heavy reading sections: constrain width with `style="max-width: 720px; margin: auto;"` or `col-lg-8 mx-auto`
- Between heading and content within a section: `mb-3` (tight)
- Between content and CTA within a section: `mt-4` (breathing room before the action)

**CSS patterns:**

```html
<!-- Major topic section -->
<section class="py-5">
  <div class="container">
    <div class="row">
      <div class="col-lg-8 mx-auto"> <!-- narrow for readability -->
        <h2 class="fw-bold mb-3">...</h2>
        <p>Long-form educational content...</p>
      </div>
    </div>
  </div>
</section>

<!-- Compact utility section -->
<section class="py-3 border-top border-bottom">
  <div class="container">
    <!-- Trust bar, stats, etc. -->
  </div>
</section>
```

**Responsive spacing:** Use Bootstrap responsive utilities: `py-3 py-md-4 py-lg-5` so mobile gets tighter spacing (content density matters when scrolling is the primary interaction).

---

## 4. Attention Anchoring

**What:** Every section benefits from a visual element that the eye lands on first, before reading the text. Without an anchor, the eye has nothing to grab onto, and it may skip the section.

**Why it matters:** Pure text sections (heading + paragraphs) are often invisible to scanning visitors. An anchor gives them a reason to stop scrolling.

**Design intuition:** When you notice a section that's just heading and paragraphs, consider whether a visual anchor would help the visitor engage with it. Not every section needs a dramatic anchor — sometimes the heading itself, styled distinctively, is enough. But most sections benefit from at least one element that isn't body text.

**Images as conversion tools:** Images serve specific conversion functions:
- **Emotional connection** — a parent sees a child in a safe environment and their anxiety drops. That emotional shift keeps them on the page.
- **Pattern interrupt** — every competitor's page is text-heavy. An image breaks the pattern and signals "this is a real place with real people."
- **Scroll motivation** — a visually appealing section makes the reader trust the rest of the page is worth their time.
- **Trust building** — real photos of the team, office, or work product prove legitimacy in a way text cannot.

**Hero image considerations by intent:**
- **Urgent/fear intent:** Image should BE the hero (T7 full-width background). Phone CTA is the primary action overlaid on the image.
- **Planning/research intent:** Image can be a split panel element (T4). Sidebar can hold a form or info card.

**Anchor types with HTML:**

```html
<!-- 1. Oversized stat/number -->
<div class="d-flex align-items-center gap-3 mb-4">
  <div class="display-5 fw-bold" style="color: var(--pd-primary);">24/7</div>
  <div>
    <div class="fw-semibold">Emergency availability</div>
    <div class="small text-muted">Including holidays and weekends</div>
  </div>
</div>

<!-- 2. Icon circle -->
<div class="icon-circle mb-3">
  <i class="bi bi-shield-check"></i>
</div>

<!-- 3. Colored badge/pill -->
<span class="badge rounded-pill px-3 py-2 mb-3" style="background: var(--pd-primary-light); color: var(--pd-primary-dark);">
  <i class="bi bi-star-fill me-1"></i> Top Rated in Dallas
</span>

<!-- 4. Pull quote (large, italicized) -->
<blockquote class="fs-4 fst-italic mb-4" style="border-left: 4px solid var(--pd-primary); padding-left: 1.5rem;">
  "They showed up in 45 minutes and fixed the leak on the spot."
</blockquote>

<!-- 5. Highlighted callout box -->
<div class="p-4 rounded-3 mb-4" style="background: var(--pd-primary-light); border-left: 4px solid var(--pd-primary);">
  <div class="fw-bold mb-1">Did you know?</div>
  <p class="mb-0">80% of emergency plumbing calls happen between 6pm and midnight.</p>
</div>
```

---

## 5. Symmetry and Intentional Asymmetry

**What:** Symmetrical layouts feel stable, trustworthy, and predictable. Asymmetric layouts feel dynamic, interesting, and human. A good page mixes both.

**Why it matters:** All-symmetrical pages feel corporate and stiff. All-asymmetric pages feel chaotic. The balance between them creates visual interest while maintaining professionalism.

**Design intuition:** Think about what each section's content and purpose calls for:
- **Symmetry suits:** Trust/credibility sections (even card grids, centered headings), FAQ, final CTA — places where stability and authority matter.
- **Asymmetry suits:** Hero (text 60% / form 40%), differentiator sections (text + image side by side), testimonial callouts, process sections with alternating image/text sides — places where you want visual energy and interest.

If you find yourself centering everything, that's a signal to introduce some asymmetry. If everything feels dynamic and off-balance, anchor a few sections with centered, symmetrical layouts.

**CSS patterns:**

```html
<!-- Symmetrical: centered, even columns -->
<div class="text-center mb-4">
  <h2 class="fw-bold">Why Homeowners Trust Us</h2>
  <p class="text-muted">Over 500 five-star reviews in the Dallas area</p>
</div>
<div class="row g-4">
  <div class="col-md-4"><!-- card --></div>
  <div class="col-md-4"><!-- card --></div>
  <div class="col-md-4"><!-- card --></div>
</div>

<!-- Asymmetrical: weighted columns -->
<div class="row align-items-center g-4">
  <div class="col-lg-7">
    <h2 class="fw-bold">...</h2>
    <p>...</p>
  </div>
  <div class="col-lg-5">
    <!-- image, card, or sidebar -->
  </div>
</div>

<!-- Asymmetrical: offset content -->
<div class="row">
  <div class="col-lg-8 offset-lg-2"><!-- narrow centered content --></div>
</div>
```

---

## 6. Reading Patterns

**What:** Eye-tracking research shows three dominant reading patterns on the web. Each one maps to a specific layout type.

**Why it matters:** Matching your layout to the expected reading pattern means visitors naturally find the most important information. Fighting the pattern creates confusion.

**Design intuition:** Tag each section with the reading pattern it naturally supports. See `references/reading-patterns.md` for the full mapping.

- **F-pattern** → single column, left-aligned text, narrow container
- **Z-pattern** → two elements at top (heading + badge), two at bottom (detail + CTA)
- **Gutenberg** → equal-weight grid (cards, features)

The dominant intent shapes which patterns appear most on the page, but most pages use a mix of all three.

---

## 7. Visual Grids Without Borders

**What:** Content alignment creates implied structure without visible lines. Items aligned to the same baseline or vertical axis feel connected without needing a border to prove it.

**Why it matters:** Borders and heavy card outlines make pages feel boxy and rigid. Modern design uses spacing, shadows, and alignment to imply structure.

**Design intuition:** Default to borderless containers. Use `shadow-sm` for elevation, `gap` utilities for consistent spacing, and background color changes for grouping. Reserve explicit borders for when there's a semantic reason (e.g., a form card that needs visual containment, or an accent border-left that draws attention to a callout).

**CSS patterns:**

```html
<!-- Instead of bordered cards, use shadow and spacing -->
<div class="card border-0 shadow-sm rounded-3">
  <div class="card-body p-4">...</div>
</div>

<!-- Instead of bordered lists, use spacing -->
<div class="row g-4">
  <div class="col-md-6">
    <div class="d-flex gap-3 align-items-start">
      <div class="icon-circle flex-shrink-0"><i class="bi bi-check-lg"></i></div>
      <div>
        <h3 class="h6 fw-bold mb-1">Feature name</h3>
        <p class="text-muted small mb-0">Description text</p>
      </div>
    </div>
  </div>
</div>

<!-- Background color instead of border for grouping -->
<section class="py-5" style="background: var(--pd-light);">
  <!-- Content appears "grouped" by the tinted background -->
</section>
```

---

## 8. Color as Information

**What:** Color should communicate meaning, not just decorate. Brand color signals "interactive" or "important." Neutral colors signal "supporting." Tinted backgrounds signal "grouped."

**Why it matters:** When brand color is everywhere (backgrounds, headings, icons, borders), nothing stands out because everything is colored. When it's used surgically, the colored elements naturally draw attention.

**Design intuition:** Think of brand color as a highlighter. Use it to mark the things that matter most — buttons, CTAs, icon circles, key stats, accent borders. Use neutrals for everything else. If you find yourself applying brand color to more than 3-4 element types per section, you're probably diluting its impact.

**Color roles:**
- **Brand primary** (`--pd-primary`): Buttons, CTAs, icon circles, key stats, accent borders. Things the user should click or notice first.
- **Brand light** (`--pd-primary-light`): Badge backgrounds, subtle callout backgrounds. Not for section backgrounds (use `--pd-light` for that).
- **Neutral light** (`--pd-light` / `#f8f9fa`): Section background alternation. The "not-white" background.
- **White**: Default section background.
- **Dark** (`--pd-dark`): Hero overlays, footer, inverted sections.

A good rule of thumb: max 3 background colors rotating across sections — white, `var(--pd-light)`, and (sparingly, max 2x per page) `var(--pd-primary)` for accent bands.

---

## 9. Typography Rhythm

**What:** A consistent type scale creates professionalism. Inconsistent sizing (random `fs-3` here, arbitrary `1.25rem` there) feels amateur and disorienting.

**Why it matters:** Typography is the backbone of visual hierarchy. If sizes aren't consistent, the hierarchy breaks down and the visitor can't tell what's important.

**Design intuition:** Stick to a defined scale. Not because it's a rule, but because consistency in typography is one of the strongest signals of professional design. The visitor may not consciously notice consistent type sizing, but they will feel the difference.

| Element | Bootstrap Class | Usage |
|---|---|---|
| Page title (hero) | `display-4 fw-bold` | Once per page, hero only |
| Section headings | `h2` + `fw-bold` | Start of each major section |
| Section subtitle | `p.text-muted.mb-4` | Optional, one per section max |
| Intro paragraph | `p.lead` | First paragraph of a section, sparingly |
| Sub-headings | `h3.h5.fw-semibold` | Card titles, sub-sections within a section |
| Body text | Default `p` | Content paragraphs |
| Small/meta text | `small.text-muted` | Disclaimers, attributions, timestamps |
| Stats/numbers | `display-6 fw-bold` or `fs-2 fw-bold` | When number is the anchor element |

**Key consideration:** The `.lead` class exists to draw the eye into a section. If multiple paragraphs in the same section are lead-sized, the emphasis is lost. Generally one `.lead` per section is enough.

---

## 10. Progressive Disclosure

**What:** Don't dump all information at once. Show the most important content immediately; let visitors expand for details if they want them.

**Why it matters:** Information-dense pages overwhelm visitors. Progressive disclosure respects the visitor's time and attention. They get the summary; they dig deeper only if they choose to.

**Design intuition:** When you notice a section getting dense (6+ list items, a sprawling FAQ, a detailed comparison), consider whether the visitor actually needs all of it visible at once. Often the answer is no — the first 3-4 items or questions are the ones most people care about.

```html
<!-- Accordion (FAQ, detailed features) -->
<div class="accordion" id="faqAccordion">
  <div class="accordion-item border-0 border-bottom">
    <h3 class="accordion-header">
      <button class="accordion-button collapsed fw-semibold" type="button"
        data-bs-toggle="collapse" data-bs-target="#faq1">
        Question text here
      </button>
    </h3>
    <div id="faq1" class="accordion-collapse collapse" data-bs-parent="#faqAccordion">
      <div class="accordion-body text-muted">Answer text here</div>
    </div>
  </div>
</div>

<!-- Show first 3, hide rest (requires minimal JS) -->
<div id="featureList">
  <div class="feature-item">Always visible 1</div>
  <div class="feature-item">Always visible 2</div>
  <div class="feature-item">Always visible 3</div>
  <div class="feature-item d-none more-features">Hidden 4</div>
  <div class="feature-item d-none more-features">Hidden 5</div>
</div>
<button class="btn btn-link" onclick="document.querySelectorAll('.more-features').forEach(el => el.classList.toggle('d-none')); this.textContent = this.textContent === 'Show more' ? 'Show less' : 'Show more';">Show more</button>

<!-- Tab interface (for categories of content) -->
<ul class="nav nav-pills mb-4" role="tablist">
  <li class="nav-item"><button class="nav-link active" data-bs-toggle="tab" data-bs-target="#tab1">Category 1</button></li>
  <li class="nav-item"><button class="nav-link" data-bs-toggle="tab" data-bs-target="#tab2">Category 2</button></li>
</ul>
<div class="tab-content">
  <div class="tab-pane fade show active" id="tab1">...</div>
  <div class="tab-pane fade" id="tab2">...</div>
</div>
```

---

## 11. Gestalt Principles

**What:** The brain groups visual elements into patterns automatically. Five key Gestalt laws govern how visitors perceive page structure without reading a word:

- **Proximity:** Elements close together are perceived as a group. A card's icon, heading, and description feel like one unit because they're tight; the gap between cards signals separate items.
- **Similarity:** Elements that look alike (same color, shape, size, icon style) are perceived as related. All service cards sharing the same border radius and icon circle style feel like peers.
- **Common Region:** Elements inside a shared boundary (background color, card, bordered box) are perceived as a group. A tinted section background groups everything inside it.
- **Continuity:** The eye follows lines and curves. A vertical timeline, a horizontal trust bar, or a diagonal gradient all guide the eye along a path.
- **Closure:** The brain completes incomplete shapes. An implied grid (cards with consistent spacing but no visible grid lines) is perceived as a table-like structure.

**Why it matters:** These are the invisible rules visitors use to parse your layout. When Gestalt principles are violated (related items spaced far apart, unrelated items styled identically), the page feels "off" even if the visitor can't articulate why.

**Design intuition:**

1. **Proximity:** After laying out a section, ask: "Would a visitor know which items belong together based on spacing alone?" If two items should be grouped but have the same gap as unrelated items, tighten the internal spacing.
2. **Similarity:** All items in a list/grid should share the same visual treatment (icon style, card style, text format). If one card has a border and the others don't, it looks like a different category.
3. **Common region:** Background color changes naturally signal topic shifts. This reinforces section rhythm — the tinted background creates a perceived boundary around that section's content.
4. **Break similarity to highlight:** When one item in a group should stand out (e.g., a "most popular" pricing tier), break the similarity pattern deliberately: different border color, slight scale increase, or a badge. The contrast against the group makes it pop.

**CSS patterns:**

```html
<!-- Proximity: tight internal spacing, wider external -->
<div class="row g-4"> <!-- 1.5rem gap between cards (external) -->
  <div class="col-md-4">
    <div class="card border-0 shadow-sm p-4">
      <div class="icon-circle mb-2"><i class="bi bi-shield-check"></i></div> <!-- 0.5rem to heading -->
      <h3 class="h6 fw-bold mb-1">Title</h3> <!-- 0.25rem to text -->
      <p class="text-muted small mb-0">Description</p> <!-- tight internal group -->
    </div>
  </div>
</div>

<!-- Similarity: consistent treatment across peers -->
<!-- ALL cards use: border-0, shadow-sm, same icon-circle size, same heading class -->
<!-- BREAK similarity for emphasis: -->
<div class="card border-2 shadow-sm p-4" style="border-color: var(--pd-primary) !important;">
  <span class="badge bg-primary position-absolute top-0 start-50 translate-middle">Most Popular</span>
  <!-- Same internal structure, but border + badge breaks the pattern -->
</div>

<!-- Common region: background groups content -->
<section class="py-5" style="background: var(--pd-light);">
  <!-- Everything inside feels like one topic unit -->
</section>
```

---

## 12. Consistency

**What:** Maintaining uniform visual patterns (fonts, colors, button styles, spacing, card treatments, icon styles) across all pages of a site so it feels like one cohesive experience rather than a collection of unrelated pages.

**Why it matters:** Inconsistency erodes trust. If every page uses different button styles, heading sizes, or card formats, the site feels cobbled together. Visitors unconsciously associate visual consistency with professionalism and reliability.

**Design intuition:** Visual interest between pages comes from different section ordering, treatment combinations, and content types — not from changing the fundamental building blocks (button styles, card borders, icon sizes). If a card style, icon-circle size, or CTA button already exists from a previous page for this client, use the same one.

**Cross-page checklist:**
- Same `:root` custom properties block
- Same button classes (`.btn-pd`, `.btn-pd-outline`)
- Same icon circle sizes (`.icon-circle`, `.icon-circle-sm`, `.icon-circle-lg`)
- Same card treatment (`.card-hover`, `border-0 shadow-sm`)
- Same heading scale (`display-4` hero, `h2 fw-bold` sections, `h5 fw-semibold` sub-items)
- Same spacing rhythm (`py-5` major, `py-4` related, `py-3` compact)

---

## 13. Fitts's Law

**What:** The time to reach a target is a function of the target's size and distance from the user's current focus. Larger targets closer to the user's attention are faster and easier to click. This is a foundational law of interaction design.

**Why it matters:** Service pages live or die on whether visitors click the CTA. A small "Book Now" link tucked in the corner fails Fitts's Law on both dimensions: it's small and far from where the eye is reading. A full-width button directly below the section content succeeds on both.

**Design intuition:** When placing CTAs, think about where the visitor's eye already is. After reading a section, their attention is at the bottom of the content. That's where the CTA should be. On mobile, a fixed-bottom phone button ensures the target is always within thumb reach for urgent pages.

Key considerations:
- Primary CTAs should be generously sized (`btn-lg` minimum, `btn-lg px-5 py-3` for hero CTAs)
- On mobile, primary CTAs should be full-width (`d-block` or `w-100`)
- Phone numbers and email links benefit from generous padding even when inline
- Two related CTAs (primary + secondary) should be adjacent (`d-flex gap-3`) so the user doesn't have to travel between options

**CSS patterns:**

```html
<!-- Hero CTA: large, prominent, immediate -->
<div class="d-flex flex-wrap gap-3 mt-4">
  <a href="tel:+61291593764" class="btn btn-pd btn-lg px-5">
    <i class="bi bi-telephone-fill me-2"></i>Call Now
  </a>
  <a href="#contact" class="btn btn-pd-outline btn-lg px-4">Book Online</a>
</div>

<!-- Mobile: full-width stacked buttons -->
<div class="d-grid gap-2 d-md-flex mt-4">
  <a href="tel:+61291593764" class="btn btn-pd btn-lg">
    <i class="bi bi-telephone-fill me-2"></i>Call Now
  </a>
  <a href="#contact" class="btn btn-pd-outline btn-lg">Book Online</a>
</div>

<!-- Sticky mobile CTA for emergency pages -->
<div class="fixed-bottom d-md-none p-2" style="background: var(--pd-primary); z-index: 1050;">
  <a href="tel:+61291593764" class="btn btn-light btn-lg w-100 fw-bold py-3">
    <i class="bi bi-telephone-fill me-2"></i>Call (02) 9159 3764
  </a>
</div>

<!-- Generous touch targets for inline links -->
<a href="tel:+61291593764" class="d-inline-block p-2 fw-semibold text-decoration-none"
   style="color: var(--pd-primary);">
  <i class="bi bi-telephone me-1"></i>(02) 9159 3764
</a>
```

---

## Quick Reference: CSS Utility Classes

These utility classes should be defined in the page's `<style>` block:

```css
:root {
  --pd-primary: /* brand color */;
  --pd-primary-dark: /* 20% darker */;
  --pd-primary-light: /* 8% opacity */;
  --pd-accent: /* complementary */;
  --pd-light: #f8f9fa;
  --pd-dark: #1a1a2e;
  --pd-radius: 0.75rem;
}

.btn-pd { background: var(--pd-primary); border-color: var(--pd-primary); color: #fff; font-weight: 600; }
.btn-pd:hover { background: var(--pd-primary-dark); color: #fff; transform: translateY(-1px); box-shadow: 0 4px 12px rgba(0,0,0,0.15); }
.btn-pd-outline { border: 2px solid var(--pd-primary); color: var(--pd-primary-dark); font-weight: 600; background: transparent; }
.btn-pd-outline:hover { background: var(--pd-primary); color: #fff; }

.icon-circle { width: 56px; height: 56px; border-radius: 50%; background: var(--pd-primary-light); color: var(--pd-primary); display: inline-flex; align-items: center; justify-content: center; font-size: 1.5rem; flex-shrink: 0; }
.icon-circle-sm { width: 40px; height: 40px; font-size: 1.1rem; }
.icon-circle-lg { width: 72px; height: 72px; font-size: 2rem; }

.step-number { width: 48px; height: 48px; border-radius: 50%; background: var(--pd-primary); color: #fff; display: inline-flex; align-items: center; justify-content: center; font-weight: 700; font-size: 1.25rem; flex-shrink: 0; }

.card-hover { transition: transform 0.2s ease, box-shadow 0.2s ease; border: none; }
.card-hover:hover { transform: translateY(-4px); box-shadow: 0 12px 24px rgba(0,0,0,0.08); }

.zone-group { scroll-margin-top: 80px; }

.accent-border-left { border-left: 4px solid var(--pd-primary); padding-left: 1.5rem; }

.bg-brand-light { background: var(--pd-primary-light); }
.text-brand { color: var(--pd-primary); }
.text-brand-dark { color: var(--pd-primary-dark); }
```
