# Contributing to Bilingual Annotator Toolkit

Thanks for helping improve these Claude Skills. Since this is prompt engineering, not application code, review focuses on instruction precision and predictability — not syntax.

## How to help
1. **Fix prompt leakage / drift** — if Claude ignores the color-dimension preset, breaks the dual-column layout, or drifts from `TRANSLATION_MODE`, propose tighter constraints or clearer negative rules.
2. **Add new document-type presets** — extend `DIM_PRESET` / `DOC_TYPE_FUNCTIONS` in `skills/bilingual-doc-annotator/SKILL.md` for genres not yet covered (e.g. medical reports, financial filings).
3. **CSS/HTML robustness** — improve the embedded stylesheet the skill instructs Claude to generate (cross-browser, dark mode, RTL correctness).

## Pull request process
- Fork, branch from `main`.
- If you edit a `SKILL.md`, include a short before/after example of the generated HTML in your PR description.
- Keep frontmatter (`name`, `description`) valid YAML — this is what Claude Code uses for skill discovery. Don't rename the file away from `SKILL.md` or move it out of its `skills/<name>/` folder.
- No personal API keys, private documents, or real identifiers in examples.

## Structure (do not change without discussion)
```
skills/
  bilingual-doc-annotator/SKILL.md
  study-visual-generator/SKILL.md
```
This exact `skills/<name>/SKILL.md` layout is required for Claude Code's skill auto-discovery. Flat `.md` files at the `skills/` root will not be picked up.
