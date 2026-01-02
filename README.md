# Kestrel-llm Tool

Small, dependency-free utilities for maintaining an `LLM.txt` file in a repo. The `LLM.txt` contains a description about each file and line number for every class and function.

Checkout the [LLM.txt](LLM.txt) for this project!

## Install

From this repo:

```bash
python -m pip install -e .
```

From PyPI:

```bash
python -m pip install kestrel-llm
```

## Commands

Run these from **any directory inside** a repo that contains `LLM.txt` (or `llm.txt`)
somewhere above your current working directory.

- **`llm-check`**: verify `LLM.txt` covers all `.py` and `.md` files, enforces exactly two-sentence
  summaries, and enforces alphabetical sorting of both section headers and entries.
- **`llm-fix`**: sort sections/entries in `LLM.txt` and refresh `Symbols:` blocks.
- **`llm-sync`**: sort, strictly verify, refresh `Symbols:` blocks, then strictly verify again.

## Common options

- **`--repo-root PATH`**: override the repo root used for scanning.
- **`--llm-file PATH`**: override the `LLM.txt` path.
- **`--exclude-dir NAME`**: exclude additional directory names when scanning (repeatable).
- **`--log-level LEVEL`**: set logging level (or use `LOG_LEVEL` env var).

## Releasing

Bump `[project].version` in `pyproject.toml` and push to `main`. GitHub Actions will create a tag + GitHub Release for that version (for example `0.1.5`), which triggers the existing “Publish to PyPI” workflow.
