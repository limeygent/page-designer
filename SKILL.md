---
name: page-designer
description: Designs visually appealing, layout-first Bootstrap 5 page structures using visual design principles (hierarchy, rhythm, spatial awareness, reading patterns). Takes search intent analysis and produces a visual blueprint before content is written. Use this skill when users want to create service pages, landing pages, or any web page that needs to look custom-designed rather than template-stamped. Triggers on requests like "design a page", "create a layout", "build a page for my business", "make a visually appealing page", or when users want pages that don't look AI-generated or mass-produced.
---

# Page Designer — Layout-First Visual Design

This skill produces visually appealing Bootstrap 5 page layouts by thinking like a designer, not following a template. The core idea: **understand the page's purpose and audience first, then design a visual layout that serves them, then fill with content**.

AI-generated pages tend to look identical because they repeat the same H2-paragraph-list pattern section after section. A human designer would never do this. They'd sense the page's mood, vary section styles intuitively, and create visual rhythm. This skill develops that design instinct rather than replacing it with a checklist.

## How This Skill Fits With Other Skills

The page-designer is a **visual layout layer**, not a content strategy layer. It works alongside existing skills:

```
Intent Analyzer → Service-Page Skill (determines WHAT sections + content flow)
                         ↓
                  Page Designer (determines HOW each section LOOKS visually)
                         ↓
                  Service-Page / Content-Council (writes content to fit the layout)
```

**The service-page skill owns the section sequence.** It decides which blocks appear and in what order based on intent analysis, MECLABS conversion formula, and niche-specific logic. The page-designer does NOT override this ordering. Instead, it takes the service-page's section list as input and applies visual treatments to make each section look distinct and professional.

**Content constraints flow back.** When the page-designer assigns a treatment to a section, it also provides content guidance (approximate lengths, item counts, format suggestions) that the content-writing skill should respect so content fits the visual layout properly.

## Bootstrap-First CSS Strategy

Use Bootstrap 5 classes for everything possible. Custom CSS should be limited to a small shared stylesheet (CSS custom properties + 10-15 utility classes) that gets reused across all pages for a given site. The shared CSS block is defined in `references/design-principles.md` under "Quick Reference: CSS Utility Classes."

Do not write one-off CSS for individual sections. If Bootstrap doesn't have the exact class you need, use inline `style` attributes for small tweaks (e.g., `style="border-left: 4px solid var(--pd-primary);"`) rather than inventing new class names.

## Required Inputs

1. **Primary keyword / page topic** (e.g., "emergency plumber", "cosmetic dentist", "pool installation")
2. **Business niche** (e.g., plumbing, dental, HVAC, pools, legal)
3. **Brand color** (hex code, e.g., `#F5A623`)
4. **Intent analysis** — either provide output from the intent-analyzer skill, or the skill will run a lightweight intent assessment inline
5. **Section sequence** (optional but preferred) — if the service-page skill has already determined the section ordering, provide it. The page-designer will apply visual treatments to this existing sequence rather than creating its own.

## Optional Inputs

- Business name and location
- Specific services to feature
- Available assets (photos, testimonials, team bios, reviews)
- Hero style preference
- Target section count
- Client profile slug (reads from `~/.claude/config/clients/{slug}/profile.json`)

## The Design Process

### Phase 1: Understand the Page

Before touching layout, spend time with the content and context.

**What is this page about?**
Read the keyword, niche, and any intent analysis. But go beyond the data. Ask yourself:
- Who is arriving on this page, and what just happened to them?
- Are they scared, curious, excited, skeptical?
- What does this business want the visitor to DO after reading?
- What is the one thing this page must communicate above all else?

**What does this page need to feel like?**
A pediatric strep throat page needs to feel calm and competent. A pool installation page needs to feel aspirational and trustworthy. An emergency plumber page needs to feel fast and reliable. The feeling you choose shapes every layout decision that follows.

**How much content is there, and what kind?**
A page with 14 sections of educational content needs a different visual strategy than a page with 8 sections of quick-scan trust signals. Long-form reading sections benefit from different principles than dense comparison grids.

If intent-analyzer output is provided, extract the emotional and functional drivers. If not, do a quick inline assessment. Read `references/reading-patterns.md` for how intent tends to map to layout strategies — but treat these as starting points for your thinking, not assignments.

### Phase 2: Design the Layout

This is the creative work. You have a toolkit of treatments, components, and design principles. Draw from them based on what THIS page needs.

**Start with the hero.** The hero sets the tone for the entire page. What does the visitor need to see first? For urgent pages, they need a phone number and reassurance. For aspirational pages, they need a vision of the outcome. For research pages, they need a clear statement of what they'll learn.

**Then sketch the flow.** Think about the visitor's journey down the page:
- What questions arise in sequence?
- Where does trust need to be reinforced?
- Where does the page need a visual break?
- Where should CTAs appear based on the visitor's readiness?

**Choose treatments from your palette.** See `references/section-treatments.md` for 7 treatment types. Think of these as colors on a palette — you wouldn't paint a canvas with only one color, and you'd consider which colors work well next to each other. Variety creates visual interest. If you notice two adjacent sections looking similar, that's a signal to reconsider.

**Select component variants.** See `references/component-variants.md`. When a section contains a list, data, testimonials, or steps, choose how to present it. The same information can look completely different depending on the variant. Varying presentation across the page prevents the "template" feeling.

**Draw from design principles as needed.** See `references/design-principles.md`. These 13 principles are not a checklist to apply sequentially. They are lenses you can look through when making design decisions. For a particular page, 3-4 of these principles might be especially important. Others might barely apply. An experienced designer knows which ones matter most for the page they're building:

- **Emergency/urgent page?** Visual hierarchy and Fitts's Law are critical. Gestalt consistency matters less because the page is short.
- **Aspirational cosmetic page?** Spatial awareness and symmetry/asymmetry create that premium feel. Progressive disclosure handles the educational depth.
- **Research/comparison page?** Reading patterns and typography rhythm keep dense content scannable. Color as information helps structure complex data.

**Build the HTML.** Generate the Bootstrap 5 HTML, applying the design decisions you've made. Use the CSS custom properties setup:

```css
:root {
  --pd-primary: {BRAND_COLOR};
  --pd-primary-dark: {derived darker};
  --pd-primary-light: {brand at 8% opacity};
  --pd-accent: {complementary or same as primary};
  --pd-light: #f8f9fa;
  --pd-dark: #1a1a2e;
  --pd-radius: 0.75rem;
}
```

Output the complete HTML file to the specified output path, or to `page-designer-output/` in the current working directory.

### Phase 3: Refine and Review

After designing the layout (or generating the HTML), step back and look at the whole page.

**Does it flow?** Scroll through mentally. Does each section feel like a natural next step? Are there jarring transitions?

**Does it breathe?** Is there enough whitespace, or does it feel dense and overwhelming?

**Does it look hand-designed?** This is where `references/anti-patterns.md` helps. Scan for the common tells of mass production — not as a pass/fail gate, but as a designer noticing "these three sections all look the same, let me vary one."

**Does the visual hierarchy work?** Can someone scan just the headings, stats, and bold text and get the gist? If not, the hierarchy needs work.

**Does it match the intent?** An emergency page that feels leisurely, or a cosmetic page that feels clinical — these are design/intent mismatches worth catching.

Optionally, run the design review from `references/visual-auditor.md` for a structured look at specific design aspects.

## Content Population (Handoff to Service-Page Skill)

The page-designer outputs an HTML skeleton with content placeholders and **content guidance** for each section. The service-page skill (or content-council) then writes content that fits within these guidelines.

**Content guidance per section includes:**
- **Approximate word range** for headings, body text, list items
- **Suggested item count** for lists, cards, FAQ questions
- **Format suggestion** (bullet list, numbered steps, cards, accordion, table)
- **Visual anchor** the content should include (stat, badge, icon reference)

**Placeholder format in the HTML skeleton:**
```html
<!-- SECTION: [purpose] | TREATMENT: [T1-T7] | GUIDANCE: [summary] -->
<section class="zone-group py-5" style="background: var(--pd-light);">
  <div class="container">
    <!-- [H2: ~8 words, left-aligned] -->
    <!-- [SUBTITLE: ~15 words, text-muted] -->
    <!-- [CONTENT: 4 icon+text items in 2-col grid, each ~20 words] -->
  </div>
</section>
```

**Adapting when content doesn't fit:** If the content-writing skill produces content that doesn't fit a section's layout (e.g., 200 words for a section designed for 50), either:
1. Ask the content skill to condense, or
2. Adjust the treatment to accommodate longer content (e.g., swap from T5 Accent Band to T1 Open Canvas)

The goal is finding the right balance where content and layout serve each other.

## Image Strategy

Images are a conversion tool, not decoration. They create emotional connection, provide pattern interrupts (break "sea of text"), and motivate scrolling.

- **Hero images:** For urgent/fear intent, consider T7 Full-Width Image Hero (image as background with text overlay). For planning/research intent, T4 Split Panel works (image in one column, text in the other).
- **Every image placeholder should describe the ideal image:** subject, setting, mood, lighting. Not just "doctor photo" but "Friendly pediatrician examining child's throat, warm lighting, child comfortable, parent visible in background."
- **Form placement by intent:** Forms are secondary conversion paths.
  - **Urgent/fear intent (sick visits, emergencies, leaks):** No form on the page. The visitor will call. Phone number is the only CTA. Link to contact page for after-hours visitors.
  - **Planning/research intent (cosmetic, remodels, consultations):** Form in the hero sidebar (T4 split panel) or standalone section. These visitors prefer submitting a request over calling.
  - **Hybrid intent:** Phone CTA primary, form available but not prominent. Place form near the bottom after trust is built.
- **Avoid anchor collision:** Be careful placing two competing visual elements of equal weight in the same section (image + form, image + large stat). If both need prominence, give each its own section.

## No Em-Dashes

Do not use em-dashes (---) in content. This is an AI writing tell. Use colons, commas, periods, or parentheses instead.

## Reference Files

Load these during execution as needed, not all upfront:

| File | When It Helps | What It Contains |
|---|---|---|
| `references/design-principles.md` | When making layout decisions | 13 design principles with CSS patterns and intuition guidance |
| `references/section-treatments.md` | When choosing section visual styles | 7 treatment types with complete HTML/CSS code |
| `references/component-variants.md` | When deciding how to present content | 3-4 visual options for lists, data, testimonials, CTAs, steps |
| `references/anti-patterns.md` | When reviewing for quality | 9 mass-production signals with context on when they matter |
| `references/reading-patterns.md` | When mapping intent to layout | F/Z/Gutenberg patterns mapped to Bootstrap layouts |
| `references/visual-auditor.md` | When doing a thorough design review | 24 design review considerations |
| `references/examples/layout-blueprint-example.md` | Anytime (reference) | Sample blueprints showing expected output formats |
