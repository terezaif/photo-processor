# Painting Photo Processor

Perspective correction and background removal for rectangular framed paintings. Built for preparing artwork photos for web galleries — especially iPhone snapshots taken at awkward angles.

## What it does

Drop in a photo of a framed painting. Click (or adjust) the four corners of the frame. The tool straightens the perspective and crops out the background in one step, giving you a clean, corrected image of just the painting.

## How it works

The tool computes an **8-parameter homography** (perspective transform) from the four corner points you select. For each pixel in the output image, it applies the inverse transform to find the corresponding source pixel, using **bilinear interpolation** for smooth results. The math boils down to solving an 8x8 linear system via Gaussian elimination with partial pivoting.

On load, it also attempts **auto-detection** of the frame edges by scanning inward from each side of the image and looking for color transitions. This works well when the painting is photographed against a contrasting background. You can always adjust the corners manually by dragging.

## Tech

- **Pure JavaScript** — no external libraries, no build step, no dependencies
- **Single HTML file** — just open it in a browser
- **Canvas API** for all image processing
- **Runs entirely in the browser** — nothing is uploaded anywhere
- **Outputs PNG or WebP** with transparency support

## Usage

Open `painting-photo-processor.html` in any modern browser. That's it.

1. Drop or select a photo of a framed painting
2. Adjust the four corner markers to match the frame edges
3. Click "Correct Perspective"
4. Download the result as PNG or WebP

## Built by

[Tereza Iofciu](https://github.com/terezaif) · Code generated with [Claude](https://www.anthropic.com/claude) (Opus 4.6) by Anthropic
