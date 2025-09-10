---
Created: 2025-06-23T20:22
---
## What Is CI/CD?

|   |   |   |
|---|---|---|
|Term|Stands For|Purpose|
|**CI**|Continuous Integration|Automatically test and integrate code changes|
|**CD**|Continuous Delivery/Deployment|Automatically deliver or deploy code to production|

  

## CI/CD Pipeline Overview

A CI/CD pipeline is an **automated workflow** that takes code from commit to production, including:

```CSS
[ Commit Code ] ➡ [ Test ] ➡ [ Build ] ➡ [ Deploy ]
```

  

## Common Stages in a CI/CD Pipeline

|   |   |   |
|---|---|---|
|Stage|What It Does|Example Tool / Step|
|**Checkout**|Pull latest code from version control (e.g. Git)|`git checkout`|
|**Install**|Install dependencies|`npm install`, `pip install`|
|**Test**|Run automated tests (unit, integration, etc.)|`npm test`, `pytest`, `jest`|
|**Build**|Compile/minify/transpile code|`npm run build`, `webpack`|
|**Lint**|Enforce code style and quality|`eslint`, `prettier`|
|**Deploy**|Send code to staging/production|SSH, Docker, Cloud Deploy|
|**Notify**|Report success/failure to devs|Slack, Email, GitHub Status Checks|

  

## Continuous Integration (CI)

- **Goal:** Detect bugs early by integrating and testing code **frequently**.
- Run on **every push** or pull request.
- Validates that your app is still working.

  

## Continuous Delivery vs Deployment

|   |   |
|---|---|
|Term|What It Means|
|**Continuous Delivery**|Code is **ready for manual release** anytime|
|**Continuous Deployment**|Code is **automatically released** to users|

  

## Popular CI/CD Tools

|   |   |   |
|---|---|---|
|Tool|Type|Notes|
|**GitHub Actions**|Cloud CI/CD|Built into GitHub, uses YAML workflows|
|**GitLab CI/CD**|Cloud/on-prem|Strong Docker & Kubernetes integration|
|**CircleCI**|Cloud CI/CD|Fast builds, config-as-code|
|**Jenkins**|Self-hosted|Highly customizable|
|**Travis CI**|Cloud CI/CD|Simple YAML config|
|**Vercel/Netlify**|CI + hosting|Auto-deploys static sites|
|**Bitbucket Pipelines**|Cloud CI/CD|Integrated with Bitbucket repos|

  

## Sample: GitHub Actions CI Workflow

```YAML
name: CI

on:
  push:
    branches: [ main ]

jobs:
  build-and-test:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 18

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test
```

  

## Best Practices

- ✅ Run tests on **every PR and push**
- ✅ Separate **test**, **build**, and **deploy** steps
- ✅ Use **secrets/environment variables** (never hardcode credentials)
- ✅ Add **status badges** to your README
- ✅ Use **staging environments** before production deployment
- ✅ Rollback or monitor production after deploys