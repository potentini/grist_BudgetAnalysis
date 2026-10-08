# Repository Guidelines

## Project Structure

The Grist custom widget is the standalone page `src/grist-widget.html`. `README.md` documents its Anthony2 source columns and Grist setup. No separate tests, assets, or build configuration exist yet. Keep future application code under `src/`, tests under `tests/` or beside their modules, and static files under `assets/`; update this section when the layout changes.

## Build, Test, and Development

No build, test, or local-run commands are configured yet. Do not assume a framework or package manager. When adding one, document the canonical setup and verification commands in the project README and keep dependency declarations and lockfiles together. Before proposing a command, confirm it is defined by the repository's manifest or scripts.

## Coding Style and Naming

Follow the conventions of the language and framework introduced by the project, and use its formatter and linter when configured. Prefer clear, descriptive names; use `PascalCase` for types, `camelCase` for functions and variables, and `kebab-case` for filenames unless the selected ecosystem specifies otherwise. Keep changes focused and avoid adding dependencies without a clear need.

## Testing

There is no test framework or coverage threshold yet. Add tests with new behavior and place them in the project's established test location once one exists. Use names that describe the behavior under test, such as `test_budget_totals`, and document the command that runs the suite. Do not report tests as passing unless they were run.

## Commits and Pull Requests

No Git history is available to establish an existing commit convention. Use short, imperative commit subjects (for example, `Add budget import`) until the project adopts a documented format. Pull requests should explain the user-facing change, summarize implementation choices, list verification performed, and link any related issue. Include screenshots for visual changes.

## Configuration and Sensitive Data

Keep credentials and private financial data out of source control. Put local-only settings in an ignored environment file, provide a safe example file when configuration becomes necessary, and never commit real secrets or customer data.
