# Agent Guidelines

## Crucial Rule: Do Not Edit Git Submodules

To preserve the integrity of the repository's dependency model, all AI agents operating in this workspace must adhere to the following rule:

> [!IMPORTANT]
> **NEVER edit, update, delete, or commit changes to files inside the Git submodules.**

### Reasons
1. **Upstream Alignment**: Submodules are independent repositories maintained separately. Directly editing files within them diverges from upstream sources.
2. **Detached HEAD & Versioning**: Modifying files inside submodules can lead to detached HEAD states and make dependency version management complex and error-prone.
3. **Clean Commits**: Project modifications should strictly focus on the parent repository. Any changes to submodules must be done by modifying the submodule upstream or updating the tracked commit reference in the parent repository.
