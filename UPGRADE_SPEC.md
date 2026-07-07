# Task: upgrade an existing SH course tutorial with an EXTENSIVE descriptive-analysis section

The tutorial already has a short descriptive section plus a published-regression reproduction and an
out-of-sample prediction/extension. Bring its descriptive section up to the depth of the newer
tutorials: REPLACE the short descriptive section with a full EDA. Leave everything else unchanged.

## Hard constraints
- KEEP the reproduction and the prediction/extension sections and all their results exactly as-is.
- The tutorial reads its data from a raw GitHub URL — DO NOT change how data is loaded; just compute
  the EDA on the already-loaded data frame.
- Code-wrapping is already configured in the YAML `header-includes` (fvextra breaklines). DO NOT add
  `breakanywhere`, `seqsplit`, or a `\texttt` redefinition (they make pdflatex hang). Ensure the setup
  chunk has `options(width = 80)` (add it if missing).
- Keep every executable code line <= ~80 chars; round/select wide tables so nothing overflows the margin.
- Render with:
  `Rscript -e 'Sys.setenv(RSTUDIO_PANDOC="/Applications/RStudio.app/Contents/Resources/app/quarto/bin/tools/aarch64"); rmarkdown::render("x.Rmd", quiet=TRUE)'`

## Packages you may use (installed)
base R, ggplot2, dplyr, tidyr, knitr, GGally (ggcorr/ggpairs — NOTE: if `GGally::ggcorr` errors on the
installed ggplot2 4.x, build the correlation heatmap with a plain `ggplot()+geom_tile()` instead),
patchwork, gridExtra, e1071 (`skewness`,`kurtosis`), plus whatever the tutorial already loads. NOT
installed: corrplot, skimr, moments, psych.

## The extensive "Descriptive analysis" must cover (adapt to the data type)
1. Dataset & provenance: unit of analysis, N, #/type of variables, source, coverage, sampling; a
   variable-dictionary table (variable, role, type, description/coding) for the outcome + predictors.
2. The outcome in depth: full distribution (histogram+density, or class-balance bar for binary); a
   stats table with n, mean, sd, min, Q1, median, Q3, max, IQR, and skewness & kurtosis (e1071);
   discuss shape/skew/zero-inflation/floor-ceiling/outliers and whether a transform is warranted; for
   binary outcomes give the base rate and what it implies for evaluation.
3. Univariate predictor distributions: faceted histograms/boxplots for numeric + a full summary-stats
   table (n, n_missing, mean, sd, min, Q1, median, Q3, max, skew); frequency tables + bar charts for
   categorical/binary.
4. Missing-data analysis: per-variable missing counts/percentages + a pattern view (co-missingness /
   complete-case count); note the likely mechanism and how the reproduction handles it.
5. Bivariate relationships with the outcome: outcome vs each key predictor — scatter+smoother (with r)
   for numeric, boxplots/grouped means (with a test/effect size) for categorical; one tidy
   marginal-association table.
6. Multivariate structure/collinearity: a correlation heatmap of numeric predictors + VIFs from the
   reproduction model; flag |r| > 0.7.
7. Interpretive narrative throughout, tying the descriptives to the modeling that follows.

For wide datasets, profile the outcome + most important predictors thoroughly and give a full summary
TABLE for all — don't emit dozens of tiny panels. Make it clearly, substantially more extensive than
the original short section.

## After editing
Re-render to PDF (data comes over the web — it must knit). Report: PDF path, new page count,
confirmation the reproduction/prediction results are unchanged, and a bullet list of the new EDA content.
