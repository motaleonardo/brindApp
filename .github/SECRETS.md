# 🔐 GitHub Secrets Setup for BRIND CI/CD

This document lists all the secrets you need to configure in your GitHub repository for the CI/CD pipelines to work.

## How to Add Secrets

1. Go to your GitHub repository
2. Click **Settings** → **Secrets and variables** → **Actions**
3. Click **New repository secret**
4. Add each secret listed below

---

## Required Secrets

### Backend Deployment (Production Server)

| Secret Name           | Description                              | Example                                  |
| --------------------- | ---------------------------------------- | ---------------------------------------- |
| `PROD_SERVER_HOST`    | IP or hostname of your production server | `45.123.456.78`                          |
| `PROD_SERVER_USER`    | SSH username for deployment              | `deploy`                                 |
| `PROD_SERVER_SSH_KEY` | Private SSH key for server access        | `-----BEGIN OPENSSH PRIVATE KEY-----...` |
| `PROD_HEALTH_URL`     | Base URL for health check                | `https://api.brind.app`                  |

### Mobile (Expo EAS)

| Secret Name  | Description                      | How to Get                                                                                 |
| ------------ | -------------------------------- | ------------------------------------------------------------------------------------------ |
| `EXPO_TOKEN` | Expo access token for EAS builds | [expo.dev/accounts/settings](https://expo.dev/accounts/[account]/settings) → Access Tokens |

---

## Optional Secrets (Future Use)

### Code Coverage

| Secret Name     | Description                   |
| --------------- | ----------------------------- |
| `CODECOV_TOKEN` | Token for Codecov integration |

### App Store Deployment

| Secret Name                   | Description                      |
| ----------------------------- | -------------------------------- |
| `APPLE_ID`                    | Apple ID for App Store Connect   |
| `APPLE_APP_SPECIFIC_PASSWORD` | App-specific password            |
| `GOOGLE_SERVICE_ACCOUNT_KEY`  | Google Play service account JSON |

---

## Quick Checklist

- [ ] `PROD_SERVER_HOST`
- [ ] `PROD_SERVER_USER`
- [ ] `PROD_SERVER_SSH_KEY`
- [ ] `PROD_HEALTH_URL`
- [ ] `EXPO_TOKEN`

---

## Generating SSH Keys

```bash
# Generate a new SSH key pair for deployments
ssh-keygen -t ed25519 -C "github-actions-deploy" -f ~/.ssh/brind_deploy

# Display the private key (add this to PROD_SERVER_SSH_KEY)
cat ~/.ssh/brind_deploy

# Display the public key (add this to server's ~/.ssh/authorized_keys)
cat ~/.ssh/brind_deploy.pub
```

> ⚠️ **Security Note**: Never commit secrets to the repository. Always use GitHub Secrets.
