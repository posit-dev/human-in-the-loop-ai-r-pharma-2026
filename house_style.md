# House Style Guide for Tables, Figures & Listings (Training Copy)

> **What this is:** a short, invented-but-realistic style guide, modeled on the
> kind of internal standard biostatistics/programming groups keep.

---

## 1. Kaplan-Meier figures

- **Palette (by arm, in this fixed order):** Placebo = `#BDBDBD` (grey),
  low dose = `#4A90D9` (blue), high dose = `#D9534F` (red). Always map arms
  to colors in protocol order, not alphabetical order.
- **Always include:** a number-at-risk table below the x-axis, and a 95%
  confidence band (shaded, 20% opacity). The risk table should be no smaller than 85% of the plot to ensure legibility.
- **Legend placement:** the legend must never overlap the plot area, since
  this obscures the data. Always orient the legend horizontally and place it beneath the plot.
- **Axis labels:** x-axis in days unless the audience is a general
  clinical one, in which case convert to months (divide by 30.4375) and
  say so in a footnote.
- **Title format:** `"<Endpoint> by Treatment Arm"` -- e.g.
  *"Progression-Free Survival by Treatment Arm"*. No dataset name, no
  study ID, in the title itself (those go in a caption/footnote).
- **Censoring marks:** show tick marks for censored observations; do not
  hide them for a "cleaner" look.
- **Y axis limits:** the y axis should always begin at 0 and end at 1.

## 2. Tables (TLGs generally)

- **Rounding:** percentages to 1 decimal place; continuous summary
  statistics (mean, SD, median) to 1 more decimal place than the
  recorded precision of the raw variable.
- **Cell format for counts:** `n (xx.x%)` -- e.g. `23 (24.0%)` -- always
  with the percent sign, always one space before the parenthesis.
- **Denominators:** every percentage is out of the column's total N
  (the treated/analysis population for that column), never out of the
  count of subjects who happen to have a non-missing value, unless a
  footnote says otherwise.
- **Zero cells:** show `0` or `0 (0.0%)`, never a blank cell and never `NA`.
- **Column order:** Placebo, then active arms in ascending dose order,
  then (if present) a combined/"All Subjects" column last.
- **Footnote style:** numbered footnotes as superscript letters in the
  header (`a`, `b`, `c`...), spelled out below the table, in the order
  they first appear reading left-to-right, top-to-bottom.
- **Sorting within a table:** for AE-type tables, sort System Organ Class
  and Preferred Term by descending frequency in the **total** column, not
  alphabetically -- unless a listing (not a summary table), which sorts
  alphabetically by subject ID.

## 3. Populations & flags

- **Safety population (SAFFL = "Y"):** at least one non-zero dose of
  study treatment. This is the default denominator for AE tables unless
  stated otherwise.
- **Treatment-emergent (TRTEMFL = "Y"):** onset on or after the date of
  first dose (`>=`, inclusive), and no later than 30 days after the date
  of last dose. Same-day-as-first-dose AEs are always treatment-emergent
  -- do not exclude them.

## 4. File & object naming (for generated code)

- Analysis dataset objects in an R session: lower-case dataset name
  (`adsl`, `adae`), never with a suffix like `_final` unless it's a true
  work-in-progress intermediate.
- Output objects (tables/figures) use the *table shell ID* as the object
  name where one exists, e.g. `t_ae_soc_pt`, `f_km_pfs`.
