# GitHub Visual Methods For Steven SuperPPT

Use this reference when a slide deck needs a stronger visual-design pass or when choosing the production route.

## Sources Surveyed

- Huashu Design: uses HTML as a visual production substrate while insisting the medium persona must match the output, with core asset protocol, three design directions, anti-slop checks, and five-axis critique. Borrow the taste preflight and asset-first rule. Source: https://github.com/alchaincyf/huashu-design/blob/master/SKILL.md
- Anthropic `frontend-design`: commits to a bold aesthetic direction before implementation and avoids generic AI frontend aesthetics. Borrow the "point of view before code" stance. Source: https://github.com/anthropics/claude-code/blob/main/plugins/frontend-design/skills/frontend-design/SKILL.md
- Anthropic `canvas-design`: creates a visual philosophy before rendering a static artifact. Borrow this for covers, hero slides, section openers, and poster-like slides. Source: https://github.com/anthropics/skills/blob/main/skills/canvas-design/SKILL.md
- `awesome-claude-design`: design-system inspiration files in `DESIGN.md` form. Borrow the compact design-system-memory pattern for repeatable deck styles. Source: https://github.com/VoltAgent/awesome-claude-design
- `awesome-design-skills`: curated `SKILL.md` + `DESIGN.md` design systems. Borrow testable quality gates and reusable design-system packaging. Source: https://github.com/bergside/awesome-design-skills
- `claude-design-skill`: portable design skill with progressive disclosure. Borrow the lean-root plus references pattern. Source: https://github.com/jiji262/claude-design-skill
- MiniMax `pptx-generator` skill: uses PptxGenJS, slide-type planning, theme contracts, and required QA. Borrow the idea of classifying slide roles before generating slides. Source: https://github.com/MiniMax-AI/skills/blob/main/skills/pptx-generator/SKILL.md
- `pptx-from-layouts-skill`: emphasizes using real PowerPoint master layouts and placeholders instead of fighting templates with overlays. Borrow this whenever a corporate template exists. Source: https://github.com/tristan-mcinnis/pptx-from-layouts-skill
- `dom-to-pptx`: converts DOM structures into editable PPTX content and is useful for HTML-first decks that need PowerPoint handoff. Treat output as something to verify, not magic. Source: https://github.com/atharva9167j/dom-to-pptx
- `html2pptx`: shows an HTML-to-PPTX converter route with text boxes, styling, lists, positioned elements, and tables. Useful for pipeline ideas, but still verify fidelity slide by slide. Source: https://github.com/abdelkrimkr/html2pptx
- `marp2pptx`: parses Markdown and builds editable PPTX from scratch with auto-sizing and CJK support. Borrow the principle that editable PPTX often needs native reconstruction, not screenshot export. Source: https://github.com/ebibibi/marp2pptx
- Slidev docs: Markdown-first web presentation workflow. Good for fast content iteration and developer-friendly previews. Source: https://github.com/slidevjs/slidev/blob/main/docs/guide/syntax.md
- `gstack` design review skill: reinforces scan-first design, hierarchy, clearly defined areas, and reducing unnecessary words. Source: https://github.com/garrytan/gstack/blob/main/plan-design-review/SKILL.md
- `web-design-rules-and-guidelines`: visual hierarchy comes from position, size, color, spacing, borders, shadows, and guided reading path. Source: https://github.com/abbas-roholamin/web-design-rules-and-guidelines
- GitHub `awesome-copilot` Power BI report design guidance: useful for information architecture, semantic colors, contrast, and data-slide hierarchy. Source: https://github.com/github/awesome-copilot/blob/main/instructions/power-bi-report-design-best-practices.instructions.md
- GDocs design system gist: clear CRAP framing: contrast, repetition, alignment, proximity. Source: https://gist.github.com/calenwalshe/16e21ee11b676516bd706f05dc981aec

## Visual Method Stack

### 1. Architecture Before Decoration

Decide the information architecture before choosing colors:

- What decision or understanding should this slide create?
- What is the single headline claim?
- What visual object proves or dramatizes the claim?
- What can be moved to speaker notes or appendix?

If the slide has no clear ask, the problem is writing, not styling.

### 1.5 Aesthetic Direction Before Rendering

Borrow the Huashu and Anthropic design-skill pattern: decide the creative posture before writing layout code.

- name the medium persona: presentation designer, information designer, editorial designer, product demo designer, or motion designer
- name the design philosophy in one phrase, such as "Geometric Evidence", "Editorial Precision", or "Kinetic Executive"
- decide what makes this deck recognizable beyond a palette
- if direction is unclear, produce three materially different directions and choose one before full production
- when real brands, products, UIs, or documents appear, real assets outrank style adjectives

Do not start with a template-like layout and then "make it premium." The point of view comes first.

### 2. Scan-First Hierarchy

Design for a 3-second scan:

- largest or highest-contrast element equals the main point
- top-left or centered focal area carries the first read
- headings and highlighted terms create a reading path
- secondary text is visibly secondary
- decorative elements never outrank the message

For business decks, the audience often scans thumbnails first. Make the thumbnail read.

### 3. CRAP For Slides

- **Contrast**: make title, proof, and footnote obviously different. Use size, weight, opacity, and color.
- **Repetition**: repeat slide grammar, margins, title position, badge style, and chart conventions.
- **Alignment**: align to a visible or invisible grid. Avoid almost-aligned objects.
- **Proximity**: group related labels, values, and explanatory copy. Increase distance between unrelated groups.

### 4. Token Discipline

Use fewer visual tokens than the model wants to invent:

- 3-4 type sizes
- 2 font weights
- 1 primary accent plus semantic support colors
- 8px or equivalent spacing rhythm
- 1-2 corner-radius values
- 1 shadow/depth recipe, if any

Avoid one-note color palettes. A deck can have a dominant tone, but it still needs neutral structure and meaningful accent contrast.

### 5. AI Plate Discipline

Invoke `$imagegen` for generated raster assets. Its default route is the built-in image tool; do not invent one-off SDK runners or CLI usage unless the user explicitly asks for that fallback.

Use image generation for:

- background wireframes
- abstract systems
- product/environment mood
- material and lighting studies
- hero objects without text
- metaphor plates that would take too long to draw manually

Do not use image generation for:

- precise Chinese or English text
- numbers
- charts
- diagrams that must be audited
- logos unless supplied as exact assets
- UI screenshots that must match a real product

Good plate prompts specify safe zones, no text, low contrast behind content, and the desired reading path.

Every project-bound generated plate must be copied into the deck workspace, usually under `assets/plates/`, and must be referenced from there.

### 6. Editable PPTX Discipline

If PowerPoint editing matters:

- prefer master layouts and placeholders when a template is available
- keep titles, body, labels, and charts as native objects
- use background images as plates, not as flattened full-slide screenshots with burned-in content
- verify after export that text boxes, charts, and shapes are selectable

If fidelity matters more than editability, keep the HTML/PDF/image output as the canonical final and tell the user.

### 7. Data And Report Slides

For KPI or report pages:

- put the primary conclusion above the chart
- use semantic colors consistently
- add labels where color alone carries meaning
- avoid chart junk and redundant legends
- make negative/positive/neutral states clear in grayscale
- keep table density controlled; split dense tables into appendix when possible

### 8. QA Checklist

Before completion:

- thumbnail scan tells a coherent story
- every slide has one dominant message
- no text is clipped or overlapping
- image plate does not compete with foreground content
- color contrast survives projector/screenshot viewing
- output file opens
- important text remains editable if promised
- source files can regenerate the deck
- five-axis review has no weak axis below 7/10 for important slides
