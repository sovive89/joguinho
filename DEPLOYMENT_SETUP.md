# Vercel Deployment Setup Guide

This guide will help you deploy **Joguinho** to Vercel with automatic CI/CD via GitHub Actions.

## Prerequisites

- [Vercel Account](https://vercel.com/signup)
- [GitHub Account](https://github.com)
- Access to your Vercel project

## Step 1: Link Repository to Vercel

1. Go to [Vercel Dashboard](https://vercel.com/dashboard)
2. Click **"Add New..."** → **"Project"**
3. Import your GitHub repository `sovive89/joguinho`
4. Click **"Import"**

## Step 2: Set Up GitHub Actions Secrets

Add the following secrets to your GitHub repository:

### Getting Your Vercel Tokens:

1. Visit [Vercel Account Settings](https://vercel.com/account/tokens)
2. Create a new token and copy it

### Adding Secrets to GitHub:

1. Go to your repository → **Settings** → **Secrets and variables** → **Actions**
2. Click **"New repository secret"** and add:

| Secret Name | Value |
|---|---|
| `VERCEL_TOKEN` | Your Vercel API token |
| `VERCEL_ORG_ID` | Your Vercel Organization ID (from Vercel dashboard) |
| `VERCEL_PROJECT_ID` | Your Vercel Project ID (from Vercel dashboard) |

### Finding Your IDs:

- **VERCEL_ORG_ID**: In Vercel Dashboard → Settings → General → ID
- **VERCEL_PROJECT_ID**: In Vercel Dashboard → Project Settings → Project ID

## Step 3: Verify Deployment

1. Push changes to `main` branch
2. Watch the GitHub Actions workflow run (Actions tab)
3. Once deployed, visit your live site at the Vercel URL

## File Descriptions

- **`vercel.json`** - Vercel build and routing configuration
- **`.github/workflows/deploy-vercel.yml`** - Automated deployment workflow
- **`.vercelignore`** - Files to ignore during deployment

## How It Works

- **On Push to `main`**: Automatic production deployment to Vercel
- **On Pull Requests**: Preview deployment (temporary environment)
- **Automatic Rollback**: Failed deployments don't affect production

## Troubleshooting

### Workflow Fails
- Check that all three secrets are correctly set in GitHub
- Verify IDs match your Vercel account

### Site Not Updating
- Check GitHub Actions workflow logs
- Ensure `jogo_main.html` is in repository root

### Firebase Issues
- Firebase credentials are embedded in the HTML
- Ensure your Firebase project is accessible from Vercel's servers

## Next Steps

1. Merge this branch to `main`: `git merge setup/deployment`
2. Push to trigger automatic deployment
3. Monitor at https://github.com/sovive89/joguinho/actions

---

**Questions?** Check [Vercel Docs](https://vercel.com/docs) or [GitHub Actions Docs](https://docs.github.com/en/actions)