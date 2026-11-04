# Scientific Python

Use these guidelines for computational biology and machine learning. Follow the project's existing conventions and make focused, reviewable changes.

## Project context

Fill in these details when starting a project. Do not guess missing commands or scientific settings.

- Goal:
- Environment and setup command:
- Test and smoke-run commands:
- Data and output locations:
- Split unit and evaluation metrics:

## Code

- Use Python. Prefer uv, pyproject.toml, and a committed uv.lock for new projects; preserve existing environments and supported library versions.
- Write small functions with descriptive names, useful type hints, and brief explanations of non-obvious scientific logic.
- Use the configured formatter and linter; prefer Ruff for new projects.
- Avoid unrelated refactoring, unnecessary dependencies, and hidden notebook state.
- Keep secrets, restricted data, and large generated artifacts out of Git.

## Scientific integrity

- Keep raw data unchanged. Record data/reference versions, filtering, code revision, configuration, environment, seeds, and run commands.
- Validate IDs, shapes, missing values, and join cardinality. Align tables and matrices by explicit identifiers.
- Preserve the distinction between raw counts and transformed data. Keep sparse matrices sparse when practical.
- Split at the unit required by the research question, such as patient, donor, study, or drug. Check overlap and keep related records together.
- Fit learned preprocessing and feature selection on training data within each fold. Tune on validation data; reserve the test set for final evaluation.
- Keep split assignments and evaluation rules consistent across methods. Disclose protocol changes and any use of held-out data during development.
- Treat biological replicates as the independent sampling unit; cells and random seeds do not replace independent donors or patients.
- Report relevant metrics, uncertainty, exclusions, and failed runs. Do not select only favorable results or imply causality from association.

## Verification

- Start with a small representative run before expensive analyses. Confirm scope before unplanned costly jobs or destructive actions.
- Run the project's relevant checks and verify ID alignment, split independence, and numerical behavior when affected.
- Do not weaken checks to make a result pass. Report changes to sample counts or numerical results.
- Finish with a short account of changes, checks and outcomes, and remaining limitations. Never claim a check or experiment was run when it was not.
