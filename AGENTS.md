# Repository Guidelines

## Project Structure & Module Organization
- `drawio/`: Draw.io source diagrams (architecture, deployment). Example: `drawio/系統架構圖.drawio`.
- `plantUML/`: UML sources organized by type:
  - `activity/`, `sequence/`, `state/`, `class/`, `component/`, `package/`, `deployment/`, `user_case/`, `system-flow/`, `database/`.
- `wiki/`: Project notes and references.
- Outputs are not committed by default. Prefer exporting to `dist/` locally (add to `.gitignore` if needed).

## Build, Test, and Development Commands
- Render PlantUML (local CLI): `plantuml -tpng plantUML/sequence/*.puml -o dist/sequence`
- Render PlantUML (Docker): `docker run --rm -v "$PWD":/ws -w /ws ghcr.io/plantuml/plantuml -tpng plantUML/state/*.puml -o dist/state`
- Export Draw.io (CLI): `drawio --export --format png --output dist/drawio drawio/*.drawio`
- Export Draw.io (Node): `npx @drawio/cli --export --format pdf --output dist/drawio drawio/系統架構圖.drawio`
Each command writes images to `dist/…`; create folders first (e.g., `mkdir -p dist/sequence`).

## Coding Style & Naming Conventions
- Follow `.editorconfig`: 4-space indent, UTF-8, LF endings.
- File names: use descriptive English where possible; allowed localized names for domain diagrams. Patterns seen: `*_overview.puml`, `*_edit.puml`, `analysis-class-1.puml`.
- Keep one diagram per `.puml`/`.drawio` file; prefer snake_case for scenario names and kebab-case for series (e.g., `design-class-2.puml`).
- Organize by UML type folder; avoid duplicates across folders.

## Testing Guidelines
- All `.puml` must render without errors: `plantuml -checkonly plantUML/**/**/*.puml`.
- Visually review exports before committing source changes. Large layout shifts should be explained in the PR.

## Commit & Pull Request Guidelines
- Use Conventional Commits where practical: `feat:`, `refactor:`, `fix:`, `docs:`. Examples exist in history (e.g., `feat: 更新系統架構圖`).
- Commit message: imperative mood, concise scope, mention folder (e.g., `sequence:`) when helpful.
- PRs: include summary, affected folders, sample exported images or screenshots, and linked issue/Task ID. Keep PRs focused (one domain/topic per PR).

## Security & Configuration Tips
- Do not embed secrets in diagrams. Use placeholders (e.g., `DB_PASSWORD`).
- Prefer generic icons/logos unless licenses allow redistribution. Note third-party references in `wiki/`.
