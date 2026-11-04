# Scientific Coding Agent

A minimal instruction template for scientific Python projects in computational biology and machine learning.

## Start a project

1. Copy or merge [AGENTS.md](AGENTS.md) into your project, preserving existing project-specific instructions. If GitHub shows **Use this template**, you can also create a repository from it.
2. Fill in its project context: research question, exact setup/check/smoke-run commands, data access and versions, output locations, splits, metrics, baselines, and compute limits. Replace placeholders with actual project settings.
3. Replace this README with your project's purpose, setup, and usage.

The guide covers leakage prevention, fair baseline comparisons, independent sampling and uncertainty, negative results, reproducible run records, and cost-aware GPU/HPC jobs. Plain files are enough for experiment tracking; no tracking service is required.

Confirm how your coding tool loads instructions; tools that do not read AGENTS.md need the guidance supplied explicitly or in their supported instruction file. Project-specific context should supply concrete settings and document justified departures from the template.

## Scope and maintenance

This is a Python-focused instruction template, with no example pipeline, runtime dependencies, or executable test suite. Preserve existing project environments. Review generated code and evidence before relying on scientific conclusions.

Keep changes focused. For documentation edits, review the diff, relative links, and consistency between this README and AGENTS.md.

## License

No license has been selected. License selection remains a maintainer decision.
