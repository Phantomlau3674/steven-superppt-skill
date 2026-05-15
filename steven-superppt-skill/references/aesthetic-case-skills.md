# Aesthetic Case Skills For Steven SuperPPT

Use this reference when a deck needs stronger taste, better visual direction, or a repair pass after looking generic, flat, PPT-like, or too AI-generated.

## What To Borrow

### Huashu Design

Source: https://github.com/alchaincyf/huashu-design/blob/master/SKILL.md

Borrow these habits:

- **HTML is a tool, not the medium**: a slide should not look like a web page just because it is built in HTML.
- **Embody the right expert**: presentation designer for decks, information designer for proof/data, motion designer for animated explainers, prototype designer for app demos.
- **Core asset protocol**: when a deck references a real brand/product/app/document, use real logo, product imagery, UI screenshots, proof pixels, and source material before decorative style.
- **Three direction exploration**: when the visual direction is not locked, create three materially different directions, not three palette swaps.
- **Junior pass before full pass**: show structure and assumptions early; do not hide weak thinking under polished decoration.
- **Five-axis review**: critique philosophy/thesis fit, hierarchy, craft, function, and originality, then repair the weak axis.

Deck adaptation:

- For a business PPT, do not copy Huashu's full animation/video workflow by default. Borrow the taste preflight, asset protocol, direction map, and critique rigor.
- For a PPT that will become a video or animated HTML deck, borrow the continuous narrative rule: adjacent slides should transform, pass a motif, or create a deliberate cut rather than behaving like unrelated pages.

### Anthropic Frontend Design

Source: https://github.com/anthropics/claude-code/blob/main/plugins/frontend-design/skills/frontend-design/SKILL.md

Borrow these habits:

- Commit to a bold aesthetic direction before implementation.
- Pick typography and palette as a point of view, not defaults.
- Make one memorable choice the audience can recall.
- Avoid generic AI design families such as safe centered layouts, timid gradients, and interchangeable cards.

Deck adaptation:

- A deck needs less interface chrome than a web app. Use the bold direction to guide type, composition, image language, and transitions, not to add UI widgets.

### Anthropic Canvas Design

Source: https://github.com/anthropics/skills/blob/main/skills/canvas-design/SKILL.md

Borrow these habits:

- Create a visual philosophy before drawing the artifact.
- Let space, form, color, rhythm, texture, and composition communicate, not paragraphs.
- Keep text sparse and integrated into the visual system.
- Make the work feel painstakingly crafted, not generated from a template.

Deck adaptation:

- Use this for covers, hero slides, posters, section openers, or conceptual slides.
- Do not over-apply it to dense report slides where clarity and auditability matter more than poster-like expression.

### Frontend Slides

Reference pattern: frontend slide skills that create zero-dependency, viewport-safe HTML presentations and style previews.

Borrow these habits:

- Show visual previews instead of asking abstract style questions.
- Keep every slide viewport-safe with no scrolling.
- Avoid generic purple-gradient/startup decks.
- Use atmospheric backgrounds, strong type hierarchy, and clear visual direction.

Deck adaptation:

- For ambiguous taste requests, create three one-slide style previews first.
- Delete preview files after the final direction is selected unless the user wants to keep them.

### Awesome Claude Design

Sources:

- https://github.com/VoltAgent/awesome-claude-design
- https://github.com/rohitg00/awesome-claude-design

Borrow these habits:

- Treat `DESIGN.md`-style files as compact design-system memory: brand idea, type, palette, spacing, surfaces, components, motion, and anti-patterns.
- Browse aesthetic families for inspiration, but translate them into a deck-specific visual system instead of copying a whole UI theme.

Deck adaptation:

- Create `references/visual-system.md` for the current deck when the project is more than a one-off slide.
- Include exact tokens and rules, not adjectives only.

### Awesome Design Skills / TypeUI

Source: https://github.com/bergside/awesome-design-skills

Borrow these habits:

- Pair `SKILL.md` execution rules with human-readable design intent.
- Use testable quality gates: contrast, spacing rhythm, responsive behavior, accessibility, and do/don't rules.
- Think in reusable visual systems rather than one-off decorated screens.

Deck adaptation:

- If the user wants a repeatable PPT style, turn the chosen direction into a reusable mini design system.

### Interface Design

Source: https://github.com/Dammyjay93/interface-design

Borrow these habits when the deck contains dashboards, SaaS screens, tools, admin panels, or operational data:

- explore the domain before drawing controls
- choose a signature element, not a generic dashboard template
- enforce design tokens and consistency across sessions
- run a critique pass to catch default-looking output

Deck adaptation:

- Use for dashboard/report slides and product-demo slides, not for marketing hero slides.

### Portable Claude Design Skill

Source: https://github.com/jiji262/claude-design-skill

Borrow these habits:

- Keep a lean root skill and push heavy design examples into references.
- Include starter assets and sample outputs only when they make repeated work faster.

Deck adaptation:

- Keep this PPT skill lean. Put case-study details here, not in `SKILL.md`.

## Three-Direction Prompt For Decks

When taste is unclear, generate three options:

```text
Design three materially different slide directions for this deck.
For each: name, emotional effect, metaphor, composition logic, palette pressure,
type posture, imagegen plate style, precision-layer style, risk if executed badly,
and one hero-slide sketch.
Options must differ in visual philosophy, not only colors.
```

Default directions:

- `safe_professional`: evidence-led, crisp, restrained, reliable.
- `kinetic_immersive`: spatial, cinematic, motion-ready, memorable.
- `poetic_distinctive`: metaphor-led, editorial, quieter or stranger, high differentiation.

## Anti-Slop Bar

Reject these unless the deck's brief explicitly justifies them:

- generic purple/blue gradient with glass cards
- dashboard chips used as decoration
- fake product UI or fake proof screenshots
- AI-generated Chinese text inside an image
- decorative icons that repeat the label instead of adding meaning
- one-note palettes with no semantic accent
- centered title plus six cards on every slide
- stock-like hero image with no recognizable subject
- busy background plate behind dense text
- unverified brand assets or hand-drawn approximations of real logos/products

## Five-Axis Deck Review

Score the actual preview or slide thumbnails:

- `thesis_fit`: visual philosophy matches the deck's purpose and audience
- `visual_hierarchy`: first, second, and third read are obvious
- `craft_quality`: spacing, crop, type, alignment, color, and image treatment feel deliberate
- `functional_clarity`: every element helps understanding or persuasion
- `originality`: avoids the common AI/template look

If any axis is below 7/10, revise before final handoff. If the cover, hero slide, or decision slide has weak hierarchy or originality, revise even if the rest of the deck is acceptable.
