# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

LaTeX thesis template for bachelor/master theses at Technische Hochschule Nürnberg Georg Simon Ohm. Uses KOMA-Script (`scrbook`) document class, compiled with `pdflatex` and `bibtex`. Produces PDF/A-3b compliant output via the `pdfx` package.

## Build Commands

- **Build thesis PDF:** `make run` (or just `make`)
- **Clean build artifacts:** `make clean`

The build pipeline runs: `pdflatex` (draft) x2 for aux → `bibtex` → `pdflatex` (draft) → `pdflatex` (final). Requires a complete TeX distribution with `pdflatex` and `bibtex`.

**Prerequisite:** The signed form `SB_0050_FO_Pruefungsrechtliche_Erklaerung_und_Erklaerung_zur_Veroeffentlichung_der_Abschlussarbeit_public.pdf` must exist in the root directory. Download from the Ohm intranet.

## Architecture

- **`thesis.tex`** — Main document. Contains all package imports, page setup, metadata commands (title, author, degree program, reviewers), and document structure. Thesis metadata is defined via `\newcommand` at the top (lines 22-32).
- **`cover.tex`** — Title page layout with TH Nürnberg logo.
- **`content/`** — Chapter files: `0_abstract.tex` through `6_summary.tex`, plus `a1_supplemental.tex` for appendix.
- **`refs.bib`** — BibTeX bibliography database.
- **`wmaainf.bst`** — Custom bibliography style (alphanumeric labels, alphabetical order).
- **`glossary.tex`** — Glossary entries loaded via `\makenoidxglossaries`.
- **`figures/`** — Image assets (includes TH Nürnberg logo).
- **`listings/`** — External code files for `\lstinputlisting`.

## Key Conventions

- **Sprache:** Die Arbeit ist auf Deutsch. Babel ist konfiguriert mit `\usepackage[english,ngerman]{babel}` (ngerman als letzte/aktive Sprache). Zum Umschalten auf Englisch die Reihenfolge tauschen.
- **One sentence per line** in .tex files for clean git diffs; use soft wrap, not hard line breaks.
- **UTF-8 encoding** required on all files.
- **Custom abbreviation commands** defined in `thesis.tex` (lines 118-126): `\ua`, `\zB`, `\dahe`, `\bzw`, `\eg`, `\ie`, `\wrt`, `\etal`.
- Headline capitalization follows the IEEE Style Manual.
