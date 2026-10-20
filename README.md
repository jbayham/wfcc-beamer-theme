# WFCC Beamer theme

A standalone version of the dark theme used for the WFCC Smoke Forum deck: navy background, warm orange accents, muted secondary text, section labels, and a compact footer. No research data or parent-project paths are needed.

## Quick start

1. Copy this folder anywhere, or upload its contents to an Overleaf project.
2. Edit the metadata and slide content in `example.tex`.
3. Run `latexmk -pdf example.tex` from this folder. Open `example.pdf`.

Use pdfLaTeX with a current TeX Live or MiKTeX installation. The example requires Beamer, TikZ/PGF, adjustbox, booktabs, biblatex, Biber, and latexmk. Source Sans Pro is used when installed; Latin Modern is the fallback. Overleaf: select `example.tex` as the main document and pdfLaTeX as compiler.

## Use in another deck

Copy `beamerthemeWFCC.sty` beside your `.tex` file and add:

```tex
\documentclass[aspectratio=169]{beamer}
\usetheme{WFCC}
\title[Short title]{Full presentation title}
\author[Short author]{Full author name}
\institute{Your institution}
\date{Your date}
\WFCCevent{Your event}
\begin{document}
\begin{frame}[plain]
  \titlepage
\end{frame}
% Your frames here
\end{document}
```

The footer uses the short author, short title, short date, and frame number. Use short forms that fit on one line. Use `\section{...}` to set the small section heading. The theme does not load biblatex: choose your own citation style in the document.

## Title image and customization

The default title has a plain navy panel on the right. To add a photo, place a licensed JPG, PNG, or PDF in `assets/` and set `\WFCCtitleimage{assets/title-photo.jpg}` before the document. It is scaled proportionally and center-cropped to fill the entire right 43.7% of the slide, including the top, right, and bottom edges. A missing image produces a warning and uses the color fallback. Portrait images work best; crop off-center subjects beforehand.

Optional collaborators: `\WFCCcollaborators{With ...}`. Keep cover text short enough to fit the left column. Use `[plain]` frames for full-slide figures. Bullet spacing is set per list with `\setlength{\itemsep}{5mm}`.

After loading the theme, override colors with `\definecolor{smokeorange}{HTML}{F5A33B}` (or another palette color). Available names: `smokebg`, `smokesurface`, `smokeink`, `smokemuted`, `smokeorange`, `smokepurple`, and `smokeline`.

## Files and sharing

- `beamerthemeWFCC.sty`: reusable theme, including the title layout.
- `example.tex` and `example.pdf`: six-slide demonstration and compiled preview.
- `references.bib`: one example citation.
- `assets/example-figure.tex` and `.pdf`: self-contained figure source and compiled asset; no third-party photography.
- `latexmkrc`: local build defaults.

To regenerate the example figure, run `pdflatex -output-directory=assets assets/example-figure.tex`, then rebuild the deck. The prebuilt figure means the standalone LaTeX package is only needed when regenerating that asset.

This directory can be the root of a separate GitHub repository. Share a tagged release ZIP or the supplied ZIP; no files outside this folder are required. Do not include TeX build intermediates. Add your preferred license before making a public release; see `LICENSE.md`.
