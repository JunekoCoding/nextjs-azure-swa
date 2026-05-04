# Next.js + Azure Static Web Apps (CI/CD Lab)

This repo is a small lab/demo showing how to deploy a Next.js (App Router) site to **Azure Static Web Apps** using **GitHub Actions**.

- The web app code lives in `my-app/` (Next.js 15 + React 19 + Tailwind).
- CI/CD is in `.github/workflows/azure-static-web-apps-*.yml` and runs on every push to `main`.

## Run locally

Prereqs:
- Node.js LTS (recommended)

```bash
cd my-app
npm ci
npm run dev
```

Open http://localhost:3000

Optional (production build):

```bash
npm run build
npm run start
```

## Deploy to Azure Static Web Apps (portfolio)

### Option A (recommended): connect the repo from Azure

1. Create an **Azure Static Web Apps** resource in the Azure Portal.
2. During creation, connect it to your GitHub repo and choose the `main` branch.
3. Set **App location** to `my-app`.
4. Azure will configure a deployment token in your GitHub repo secrets.

### Option B: use the existing workflow + add the secret yourself

The workflow expects a GitHub Actions secret named:
- `AZURE_STATIC_WEB_APPS_API_TOKEN`

Steps:
1. In Azure Portal → your Static Web App → **Deployment token** → copy the token.
2. In GitHub → your repo → **Settings → Secrets and variables → Actions** → create a new secret:
   - Name: `AZURE_STATIC_WEB_APPS_API_TOKEN`
   - Value: (paste the deployment token)
3. Push to `main` and the GitHub Action will build + deploy.

## What to change to make it “yours”

Edit the landing page here:
- `my-app/app/page.tsx`

