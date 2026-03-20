# Anti-Patterns: Mass-Production Signals

These are patterns that frequently signal mass-produced, template-stamped design. When you notice one in your layout, pause and consider: is this a problem here, or is it intentional?

Most of the time, these patterns weaken the design. But context determines whether they're actually issues. Use these as things to **notice**, not as automatic failures. A designer who blindly avoids every pattern on this list is just following a different kind of template.

---

## 1. H2 Parade

**What it looks like:** 3 or more consecutive sections that start with `<h2>` followed immediately by a `<p>` paragraph, then content. Every section opener looks identical.

**Why it often weakens design:** A hand-designed page would vary how sections begin. Some start with a badge, some with a stat, some with a centered heading, some with an icon row. When every section opens the same way, the rhythm becomes robotic.

**When this might be acceptable:** A short page (5-6 sections) where the headings themselves are varied enough in style (some centered, some left-aligned, some with badges above them) that the consistent H2 opening doesn't feel repetitive.

**Fix strategies:**
- Lead one section with a stat/number anchor instead of an H2
- Use a badge or pill above the H2 in another section: `<span class="badge ...">How It Works</span>` then `<h2>`
- Center the heading in one section while left-aligning others
- Start one section with a visual element (icon grid, image) and put the H2 below or beside it
- Use an H3 instead of H2 for a less-prominent section (FAQ, disclaimers)

---

## 2. White Wall

**What it looks like:** 3 or more consecutive sections with white backgrounds (`#fff`).

**Why it often weakens design:** Without background alternation, sections blur together. The visitor can't tell where one topic ends and the next begins without reading every heading.

**When this might be acceptable:** Rarely. This is one of the strongest mass-production signals. But if the sections have dramatically different internal layouts (card grid followed by split panel followed by single-column text), the structural variety can partially compensate.

**Fix strategies:**
- Insert a T2 tinted band (gray or brand-light background) between white sections
- Use a T5 accent band as a visual divider (CTA, stat bar)
- Add a `border-top` to create subtle separation without a full background change
- Use `style="background: var(--pd-light);"` on the middle section

---

## 3. Card Carpet

**What it looks like:** 2 or more sections on the same page using identical card grid layouts (same column count, same card structure).

**Why it often weakens design:** If both your "Services" and "Why Choose Us" sections are 3-column card grids with icon-circle + title + text, the page feels generated from a single template.

**When this might be acceptable:** When the two card grids have clearly different purposes and visual treatments (one is a 3-column icon grid, the other is a 2-column comparison with highlighted borders). The key is that they shouldn't look like the same component copy-pasted.

**Fix strategies:**
- If one section uses cards, the other should use a different variant: icon+text rows (L1), numbered steps (L2), or two-column split list (L4)
- Vary column count: if services uses `col-md-4` (3 cards), features should use `col-md-6` (2 cards) or `col-md-3` (4 cards)
- Change card internals: one uses centered icon + text, the other uses left-aligned d-flex layout
- Switch one from cards to a different treatment entirely (T2 tinted band with icon rows)

---

## 4. Icon Assembly Line

**What it looks like:** Every list on the page uses the same icon pattern. Typically `<i class="bi bi-check-circle-fill text-success me-2">` before every list item, in every section.

**Why it often weakens design:** When check-circle icons mark every list item across 4 different sections, it's a strong signal that an AI generated the page with a single list template.

**When this might be acceptable:** A very short page where only one or two sections have lists, so the repetition isn't noticeable.

**Fix strategies:**
- Use check marks in one section, arrow-right in another, numbered steps in a third
- One section uses `bi-check2` (simple check), another uses `bi-arrow-right-circle`
- Replace icon lists with plain `<ul>` bullet points in at least one section
- Use step-number circles instead of icons for sequential content
- Use `bi-x-circle text-danger` for "what to avoid" lists alongside `bi-check-circle` for "what we offer"

---

## 5. Symmetry Overload

**What it looks like:** Every section on the page is center-aligned with symmetrical column layouts. All headings centered, all grids even, no asymmetric splits anywhere.

**Why it often weakens design:** Real pages mix centered and left-aligned content. All-centered feels like a default template choice rather than intentional design.

**When this might be acceptable:** A very short, conversion-focused page (like a landing page with 4-5 sections) where centered alignment creates a focused, funnel-like feel.

**Fix strategies:**
- Left-align headings in text-heavy sections (T1 Open Canvas)
- Use asymmetric splits (T4 Split Panel with `col-lg-7` + `col-lg-5`) for at least 2 sections
- Right-align a CTA button or form in at least one section
- Use `col-lg-8` (offset from center) for reading sections instead of `col-lg-12 text-center`

---

## 6. Table Tunnel

**What it looks like:** 3 or more tables on a single page without any alternative data presentation (cards, icon grids, accordions) between them.

**Why it often weakens design:** Tables are an easy default for AI because any comparison can be expressed as a table. Human designers use tables sparingly and choose the presentation that best fits the data type.

**When this might be acceptable:** A genuinely data-heavy reference page (like a pricing comparison or spec sheet) where tables are the clearest way to present the information and the audience expects tabular data.

**Fix strategies:**
- Replace one table with side-by-side comparison cards (D2)
- Replace one table with an icon key-value grid (D3)
- Use an accordion (D4) for dense reference data that not everyone needs
- Keep the most important comparison as a table, convert others to card or list formats

---

## 7. CTA Echo

**What it looks like:** The same CTA button text appears 2+ times verbatim on the page (e.g., "Get Free Quote" appears in 3 places).

**Why it often weakens design:** Progressive CTA text is a hallmark of professional pages. The button copy should evolve as the reader gains information and trust. Repeating the exact same text signals zero thought was given to the conversion flow.

**When this might be acceptable:** Very short pages (4-5 sections) where only 2 CTAs exist, or when the phone number CTA naturally repeats (phone numbers are exempt from this concern).

**Fix strategies:**
Use progressive CTA language that evolves:
- **Position 1 (hero):** Match the dominant intent. "Call (214) 555-1234" or "Get Free Quote"
- **Position 2 (after services/benefits):** Reference what they just learned. "Get a Quote for [Specific Service]"
- **Position 3 (mid-page):** Leverage accumulated trust. "Join 500+ Dallas Homeowners"
- **Position 4 (after testimonials):** Address remaining objections. "No obligation, no pressure"
- **Position 5 (final):** Close the argument. "Ready for [specific outcome]?"

---

## 8. Spacing Monotony

**What it looks like:** Every section on the page uses identical vertical padding (typically `py-5` on everything).

**Why it often weakens design:** Equal spacing means no section feels more or less important than any other. A designer would use tighter spacing for utility sections (trust bar, CTA band) and more generous spacing for major content sections.

**When this might be acceptable:** Very rarely. Even on simple pages, varying the spacing creates subtle visual rhythm that makes the page feel more crafted.

**Fix strategies:**
- Hero: `py-5` or `py-5 py-lg-6` (custom larger padding)
- Trust bar / stats: `py-3` (compact)
- Content sections: `py-5` (standard)
- CTA bands: `py-4` (slightly less than content)
- FAQ: `py-5` (standard)
- Final CTA: `py-5` (standard)
- Between related sections: reduce gap by removing top padding on the second: `pt-0 pb-5`

---

## 9. Anchor Collision

**What it looks like:** A section contains two competing visual anchors of similar visual weight (e.g., image + form, image + large stat, form + video).

**Why it often weakens design:** The eye bounces between the two anchors, unsure which to focus on. The reader doesn't instinctively know what action to take. This splits attention and reduces conversion.

**When this might be acceptable:** When the two elements have clearly different visual weights (one is a full-width background image, the other is text overlaid on it) so there's no actual competition for attention.

**Fix strategies:**
- Move one anchor to its own section (e.g., form moves below trust bar, image becomes background)
- Make one clearly dominant and the other supporting (e.g., image is the full-width background, text overlays it)
- For hero sections: choose one primary conversion element. For urgent intent, the phone CTA is the anchor. For planning intent, the form can be the anchor.

**Common cases:**
- Hero with image + form side by side: move form below trust bar, make image the full-width hero background
- Section with table + testimonial card: give each its own section
- CTA band with both a stat callout and a button: make the stat smaller/supporting, button is the anchor

---

## Design Review Prompts

After designing your layout, ask yourself these questions:

- Do adjacent sections have enough visual contrast? (Different backgrounds, layouts, or component styles)
- Does every section have something for the eye to land on before reading the text?
- Is the page scannable? (Can someone get the gist from just headings + bold text)
- Are at least 3 different content presentation formats used across the page?
- Is brand color reserved for interactive/important elements, not used as general decoration?
- Does the page mix symmetric and asymmetric layouts?
- Does CTA text evolve across positions on the page?
- Does spacing vary between sections based on their purpose?
- Are icon patterns varied across lists on the page?
