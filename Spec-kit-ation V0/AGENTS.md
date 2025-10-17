# Repository Guidelines

## Project Structure & Module Organization
This repository documents the Spec-kit-ation pipeline through agent-specific folders. The root `README.md` gives the high-level workflow. Each directory such as `Agent Plan/`, `Agent Spécification/`, or `Agent Tâche/` contains three core assets: `Prompt Agent.md` describing the role, `prompt demande *.md` detailing the interrogation checklist, and `README.md` with usage notes. Some agents (Plan, Spécification, Tâche, Constitution) also provide `template *.md` files that define the deliverable format; reuse those when onboarding new variants. When adding a fresh agent, mirror this structure and keep filenames descriptive (e.g. `template analyse.md`) so cross-links stay predictable.

## Build, Test, and Development Commands
No compilation step is required, but keep documentation consistent. Useful commands:
- `rg 'TODO'` — quick scan for outstanding placeholders before publishing.
- `npx markdownlint "**/*.md"` — optional lint to enforce Markdown structure across agent files.

## Coding Style & Naming Conventions
Author content in Markdown with a single `#` title per document and sentence-case section headings. Bullet lists should capture decision grids; prefer short explanatory sentences over long paragraphs. Maintain accented directory names (`Agent Spécification/`, `Agent Tâche/`) exactly to avoid broken links. Within templates, keep identifier blocks (version, statut) aligned with two-space indentation for nested lists, and reference other artefacts using relative paths.

## Testing Guidelines
Before committing, lint with `npx markdownlint` and skim rendered output to verify anchor links, especially between agent prompts and templates. When updating a template, open the corresponding agent README to confirm examples still match the expected schema. Note manual checks in the PR description if the change spans multiple agents.

## Commit & Pull Request Guidelines
The history uses short, French commit messages (`Premier commit`). Follow that tone: capitalise the first word, write in the imperative or past-participle form (e.g. `Met à jour template plan`). Group related edits per agent and include the agent name in the subject when helpful. Pull requests should summarise affected artefacts, link to any upstream issue or prompt change, and attach screenshots or exports if the rendered layout shifts.

## Agent Workflow Tips
Update prompts and templates in tandem: when a checklist question changes, reflect the same nuance in the template’s validation section. Keep version headers (v1.0, date) current so downstream implementers know which document to consume. When introducing a new workflow step, stage it first in `Agent Analyse/` to validate coherence before propagating to other folders.
