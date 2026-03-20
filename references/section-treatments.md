# Section Treatments

7 visual treatments that give each section its own character. Think of these as a palette — you wouldn't paint a canvas with only one color, and you'd consider which colors work well next to each other.

Variety across treatments creates the feeling of a hand-designed page. If you notice two adjacent sections sharing the same visual structure, consider whether a different treatment would create better contrast. The goal is visual interest, not mechanical non-repetition.

---

## T7: Full-Width Image Hero

**Character:** Immersive, emotional, high-impact. The image IS the section. Sets the tone for the entire page.
**Background:** Full-width background image with dark gradient overlay for text legibility
**Layout:** Single column text overlay (col-lg-8), left-aligned
**Best for:** Hero sections only. Max 1 per page.
**Reading pattern:** Z-pattern (badges top-left, heading center-left, CTA bottom-left)

Images are a conversion tool, not decoration. They create emotional connection (a parent sees a safe medical environment and their anxiety drops), provide a pattern interrupt (breaks the "sea of text" that every competitor has), and motivate scrolling (a visually appealing hero signals the rest of the page is worth reading).

**When to use T7 vs T4 (Split Panel) for heroes:**
- **T7 (full-width image):** Urgent/fear intent. The emotional reassurance of the image matters more than a sidebar form or info card. Phone CTA is the primary action.
- **T4 (split panel):** Planning/research intent. The right column can hold a form, comparison card, or info sidebar because the visitor is browsing, not in crisis.

```html
<!-- IMAGE PLACEHOLDER: Describe the ideal image in an HTML comment -->
<!-- e.g., "Friendly pediatrician examining child, warm lighting, parent nearby" -->
<section id="hero" class="zone-group py-5" style="background: linear-gradient(rgba(0,0,0,0.45), rgba(0,0,0,0.55)), url('hero-image.jpg') center/cover no-repeat; min-height: 480px; display: flex; align-items: center;">
  <div class="container">
    <div class="row">
      <div class="col-lg-8">
        <div class="d-flex flex-wrap gap-2 mb-3">
          <span class="badge rounded-pill p-2 px-3" style="background: rgba(255,255,255,0.15); color: #fff; backdrop-filter: blur(4px);">
            <i class="bi bi-shield-check me-1"></i>Trust Signal 1
          </span>
          <span class="badge rounded-pill p-2 px-3" style="background: rgba(255,255,255,0.15); color: #fff; backdrop-filter: blur(4px);">
            <i class="bi bi-clock me-1"></i>Trust Signal 2
          </span>
        </div>
        <h1 class="display-5 fw-bold mb-3 text-white">Page Headline Here</h1>
        <p class="lead mb-4 text-white opacity-85">Supporting value proposition, 1-2 sentences max.</p>
        <div class="d-flex flex-wrap gap-3">
          <a href="tel:+1234567890" class="btn btn-pd btn-lg">
            <i class="bi bi-telephone-fill me-2"></i>Call Now
          </a>
          <a href="#lead-form" class="btn btn-outline-light btn-lg fw-semibold">
            <i class="bi bi-calendar-check me-2"></i>Book Online
          </a>
        </div>
      </div>
    </div>
  </div>
</section>
```

**Image placeholder rule:** When no real image is available, use the gradient over `var(--pd-light)` as a temporary background, and include an HTML comment describing the ideal image in detail (subject, setting, mood, lighting).

**Responsive behavior:**
- Desktop: full viewport width, min-height 480px, text left-aligned in col-lg-8
- Tablet: same layout, min-height 400px
- Mobile: stacks naturally, min-height 360px, full-width text

---

## T1: Open Canvas

**Character:** Clean, spacious, text-focused. The page "exhales" here.
**Background:** White (`#fff`)
**Layout:** Single column, left-aligned or narrow centered
**Best for:** Introductions, educational text, process explanations, long-form content
**Reading pattern:** F-pattern (left-aligned scan)

```html
<section class="zone-group py-5">
  <div class="container">
    <div class="row">
      <div class="col-lg-8">
        <h2 class="fw-bold mb-3">Section Heading</h2>
        <p class="lead text-muted mb-4">One-sentence section summary.</p>
        <p>Body content with natural paragraph flow. This treatment works because
        it gives dense content room to breathe. The narrow column width (col-lg-8)
        keeps line length readable at ~65-75 characters.</p>
        <p>Second paragraph continues the narrative...</p>
      </div>
    </div>
  </div>
</section>
```

**Variations:**
- Center-aligned: `col-lg-8 mx-auto text-center` for mission statements or key messages
- With accent border: add `accent-border-left` class to the content column for emphasis
- With callout box: insert a `bg-brand-light p-4 rounded-3` callout mid-content

---

## T2: Tinted Band

**Character:** Grouped, distinct from neighbors. Signals "this is a self-contained topic."
**Background:** `var(--pd-light)` (#f8f9fa) or `var(--pd-primary-light)` for stronger brand feel
**Layout:** Full-width background band with `container` inside
**Best for:** Why-choose sections, benefits, trust signals, feature lists, comparisons
**Reading pattern:** F-pattern or Gutenberg (depending on content)

```html
<section class="zone-group py-5" style="background: var(--pd-light);">
  <div class="container">
    <div class="text-center mb-5">
      <h2 class="fw-bold">Why Homeowners Choose Us</h2>
      <p class="text-muted">Serving Dallas-Fort Worth since 2008</p>
    </div>
    <div class="row g-4">
      <div class="col-md-6">
        <div class="d-flex gap-3 align-items-start">
          <div class="icon-circle flex-shrink-0">
            <i class="bi bi-shield-check"></i>
          </div>
          <div>
            <h3 class="h5 fw-semibold mb-1">Licensed and Insured</h3>
            <p class="text-muted mb-0">TX License #12345. $2M liability coverage on every job.</p>
          </div>
        </div>
      </div>
      <div class="col-md-6">
        <div class="d-flex gap-3 align-items-start">
          <div class="icon-circle flex-shrink-0">
            <i class="bi bi-clock-history"></i>
          </div>
          <div>
            <h3 class="h5 fw-semibold mb-1">Same-Day Response</h3>
            <p class="text-muted mb-0">Average arrival time: 47 minutes for emergencies.</p>
          </div>
        </div>
      </div>
      <div class="col-md-6">
        <div class="d-flex gap-3 align-items-start">
          <div class="icon-circle flex-shrink-0">
            <i class="bi bi-star-fill"></i>
          </div>
          <div>
            <h3 class="h5 fw-semibold mb-1">4.9 Stars from 380+ Reviews</h3>
            <p class="text-muted mb-0">Consistently rated the top plumber on Google in North Dallas.</p>
          </div>
        </div>
      </div>
      <div class="col-md-6">
        <div class="d-flex gap-3 align-items-start">
          <div class="icon-circle flex-shrink-0">
            <i class="bi bi-cash-stack"></i>
          </div>
          <div>
            <h3 class="h5 fw-semibold mb-1">Upfront Pricing</h3>
            <p class="text-muted mb-0">Written quote before work begins. No surprise charges.</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
```

**Variations:**
- 3-column: `col-md-4` for 3 items, centered heading
- Brand-tinted: `background: var(--pd-primary-light)` for stronger brand association
- With divider: add `<hr class="my-4 opacity-10">` between grouped items

---

## T3: Card Grid

**Character:** Scannable, modular. Each card is a self-contained unit.
**Background:** White (`#fff`)
**Layout:** 2-4 equal-width cards in a row
**Best for:** Services menu, features, team members, pricing tiers
**Reading pattern:** Gutenberg (equal visual weight across cells)

```html
<section class="zone-group py-5">
  <div class="container">
    <div class="text-center mb-5">
      <h2 class="fw-bold">Our Services</h2>
      <p class="text-muted">Residential and commercial plumbing across Dallas-Fort Worth</p>
    </div>
    <div class="row g-4">
      <div class="col-sm-6 col-lg-3">
        <div class="card card-hover h-100 shadow-sm rounded-3">
          <div class="card-body p-4 text-center">
            <div class="icon-circle-lg mx-auto mb-3">
              <i class="bi bi-droplet-half"></i>
            </div>
            <h3 class="h5 fw-semibold mb-2">Leak Repair</h3>
            <p class="text-muted small mb-3">Fast detection and repair of hidden and visible leaks in pipes, faucets, and fixtures.</p>
            <a href="#" class="btn btn-sm btn-pd-outline">Learn more</a>
          </div>
        </div>
      </div>
      <div class="col-sm-6 col-lg-3">
        <div class="card card-hover h-100 shadow-sm rounded-3">
          <div class="card-body p-4 text-center">
            <div class="icon-circle-lg mx-auto mb-3">
              <i class="bi bi-thermometer-half"></i>
            </div>
            <h3 class="h5 fw-semibold mb-2">Water Heaters</h3>
            <p class="text-muted small mb-3">Installation, repair, and maintenance for tank and tankless water heater systems.</p>
            <a href="#" class="btn btn-sm btn-pd-outline">Learn more</a>
          </div>
        </div>
      </div>
      <!-- 2 more cards... -->
    </div>
  </div>
</section>
```

**Variations:**
- 2-column: `col-md-6` for fewer, larger cards (pricing, comparisons)
- 3-column: `col-md-4` for feature trios
- With image top: `<img src="..." class="card-img-top" alt="...">` before card-body
- Left-aligned cards: remove `text-center`, use `d-flex gap-3` with icon on left

---

## T4: Split Panel

**Character:** Dynamic, visual + text balance. Creates visual interest through asymmetry.
**Background:** White or gradient
**Layout:** Asymmetric columns (60/40 or 50/50)
**Best for:** Hero sections, differentiators, case studies, about/team, process with imagery
**Reading pattern:** Z-pattern (eye crosses from left column to right)

```html
<section class="zone-group py-5">
  <div class="container">
    <div class="row align-items-center g-4 g-lg-5">
      <div class="col-lg-7">
        <span class="badge rounded-pill px-3 py-2 mb-3" style="background: var(--pd-primary-light); color: var(--pd-primary-dark);">
          How It Works
        </span>
        <h2 class="fw-bold mb-3">From Call to Completion in 3 Steps</h2>
        <div class="d-flex gap-3 mb-4">
          <div class="step-number">1</div>
          <div>
            <h3 class="h6 fw-bold mb-1">Call or Book Online</h3>
            <p class="text-muted mb-0">Describe the issue. We will give you a time window and a technician name.</p>
          </div>
        </div>
        <div class="d-flex gap-3 mb-4">
          <div class="step-number">2</div>
          <div>
            <h3 class="h6 fw-bold mb-1">On-Site Diagnosis</h3>
            <p class="text-muted mb-0">Your technician inspects the problem and gives you a written quote before touching anything.</p>
          </div>
        </div>
        <div class="d-flex gap-3">
          <div class="step-number">3</div>
          <div>
            <h3 class="h6 fw-bold mb-1">Fix and Follow-Up</h3>
            <p class="text-muted mb-0">Work completed same-day in most cases. We follow up within 48 hours to confirm everything is working.</p>
          </div>
        </div>
      </div>
      <div class="col-lg-5">
        <div class="card border-0 shadow rounded-3 overflow-hidden">
          <!-- Image placeholder or sidebar content -->
          <div class="p-5 text-center" style="background: var(--pd-light);">
            <i class="bi bi-image display-1 text-muted opacity-25"></i>
            <p class="text-muted small mt-2">Image: technician at work</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
```

**Variations:**
- Reversed: image/visual on left (`order-lg-1`), text on right (`order-lg-2`)
- 50/50: `col-lg-6` each for balanced split
- With form: right column contains a lead capture form instead of an image
- Gradient background: `style="background: linear-gradient(135deg, var(--pd-light) 0%, #fff 100%);"` for hero

---

## T5: Accent Band

**Character:** High impact, brand statement. Breaks the white/gray monotony with bold color.
**Background:** `var(--pd-primary)` with white text
**Layout:** Centered, compact padding (`py-4`)
**Best for:** CTA bands, key statistics, guarantees, special offers
**Reading pattern:** Z-pattern (heading left/center, CTA right)
**Usage limit:** Maximum 2 per page. Overuse dilutes the impact.

```html
<section class="zone-group py-4" style="background: var(--pd-primary);">
  <div class="container">
    <div class="row align-items-center">
      <div class="col-lg-8">
        <h2 class="h4 fw-bold text-white mb-1">Ready to get your pool project started?</h2>
        <p class="text-white opacity-75 mb-lg-0">Free custom quote with 3D design preview. No obligation.</p>
      </div>
      <div class="col-lg-4 text-lg-end">
        <a href="tel:+12145551234" class="btn btn-light btn-lg fw-semibold me-2">
          <i class="bi bi-telephone-fill me-2"></i>Call Now
        </a>
        <a href="#" class="btn btn-outline-light btn-lg fw-semibold">
          Get Free Quote
        </a>
      </div>
    </div>
  </div>
</section>
```

**Variations:**
- Stats band: 3-4 stats in columns with `display-6 fw-bold text-white` numbers
- Guarantee band: centered text with shield icon, single line
- Dark variant: `background: var(--pd-dark)` instead of brand color for a different accent

```html
<!-- Stats variant -->
<section class="py-4" style="background: var(--pd-primary);">
  <div class="container">
    <div class="row text-center text-white g-3">
      <div class="col-6 col-md-3">
        <div class="display-6 fw-bold">15+</div>
        <div class="small opacity-75">Years Experience</div>
      </div>
      <div class="col-6 col-md-3">
        <div class="display-6 fw-bold">2,400+</div>
        <div class="small opacity-75">Pools Installed</div>
      </div>
      <div class="col-6 col-md-3">
        <div class="display-6 fw-bold">4.9</div>
        <div class="small opacity-75">Google Rating</div>
      </div>
      <div class="col-6 col-md-3">
        <div class="display-6 fw-bold">Lifetime</div>
        <div class="small opacity-75">Structural Warranty</div>
      </div>
    </div>
  </div>
</section>
```

---

## T6: Boxed Container

**Character:** Featured, contained. A "spotlight" on specific content.
**Background:** White page background with an inner box that has visual distinction
**Layout:** Container with border-left, shadow, or subtle background
**Best for:** Testimonial callouts, pricing highlights, guarantees, featured content, comparison callouts
**Reading pattern:** Gutenberg or F-pattern depending on content

```html
<section class="zone-group py-5">
  <div class="container">
    <div class="row">
      <div class="col-lg-8 mx-auto">
        <div class="p-4 p-lg-5 rounded-3 shadow-sm" style="border-left: 5px solid var(--pd-primary);">
          <div class="d-flex gap-2 mb-3">
            <i class="bi bi-star-fill text-warning"></i>
            <i class="bi bi-star-fill text-warning"></i>
            <i class="bi bi-star-fill text-warning"></i>
            <i class="bi bi-star-fill text-warning"></i>
            <i class="bi bi-star-fill text-warning"></i>
          </div>
          <blockquote class="fs-5 mb-3">
            "They showed up within an hour, diagnosed the issue in minutes, and had our AC running
            before dinner. The price was exactly what they quoted on the phone."
          </blockquote>
          <div class="d-flex align-items-center gap-3">
            <div class="rounded-circle bg-light d-flex align-items-center justify-content-center" style="width: 48px; height: 48px;">
              <i class="bi bi-person-fill text-muted fs-5"></i>
            </div>
            <div>
              <div class="fw-semibold">Sarah M.</div>
              <div class="small text-muted">Frisco, TX</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
```

**Variations:**
- Shadow box: `shadow` instead of `border-left` for floating card effect
- Brand background box: `style="background: var(--pd-primary-light);"` with no shadow
- Side-by-side boxes: two `col-md-6` boxes for comparison (e.g., "Before / After" or "With us / Without us")
- Pricing box: centered with price as `display-5 fw-bold`, features list below

```html
<!-- Comparison variant -->
<section class="zone-group py-5">
  <div class="container">
    <h2 class="fw-bold text-center mb-5">What Makes Us Different</h2>
    <div class="row g-4">
      <div class="col-md-6">
        <div class="p-4 rounded-3 h-100" style="background: var(--pd-light);">
          <h3 class="h5 fw-semibold text-muted mb-3">Typical Pool Contractor</h3>
          <ul class="list-unstyled mb-0">
            <li class="mb-2"><i class="bi bi-x-circle text-danger me-2"></i>Generic designs from a catalog</li>
            <li class="mb-2"><i class="bi bi-x-circle text-danger me-2"></i>Subcontractors you have never met</li>
            <li class="mb-2"><i class="bi bi-x-circle text-danger me-2"></i>Weather delays with no communication</li>
            <li><i class="bi bi-x-circle text-danger me-2"></i>Warranty limited to 1 year</li>
          </ul>
        </div>
      </div>
      <div class="col-md-6">
        <div class="p-4 rounded-3 h-100 shadow-sm" style="border: 2px solid var(--pd-primary);">
          <h3 class="h5 fw-semibold mb-3" style="color: var(--pd-primary);">Sunshine Pools</h3>
          <ul class="list-unstyled mb-0">
            <li class="mb-2"><i class="bi bi-check-circle-fill me-2" style="color: var(--pd-primary);"></i>Custom 3D design for your exact yard</li>
            <li class="mb-2"><i class="bi bi-check-circle-fill me-2" style="color: var(--pd-primary);"></i>Our own crew, start to finish</li>
            <li class="mb-2"><i class="bi bi-check-circle-fill me-2" style="color: var(--pd-primary);"></i>Daily photo updates via app</li>
            <li><i class="bi bi-check-circle-fill me-2" style="color: var(--pd-primary);"></i>Lifetime structural warranty</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</section>
```

---

## Treatment Selection Quick Reference

Use this table when assigning treatments to your section sequence:

| Section Type | Often Works Well | Less Common For |
|---|---|---|
| Hero | T7 (full-width image) or T4 (split panel) | T2, T6 |
| Trust bar / stats | T5 (accent band) or T2 (tinted) | T1, T3 |
| Services grid | T3 (card grid) | T5 |
| Why choose / benefits | T2 (tinted band) | T5 |
| Process / how it works | T4 (split panel) or T1 (open canvas) | T5 |
| Testimonials | T6 (boxed container) or T2 (tinted) | T3 |
| FAQ | T1 (open canvas) or T2 (tinted) | T5, T3 |
| Mid-page CTA | T5 (accent band) | T1, T3 |
| Pricing | T6 (boxed container) or T3 (card grid) | T5 |
| Team / about | T4 (split panel) or T3 (card grid) | T5 |
| Final CTA | T4 (split panel) or T5 (accent band) | T1 |
| Comparison / diagnostic | T6 (boxed container) or T1 (open canvas) | T5 |
| Local knowledge | T2 (tinted band) or T1 (open canvas) | T3, T5 |
