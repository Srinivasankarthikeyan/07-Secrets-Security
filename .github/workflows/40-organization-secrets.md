# 40 - Organization Secrets

Organization secrets allow you to share secrets across multiple repositories within an organization.

## Key Features
- **Centralized Management:** Manage secrets in one place instead of repeating them in every repo.
- **Access Policies:** You can restrict organization secrets to specific repositories (Selected repositories) or allow all repositories to use them.

## Setup Steps
1. Navigate to Organization **Settings > Actions > Secrets and variables > Actions**.
2. Click **New organization secret**.
3. Give it a name, value, and set **Repository access**.

## Usage in YAML
Usage is identical to repository secrets:
```yaml
steps:
  - run: echo "Org Secret: ${{ secrets.ORG_LEVEL_SECRET }}"
```

## Exam Tips
- Organization secrets are NOT available to public repositories if the secret's visibility is set to "Private".
- If a repository secret and an organization secret have the same name, the repository secret takes precedence.
