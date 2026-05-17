# Steven SuperPPT Skill

Steven SuperPPT Skill is a public, portable presentation-design skill for planning, polishing, visually directing, and producing high-aesthetic PPT/PPTX/PowerPoint or HTML slide decks.

It is designed for three common workflows:

- Plan and polish a deck page by page from a topic, brief, notes, or source material.
- Extract a reusable visual system from user-provided style references such as screenshots, decks, PDFs, websites, logos, product photos, or moodboards.
- Produce hybrid decks where generated image plates or sourced visuals carry atmosphere, while HTML/SVG/Canvas/PPTX objects carry precise text, numbers, labels, charts, and diagrams.

## Image Generation Environments

When direct image generation is available, use the image-generation skill/tool in your agent environment.

When direct image generation is not available, the skill switches to prompt-handoff mode:

- It writes `references/imagegen-prompt-pack.md`.
- It writes `references/imagegen-handoff.md` with copy-ready prompts.
- It writes `references/asset-manifest.json` so generated assets can be placed later.
- It builds a usable draft with sourced assets, neutral placeholders, or programmatic backgrounds when practical.

## Visual Asset Density

At startup, the skill asks or infers how image-rich the deck should be:

| Mode | Use when | Image strategy |
|---|---|---|
| `lean` | Information-first reports, analysis, legal, compliance, board updates | Generate only cover, major section, and essential metaphor plates |
| `standard` | Default polished business decks | Generate cover variants, section plates, and key-slide visuals |
| `image-rich` | Launch events, keynotes, product demos, campaign decks, cinematic decks | Plan a visual asset for every slide, with extra variants for hero/product/transition slides |
| `auto` | You want the agent to decide | Resolve to one of the above and record the reason |

## Install

Copy the `steven-superppt-skill/` folder into your agent's skills directory.

For Codex-style environments, that is usually:

```text
~/.codex/skills/steven-superppt-skill/
```

The skill folder itself contains:

```text
steven-superppt-skill/
  SKILL.md
  agents/openai.yaml
  assets/samples/uffizi-main-works.pptx
  references/
```

## Sample Deck

The repository includes a complete editable PPTX sample:

```text
steven-superppt-skill/assets/samples/uffizi-main-works.pptx
```

It demonstrates a 12-slide museum-style deck generated from a short prompt, with artwork imagery embedded and text kept editable in Office.

## Use

Invoke it explicitly:

```text
Use $steven-superppt-skill to turn this topic into a polished 12-page launch deck.
```

With style references:

```text
Use $steven-superppt-skill. Use these screenshots as the visual reference, plan the deck page by page, then produce a PPTX and HTML preview.
```

Without image-generation access:

```text
Use $steven-superppt-skill in prompt-handoff mode. Create the image prompts and asset manifest for me to generate externally.
```

For a visual-heavy launch or keynote:

```text
Use $steven-superppt-skill with image-rich visual asset density to make a product launch deck.
```

## Public Sharing Notes

This repository intentionally avoids private company references, local machine paths, and brand-specific rules. Add your own brand/template skill separately when needed.
