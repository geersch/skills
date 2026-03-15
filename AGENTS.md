This file provides guidance to AI coding agents like Claude Code, OpenCode, and other AI coding assistants when working in this repository.

## What this repository is

A skills library for AI-assisted development. Content lives under `skills/` as Markdown skill definitions and reference documents, not a typical application codebase.

## Structure

Each skill is a self-contained directory under `skills/<skill-name>/`:

- `SKILL.md`: entrypoint for the skill (metadata, when-to-use, instructions, links)
- `references/*.md`: detailed reference documents referenced from `SKILL.md`

Current top-level skills:

- `node`
- `vitest`

## Editing rules

1. Treat `skills/*/SKILL.md` as an index contract.
   - Every `references/*.md` file must be explicitly mentioned and linked from that skill's main `SKILL.md`.
   - If you add/rename/remove any `references/*.md`, update the corresponding links in `SKILL.md` in the same change.

2. Preserve skill metadata/frontmatter format.
   - Skill and reference docs use YAML frontmatter (`name`, `description`, `metadata.tags`).

3. Keep naming consistent with existing directory structure.
   - Add new guidance under an existing skill's `references/` unless you are intentionally creating a new skill.
