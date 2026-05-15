# Content And Style Scenarios

Use this reference for the two optional work modes that often happen before production: planning the PPT content and deriving style from user-provided references.

## Scenario 1: Content Planning And Full Polish

Use when the user gives only a topic, goal, raw notes, meeting background, source docs, or asks for page-by-page PPT planning.

### Output

Create `outline.md` before building visuals. Treat it as the canonical plan. For high-stakes decks, also create `references/content-plan.json`.

Minimum `outline.md` shape:

```markdown
# Deck Outline

Goal:
Audience:
Delivery context:
Core thesis:
Narrative arc:

| slide_id | role | job | polished_headline | on_slide_copy | speaker_intent | evidence_status | visual_job | asset_need | imagegen_need |
|---|---|---|---|---|---|---|---|---|---|
```

### Planning Rules

- Turn user intent into a narrative arc: hook, context, thesis, proof, implications, decision/close.
- Write slide headlines as claims. Avoid topic labels such as "背景", "优势", "方案", "总结" unless they are rewritten into specific takeaways.
- Keep each slide to one job and one dominant message.
- Polish the actual on-slide copy, not only the outline. If a later renderer needs to build directly from `outline.md`, it should have enough copy to do so.
- Add speaker notes only when they clarify flow or keep the slide clean.
- Mark evidence as `verified`, `user-provided`, `needs research`, or `assumption`.
- Keep `slide_id` stable once visual or asset work starts.
- If facts may have changed or are high-stakes, research/verify before finalizing the content plan.
- Do not hide weak content under visuals. If a slide has no evidence, argument, or emotional job, merge it or remove it.

### Content Polish Checklist

- The first slide creates a reason to care.
- Every middle slide advances the argument.
- The final slide makes the ask, decision, recommendation, or memory point explicit.
- Long bullets are rewritten into short claims, labels, or comparisons.
- Repeated ideas are consolidated.
- Each slide's visual idea follows from the slide job, not from decoration.

## Scenario 2: User-Provided Style References

Use when the user provides or links:

- screenshots or images
- an existing PPT/PPTX/PDF
- a website or HTML page
- a brand guide, logo, product photo, UI screenshot, or visual moodboard
- wording such as "参考这个风格", "做成这种高级感", "按这个样式"

### Output

Create `references/style-reference-analysis.md`.

Minimum shape:

```markdown
# Style Reference Analysis

Reference inventory:

| ref_id | type | path_or_url | ownership/provenance | usable_for |
|---|---|---|---|---|

Extracted visual system:
- typography:
- palette:
- layout/grid:
- spacing/density:
- surfaces/depth:
- image treatment:
- chart/data treatment:
- motion/transition feel:
- recurring motifs:

Adaptation:
- keep:
- adapt:
- reject:
- risk:

Deck visual system:
```

### Inspection Rules

- For image references, inspect the actual image when available. In Codex Desktop, use `view_image` for local images when needed.
- For PPT/PPTX/PDF references, extract slide thumbnails or screenshots when practical.
- For website references, open or screenshot the page when practical.
- Preserve the user's visible intent, not accidental artifacts such as compression, bad crop, or UI chrome.
- Do not blindly clone a copyrighted or third-party deck. Translate its principles into a new deck-specific visual system unless the user provides it as an owned template or explicit brand system.
- If a reference conflicts with the deck's audience or content density, explain the adaptation in the analysis file and prioritize communication clarity.

### Style Extraction Questions

- What is the first-read hierarchy?
- What makes the reference recognizable beyond color?
- How dense is each page?
- What image treatment is used: full-bleed, product cutout, editorial crop, soft plate, diagrammatic, or texture?
- Are shapes functional or decorative?
- How are numbers and proof treated?
- What should never be copied because it would look generic, fake, or off-brand?

## Multi-Imagegen Planning

Use when the deck needs more than one generated bitmap asset.

Create `references/imagegen-prompt-pack.md` before calling `$imagegen`.

If direct image generation is unavailable, create `references/imagegen-handoff.md` with the same prompts in copy-ready form and mark the relevant manifest entries as `waiting-for-user-generated-asset`.

Minimum entry shape:

```markdown
## Asset: S03-thermal-plate-v1

- slide_id: S03
- visual_job: explain sustained performance with a premium thermal-flow metaphor
- proof_role: background|metaphor|object|texture|section_plate
- variant_count: 3
- prompt:
- negative_constraints: no text, no logos, no UI, no labels
- safe_zones:
- overlay_plan: headline and numeric labels drawn in HTML/Canvas/PPTX
- expected_variant_paths:
  - assets/generated/S03-thermal-plate-v1.png
  - assets/generated/S03-thermal-plate-v2.png
  - assets/generated/S03-thermal-plate-v3.png
- expected_final_path: assets/plates/S03-thermal-plate.png
- acceptance_criteria:
```

### Batch Rules

- Generate 2-4 variants for hero, cover, section, or style-setting plates.
- Generate one strong variant for minor support plates unless the first output fails.
- Create or update `references/asset-manifest.json`: selected, rejected, waiting-for-user-generated-asset, source paths, variant paths, final workspace paths, and selection reasons.
- Copy selected assets into `assets/plates/` or `assets/generated/`; leave originals in `$CODEX_HOME/generated_images/...`.
- Do not keep discarded variants in the project unless the user asks for review artifacts.
- Re-check text policy: no generated Chinese text, numbers, proof labels, UI claims, or logos inside bitmap plates.

## Mode Combination

Common combinations:

- **Topic only**: content planning -> aesthetic preflight -> imagegen prompt pack -> build.
- **Topic plus style screenshots**: content planning -> style reference analysis -> aesthetic preflight -> build.
- **Existing deck plus "make it prettier"**: extract current content -> style reference analysis if references exist -> rewrite weak slide headlines -> rebuild.
- **Finished content plus image-heavy deck**: aesthetic preflight -> imagegen prompt pack -> generate variants -> compose precision layer.
