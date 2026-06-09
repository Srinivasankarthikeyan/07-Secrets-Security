# 44 - Fine-Grained Permissions

Beyond the `permissions` block in YAML, GitHub offers fine-grained control at the repository level.

## Default Workflow Permissions
Found in **Settings > Actions > General**:
- **Read and write permissions:** GITHUB_TOKEN has broad access by default (not recommended for security).
- **Read repository contents and packages permissions:** GITHUB_TOKEN only has read access. This is the more secure default.

## Fine-grained Personal Access Tokens (PATs)
Unlike classic PATs, fine-grained PATs:
- Are scoped to specific repositories.
- Have expiration dates.
- Have specific permissions (e.g., only `metadata:read` and `issues:write`).

## Exam Tips
- Always prefer the built-in `GITHUB_TOKEN` over a PAT when possible.
- If you must use a PAT, use a Fine-grained PAT.
- The `permissions` key in YAML overrides the default settings in the UI for that specific workflow.
