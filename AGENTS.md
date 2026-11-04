# Scientific Python guidelines

Write clear, reproducible code for computational biology and machine learning. Prioritize scientific correctness and focused, reviewable changes.

## Working approach

- Read relevant code, project instructions, environment files, and documented commands before editing. Follow existing conventions and preserve unrelated work.
- Make the smallest change that solves the task. Avoid speculative abstractions, broad reformatting, unnecessary dependencies, and silent fallbacks.
- State material assumptions. Ask when an unresolved choice changes the scientific question, data access, evaluation protocol, or substantial compute cost.
- Never invent results, citations, dataset properties, or successful checks. Distinguish observations from hypotheses and untested claims.

## Environment and code

- Use the project's supported Python version, package manager, lockfiles, and configured tools. Prioritize compatibility with PyTorch, CUDA, and bioinformatics libraries over newer syntax.
- For new projects, prefer uv with pyproject.toml and a committed uv.lock. A PEP 723 script is sufficient for a standalone analysis.
- Reuse existing formatting and linting configuration; prefer Ruff for new projects. Add dependencies and caching only when needed.
- Prefer small functions, descriptive names, explicit inputs/outputs, and useful type hints. Keep argument parsing in main() and executable code behind a main guard.
- Document non-obvious scientific assumptions, units, and numerical choices. Avoid comments that repeat the code.
- Keep secrets, restricted data, model weights, and large generated artifacts out of Git. Use approved storage and environment variables for credentials.

## Reproducibility and data integrity

- Keep raw inputs immutable and derived outputs separate. Do not overwrite prior experiment results.
- Record data sources and versions, reference genome/annotation versions, filtering rules, and sample counts. Use checksums when practical.
- Save the code revision, local changes, resolved configuration, environment, split assignments, seeds, and run command with results.
- Seed relevant Python, NumPy, and PyTorch generators. Record device, precision, and determinism settings when relevant; a seed alone does not guarantee identical results.
- Use configurable or project-relative paths. Scripts must not depend on hidden notebook state or machine-specific paths. Run notebooks from a clean state when their outputs are deliverables.
- Validate identifiers, shapes, units, missingness, duplicates, and expected ranges. Join by explicit keys and check cardinality and unmatched records; never assume row order matches matrices or labels.
- Preserve patient, donor, sample, cell, gene, and perturbation identifiers. Document ambiguous identifier mappings and exclusions.
- For single-cell analyses, distinguish cells from independent biological replicates and raw counts from transformed layers. Keep QC, normalization, batch correction, covariates, and aggregation explicit.
- Preserve sparse representations where practical and check memory before densifying large matrices.
- Treat patient data and metadata as sensitive; do not expose identifiable or restricted records in examples, logs, or published outputs.

## Leakage prevention

- Define the unit of generalization before splitting. Hold out patients, donors, cell lines, studies, drugs, time periods, or sequence-similarity groups as the research question requires.
- Keep related records and technical replicates together when independence requires it. Check identifier, duplicate, and relevant biological overlap across splits.
- Save and reuse split assignments. Do not silently change cohorts, exclusions, seeds, or splits during comparisons.
- Fit learned preprocessing, imputation, scaling, feature selection, dimensionality reduction, batch correction, and resampling only on training data within each fold.
- Use validation data or inner cross-validation for tuning, thresholds, calibration, and early stopping. Reserve the test set for final evaluation.
- Disclose intentional use of unlabeled held-out inputs as a transductive protocol. If test results influence development, obtain a fresh holdout or label subsequent results exploratory.
- Key caches by inputs, parameters, code/data versions, and split context to prevent stale results or cross-split reuse.

## Evaluation integrity

- Specify the endpoint, cohort, metrics, aggregation unit, and comparison protocol before interpreting results.
- Compare baselines and proposed methods using equivalent data access, splits, preprocessing, and evaluation rules. Report tuning budgets and meaningful differences.
- Report denominators, exclusions, missing predictions, failed runs, and relevant subgroup results. Do not select only favorable seeds, folds, or metrics.
- Quantify uncertainty at the independent biological sampling unit. Respect patient/donor/study dependence in bootstraps and tests; seed variability is not biological uncertainty.
- Report effect sizes and multiple-testing correction where appropriate. Distinguish predictive association from causal or mechanistic evidence.
- Do not weaken checks or change evaluation rules to improve reported results. Explain intentional changes to numerical behavior and assess their scientific impact.

## Compute and verification

- Start with a small representative smoke run. Estimate memory, runtime, storage, and accelerator needs before expensive work.
- Follow HPC scheduler policies. Confirm scope before unplanned costly jobs, large sweeps, external data transfers, or destructive operations.
- Run configured checks and focused tests appropriate to the change. Verify scientific invariants such as split independence, ID alignment, missing-data handling, and known toy results.
- Compare numerical outputs against a baseline or independent reference when behavior may change. Use justified numerical tolerances.
- Finish with what changed, why, checks run and their outcomes, numerical effects, and remaining limitations. Clearly identify experiments or checks that were not run.
