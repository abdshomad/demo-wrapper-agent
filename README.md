# Demo Wrapper Agent

This repository contains the `demo-wrapper-agent` workspace. It is structured to work with external dependencies via Git submodules.

## AI Agent Guidelines & Repository Rules

To ensure smooth and reliable development, all AI agents operating in this workspace must strictly follow the repository rules.

> [!IMPORTANT]
> **NEVER edit, update, delete, or commit changes to files inside Git submodules.**

### Key Rules:
1. **Parent Repository Only**: All agent modifications must be performed in the parent repository. Do not modify files within submodule directories.
2. **Docker & Port Management**: Use `docker-compose.yml` and store the app's `PORT` configuration in `.env`.
3. **Management Scripts**: Implement stack control scripts (`install.sh`, `start.sh`, `stop.sh`, `restart.sh`, and `monitor.sh`) to run all application processes in the background, adapting to Linux, Windows, and macOS.
4. **E2E Testing**: Save E2E test screenshots organized using a numbered module, function, and step hierarchy in the `/screenshots/` folder.
5. **Blocking Issues**: Record blocking issues with numbered filenames in the `/issues/` folder.
6. **Read the Full Guidelines**: Refer to the detailed guidelines inside [AGENTS.md](AGENTS.md) before performing any tasks or commits.

---

For any questions or clarification, please contact the repository administrator.