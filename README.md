# Applied Statistics and Experiments — Research Project Template

This repository is the official template for the **course research project** in *Applied Statistics and Experiments*. It provides a ready-to-use LaTeX skeleton so that you can focus on your statistical analysis and writing rather than on document formatting.

## What's in this repository

```
.
├── README.md               # This file
├── main.tex                 # Entry point — compiles the full report
├── sections/                # optional
│   ├── 01_introduction.tex
│   ├── 02_related_work.tex
│   ├── 03_data_and_methods.tex
│   ├── 04_experimental_design.tex
│   ├── 05_results.tex
│   ├── 06_discussion.tex
│   └── 07_conclusion.tex
├── tikz/                 # TikZ plots, diagrams (.tex, .pdf)
├── tables/                  # Standalone .tex files for large tables (optional)
├── data/                    # Raw or processed datasets used in the analysis
├── code/                    # Analysis scripts (R, Python, etc.)
├── references.bib           # BibTeX bibliography
└── *.cls / *.sty            # any other LaTeX related files
```

Feel free to add or remove sections to fit the scope of your project, but keep the overall structure recognizable — it makes grading and peer review faster and more consistent.

## Getting started

1. **Clone your repo:**
   ```bash
   git clone <your-repo-url>
   cd <your-repo-name>
   ```
2. **Compile the report.** You can compile with a local LaTeX distribution. Locally requires `latexmk` is installed:
   ```bash
   latexmk -pdf -interaction=nonstopmode -file-line-error main.tex
   ```
3. **Edit content**, not structure. Write your project inside the files under
   `sections/`; `main.tex` simply `\input{}`s them in order.


## Project requirements

Your paper should include, at minimum:

- **Introduction** — research question(s) and motivation
- **Related work** — brief review of relevant prior studies
- **Methodology** — description of the dataset and statistical methods used
- **Results** — statistical findings, supported by tables and figures
- **Discussion** — interpretation, limitations, and threats to validity
- **Conclusion** — summary and possible future work
- **References** — properly cited using BibTeX (`references.bib`)


## Adding figures and tables
- **TikZ diagrams are required.** For flowcharts, diagrams, architecture sketches, decision trees, etc., prefer a native `tikzpicture` over a pasted-in screenshot or an externally drawn image — it stays vector-quality, matches the document's fonts, and is easy to tweak. `main.tex` already loads `tikz` (with the `positioning`, `arrows.meta`, and `shapes.geometric` libraries). For a non-trivial diagram, keep the `tikzpicture` in its own file under `figures/` and pull it in with `\input{}` rather than inlining it in a section file.
- For large or complex tables, create a separate `.tex` file under `tables/` and `\input{}` it from the relevant section — this keeps section files readable.

## Reproducibility
If your analysis relies on scripts (R, Python, Jupyter notebooks, etc.), place them in `code/` along with a short note on how to run them and which package versions are required. Where possible, keep the raw data in `data/` and treat it as read-only — write any cleaned/derived datasets to a separate file rather than overwriting the original.

## Citation style
This template uses **natbib** for citations and **cleveref** for cross-references.
Please use these consistently instead of the plain `\cite{}` / `\ref{}` commands.

- **Citations (natbib):**
  - `\citep{key}` → parenthetical citation, e.g. "(Smith et al., 2020)"
  - `\citet{key}` → in-text citation, e.g. "Smith et al. (2020) found that..."
  - The bibliography style is set to `plainnat` in `main.tex`, which is compatible with natbib. Do not switch back to plain `\cite{}` with this style.

- **Cross-references (cleveref):**
  - `\Cref{fig:my-figure}` / `\cref{fig:my-figure}` → automatically inserts the correct label word (e.g. "Figure 3", "Table 2", "Section 4") based on what you're referencing, so you don't need to write `Figure~\ref{...}` by hand.
  - Use `\Cref{...}` at the start of a sentence (capitalized) and `\cref{...}` mid-sentence.
  - `cleveref` must be loaded **after** `hyperref` in the preamble — this is already set up correctly in `main.tex`; do not reorder these two packages.

Use consistent BibTeX entries in `references.bib`, and cite them with `\citep{}` / `\citet{}` rather than pasting formatted references directly into the text.

## main.tex
A worked appendix in `main.tex` shows ready-to-copy snippets for a figure, a table, a TikZ diagram, and both citation commands — compile the template as-is to see them rendered, then delete the appendix once you no longer need it.

## Submission checklist
- [ ] Report compiles cleanly with no errors or missing references. Warnings are acceptable.
- [ ] All figures/tables are referenced in the text
- [ ] Code (if any) runs and reproduces the reported results
- [ ] Bibliography is complete and consistently formatted

## Questions

If you run into template issues (compilation errors, missing packages, etc.), reach out to the course instructor before the submission deadline.
