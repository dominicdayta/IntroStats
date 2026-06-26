# Lecture Notes on Introductory Statistical Inference

Lecture notes and companion Beamer slides for **Stat 195**, a bridge course on statistical inference for incoming graduate students in the Professional Masters in Data Science program at the University of the Philippines. Most students arrive with little or no background in probability theory or statistical inference. These materials aim to give them enough of the fundamentals—normally spread across several undergraduate statistics courses—to prepare for later work in statistical modeling and machine learning, while staying readable for a first exposure.

## Repository layout

```
IntroStats/
├── lecture-notes/          # Article-style notes (one self-contained folder per week)
│   ├── week-1-basic-concepts/
│   ├── week-2-foundations/
│   ├── week-3-estimation/
│   ├── week-4-correlation/
│   └── week-5-nonparametrics/
└── lecture-slides/         # Beamer slides derived from the notes
    └── week-1-basic-concepts/
```

Each week under `lecture-notes/` is compiled on its own. A typical folder contains:

| File | Purpose |
|------|---------|
| `week-N.tex` | Main document for that week |
| `kafkanotes.sty` | Shared style file (margin notes, layout, fonts) |
| `images/` | Figures referenced by that week's `.tex` file (when present) |

Slides live under `lecture-slides/` in matching week folders. Each slide deck is a standalone `main.tex` file. Only Week 1 slides are included so far; additional weeks can follow the same pattern.

## Contents

| Week | Folder | Topics |
|------|--------|--------|
| **I. Basic Concepts in Statistics** | `week-1-basic-concepts` | Data collection and summarization; variables and measurement; basic probability; Kolmogorov's axioms |
| **II. Foundations of Inference** | `week-2-foundations` | Random variables and distributions; sampling distributions; law of large numbers; central limit theorem |
| **III. Estimation and Hypothesis Testing** | `week-3-estimation` | Point and interval estimation; confidence intervals; introductory hypothesis tests |
| **IV. Correlation and Regression Analysis** | `week-4-correlation` | Measuring association; simple linear regression; modeling relationships between variables |
| **V. Nonparametric Statistics** | `week-5-nonparametrics` | When parametric assumptions fail; rank-based and distribution-free alternatives |

## Requirements

A full **TeX Live** installation (2020 or later) is recommended. The notes are built with **pdfLaTeX**.

### LaTeX packages

**Lecture notes** — loaded via `kafkanotes.sty` and the main `.tex` files:

- `geometry`, `amsmath`, `graphicx`, `floatrow`, `sidenotes`
- `titlesec`, `fancyhdr`, `lmodern`, `hyperref`
- `multirow` (weeks 3–5)

**Lecture slides** — Beamer with the `tcolorbox` inner theme.

On a minimal TeX Live install, missing packages can be added with `tlmgr`, for example:

```bash
tlmgr install sidenotes floatrow tcolorbox multirow
```

## Compiling

Run all commands from inside the relevant week folder so that `kafkanotes.sty` and `images/` resolve correctly.

### Lecture notes

```bash
cd lecture-notes/week-1-basic-concepts
pdflatex week-1.tex
pdflatex week-1.tex    # second pass for table of contents and cross-references
```

Replace the directory and filename for other weeks (`week-2.tex`, `week-3.tex`, etc.).

Using `latexmk` (handles multiple passes automatically):

```bash
cd lecture-notes/week-1-basic-concepts
latexmk -pdf week-1.tex
```

The output PDF is written alongside the source (e.g. `week-1.pdf`). Build artifacts (`.aux`, `.log`, `.toc`, …) are listed in `.gitignore`.

### Lecture slides

```bash
cd lecture-slides/week-1-basic-concepts
pdflatex main.tex
pdflatex main.tex
```

Or, with `latexmk`:

```bash
cd lecture-slides/week-1-basic-concepts
latexmk -pdf main.tex
```

## License

This project is licensed under the [GNU General Public License v3.0](LICENSE).
