# AGENTS refactor prompts

## 1. Use Claude Sonnet 5 to read the giant legacy AGENTS.md and `docs/agents/` and produce an audit.
You are a senior agent-harness engineer and staff architect.

Task: Audit these legacy AGENTS.md and `docs/agents/` files. Do not rewrite them yet.

Produce:
1. Instructions that are still valuable and project-specific.
2. Instructions that are stale, vague, duplicated, contradictory, or harmful.
3. Instructions that should become scripts, tests, lint rules, CI checks, or package.json commands.
4. Content that belongs in AGENTS.md.
5. Content that belongs in deeper docs.
6. Content that should be deleted.
7. Missing repo facts that must be verified from package.json, test config, CI config, tsconfig, and build tooling.
8. Questions or TODOs that require repo inspection.
9. A proposed target documentation structure.

Use harness-engineering principles:
- AGENTS.md should be a compact repo map, not an encyclopedia.
- Detailed guidance should live in smaller docs.
- Rules should be mechanically verifiable where possible.
- Preserve project-specific truths.
- Do not invent repo facts.

Write down the audit to `docs/plans/` as a markdown file.


## 2. Claude Fable 5 designs the harness architecture. Fable should do the judgment-heavy part: deciding what the docs should become.
You are designing a vendor-agnostic agent harness for a legacy React application.

Do not write OpenAI-style docs, Claude-style docs, Cursor-style docs, or Codex-style docs. Write repository-local, vendor-agnostic harness docs that any capable coding agent or human maintainer can use.

Inputs:
- Audit of the old AGENTS.md and `docs/agents/` (docs/plans/<your_audit_file>.md)
- Repository metadata
- Current package.json scripts
- Build/test/lint/typecheck/format config
- CI config
- Relevant existing docs

Goal:
Design a durable, vendor-neutral documentation harness that helps any coding agent or human contributor work safely in this repo.

Do not write the final docs yet. First design the structure.

Return:
1. Recommended target file structure.
2. Purpose of each file.
3. What content belongs in AGENTS.md versus deeper docs.
4. Whether files should be deleted, replaced, or kept as a tiny PR checklist.
5. Mapping from old sections to new locations.
6. Rules that should become mechanical checks.
7. Rules that should stay as human/agent judgment.
8. Repo facts still requiring verification.
9. Naming conventions for the docs.
10. A maximum length budget for each file.

Constraints:
- Avoid vendor-specific phrasing such as “Claude should,” “ChatGPT should,” “Codex should,” or “Cursor should.”
- Avoid model-specific assumptions.
- Avoid instructions that only work in one IDE or agent runtime.
- Prefer commands, paths, and acceptance criteria over vague advice.
- Keep the root AGENTS.md short enough to be read on every task.
- Make stale docs easier to detect.


## 3. Claude Fable 5 writes the first full version. This is the pass where the actual docs should be written. Since you want agnostic harness docs, Claude Fable should be the primary author, not ChatGPT.
Using the approved redesign (docs/plans/<your_audit_file>.md), write the vendor-agnostic agent harness docs.

Do not write OpenAI-style docs, Claude-style docs, Cursor-style docs, or Codex-style docs. Write repository-local, vendor-agnostic harness docs that any capable coding agent or human maintainer can use.

Write full contents for all the cited files.

Style requirements:
- Vendor-agnostic.
- Concise.
- Direct.
- Command-oriented.
- Repository-specific where facts are known.
- Explicit TODOs where facts are unverified.
- No generic React advice unless it affects this repository.
- Prefer objective acceptance criteria.
- Keep each doc maintainable.

The instructions in the approved architecture artifact overrides any directions above.


## 4. GPT-5.5 Thinking critiques neutrality and portability. Use ChatGPT here as a skeptical reviewer, not the main style-setter.
Review these proposed vendor-agnostic agent harness docs.

Your job is critique only. Do not rewrite everything unless necessary.

Check for:
1. Vendor-specific assumptions.
2. Claude/OpenAI/Cursor/Codex-specific phrasing.
3. Instructions that only work in one coding agent.
4. Overloaded AGENTS.md content.
5. Duplicated guidance across files.
6. Vague rules that should become commands, tests, lint rules, CI gates, or acceptance criteria.
7. Missing legacy-app safety rails.
8. Unsupported assumptions about the React app.
9. Places where repo facts should be marked TODO instead of asserted.
10. Sections that are too generic to be useful.

Return:
- High-priority issues.
- Medium-priority issues.
- Concrete edits.
- Sections that should be deleted or moved.


## 5. Claude Fable 5 applies the critique. Since Claude authored the first version, let Fable apply the critique and keep the tone consistent.
Apply this critique to the vendor-agnostic agent harness docs.

Return final full contents for:
- AGENTS.md
- docs/agents/*

Requirements:
- Preserve vendor neutrality.
- Keep AGENTS.md concise.
- Avoid duplication.
- Mark unverified repo facts as TODO.
- Prefer commands and file paths.
- Preserve project-specific legacy-app safety rules.
- Do not invent facts.


## 6. GPT-5.5 Thinking does the final consistency pass. This is a final polish.
Perform a final consistency pass on these vendor-agnostic agent harness docs.

Do not change the architecture unless there is a serious issue.

Fix:
- Inconsistent terminology.
- Duplicate rules.
- Overly wordy sections.
- Missing cross-links.
- Missing TODO markers.
- Ambiguous validation language.
- Any remaining vendor-specific wording.

Return:
1. Final patch-style edits only.
2. A short migration report.
3. A final validation checklist.
4. Remaining human-verification TODOs.
