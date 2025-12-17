# Repo Summary Sync — Operator Instructions

**Goal:** Ensure the repos `LLM.txt` is fully in sync with the repository, with **exactly two sentences** per file entry, and the file sorted as required.

## Rules for Summaries

* Write **exactly two sentences** per file. No fragments, no bullet points, no code blocks.
* Style: present tense, active voice, concise and specific. Mention purpose, key responsibilities, notable inputs/outputs, and important dependencies or side effects.
* Do **not** change or reword existing entries unless required by the tool; follow the **exact formatting conventions already present** in `LLM.txt` (headers, separators, ordering).
* Only include **text/code files** (source, configs, docs). **Skip** binaries and generated artifacts (e.g., images, archives, lockfiles, build outputs, `.git`, `.venv`, `node_modules`, caches).

## Procedure

1. From the repo root, run:

   ```bash
   llm-sync
   ```

   * Treat its output as the source of truth for **missing**, **duplicate**, or **unsorted** entries.
2. For each **missing** file it reports:

   * Open the file, review its contents and role in the project.
   * Draft a **two-sentence** summary per the Rules above.
   * Add the entry to `LLM.txt`, mirroring the file’s path and the file’s existing formatting style in `LLM.txt`.

3. Re-run `llm-sync` and repeat edits until it returns clean.

## Acceptance Criteria

* `llm-sync` reports **no missing files**, **no duplicate entries**, **no repeated headers**, **no unsorted entries**, and **all entries are exactly two sentences**.
* `LLM.txt` format and style match existing conventions; no duplicate entries; binaries and generated files are excluded.

**Notes**

* If a file is non-summarizable (binary or generated), exclude it; if the verifier still flags it, add a minimal two-sentence rationale stating it’s a generated/binary asset and where its source is defined.
* Maintain idempotency: subsequent runs of the verify script should remain clean without manual intervention.
