# Demo Wrapper Agent — Guidelines

## Crucial Rule: Do Not Edit Git Submodules

To preserve the integrity of the repository's dependency model, all AI agents operating in this workspace must adhere to the following rule:

> [!IMPORTANT]
> **NEVER edit, update, delete, or commit changes to files inside the Git submodules.**

### Reasons
1. **Upstream Alignment**: Submodules are independent repositories maintained separately. Directly editing files within them diverges from upstream sources.
2. **Detached HEAD & Versioning**: Modifying files inside submodules can lead to detached HEAD states and make dependency version management complex and error-prone.
3. **Clean Commits**: Project modifications should strictly focus on the parent repository. Any changes to submodules must be done by modifying the submodule upstream or updating the tracked commit reference in the parent repository.

## Agent Workflow

This workspace uses two submodule instruction sets. **Read and follow both before performing any task:**

| Role | File | Purpose |
|------|------|---------|
| Orchestrator | [`next-methods/AGENTS.md`](next-methods/AGENTS.md) | NEXT-Method: method pick, state machine, `n`/`e` ticks, AFK (`/goal`, `/loop`, `/schedule`) |
| Task engine | [`autonomous-coding-agents/AGENTS.md`](autonomous-coding-agents/AGENTS.md) | Enhancement queue (`plans/next-enhancements.md`), `n`/`e` rules, feature docs, mock/live mode |

**Path resolution:** When [`next-methods/AGENTS.md`](next-methods/AGENTS.md) references `autonomous-coding-agents/AGENTS.md`, use the root-level submodule at [`autonomous-coding-agents/AGENTS.md`](autonomous-coding-agents/AGENTS.md) in this workspace.

**Engines (always on):** [`autonomous-coding-agents/AGENTS.md`](autonomous-coding-agents/AGENTS.md) drives `n`/`e`; planning submodules under `next-methods/` (BMAD, Spec Kit, OpenSpec, design.md, Pocock, Karpathy) are invoked per the method chosen in [`next-methods/AGENTS.md`](next-methods/AGENTS.md).

All project artifacts (`plans/`, `docs/`, `_bmad-output/`, etc.) live at **this repo root**, not inside submodule directories.

## Repository Configuration & Management

- **Docker Compose**: Provide a `docker-compose.yml` to run the application.
- **Port Management**: Store the port info in a `.env` file (e.g., `PORT=3000`).
- **Management Scripts**: Implement `install.sh`, `start.sh`, `stop.sh`, `restart.sh`, and `monitor.sh` (as one-liners where possible) for stack management. All application processes and scripts must run in the background. The scripts should adapt to Linux, Windows, and macOS environments.

## Screen & Navigation Guidelines

When building UI screens:

1. **Keep screens simple**: Each screen should do one thing well. Prefer the smallest useful layout and the fewest controls needed for that function.
2. **Split complexity across screens**: When a screen grows complex, add another screen instead of cramming more into one view.
3. **Organize by module and function**: Use menus, sub-menus, and tabs that mirror the module/function structure (e.g. module → function → action).
4. **One feature, one navigation entry**: Every feature gets its own menu or sub-menu item so users can reach it directly without hunting through unrelated screens.

## E2E Testing & Screenshot Guidelines

When intentionally testing features:
1. Use browser tools to execute end-to-end (E2E) verification of all features.
2. Save results and screenshots in the `/screenshots/` directory.
3. Organize output using a numbered directory and filename hierarchy:
   - Structure: `screenshots/<module_number>_<module_name>/<function_number>_<function_name>/<step_number>_<before|after>_<action_name>.png`

## Issue Tracking & Blockers

- **Blocking Issues**: Record all blocking issues in the `/issues/` folder with numbered filenames.

## User Guide Development Guidelines

When creating, modifying, or extending the user guide or presentation slides:

### File layout

All guide content lives under the repo root `user-guides/` folder using this nested path pattern:

```
user-guides/{NN}-{module-name}/{NN}-{feature-name}/
```

- `{NN}` = two-digit number (e.g. `01`, `02`)
- One feature folder per guide screen; place guide files (e.g. `index.tsx`) inside the feature folder

Example: `user-guides/02-executive-command-center/01-decision-scenario-simulator/index.tsx`

### Scope

All user-guides files belong in the **parent repo root**, never inside git submodule directories. See **Do Not Edit Git Submodules** above. Import shared code via project path aliases (e.g. `@/…`), not deep relative paths into submodule trees.

### Welcome / feature catalog

The intro screen (`user-guides/01-welcome/00-general-overview/index.tsx`) must include a searchable feature catalog sourced from `docs/feature-list.md`. Each catalog entry should document:

1. **Task ID** — e.g. `Task 8.2`
2. **Implementation** — technical details under the hood (APIs, models, regex patterns, etc.)
3. **Compliance** — applicable regulations or standards, when relevant
4. **Impact** — business or performance outcomes

### Content and interaction

1. **Callouts**: Prevent text and hotspot callouts from overlapping; fill them with realistic sample data. Match existing typography guidelines.
2. **Interactivity**: Prefer interactive simulations, canvas or SVG animations, or dynamic charts (e.g. `framer-motion`, `recharts`) over static text or mockups when demonstrating feature behavior.
3. **Playback**: Support autoplay with an 8-second advance timer between steps.
4. **Keyboard navigation**:

| Key | Action |
|-----|--------|
| `ArrowRight`, `ArrowDown`, `Space` | Next step |
| `ArrowLeft`, `ArrowUp` | Previous step |
| `PageDown` | Next module |
| `PageUp` | Previous module |
| `Escape` | Exit guide |

## Begin

Follow [`next-methods/AGENTS.md`](next-methods/AGENTS.md) § Begin: ask for the project idea, recommend a method, show the menu, and wait.
