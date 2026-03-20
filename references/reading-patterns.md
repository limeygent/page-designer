# Reading Patterns and Layout Mapping

Three dominant patterns from eye-tracking research. Each one maps to specific Bootstrap layout decisions and section types.

---

## F-Pattern

**How it works:** The eye scans horizontally across the top of a section, drops down, scans a shorter horizontal line, then scans vertically down the left side. Content on the right side of the page gets decreasing attention.

**When it happens:** Text-heavy content where the visitor is reading (not scanning). Educational sections, detailed explanations, FAQ answers, long-form content.

**Layout implications:**
- Left-align all content. Centering fights the F-pattern.
- Important information goes in the first sentence of each paragraph (the horizontal scan).
- Use narrow containers (`col-lg-8` or `max-width: 720px`) to keep line length readable.
- Bold key phrases within paragraphs since the vertical scan catches bolded text.
- Lists and subheadings break up the vertical scan and re-trigger horizontal reads.

**Bootstrap pattern:**
```html
<section class="py-5">
  <div class="container">
    <div class="row">
      <div class="col-lg-8">
        <h2 class="fw-bold mb-3">Section Heading</h2>
        <p class="lead text-muted mb-4">Key summary sentence (first horizontal scan).</p>
        <p><strong>Important point</strong> followed by supporting detail. The bold phrase
        catches the vertical scan.</p>
        <h3 class="h5 fw-semibold mt-4 mb-2">Sub-heading (re-triggers horizontal scan)</h3>
        <p>More detail...</p>
      </div>
    </div>
  </div>
</section>
```

**Best for sections:** Educational content, FAQ expanded answers, process explanations, local knowledge, about/story sections.

---

## Z-Pattern

**How it works:** The eye follows a Z-shape: top-left to top-right (first scan), diagonal down-left (transition), bottom-left to bottom-right (second scan). This creates four focal points:
1. Top-left: Primary heading/message
2. Top-right: Trust signal or supporting element
3. Bottom-left: Supporting detail or secondary message
4. Bottom-right: Call to action

**When it happens:** Sections with less text where the visitor is scanning, not reading. Hero sections, CTA bands, feature highlights, pricing sections.

**Layout implications:**
- Two-column layouts naturally support the Z. Text left, visual/CTA right.
- The diagonal (points 2 to 3) is the weakest spot. Don't put critical info there.
- The bottom-right is the strongest CTA position. Place your button there.
- Works best with concise content (not paragraphs of text).

**Bootstrap pattern:**
```html
<section class="py-5" style="background: linear-gradient(135deg, var(--pd-light) 0%, #fff 100%);">
  <div class="container">
    <div class="row align-items-center g-4">
      <div class="col-lg-7">
        <!-- Top-left: Heading (point 1) -->
        <h1 class="display-5 fw-bold mb-3">Primary Message Here</h1>
        <!-- Bottom-left: Supporting detail (point 3) -->
        <p class="lead mb-4">Supporting details and value proposition.</p>
        <!-- Bottom area: CTA (point 4 flows naturally) -->
        <div class="d-flex flex-wrap gap-3">
          <a href="#" class="btn btn-pd btn-lg">Primary Action</a>
          <a href="#" class="btn btn-pd-outline btn-lg">Secondary Action</a>
        </div>
      </div>
      <div class="col-lg-5">
        <!-- Top-right: Trust signal or visual (point 2) -->
        <div class="card shadow rounded-3">
          <div class="card-body p-4">
            <!-- Form, image, or trust content -->
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
```

**Best for sections:** Hero, mid-page CTA, pricing cards, guarantee/warranty, final CTA.

---

## Gutenberg Diagram (Terminal Areas)

**How it works:** In a grid of equally-weighted items, the eye follows gravity: top-left (primary optical area) to bottom-right (terminal area). The top-right and bottom-left are "fallow areas" that receive less attention.

**When it happens:** Grid layouts where all items are similar (cards, features, services, team members). No single item dominates.

**Layout implications:**
- Put the most important item in the top-left position of the grid.
- Put the CTA or desired action in the bottom-right position.
- Top-right and bottom-left items get the least attention. Place less-critical items there.
- Works with 3-column and 4-column grids. Less effective with 2-column (which becomes Z-pattern).

**Bootstrap pattern:**
```html
<section class="py-5">
  <div class="container">
    <div class="text-center mb-5">
      <h2 class="fw-bold">Our Services</h2>
    </div>
    <div class="row g-4">
      <!-- Top-left: most important service (primary optical area) -->
      <div class="col-sm-6 col-lg-4">
        <div class="card card-hover h-100 shadow-sm">...</div>
      </div>
      <!-- Top-center: second most important -->
      <div class="col-sm-6 col-lg-4">
        <div class="card card-hover h-100 shadow-sm">...</div>
      </div>
      <!-- Top-right: fallow area -->
      <div class="col-sm-6 col-lg-4">
        <div class="card card-hover h-100 shadow-sm">...</div>
      </div>
      <!-- Bottom-left: fallow area -->
      <div class="col-sm-6 col-lg-4">
        <div class="card card-hover h-100 shadow-sm">...</div>
      </div>
      <!-- Bottom-center -->
      <div class="col-sm-6 col-lg-4">
        <div class="card card-hover h-100 shadow-sm">...</div>
      </div>
      <!-- Bottom-right: terminal area (CTA card or most converting service) -->
      <div class="col-sm-6 col-lg-4">
        <div class="card card-hover h-100 shadow-sm border-2" style="border-color: var(--pd-primary) !important;">
          <!-- highlighted card -->
        </div>
      </div>
    </div>
  </div>
</section>
```

**Best for sections:** Services grid, feature cards, team members, pricing tiers, benefits grid.

---

## Intent-to-Pattern Mapping

The dominant intent driver shapes which reading patterns tend to appear most on the page. These are tendencies, not prescriptions — a fear/urgency page might still have one strong F-pattern section for educational content, and a research page will use Z-pattern for its hero and CTA breaks.

| Intent Driver | Tends Toward | Layout Emphasis |
|---|---|---|
| **Fear / Urgency** | Z-pattern dominant | Quick scans, two-column hero with phone CTA, accent band CTAs. Minimize F-pattern (they are not going to read paragraphs). |
| **Hope / Aspiration** | Mix of Z and Gutenberg | Visual showcase grids (Gutenberg), aspirational hero (Z), spacious layouts |
| **Uncertainty / Research** | F-pattern dominant | Left-aligned reading sections, comparison content, detailed FAQ. Use Z for hero and CTA breaks. |
| **Problem Resolution** | Z-pattern into F-pattern | Z-pattern hero (problem acknowledgment + CTA), then F-pattern for process steps and educational content |

### Emergency pages (fear + urgency)
- Hero: Z-pattern (phone number in top-right focal point)
- Trust bar: Gutenberg (4 equally weighted trust signals)
- CTA: Z-pattern (heading left, button right)
- Minimal F-pattern sections (people in crisis don't read)

### Planning pages (hope + research)
- Hero: Z-pattern (value prop + form/image)
- Services: Gutenberg (card grid)
- Educational sections: F-pattern (left-aligned, narrow)
- Testimonials: vary between Z and Gutenberg
- FAQ: F-pattern (reading content)

### Hybrid pages (mixed urgency)
- Hero: Z-pattern with dual-path triage
- Balance of all three patterns across sections
- Emergency path sections use Z, planning path sections use F

---

## Section-Pattern Quick Reference

| Section Type | Reading Pattern | Alignment | Container Width |
|---|---|---|---|
| Hero | Z-pattern | Left-aligned text + right visual | Full container |
| Trust bar | Gutenberg | Center-aligned | Full container |
| Services grid | Gutenberg | Center heading, grid content | Full container |
| Why choose | F or Gutenberg | Left-aligned (F) or centered grid (G) | `col-lg-10` or full |
| Process steps | F-pattern | Left-aligned | `col-lg-8` or split panel |
| Testimonials | Z or Gutenberg | Varies by variant | `col-lg-8` (single) or full (cards) |
| FAQ | F-pattern | Left-aligned | `col-lg-8 mx-auto` |
| CTA band | Z-pattern | Left text, right button | Full container |
| Pricing | Gutenberg | Center-aligned grid | Full container |
| Local knowledge | F-pattern | Left-aligned | `col-lg-8` |
| About/team | Z or F-pattern | Split panel or left-aligned | Full container |
| Final CTA | Z-pattern | Centered or split | `col-lg-8 mx-auto` or full |
