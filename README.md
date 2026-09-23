# Handcrafted Diptych Poster Skill

Turn a reference image into a vertical art poster: an editorial reference presentation above, a sparse handcrafted miniature reinterpretation below.

The miniature preserves the image's defining silhouette, color relationships, and spatial structure through clay, felt, hand-cut paper, string, or cardboard. Think photographed art maquettes, visible fibers, and carefully cut edges, with generous negative space.

**中文简介：** 将任意参考图转化为上下等高的双联艺术海报。上半呈现参考图，下半用黏土、毛毡、手剪纸、线绳或纸板提炼为微缩舞台装置。默认主体占下半画幅约 20–30%，保留大量留白，强调真实手工质感，避免幼稚玩具感和廉价模板感。

## What this repository provides

- A reusable agent Skill with clear activation conditions and an image-analysis workflow.
- A prompt template, material-selection guidance, negative constraints, and adjustable settings.
- Four subject-specific example prompt files, each with an invocation and a concrete production brief.
- Composition geometry, original-image preservation guidance, and a print-handoff reference.
- Optional Codex interface metadata and an MIT license.

This is an instruction package, not a standalone image generator. No API keys, paid-service integration, or executable installation scripts are included. An image-capable assistant can analyze the input; image generation/editing and composition tools are needed to produce the final artwork. It can also operate in prompt-only mode.

## Quick start

1. Make this folder available to a host that supports `SKILL.md`, using that host's skill-loading mechanism. Keep the supporting directories alongside the entrypoint.
2. Attach your reference image.
3. Invoke the Skill, for example:

```text
Use $handcrafted-diptych-poster-skill with my attached image.
Create a 2:3 vertical poster with equal-height upper and lower panels.
Preserve the original image in the upper panel using contain-fit.
Translate the subject below into a clay and hand-cut-paper miniature,
at approximately 25% of the lower panel area. No text; high palette fidelity.
```

If your assistant does not support Skill discovery, provide [SKILL.md](SKILL.md) as instructions and make its linked resources available. Tool use and installation differ by host; the prompt method does not require a specific provider.

For prompts only:

```text
Use this Skill to analyze my attached image and produce a ready-to-use
lower-panel generation prompt plus an assembly specification. Do not generate yet.
```

For a physical print:

```text
Use this Skill with my attached image. Target a 30 × 45 cm poster at 300 PPI,
with two equal-height panels and no text. Preserve the original above.
Verify actual output dimensions and report any upscaling or print limitations.
```

## Design defaults

| Setting | Default |
| --- | --- |
| Overall poster | Vertical 2:3 |
| Panel division | Top and bottom equal in height |
| Upper panel | Original image, uniformly scaled to fit on a matching matte |
| Miniature | Approximately 25% of lower-panel area, measured by bounding box |
| Position | Centered horizontally, slightly below center |
| Materials | Two or three selected for the reference |
| Text | None |
| Palette | High fidelity to the reference's dominant color relationships |
| Empty space | Approximately 70–80% outside the miniature box |

The full parameter table and override rules live in [SKILL.md](SKILL.md). The panel ratio **1:1 means equal height**, not two square images. Miniature scale is **area**, not the object's height: a box at half the panel width and half its height occupies 25% of the area.

## Preserve versus re-render

The default workflow generates only the lower panel and places the original reference above it using a composition tool. This protects the original image from generative changes. A reference with a different aspect ratio is fitted within the panel; cropping needs user direction or acceptance.

A single integrated generation can be used when an editorial re-render is acceptable. It may change faces, objects, logos, or lettering and must not be described as an unchanged reference. If composition is unavailable, the assistant should explain the limitation and deliver the lower panel with assembly instructions.

## Example prompts

Start with the [example index](examples/README.md):

- [Architecture: a courtyard and arch](examples/01-architecture.md)
- [Portrait: a coat and seated gesture](examples/02-portrait.md)
- [Landscape: a cliff, path, and sea](examples/03-landscape.md)
- [Still life: a vessel and folded cloth](examples/04-still-life.md)

These are hypothetical input scenarios and complete illustrative briefs. They are not prompts extracted from an unseen user image and are not validated render examples. Always replace their visual assumptions with observations from the actual attachment.

## Repository layout

```text
handcrafted-diptych-poster-skill/
├── SKILL.md
├── README.md
├── LICENSE
├── .gitignore
├── agents/
│   └── openai.yaml
├── assets/
│   └── README.md
├── examples/
│   ├── README.md
│   ├── 01-architecture.md
│   ├── 02-portrait.md
│   ├── 03-landscape.md
│   └── 04-still-life.md
└── references/
    └── layout-and-print.md
```

## Quality and known limits

Review the image using the checklist in `SKILL.md`. Generative tools may miss exact panel proportions, scale, material texture, or text. Precise geometry and typography are best verified during composition. This release contains authored instructions and illustrative prompts; it does not claim cross-model visual testing.

“High resolution” in a prompt does not guarantee printable pixels. The [print reference](references/layout-and-print.md) covers measured dimensions, effective PPI, bleed, color profiles, and transparent upscaling disclosures.

## Publish on GitHub

The folder is ready to use as a repository root. Suggested repository name: **handcrafted-diptych-poster-skill**.

Suggested description:

> An image-to-poster AI Skill for equal-panel vertical diptychs with tactile handcrafted miniature reinterpretations.

Suggested topics: `ai-skill`, `image-generation`, `prompt-engineering`, `diptych`, `poster-design`, `miniature-art`, `art-direction`.

Create a repository under your account and upload this folder's contents, including `.gitignore`. No remote repository is created by this package. Add a real, rights-cleared example image pair later if desired; see [assets guidance](assets/README.md).

## License

The authored instructions and example prompts are available under the [MIT License](LICENSE). The license does not grant rights to third-party reference images, trademarks, fonts, or separately licensed assets. Generated-output terms depend on the tool used. The repository includes no third-party reference photographs.
