# Task: verify a tutorial's reproduced regression against the ORIGINAL PUBLISHED ARTICLE

Confirm that the tutorial reproduces a set of regression coefficients that MATCH a table printed in
the original peer-reviewed article — not the replication-code output, not "approximately," not "to
Monte-Carlo error." The bar is: numbers the tutorial prints line up with numbers printed in the paper.

## Steps
1. Open the tutorial `.Rmd` and its rendered `.pdf`. Identify the reproduced regression and the exact
   coefficient values it reports (the reproduction/match table). Note the study citation it gives.
2. Obtain the ORIGINAL ARTICLE and find the specific results table:
   - Search the web for the article (title + authors). Prefer an openly readable full text: the
     journal HTML/PDF, PubMed Central, an author's posted PDF/preprint, or a working paper. Use
     WebFetch to read it. Paywalls: try PMC, the author's website/ResearchGate/SSRN, Google Scholar
     "All versions," or a preprint. Make a real effort before concluding it's inaccessible.
   - Locate the table that corresponds to the reproduced model (usually the main/Table 1-5 model).
3. Compare a SET of coefficients (at least 3-5 key terms, ideally the whole column) between the
   tutorial's reproduced values and the article's printed table, to the precision the paper reports
   (signs, magnitudes, and significance stars/CIs where given).
   - IGNORE any caveats/excuses the tutorial itself contains — verify independently against the paper.

## Decide
- **MATCH**: the tutorial's coefficients match the article table. Report the side-by-side.
- **MISMATCH → try to FIX**: if they don't match, diagnose (wrong model column, subset, transform,
  reference category, scaling, weighting) and edit the tutorial so its reproduction matches the
  article's table; re-render (see below) and re-verify. If fixed, report FIXED with the new
  side-by-side.
- **CANNOT MATCH → DROP**: if after real effort you cannot make the tutorial reproduce a set of the
  article's printed coefficients (e.g. the study reports no matchable coefficient table — a pure
  Bayesian-model-averaging PIP list, a machine-learning-only paper, or the article is genuinely
  unobtainable), recommend DROP and explain precisely why.

## Rendering (only if you edit to fix)
`Rscript -e 'Sys.setenv(RSTUDIO_PANDOC="/Applications/RStudio.app/Contents/Resources/app/quarto/bin/tools/aarch64"); rmarkdown::render("x.Rmd", quiet=TRUE)'`
Do not touch the code-wrap `header-includes`, the data-loading, or add `breakanywhere`/`seqsplit`.

## Report back (be precise; this feeds an audit)
- Study citation + a URL to the article full text you used (or state it's inaccessible and what you tried).
- The specific table referenced (e.g. "Table 3, Model 2").
- A side-by-side of the compared coefficients: term | article value | tutorial value.
- VERDICT: MATCH | FIXED | DROP — and if DROP, the precise reason.
