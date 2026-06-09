# 46 - Secure Cloud Login (OIDC Steps)

OIDC is the preferred way to connect to cloud providers. Here is the conceptual setup for AWS/Azure.

## AWS Setup
1. **Create Identity Provider:** In AWS IAM, create a new OIDC Provider for `https://token.actions.githubusercontent.com`.
2. **Assign Audience:** Use `sts.amazonaws.com`.
3. **Create IAM Role:** Create a role with a trust policy that allows the GitHub OIDC provider to assume it.
4. **Trust Policy Condition:** Restrict the role to your specific repo:
   ```json
   "Condition": {
     "StringLike": {
       "token.actions.githubusercontent.com:sub": "repo:my-org/my-repo:*"
     }
   }
   ```

## Azure Setup
1. **App Registration:** Create an App Registration in Microsoft Entra ID (Azure AD).
2. **Federated Credentials:** Add a federated credential for "GitHub Actions deploying Azure resources".
3. **Selection:** Choose your Organization, Repository, and Branch/Environment.
4. **RBAC:** Assign a role (e.g., Contributor) to the App Registration at the Subscription or Resource Group level.

## Exam Tips
- OIDC eliminates the need to rotate secrets.
- `id-token: write` is the key permission required.
