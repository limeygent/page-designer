# Layout Blueprint Examples

These show what a page-designer blueprint looks like before content is written. The blueprint defines the visual structure; the service-page skill (or content-council) fills each section with appropriate content afterward.

There's no single required format. Some designers prefer a structured table, others a narrative sketch. The thinking behind the layout matters more than how you document it.

---

## Format A: Structured Table Blueprint

### Page: Emergency Plumber Dallas

**Intent profile:**
- Emotional drivers: Fear (water damage), urgency (active leak)
- Functional drivers: Problem resolution, resource optimization (fair pricing)
- Trust heuristics: Social proof (reviews), authority (license), risk mitigation (guarantee)
- Layout strategy: Heavy top, light bottom (front-load trust + CTA)

**Brand color:** `#1B6AAA`
**Sections:** 10

---

#### Blueprint

| # | Section Purpose | Treatment | Reading Pattern | Visual Anchor | Background | Content Guidance |
|---|---|---|---|---|---|---|
| 1 | Hero: Acknowledge emergency, phone CTA | T4 Split Panel | Z-pattern | Phone number (display-5) | Gradient (brand-light to white) | H1 ~12 words, subhead ~25 words, 3 trust badges |
| 2 | Trust bar: Quick-scan credibility | T5 Accent Band | Gutenberg | 4 stat numbers | Brand primary | 4 items, number + label only, no sentences |
| 3 | Safety notice: What to do while waiting | T6 Boxed Container | F-pattern | Warning icon + red border-left | White | 4-5 bullet action items, ~8 words each |
| 4 | Services grid: What we fix | T3 Card Grid | Gutenberg | Icon circles in cards | White | 4 cards, icon + title + 1-sentence description |
| 5 | Why choose us: Differentiators | T2 Tinted Band | Gutenberg | Icon circles | Gray (#f8f9fa) | 4 items, L1 icon+text rows, ~20 words each |
| 6 | Process: How it works | T1 Open Canvas | F-pattern | Step numbers (1-3) | White | 3 steps, L2 numbered steps variant, ~25 words per step |
| 7 | Mid-page CTA | T5 Accent Band | Z-pattern | Phone button (btn-light) | Brand primary | Heading ~10 words, subtext ~15 words |
| 8 | Testimonials: Social proof | T6 Boxed Container | Z-pattern | Star rating + large quote | White | R2 large single quote variant, 1 review |
| 9 | FAQ | T2 Tinted Band | F-pattern | Accordion headers | Gray (#f8f9fa) | 5 questions, accordion, answers ~50 words each |
| 10 | Final CTA | T4 Split Panel | Z-pattern | Phone number + guarantee | White | C3 card-style CTA, heading ~10 words |

#### Treatment Sequence Check

```
T4 → T5 → T6 → T3 → T2 → T1 → T5 → T6 → T2 → T4
```

Adjacent check: No repeats. T5 appears twice but not adjacent (positions 2 and 7). Looks good.

#### Anti-Pattern Scan

- H2 Parade: Sections 3-6 all start with headings, but section 3 starts with a warning box, section 4 has centered heading + grid, section 5 has centered heading + icon rows, section 6 has left-aligned heading + steps. Three different openers. Fine.
- White Wall: Sections 3, 4, 6 are white but never 3 consecutive (section 5 is gray between 4 and 6). Fine.
- Card Carpet: Only one card grid (section 4). Fine.
- Icon Assembly Line: Section 4 uses icon-circle in cards, section 5 uses icon-circle in rows. Similar pattern. Consider changing section 5 to use `bi-check2` simple checks instead of icon-circles.
- CTA Echo: Section 1 "Call Now", section 7 "Stop the Leak", section 10 "Ready for Same-Day Repair?" All different. Fine.

---

## Format B: Narrative Blueprint

### Page: Emergency Plumber Dallas

**Brand:** #1B6AAA | **Intent:** Fear + urgency | **Mood:** Fast, reliable, trustworthy

The page needs to front-load trust and make the phone number impossible to miss. Someone with water pouring out of their ceiling is not going to read paragraphs.

**Hero:** Full-width gradient with split panel. Phone number as the dominant element, large enough to read at a glance on mobile. Two trust badges (licensed, 24/7) floating near the top. No form. No secondary messaging. Just: we are here, call us.

**Trust bar:** Compact accent band immediately below the hero. Four stats: years in business, review count, response time, satisfaction rate. These answer "can I trust you?" in 2 seconds of scanning.

**What to do while waiting:** A contained callout box with 4-5 safety actions. This is the one section where we slow down and give them reading content. Warning-styled border-left, visually distinct from the surrounding sections. Keeps them on the page while they wait.

**Services:** Card grid showing the 4 most common emergencies. Not an exhaustive list. Just enough that they see their problem represented. Icons that match the emergency type. White background, cards with shadow for depth.

**Why choose us:** Tinted band (gray bg) with icon+text rows. 4 differentiators. This needs to feel different from the services grid above — using rows instead of cards, and a background color change to create visual separation.

**How it works:** Open canvas, left-aligned, numbered steps (1-3). Simple and reassuring. The step numbers themselves anchor the section. White background — the tinted band above and the accent band below provide enough contrast.

**Mid-page CTA:** Accent band with phone button. Different text from the hero CTA: "Stop the Leak" instead of "Call Now." The visitor has now seen services and process — they're more informed.

**Testimonial:** Single large quote in a boxed container with star rating. One impactful story, not three mediocre ones. The quote should describe speed + honesty (matching the visitor's concerns).

**FAQ:** Accordion on tinted band. 5 questions max. Keep answers under 50 words — this audience wants quick reassurance, not essays.

**Final CTA:** Split panel with phone number + guarantee statement. Card-style. Text: "Ready for Same-Day Repair?" — this is the outcome-focused close.

**CTA text progression:** "Call Now" (hero) → "Stop the Leak" (mid) → "Ready for Same-Day Repair?" (final)

---

## Content Guidance

These approximate lengths help the content-writing skill produce copy that fits the visual layout. They're guidelines, not hard limits — if a point needs 30 words instead of 25 to land properly, that's fine.

```yaml
section_1_hero:
  h1_words: ~12
  subhead_words: ~25
  badges: 3
  cta_buttons: 2 (phone + secondary)

section_3_safety:
  format: bullet_list
  items: 4-5
  words_per_item: ~8

section_4_services:
  format: card_grid
  cards: 4
  card_structure: icon + title + 1_sentence

section_6_process:
  format: numbered_steps
  steps: 3
  words_per_step: ~25

section_9_faq:
  format: accordion
  questions: 5
  answer_words: ~50
```

---

## CSS Custom Properties for This Page

```css
:root {
  --pd-primary: #1B6AAA;
  --pd-primary-dark: #14507F;
  --pd-primary-light: rgba(27, 106, 170, 0.08);
  --pd-accent: #1B6AAA;
  --pd-light: #f8f9fa;
  --pd-dark: #1a1a2e;
  --pd-radius: 0.75rem;
}
```
