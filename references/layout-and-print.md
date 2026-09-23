# Layout geometry and print handoff

Use this reference when composing panels, interpreting miniature scale, or preparing a print deliverable.

## Panel geometry

For a poster of W × H pixels, each panel is W × H/2. Prefer an even integer height so the split lands on a whole pixel. A default 4000 × 6000 poster has two 4000 × 3000 panels. For a 2:3 poster, each panel is 4:3, not square. A 3:4 poster has 3:2 panels; a 4:5 poster has 8:5 panels.

Do not add a gutter to the canvas height accidentally. If requested, place a narrow separator symmetrically inside the equal panel regions. No separator is the default.

Place the original reference using uniform scaling. Default to contain-fit on a quiet matte, retaining the full image. Crop-to-fill only with user direction or acceptance. Do not stretch, hallucinate missing source borders, or silently remove defining content.

## Miniature scale and placement

Let the miniature bounding box occupy width fraction `a` and height fraction `b` of the lower panel. Its area fraction is `s = a × b`.

- Example: 50% width × 50% height = 25% area.
- Example: 60% width × 40% height = 24% area.
- Counterexample: 25% width × 25% height = 6.25% area, much smaller than the default.

Include any attached pedestal, plants, or strings in this box. Exclude diffuse shadows. This is a practical visual approximation, not foreground segmentation. Do not confuse the box area with the sum of colored pixels.

For a measured bounding-box aspect ratio `r = box_width / box_height`, lower-panel width `W`, height `L`, and desired area fraction `s`:

```text
box_width  = sqrt(s × W × L × r)
box_height = sqrt(s × W × L / r)
```

Center the box at approximately `(0.50W, 0.60L)` initially. Check all margins; tall silhouettes may need to move up or use the low end of the scale range to fit. Never flatten a tall subject to satisfy a numerical target. Explain unavoidable departures when an extreme silhouette conflicts with both scale and generous margins.

## Print size is a measured property

A prompt saying “high resolution” or “300 dpi” does not create the required pixels. Inspect the output file. Pixel requirements for a physical trim size are:

```text
pixels = round(centimeters / 2.54 × target_PPI)
```

PPI describes image pixel density at the intended print size; printer DPI is a different property. A practical target for close-viewed art prints is 300 PPI, subject to the printer's specification and viewing distance.

| Trim size | Nominal pixels at 300 PPI | Notes |
| --- | --- | --- |
| 20 × 30 cm | 2362 × 3543 | Round height up to 3544 if an exact equal pixel split is needed. |
| 30 × 45 cm | 3543 × 5315 | Round height up to 5316 for equal panel rows. |
| A3, 29.7 × 42 cm | 3508 × 4961 | Round height up to 4962; ISO A proportions differ from 2:3. |

The one-pixel adjustment is negligible in physical trim dimensions; disclose exact export dimensions. Choose poster ratio from the requested physical size rather than stretching a 2:3 artwork into A3.

An image with 1024 × 1536 pixels measures about 8.7 × 13.0 cm at 300 PPI. Changing its resolution metadata does not add detail. Upscaling may improve a delivery size but must be disclosed; inspect source-photo sharpness and miniature fibers after resizing.

## Handoff

1. Establish physical size and the printer's requirements when a finished print file is requested. For a concept request, deliver native-resolution art and explain its supported size.
2. Preserve a lossless RGB master, normally PNG or TIFF with a known embedded profile when the export tool supports it. Do not claim an embedded profile without checking it.
3. Add bleed only to the printer's specification. For example, 3 mm on all sides adds 6 mm to each trim dimension, approximately 71 pixels at 300 PPI. Keep the equal-panel split aligned to the trim design. Use deliberate background extension; do not stretch artwork.
4. Keep small labels safely inside trim; use the printer's safe-area requirements. Add exact type as a separate layout operation where possible.
5. Convert to CMYK only with an appropriate target profile and a suitable tool. Do not describe a generic RGB file as CMYK-ready or PDF/X-certified.
6. Report file format, measured dimensions, trim size, effective PPI, bleed status, profile when known, upscale status, and any unresolved production requirement.

“Print-intended concept” is appropriate when required checks cannot be completed. Reserve “print-ready” for a file checked against the actual printer's specification.
