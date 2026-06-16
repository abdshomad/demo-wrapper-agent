# Agent Guidelines

## Crucial Rule: Do Not Edit Git Submodules

To preserve the integrity of the repository's dependency model, all AI agents operating in this workspace must adhere to the following rule:

> [!IMPORTANT]
> **NEVER edit, update, delete, or commit changes to files inside the Git submodules.**

### Reasons
1. **Upstream Alignment**: Submodules are independent repositories maintained separately. Directly editing files within them diverges from upstream sources.
2. **Detached HEAD & Versioning**: Modifying files inside submodules can lead to detached HEAD states and make dependency version management complex and error-prone.
3. **Clean Commits**: Project modifications should strictly focus on the parent repository. Any changes to submodules must be done by modifying the submodule upstream or updating the tracked commit reference in the parent repository.

## Repository Configuration & Management

- **Docker Compose**: Provide a `docker-compose.yml` to run the application.
- **Port Management**: Store the port info in a `.env` file (e.g., `PORT=3000`).
- **Management Scripts**: Implement `install.sh`, `start.sh`, `stop.sh`, `restart.sh`, and `monitor.sh` (as one-liners where possible) for stack management. All application processes and scripts must run in the background. The scripts should adapt to Linux, Windows, and macOS environments.

## E2E Testing & Screenshot Guidelines

When intentionally testing features:
1. Use browser tools to execute end-to-end (E2E) verification of all features.
2. Save results and screenshots in the `/screenshots/` directory.
3. Organize output using a numbered directory and filename hierarchy:
   - Structure: `screenshots/<module_number>_<module_name>/<function_number>_<function_name>/<step_number>_<before|after>_<action_name>.png`
