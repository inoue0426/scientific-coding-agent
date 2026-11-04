# Scientific Coding Agent

Practical instructions for AI-assisted scientific Python development in computational biology and machine learning.

[AGENTS.md](AGENTS.md) covers reproducibility, biological data integrity, leakage prevention, fair evaluation, focused code changes, and verification. It is intended for workflows involving PyTorch, single-cell and bulk omics, patient data, and related analyses.

## Use

1. Read [AGENTS.md](AGENTS.md) and merge the relevant rules into your project's agent instructions.
2. Add your supported environment, exact check/run commands, data locations, split definitions, evaluation protocol, and compute limits.
3. Review generated code and verification evidence before relying on results.

Preserve project-specific instructions and existing environments. For new Python projects, the guide prefers uv and pyproject.toml; existing projects retain their supported tools and library versions.

Confirm how your coding tool loads instructions. Tools that do not read AGENTS.md may require explicit context or a different instruction file.

## Scope

This repository provides guidance, not an executable analysis pipeline or a guarantee of scientific validity. It has no runtime dependencies or executable test suite.

Keep contributions focused on concrete scientific failure modes. For documentation changes, check links, consistency, and examples, and exclude private data or personal configuration.

No license has been selected yet; public visibility alone does not grant an open-source license.
