# Scientific Python

Use these guidelines for computational biology and machine learning. Follow the project's existing conventions and make focused, reviewable changes.

## Project context

Fill in these details when starting a project and keep them current. Inspect existing instructions and files first; ask when missing settings materially affect scientific conclusions or compute cost.

- Research question and scope:
- Environment and setup command:
- Test and smoke-run commands:
- Data/reference versions, access restrictions, and locations:
- Run records and artifact locations:
- Split/generalization unit, cohort, and saved split assignments:
- Primary metrics, aggregation unit, and baselines:
- Compute budget and scheduler/resource limits:

## Code

- Use Python. Prefer uv, pyproject.toml, and a committed uv.lock for new projects; preserve existing environments and supported library versions.
- Write small functions with descriptive names, useful type hints, and brief explanations of non-obvious scientific logic.
- Use the configured formatter and linter; prefer Ruff for new projects.
- Avoid unrelated refactoring, unnecessary dependencies, and hidden notebook state.
- Keep secrets, restricted data, and large generated artifacts out of Git.

## Scientific integrity

- Keep raw data unchanged. Record data/reference versions, filtering, and sample counts.
- Validate IDs, shapes, missing values, and join cardinality. Align tables and matrices by explicit identifiers.
- Preserve the distinction between raw counts and transformed data. Keep sparse matrices sparse when practical.
- Split at the unit required by the research question, such as patient, donor, study, or drug. Check overlap and keep related records together.
- Fit learned preprocessing and feature selection on training data within each fold. Tune on validation data; reserve the test set for final evaluation.
- Save and reuse split assignments. Disclose protocol changes and any use of held-out data during development; if test results guide changes, use a fresh holdout or label subsequent results exploratory.

## Evaluation and experiment records

- Compare against simple, strong baselines with the same cohorts, splits, metrics, and equivalent data access. Justify preprocessing differences; report tuning budgets and use ablations to support claims about added complexity.
- Estimate uncertainty at the independent sampling unit, respecting patient, donor, or study dependence in confidence intervals, bootstraps, and tests. Cells and random seeds do not replace independent biological replicates.
- Report effect sizes and relevant metrics with denominators, exclusions, and missing predictions. Account for multiple testing where appropriate; do not imply causality from association.
- Preserve negative results, failed runs, and reasons for exclusion. Do not select only favorable seeds, folds, or metrics.
- Give each run a unique ID under the documented output location. Save code revision and local changes, resolved configuration, environment, data/split references, seeds, commands, metrics, logs, and artifact paths without overwriting prior results. Plain files are sufficient; use an existing tracker if configured.

## Figures

- Use Arial at 10 pt for all figure text, including titles, axis labels, ticks, legends, annotations, panel labels, and colorbars. Set figure dimensions at the intended final size so resizing does not change the required text size.
- Keep figure styling consistent through shared plotting defaults: colors, category mappings, line widths, markers, and comparable axis scales. Use color-accessible palettes and label axes with units and transformations.
- Export a vector PDF with embedded TrueType fonts and editable text for Adobe Illustrator; do not outline text or rasterize the entire figure. Verify Arial is available before rendering; do not silently substitute another font. Check font embedding, text editability, and clipping in the exported file; report any verification that could not be performed.
- Define error bars, sample counts, and the independent sampling unit in captions. Save plotting code, source-data references, and settings so figures can be regenerated.

## Verification

- Start with a small representative run before expensive analyses. Confirm scope before unplanned costly jobs or destructive actions.
- Estimate runtime, memory, storage, and GPU needs before scaling. For HPC/Slurm, follow scheduler policies, set resource and wall-time limits, bound sweep concurrency, and record job IDs and exit status. Check failed jobs before retrying; checkpoint long runs when useful.
- Run the project's relevant checks and verify ID alignment, split independence, and numerical behavior when affected.
- Do not weaken checks to make a result pass. Report changes to sample counts or numerical results.
- Finish with a short account of changes, checks and outcomes, and remaining limitations. Never claim a check or experiment was run when it was not.
