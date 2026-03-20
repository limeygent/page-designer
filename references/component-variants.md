# Component Variants

For each common content element, 3-4 visual presentations. A good instinct: when two sections present similar types of information (both are lists, both show data), using different visual variants prevents the page from feeling repetitive. This is almost always a good idea. If you use icon-rows for "Why Choose Us," consider numbered steps or card-items for "What We Offer."

---

## Lists / Feature Blocks

### Variant L1: Icon + Text Rows

The default for feature lists. Use `d-flex gap-3` for horizontal icon-text pairing. Best in 2-column layouts.

```html
<div class="row g-4">
  <div class="col-md-6">
    <div class="d-flex gap-3 align-items-start">
      <div class="icon-circle flex-shrink-0">
        <i class="bi bi-shield-check"></i>
      </div>
      <div>
        <h3 class="h6 fw-bold mb-1">Licensed and Insured</h3>
        <p class="text-muted small mb-0">TX License #TACLB12345. Full coverage on every job.</p>
      </div>
    </div>
  </div>
  <!-- more items... -->
</div>
```

### Variant L2: Numbered Steps

For sequential processes, timelines, or ranked items. The step number itself becomes the visual anchor.

```html
<div class="d-flex gap-3 mb-4">
  <div class="step-number flex-shrink-0">1</div>
  <div>
    <h3 class="h6 fw-bold mb-1">Call or Book Online</h3>
    <p class="text-muted mb-0">Tell us about the problem. We will confirm a time window.</p>
  </div>
</div>
<div class="d-flex gap-3 mb-4">
  <div class="step-number flex-shrink-0">2</div>
  <div>
    <h3 class="h6 fw-bold mb-1">On-Site Diagnosis</h3>
    <p class="text-muted mb-0">Written quote before any work starts.</p>
  </div>
</div>
<div class="d-flex gap-3">
  <div class="step-number flex-shrink-0">3</div>
  <div>
    <h3 class="h6 fw-bold mb-1">Complete and Follow Up</h3>
    <p class="text-muted mb-0">Job done, site cleaned, 48-hour follow-up call.</p>
  </div>
</div>
```

### Variant L3: Card-Style List Items

Each item gets its own contained card. Feels more modular and premium. Best for 3-4 items.

```html
<div class="row g-3">
  <div class="col-md-6 col-lg-3">
    <div class="card border-0 shadow-sm h-100 rounded-3">
      <div class="card-body p-4">
        <div class="icon-circle mb-3"><i class="bi bi-lightning-charge"></i></div>
        <h3 class="h6 fw-bold mb-2">Fast Response</h3>
        <p class="text-muted small mb-0">Average 47-minute arrival for emergency calls in the metro area.</p>
      </div>
    </div>
  </div>
  <!-- more cards... -->
</div>
```

### Variant L4: Two-Column Split List

Simple left-right split for 6+ items. No icons, just clean text with check marks or bullets. Compact and scannable.

```html
<div class="row">
  <div class="col-md-6">
    <ul class="list-unstyled">
      <li class="mb-2"><i class="bi bi-check2 me-2" style="color: var(--pd-primary);"></i>Leak detection and repair</li>
      <li class="mb-2"><i class="bi bi-check2 me-2" style="color: var(--pd-primary);"></i>Water heater installation</li>
      <li class="mb-2"><i class="bi bi-check2 me-2" style="color: var(--pd-primary);"></i>Drain cleaning</li>
    </ul>
  </div>
  <div class="col-md-6">
    <ul class="list-unstyled">
      <li class="mb-2"><i class="bi bi-check2 me-2" style="color: var(--pd-primary);"></i>Sewer line repair</li>
      <li class="mb-2"><i class="bi bi-check2 me-2" style="color: var(--pd-primary);"></i>Gas line service</li>
      <li class="mb-2"><i class="bi bi-check2 me-2" style="color: var(--pd-primary);"></i>Bathroom remodels</li>
    </ul>
  </div>
</div>
```

---

## Data / Comparisons

### Variant D1: Responsive Table

Standard table for structured data with many rows. Desktop shows full table; mobile wraps in `table-responsive`.

```html
<div class="table-responsive">
  <table class="table table-hover align-middle">
    <thead>
      <tr style="background: var(--pd-primary-light);">
        <th>Service</th>
        <th>Typical Cost Range</th>
        <th>Timeframe</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td class="fw-semibold">Leak Repair</td>
        <td>$150 - $450</td>
        <td>1 - 2 hours</td>
      </tr>
      <!-- more rows... -->
    </tbody>
  </table>
</div>
```

### Variant D2: Side-by-Side Comparison Cards

Two columns comparing options. Better than tables for binary comparisons (us vs. them, option A vs. option B).

```html
<div class="row g-4">
  <div class="col-md-6">
    <div class="p-4 rounded-3 h-100" style="background: var(--pd-light);">
      <h3 class="h5 fw-semibold text-muted mb-3">Tank Water Heater</h3>
      <ul class="list-unstyled">
        <li class="mb-2"><strong>Cost:</strong> $800 - $1,500 installed</li>
        <li class="mb-2"><strong>Lifespan:</strong> 8 - 12 years</li>
        <li class="mb-2"><strong>Hot water:</strong> 40-80 gallon reserve</li>
        <li><strong>Best for:</strong> Households with predictable usage</li>
      </ul>
    </div>
  </div>
  <div class="col-md-6">
    <div class="p-4 rounded-3 h-100 shadow-sm" style="border: 2px solid var(--pd-primary);">
      <h3 class="h5 fw-semibold mb-3" style="color: var(--pd-primary);">Tankless Water Heater</h3>
      <ul class="list-unstyled">
        <li class="mb-2"><strong>Cost:</strong> $2,500 - $4,500 installed</li>
        <li class="mb-2"><strong>Lifespan:</strong> 15 - 20 years</li>
        <li class="mb-2"><strong>Hot water:</strong> Unlimited on demand</li>
        <li><strong>Best for:</strong> Homes wanting long-term savings</li>
      </ul>
    </div>
  </div>
</div>
```

### Variant D3: Icon Key-Value Grid

For specifications, at-a-glance info, or feature snapshots. Each item is icon + label + value.

```html
<div class="row g-3 text-center">
  <div class="col-6 col-md-3">
    <div class="p-3">
      <i class="bi bi-clock fs-3 mb-2 d-block" style="color: var(--pd-primary);"></i>
      <div class="small text-muted">Response Time</div>
      <div class="fw-bold">Under 1 Hour</div>
    </div>
  </div>
  <div class="col-6 col-md-3">
    <div class="p-3">
      <i class="bi bi-calendar-check fs-3 mb-2 d-block" style="color: var(--pd-primary);"></i>
      <div class="small text-muted">Availability</div>
      <div class="fw-bold">24/7/365</div>
    </div>
  </div>
  <!-- more items... -->
</div>
```

### Variant D4: Accordion for Dense Data

When comparison data is long or complex (5+ rows), use accordion to prevent overwhelming the visitor.

```html
<div class="accordion accordion-flush" id="comparisonAccordion">
  <div class="accordion-item">
    <h3 class="accordion-header">
      <button class="accordion-button collapsed fw-semibold" data-bs-toggle="collapse" data-bs-target="#comp1">
        Tank vs. Tankless: Cost Comparison
      </button>
    </h3>
    <div id="comp1" class="accordion-collapse collapse" data-bs-parent="#comparisonAccordion">
      <div class="accordion-body">
        <!-- detailed comparison content -->
      </div>
    </div>
  </div>
  <!-- more items... -->
</div>
```

---

## Testimonials / Social Proof

### Variant R1: Card Row

Classic testimonial layout. 2-3 review cards in a row.

```html
<div class="row g-4">
  <div class="col-md-4">
    <div class="card border-0 shadow-sm h-100 rounded-3">
      <div class="card-body p-4">
        <div class="d-flex gap-1 mb-3">
          <i class="bi bi-star-fill text-warning"></i>
          <i class="bi bi-star-fill text-warning"></i>
          <i class="bi bi-star-fill text-warning"></i>
          <i class="bi bi-star-fill text-warning"></i>
          <i class="bi bi-star-fill text-warning"></i>
        </div>
        <p class="mb-3">"Quick, professional, and honest. They found the leak in 20 minutes and gave us options instead of pushing the expensive fix."</p>
        <div class="d-flex align-items-center gap-2">
          <div class="rounded-circle d-flex align-items-center justify-content-center" style="width: 36px; height: 36px; background: var(--pd-primary-light); color: var(--pd-primary);">
            <span class="fw-bold small">JM</span>
          </div>
          <div>
            <div class="fw-semibold small">James M.</div>
            <div class="text-muted" style="font-size: 0.75rem;">Plano, TX</div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <!-- more cards... -->
</div>
```

### Variant R2: Large Single Quote

One impactful testimonial, oversized. Good as a section break or after a process section.

```html
<div class="col-lg-8 mx-auto text-center">
  <i class="bi bi-quote display-4 d-block mb-3" style="color: var(--pd-primary); opacity: 0.3;"></i>
  <p class="fs-4 mb-4">"We called at 11pm on a Sunday. They answered, showed up by midnight, and stopped the flooding before it reached the living room. I cannot recommend them enough."</p>
  <div class="fw-semibold">Maria G.</div>
  <div class="small text-muted">McKinney, TX</div>
</div>
```

### Variant R3: Inline Callout with Accent Border

A testimonial embedded within another section as a callout. Compact, works as a trust signal within a content section.

```html
<div class="p-4 rounded-3 my-4" style="border-left: 4px solid var(--pd-primary); background: var(--pd-primary-light);">
  <p class="mb-2 fst-italic">"The upfront pricing was exactly what they charged. No surprises."</p>
  <div class="small fw-semibold">David K., Richardson</div>
</div>
```

### Variant R4: Photo + Quote Asymmetric

Testimonial with a profile image on one side. Creates visual interest through asymmetry.

```html
<div class="row align-items-center g-4">
  <div class="col-md-4 text-center">
    <div class="rounded-circle mx-auto overflow-hidden" style="width: 150px; height: 150px; background: var(--pd-light);">
      <i class="bi bi-person-fill display-3 text-muted" style="line-height: 150px;"></i>
    </div>
    <div class="fw-semibold mt-2">Sarah and Tom K.</div>
    <div class="small text-muted">Allen, TX</div>
  </div>
  <div class="col-md-8">
    <div class="d-flex gap-1 mb-2">
      <i class="bi bi-star-fill text-warning small"></i>
      <i class="bi bi-star-fill text-warning small"></i>
      <i class="bi bi-star-fill text-warning small"></i>
      <i class="bi bi-star-fill text-warning small"></i>
      <i class="bi bi-star-fill text-warning small"></i>
    </div>
    <p class="fs-5">"They converted us from a tank to tankless system in one day. Our gas bill dropped 30% the first month."</p>
  </div>
</div>
```

---

## CTAs (Calls to Action)

### Variant C1: Full-Width Accent Band

Bold, impossible to miss. Used as T5 accent band treatment. See `section-treatments.md` T5.

### Variant C2: Inline Button Pair

Two buttons side by side within a content section. Primary action + secondary action.

```html
<div class="d-flex flex-wrap gap-3 mt-4">
  <a href="tel:+12145551234" class="btn btn-pd btn-lg">
    <i class="bi bi-telephone-fill me-2"></i>Call (214) 555-1234
  </a>
  <a href="#quote" class="btn btn-pd-outline btn-lg">
    <i class="bi bi-calendar-check me-2"></i>Get Free Quote
  </a>
</div>
```

### Variant C3: Card-Style CTA

CTA inside a card container with supporting context. Feels less aggressive than a full-width band.

```html
<div class="col-lg-8 mx-auto">
  <div class="card border-0 shadow rounded-3">
    <div class="card-body p-4 p-lg-5 text-center">
      <h2 class="h4 fw-bold mb-2">Ready to get started?</h2>
      <p class="text-muted mb-4">Free estimates with no obligation. Most projects quoted within 24 hours.</p>
      <div class="d-flex flex-wrap justify-content-center gap-3">
        <a href="tel:+12145551234" class="btn btn-pd btn-lg">Call Now</a>
        <a href="#" class="btn btn-pd-outline btn-lg">Request Quote</a>
      </div>
      <p class="small text-muted mt-3 mb-0">
        <i class="bi bi-clock me-1"></i>Mon-Fri 7am to 7pm, Sat 8am to 4pm
      </p>
    </div>
  </div>
</div>
```

### Variant C4: Sticky Mobile Bar

Fixed to the bottom of the screen on mobile only. Always accessible without being intrusive on desktop.

```html
<div class="d-lg-none sticky-cta-mobile p-3">
  <div class="d-flex gap-2">
    <a href="tel:+12145551234" class="btn btn-pd flex-fill">
      <i class="bi bi-telephone-fill me-1"></i>Call Now
    </a>
    <a href="#quote" class="btn btn-pd-outline flex-fill">
      <i class="bi bi-chat-text me-1"></i>Text Us
    </a>
  </div>
</div>
```

---

## Process / Steps

### Variant P1: Numbered Steps (Vertical)

See Variant L2 above. Vertical numbered list with step circles.

### Variant P2: Horizontal Timeline

Steps laid out horizontally with connecting visual. Best for 3-4 steps.

```html
<div class="row g-4 text-center">
  <div class="col-md-4 position-relative">
    <div class="step-number mx-auto mb-3">1</div>
    <h3 class="h6 fw-bold">Call Us</h3>
    <p class="text-muted small">Describe the issue. We dispatch within 30 minutes.</p>
    <!-- connector line (desktop only) -->
    <div class="d-none d-md-block position-absolute top-0 start-100" style="width: 100%; height: 2px; background: var(--pd-primary-light); margin-top: 24px; transform: translateX(-50%); z-index: 0;"></div>
  </div>
  <div class="col-md-4 position-relative">
    <div class="step-number mx-auto mb-3">2</div>
    <h3 class="h6 fw-bold">We Diagnose</h3>
    <p class="text-muted small">On-site inspection with a written quote before work begins.</p>
    <div class="d-none d-md-block position-absolute top-0 start-100" style="width: 100%; height: 2px; background: var(--pd-primary-light); margin-top: 24px; transform: translateX(-50%); z-index: 0;"></div>
  </div>
  <div class="col-md-4">
    <div class="step-number mx-auto mb-3">3</div>
    <h3 class="h6 fw-bold">Problem Solved</h3>
    <p class="text-muted small">Same-day completion for most jobs. 48-hour follow-up.</p>
  </div>
</div>
```

### Variant P3: Alternating Image/Text

Each step alternates which side the visual is on. Creates a zigzag reading pattern.

```html
<!-- Step 1: text left, image right -->
<div class="row align-items-center g-4 mb-5">
  <div class="col-md-6">
    <div class="d-flex gap-3">
      <div class="step-number flex-shrink-0">1</div>
      <div>
        <h3 class="h5 fw-bold mb-2">Initial Consultation</h3>
        <p class="text-muted">We walk your property and discuss your vision, budget, and timeline.</p>
      </div>
    </div>
  </div>
  <div class="col-md-6">
    <div class="rounded-3 overflow-hidden" style="background: var(--pd-light); height: 200px;">
      <!-- image placeholder -->
    </div>
  </div>
</div>

<!-- Step 2: image left, text right (reversed) -->
<div class="row align-items-center g-4 mb-5">
  <div class="col-md-6 order-md-2">
    <div class="d-flex gap-3">
      <div class="step-number flex-shrink-0">2</div>
      <div>
        <h3 class="h5 fw-bold mb-2">Custom Design</h3>
        <p class="text-muted">3D render of your pool in your actual backyard.</p>
      </div>
    </div>
  </div>
  <div class="col-md-6 order-md-1">
    <div class="rounded-3 overflow-hidden" style="background: var(--pd-light); height: 200px;">
      <!-- image placeholder -->
    </div>
  </div>
</div>
```

### Variant P4: Icon Grid

Steps presented as a grid of icon-circles with labels. Compact, good for simple processes.

```html
<div class="row g-4 text-center">
  <div class="col-6 col-md-3">
    <div class="icon-circle-lg mx-auto mb-3"><i class="bi bi-telephone"></i></div>
    <h3 class="h6 fw-bold">1. Call</h3>
    <p class="text-muted small">Describe the problem</p>
  </div>
  <div class="col-6 col-md-3">
    <div class="icon-circle-lg mx-auto mb-3"><i class="bi bi-search"></i></div>
    <h3 class="h6 fw-bold">2. Diagnose</h3>
    <p class="text-muted small">On-site inspection</p>
  </div>
  <div class="col-6 col-md-3">
    <div class="icon-circle-lg mx-auto mb-3"><i class="bi bi-tools"></i></div>
    <h3 class="h6 fw-bold">3. Repair</h3>
    <p class="text-muted small">Same-day fix</p>
  </div>
  <div class="col-6 col-md-3">
    <div class="icon-circle-lg mx-auto mb-3"><i class="bi bi-hand-thumbs-up"></i></div>
    <h3 class="h6 fw-bold">4. Guarantee</h3>
    <p class="text-muted small">2-year warranty</p>
  </div>
</div>
```
