# Visual Design Review

Use this review to look at a page through a designer's eye. Each check highlights something a designer would notice. Not every flagged item needs fixing — context determines what matters.

## How to Review

1. Read the full HTML of the page
2. Walk through each check below
3. Record your findings: **Worth addressing**, **Worth noticing**, or **Worth considering**
4. Output the review summary (format at bottom)
5. If reviewing your own page: address the "worth addressing" items before outputting final HTML
6. If reviewing a reference/competitor page: output summary only

## Severity Guide

- **Worth addressing** — Things that frequently weaken design quality. Fix these unless you have a specific reason not to.
- **Worth noticing** — Things that might weaken the design depending on context. Consider whether they're problems for THIS page.
- **Worth considering** — Suggestions for refinement. Nice-to-haves, not defects.

---

## Structural Checks (parse HTML, no rendering needed)

### Check 1: H2 Parade
**Severity:** Worth noticing
**Detection:** Count consecutive `<section>` elements where the first visible content is `<h2>` followed by `<p>`. If 3+ in a row start with this identical pattern, flag it.
**What to look for:** Every section opener looks the same — heading, subtitle, content. No variation in how sections begin.
**Fix:** Lead one section with a badge/pill above the H2. Start another with a stat or icon. Center the heading in one section while left-aligning others.

### Check 2: White Wall
**Severity:** Worth addressing
**Detection:** Scan all `<section>` elements for their background. Sections with no background style, `background: #fff`, `background: white`, or no `bg-*` class count as "white." If 3+ consecutive sections are white, flag it.
**What to look for:** The page has a long stretch where nothing visually separates one topic from the next.
**Fix:** Insert a tinted band (`background: #f8f9fa` or `var(--pd-light)`), an accent band (T5), or a `border-top` between white sections.

### Check 3: Card Carpet
**Severity:** Worth noticing
**Detection:** Find all sections that contain a `.row` with multiple `.col-*` children containing `.card` elements. If 2+ sections use the same column count AND the same card internal structure (centered icon + title + text), flag it.
**What to look for:** Multiple sections that are visually identical grids of cards.
**Fix:** Change one section to icon+text rows (L1), numbered steps (L2), or a different column count. Vary card internals (centered vs left-aligned).

### Check 4: Icon Assembly Line
**Severity:** Worth noticing
**Detection:** Extract all `<i class="bi bi-*">` within `<ul>` or `<li>` elements. Group by icon class name. If the same icon class appears in lists across 3+ different sections, flag it.
**What to look for:** Every bullet point on the page uses `bi-check-circle-fill text-success` (or similar).
**Fix:** Rotate icons between sections: check marks in one, arrows in another, numbered steps in a third. Use plain `<ul>` bullets in at least one section.

### Check 5: Spacing Monotony
**Severity:** Worth noticing
**Detection:** Extract `py-*` classes from all `<section>` elements. If every section uses the same padding class (typically `py-5`), flag it.
**What to look for:** No visual distinction between major content sections, compact utility sections, and CTA bands.
**Fix:** Hero `py-5`, trust bar `py-3`, content sections `py-5`, CTA bands `py-4`, service areas `py-4`.

### Check 6: CTA Echo
**Severity:** Worth noticing
**Detection:** Extract text content from all `<a class="btn*">` and `<button>` elements. If the exact same text appears 2+ times across different sections, flag it. Phone numbers are exempt from this check.
**What to look for:** "Get Free Quote" or "Book Now" appearing identically 3 times.
**Fix:** Progress CTA text: hero intent-match, service-specific, social proof lever, objection handler, outcome-focused.

### Check 7: Table Tunnel
**Severity:** Worth noticing
**Detection:** Count `<table>` elements. If 3+ tables exist without card grids, accordions, or icon grids between them, flag it.
**What to look for:** Data is always presented as tables, never as cards, accordions, or comparison layouts.
**Fix:** Replace one table with side-by-side comparison cards (D2), icon key-value grid (D3), or accordion (D4).

### Check 8: Content Echo
**Severity:** Worth noticing
**Detection:** For each pair of adjacent sections, compare their text content for duplicate claims. If the same stat, credential, or feature is stated in both (e.g., "board certified" in badges AND trust bar, "same-day" in hero text AND trust bar), flag it.
**What to look for:** The reader sees the same fact twice within 2 seconds of scrolling.
**Fix:** Remove the duplicate from one section, or rephrase it to add new information.

### Check 9: Typography Scale Violation
**Severity:** Worth addressing
**Detection:**
- `display-4` class used more than once on the page (hero only)
- `.lead` class used more than once within any single `<section>`
- Heading hierarchy skips levels (e.g., H2 followed directly by H5 with no H3)
**What to look for:** Inconsistent text sizing that breaks the visual hierarchy.
**Fix:** Strict scale: `display-4/5` (hero) then `h2` (sections) then `h3/h5` (sub-sections) then body then small.

### Check 10: Progressive Disclosure Missing
**Severity:** Worth noticing
**Detection:** Find any `<ul>` or `<ol>` with 6+ `<li>` children, or any section with 6+ card items, that is NOT inside an accordion, tab interface, or collapsible container.
**What to look for:** Dense lists or grids that dump all information at once.
**Fix:** Convert to accordion, tabs, or "show first 3 / expand for more" pattern.

### Check 11: Accent Band Overuse
**Severity:** Worth noticing
**Detection:** Count sections with `background: var(--pd-primary)` or similar brand-color backgrounds. If more than 2, flag it.
**What to look for:** Brand color used so often for backgrounds that it loses impact.
**Fix:** Max 2 accent bands per page (typically mid-CTA + final CTA). Use `var(--pd-light)` or `#f8f9fa` for other tinted sections.

### Check 12: Em-Dash Detection
**Severity:** Worth noticing
**Detection:** Search page text content for `—` (U+2014 em-dash) or `–` (U+2013 en-dash).
**What to look for:** AI writing tell that makes content feel machine-generated.
**Fix:** Replace with colons, commas, periods, or parentheses.

### Check 13: Grid Alignment Inconsistency
**Severity:** Worth noticing
**Detection:** For sections with left-aligned content (not centered text sections), extract their column width classes. If some use `col-lg-8`, others `col-lg-10`, and others have no column wrapper (full container), flag the inconsistency.
**What to look for:** Left edge of content jumps around as you scroll, creating a jagged alignment.
**Fix:** Pick one consistent width for left-aligned content sections. Full `container` width is recommended. Use `col-lg-8 mx-auto` only for centered text sections (quotes, final CTAs).

---

## Visual/Compositional Checks (analyze layout relationships)

### Check 14: Anchor Collision
**Severity:** Worth addressing
**Detection:** For each section, identify elements that serve as visual anchors: `<img>` elements, `<form>` elements, elements with `display-*` classes (large stats), `.icon-circle-lg` elements. If a section contains 2+ of these at similar visual weight (e.g., both are large), flag it.
**What to look for:** The eye bounces between two competing elements, unclear which is primary.
**Fix:** Move one anchor to its own section. Or make one clearly dominant (background image) and the other supporting (overlaid text).

### Check 15: Visual Balance
**Severity:** Worth noticing
**Detection:** For split panel sections (T4 pattern: `.row` with 2 columns like `col-lg-7` + `col-lg-5`), estimate content height. If one column has 5+ content blocks and the other has 1, flag it.
**What to look for:** One column is tall and dense, the other has a small card floating at the top with empty space below.
**Fix:** Make it full-width (remove split), add content to short column, or use sticky positioning on the short column.

### Check 16: Symmetry Overload
**Severity:** Worth noticing
**Detection:** Count sections using `.text-center` on their heading or content wrapper. If more than 60% of content sections are center-aligned, flag it.
**What to look for:** Every section is centered, creating a monotonous, corporate feel.
**Fix:** Left-align headings in text-heavy sections (process, local knowledge, treatment). Use asymmetric splits (T4) for at least 2 sections.

### Check 17: Section Rhythm Violation
**Severity:** Worth addressing
**Detection:** For each pair of adjacent `<section>` elements, identify their treatment type:
- T1: white bg + single column + left-aligned
- T2: tinted bg (`#f8f9fa`, `var(--pd-light)`) + container content
- T3: white bg + card grid (`.row` with `.card` children)
- T4: any bg + asymmetric columns (`col-lg-7` + `col-lg-5` or similar)
- T5: brand-color bg + white text
- T6: white bg + inner box with border-left or shadow
- T7: background-image with overlay + text
If adjacent sections share the same treatment type, flag it.
**What to look for:** Two sections in a row that look visually identical in structure.
**Fix:** Swap one section's treatment. Consult the treatment selection reference in section-treatments.md.

### Check 18: Missing Visual Anchor
**Severity:** Worth noticing
**Detection:** For each section, check for at least one of: `<img>`, `.icon-circle`, `.step-number`, `.badge`, `blockquote`, `display-*` stat, callout box (`p-4 rounded-3` with colored bg), or `.accordion`. If a section contains only `<h2>` + `<p>` paragraphs with none of these, flag it.
**What to look for:** Sections that are pure text walls with nothing for the eye to grab onto.
**Fix:** Add a stat, icon, badge, callout box, or image to anchor the eye.

### Check 19: Undersized Trust Images
**Severity:** Worth noticing
**Detection:** Find `<img>` elements that appear in "meet the team" or doctor/team sections. Check their declared dimensions (width/height attributes or CSS). If smaller than 150px in their largest dimension, flag it.
**What to look for:** Tiny thumbnail headshots that don't build visual trust or connection.
**Fix:** Use card-style layout with large photo (aspect-ratio 3:4, full card width) or at minimum 200px circles.

### Check 20: Form vs Intent Mismatch
**Severity:** Worth noticing
**Detection:** If the page appears to be urgent-intent (keywords like "emergency", "sick visit", "same-day", "urgent"), check for `<form>` elements. If a form exists on an urgent-intent page, flag it.
**What to look for:** A "fill out this form and we'll call you back" on a page where the visitor needs help NOW.
**Fix:** Remove form from urgent pages. Phone CTA is the primary action. Link to contact page for after-hours booking.

---

## Content-Level Checks

### Check 21: Hero Has CTA
**Severity:** Worth addressing
**Detection:** Find the first `<section>` (hero). Check that it contains at least one `<a>` with `class="btn*"` or a `tel:` href.
**What to look for:** Hero section with no actionable button or phone link.
**Fix:** Add a prominent phone CTA button and/or a secondary action button.

### Check 22: CTA Progression
**Severity:** Worth considering
**Detection:** Extract all CTA button text in page order. Check if the text evolves across positions:
1. Hero: intent-match ("Call Now" or "Get Free Quote")
2. After services: service-specific ("Get Quote for [Service]")
3. Mid-page: social proof ("Join 500+ families")
4. After reviews: objection handler ("No obligation")
5. Final: outcome ("Ready for [benefit]?")
If all CTAs are generic or identical, note it.
**What to look for:** CTA text that gets more specific and confident as the reader scrolls deeper.

### Check 23: Image Alt Text
**Severity:** Worth noticing
**Detection:** Find all `<img>` elements. Check that each has an `alt` attribute that is not empty, not "image", and not just a filename.
**What to look for:** Missing or generic alt text that hurts accessibility and SEO.
**Fix:** Write descriptive alt text: "[Subject] at [Business] in [Location]" or similar.

### Check 24: Image Placeholders Documented
**Severity:** Worth considering
**Detection:** Find sections where images would be expected (hero, team, process, split panels) but no `<img>` or `background-image` exists. Check for an HTML comment describing the ideal image.
**What to look for:** Missing images with no guidance on what to photograph.
**Fix:** Add HTML comment: `<!-- IMAGE: [subject], [setting], [mood], [lighting] -->`.

---

## Review Summary Format

```
DESIGN REVIEW — [page name or URL]
========================================

Worth Addressing ([n]):
  #[n] [Check Name] — [specific finding]
  → Fix: [actionable suggestion]

Worth Noticing ([n]):
  #[n] [Check Name] — [specific finding]
  → Fix: [actionable suggestion]

Worth Considering ([n]):
  #[n] [Check Name] — [observation]
  → Suggestion: [optional improvement]

Passes ([n]):
  #1 H2 Parade — Sections use varied openers (badges, stats, icons)
  #2 White Wall — Background alternation: white, gray, white, green, gray
  [... list all passing checks ...]
```

## When to Run

- **After generating a page:** Run before outputting final HTML. Address the "worth addressing" items. Note "worth noticing" items for the user.
- **When asked to review a page:** Run on provided HTML file or URL (fetch via seo-extractor or WebFetch). Output summary only.
- **When comparing pages:** Run on both, show side-by-side summaries.

**A note on context:** When reviewing your own work, focus on the "worth addressing" items first. For competitor audits, the "worth noticing" items often reveal opportunities to differentiate. Not every flagged item is a problem — the goal is design awareness, not a perfect score.
