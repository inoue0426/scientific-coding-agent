# Scientific Coding Agent

Practical instructions for AI-assisted scientific Python and R development, with a focus on computational biology and machine learning.

[AGENTS.md](AGENTS.md) is the core guide. It covers the decisions that can change a scientific result: data alignment, biological replication, train/test separation, environment compatibility, numerical behavior, and honest verification.

## What this repository provides

A small, adaptable set of working rules for research code involving PyTorch, single-cell and bulk omics, patient data, and related statistical workflows.

The guide emphasizes:

- Reproducible inputs, environments, configurations, and experiment records.
- Splits that match the biological question, with preprocessing fitted within training folds.
- Fair comparisons, independent evaluation, and uncertainty at the correct sampling unit.
- Focused changes that respect existing code and scientific assumptions.
- Small verification runs before expensive local, GPU, or HPC jobs.

This repository contains documentation only. It does not install an agent, implement an analysis pipeline, or guarantee reproducible or scientifically valid results. Review generated code and research decisions.

## Use in a research project

1. Read [AGENTS.md](AGENTS.md) and select the rules that fit your project.
2. Add or merge them into the project's agent instructions. Preserve existing project-specific guidance rather than replacing it wholesale.
3. Add concrete commands, paths, data constraints, and evaluation details before asking an agent to run an analysis.
4. Review changes and verification evidence as you would a collaborator's contribution.

For tools that read AGENTS.md, place the adapted file in the appropriate project directory and confirm the tool's current instruction-loading behavior. Other tools may require a different instruction file or explicit context; follow their documentation rather than assuming automatic discovery.

### Project-specific details to fill in

| Area | Record in the target project |
| --- | --- |
| Environment | Supported Python/R versions, lockfiles, system/CUDA dependencies, setup command |
| Commands | Exact formatting, lint, test, smoke-run, and full-run commands |
| Data | Approved locations, access restrictions, accession/version, schema, reference annotation |
| Splits | Generalization unit, grouping keys, saved split manifest, overlap checks |
| Evaluation | Endpoint, metrics, aggregation unit, tuning protocol, untouched holdout |
| Runs | Seed/configuration capture, output locations, resource limits, scheduler usage |

For example, a project using uv might document `uv sync --locked` followed by `uv run python scripts/smoke_analysis.py`. An R project using renv might document `Rscript -e 'renv::restore(prompt = FALSE)'` followed by `Rscript scripts/smoke_analysis.R`. These are examples for a target project with the corresponding files, not commands provided by this repository. Environment restoration can download dependencies; use the project's approved setup process.

## Design choices

Existing project constraints take precedence over these defaults. The guide favors uv and pyproject.toml for new Python projects and renv for new R projects, while retaining established environments in existing work. Runtime versions follow scientific-library compatibility rather than an unconditional newest-version requirement.

Style rules support reviewability without forcing a cache dependency, redundant comments, or a new formatter onto an established codebase. Scientific protocols deserve stricter treatment: changing splits, preprocessing, exclusions, or metrics can change the question being answered.

## Contributing

Keep proposals concrete and broadly useful for scientific Python/R work. Explain the failure mode a rule addresses and any compatibility or compute tradeoff. Avoid machine-specific paths, private dataset details, personal configuration, and unnecessary framework requirements.

For documentation changes, verify relative links, Markdown structure, command examples, consistency between the two documents, and the absence of secrets or unrelated personal material. There is no executable test suite in this repository.

## License status

No license has been selected yet. Public visibility alone does not grant an open-source license; choose explicit terms before redistributing or incorporating substantial portions elsewhere.
