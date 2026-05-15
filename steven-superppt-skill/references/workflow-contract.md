# Workflow Contract

Use this file as the execution contract for `steven-superppt-skill`. It keeps content planning, style references, image assets, and final production aligned.

## Canonical Files

- `outline.md`: the single source of truth for slide content and production intent.
- `references/style-reference-analysis.md`: required when the user provides visual references.
- `references/visual-system.md`: required for reusable or multi-slide visual systems.
- `references/imagegen-prompt-pack.md`: required before generating multiple bitmap assets.
- `references/asset-manifest.json`: required when any sourced or generated image is selected for the deck.
- `references/imagegen-handoff.md`: required when direct image generation is unavailable and prompts must be handed to the user.
- `references/design-review.md`: required for high-aesthetic or final deliverables.

## `outline.md` Schema

Every slide row must include stable IDs and production fields.

```markdown
| slide_id | role | job | polished_headline | on_slide_copy | speaker_intent | evidence_status | visual_job | asset_need | imagegen_need |
|---|---|---|---|---|---|---|---|---|---|
| S01 | cover | create tension | ... | ... | ... | assumption/user-provided/verified/needs-research | ... | source/generated/programmatic/none | none/one/variants/per-slide-plate |
```

Rules:

- Keep `slide_id` stable once production starts.
- Write headlines as claims, not topic labels.
- Keep `on_slide_copy` close to final wording; do not leave vague placeholders.
- Mark evidence honestly as `verified`, `user-provided`, `needs-research`, or `assumption`.
- Use `visual_job` to explain what the visual must do for understanding or persuasion.
- Use `asset_need` and `imagegen_need` to drive asset planning.

## `style-reference-analysis.md` Schema

Required when the user provides style references.

```markdown
# Style Reference Analysis

## Reference Inventory

| ref_id | type | path_or_url | ownership/provenance | usable_for |
|---|---|---|---|---|

## Extracted Visual System

- typography:
- palette:
- layout/grid:
- spacing/density:
- surfaces/depth:
- image treatment:
- chart/data treatment:
- motion/transition feel:
- recurring motifs:

## Adaptation Rules

- keep:
- adapt:
- reject:
- risks:

## Applied Deck System

- tokens to apply:
- slide roles affected:
- constraints:
```

Rules:

- Inspect the actual reference when practical, not only the filename or user description.
- Preserve intent; do not copy accidental compression, UI chrome, or bad crops.
- Translate third-party references into a new deck-specific system unless the user owns the template or brand system.
- If the reference conflicts with readability or deck purpose, adapt it and explain why.

## `imagegen-prompt-pack.md` Schema

Required before calling `$imagegen` for multiple assets.

```markdown
## Asset: S03-thermal-plate

- slide_id: S03
- visual_job:
- proof_role: background|metaphor|object|texture|section_plate
- variant_count: 3
- prompt:
- negative_constraints: no text, no logos, no UI, no labels
- safe_zones:
- overlay_plan: all headline, labels, numbers, and claims drawn in HTML/Canvas/PPTX
- expected_variant_paths:
  - assets/generated/S03-thermal-plate-v1.png
  - assets/generated/S03-thermal-plate-v2.png
  - assets/generated/S03-thermal-plate-v3.png
- expected_final_path: assets/plates/S03-thermal-plate.png
- acceptance_criteria:
```

Rules:

- Generate 2-4 variants for cover, hero, section, or style-setting assets.
- Generate one asset for minor support plates unless the output fails.
- Keep generated images text-free unless the user explicitly asks for bitmap text and accepts the risk.
- Do not generate factual UI, dashboards, labels, logos, or proof screenshots.

## Prompt-Handoff Mode

Use this mode when direct image generation is unavailable, including non-Codex environments, missing image tools, disabled image APIs, or user preference for external image tools.

Required behavior:

- Still plan images as if they will be generated.
- Do not silently replace all imagery with low-quality placeholders.
- Create `references/imagegen-handoff.md` with copy-ready prompts.
- Mark affected `asset-manifest.json` entries as `waiting-for-user-generated-asset`.
- Tell the user expected filenames and where to place completed images.
- Continue building a usable draft with neutral placeholders or programmatic backgrounds when possible.

Minimum `imagegen-handoff.md` shape:

```markdown
# Image Generation Handoff

Direct image generation was unavailable in this environment.

## How To Use

Generate each asset in your image tool of choice, keep text disabled, then save the selected result to the expected path.

## Prompts

### S01-cover-plate

- expected_final_path: assets/plates/S01-cover-plate.png
- aspect_ratio: 16:9
- safe_zones: left-center for title, lower right clear for page number
- prompt:
- negative_prompt: no text, no logos, no UI, no labels, no watermark
- overlay_plan: all titles, labels, claims, and numbers are drawn later in HTML/Canvas/PPTX
- acceptance_criteria:
```

## `asset-manifest.json` Schema

Required when selected assets enter the deck.

```json
{
  "assets": [
    {
      "asset_id": "S03-thermal-plate",
      "slide_id": "S03",
      "kind": "generated|sourced|user-provided|programmatic",
      "prompt_pack_ref": "S03-thermal-plate",
      "source_paths": [],
      "variant_paths": [],
      "selected_path": "",
      "final_workspace_path": "assets/plates/S03-thermal-plate.png",
      "selection_reason": "",
      "usage": "background|hero|supporting|texture|object",
      "status": "planned|waiting-for-user-generated-asset|generated|selected|copied|used|rejected",
      "notes": ""
    }
  ]
}
```

Rules:

- Leave originals in their original location unless the user asks for cleanup.
- Copy selected generated outputs into the deck workspace before referencing them.
- Use unique filenames for variants.
- Remove or mark unused assets instead of leaving ambiguous files.

## Final Verification Contract

Before final response:

- `outline.md` matches final slide count or explains intentional omissions.
- `style-reference-analysis.md` exists when references were supplied.
- `imagegen-prompt-pack.md` exists when multiple generated assets were needed.
- `imagegen-handoff.md` exists when direct generation was unavailable.
- `asset-manifest.json` lists selected sourced/generated images and final workspace paths.
- HTML/PPTX/PDF output opens or can be parsed.
- A visual preview, thumbnail pass, screenshot, or exported slide image has been inspected when practical.
- Important text, claims, numbers, charts, and labels are not trapped inside generated bitmap plates.
