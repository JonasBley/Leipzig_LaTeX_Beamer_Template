# Leipzig LaTeX presentation template

A clean Beamer starter based on the supplied QubitEdu presentation. It keeps the Leipzig logo, red/aquamarine title and section artwork, white content slides, blue emphasis, typography, footer, and callouts. It contains eight slides: a title, a section divider, five example layouts, and a closing slide.

## Quick start

1. Copy this folder for each new presentation.
2. Edit `TitlePageInfo.tex` for the title, author, affiliation, and event/date.
3. Replace the example frames in `main.tex` with your content. Each layout is marked by a comment and can be copied independently.
4. Compile `main.tex` with **XeLaTeX or LuaLaTeX**. In Overleaf, upload this folder's contents, select `main.tex` as the main document, and choose XeLaTeX in the compiler settings.

Local build with latexmk:

```text
latexmk main.tex
```

Or compile twice directly:

```text
xelatex -interaction=nonstopmode -halt-on-error main.tex
xelatex -interaction=nonstopmode -halt-on-error main.tex
```

LuaLaTeX works with the same two-pass procedure. Do not use pdfLaTeX: the theme uses fontspec. The template needs ordinary TeX Live/MiKTeX packages (Beamer, fontspec, TikZ, tcolorbox, booktabs, and tabularx). It does not need BibTeX, Biber, shell escape, external fonts, or an external data source. It uses Arial if installed and TeX Gyre Heros otherwise, so line wrapping may differ slightly between computers.

## Files

| File | Purpose |
|---|---|
| `main.tex` | Main document and five commented example layouts |
| `TitlePageInfo.tex` | Metadata for each new presentation |
| `beamerthemeLeipzigClean.sty` | Consolidated theme and reusable helpers |
| `notes.tex` | Optional entry point with interleaved speaker notes |
| `images/logo_leipzig.pdf` | Original Leipzig logo |
| `images/poincare.png` | Replaceable example figure from the original deck |
| `.latexmkrc` | Local build configuration using XeLaTeX |

## Common changes

- **Aspect ratio:** change `169` to `43` in `main.tex`. Both title/section layouts are supported. Recheck your content after changing the canvas.
- **Section divider:** use `\section{Your section}`. Comment out `\makesectionpopup` to omit the divider slides. Dividers do not advance the slide counter.
- **Overview:** uncomment `\maketableofcontents` and add your sections. Compile twice.
- **Images:** place your image in `images/` and change the filename in the figure example. The sizing option preserves its aspect ratio.
- **Short source in footer:** use `\slidesource{Author, year}` within a frame. It clears automatically on the following frame. Keep footer sources short; use `\source{...}` inside the slide for longer attribution.
- **Emphasis:** use `\keyidea{Your takeaway}` for the centered blue emphasis style or `\alert{important text}` for red text.
- **Visible callouts:** use `\begin{mynote}[Title] ... \end{mynote}` or `\begin{myalert}[Title] ... \end{myalert}`.
- **Speaker notes:** put `\note{Speaking notes}` inside a frame and compile `notes.tex` instead of `main.tex`. Normal builds hide notes.
- **References:** add a Beamer `thebibliography` frame, or add your preferred bibliography package if your talk needs a managed bibliography. No study-specific bibliography is carried over.
- **Branding:** the theme defines `\presentationlogo` and `\presentationfooter`. The original section artwork also contains the university wordmark, so adapting this template to a different institution requires changing that artwork as well.

The original presentation and study content remain separate. The example image and Jones-vector slide demonstrate layouts; they are not a new report of study findings. No participant records, recruitment links, or study results are included.
