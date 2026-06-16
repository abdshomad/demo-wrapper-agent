# Demo Wrapper Agent

This repository contains the `demo-wrapper-agent` workspace. It is structured to work with external dependencies via Git submodules.

## AI Agent Guidelines & Repository Rules

To ensure smooth and reliable development, all AI agents operating in this workspace must strictly follow the repository rules.

> [!IMPORTANT]
> **NEVER edit, update, delete, or commit changes to files inside Git submodules.**

### Key Rules:
1. **Parent Repository Only**: All agent code modifications, edits, and additions must be performed directly in the parent repository. Do not make changes to files within submodule directories.
2. **Upstream Submodule Updates**: If a submodule needs to be updated, it must be updated upstream, or the tracked commit reference in the parent repository must be updated using official Git submodule commands.
3. **Read the Full Guidelines**: Refer to the detailed guidelines inside [AGENTS.md](AGENTS.md) before performing any tasks or commits.

---

For any questions or clarification, please contact the repository administrator.