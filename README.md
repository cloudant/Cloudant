# Cloudant

Please use https://github.ibm.com/cloud-docs/Cloudant for contributions.
Pushes to https://github.com/ibm-cloud-docs/Cloudant are only allowed
by members of documentation team.

# Build & CI

## Jenkins


Jenkins is used to publish docs to staging and to production.
The setup is managed by IBM Cloud Documentation team.

https://wcp-ace-docs-jenkins.swg-devops.com/job/Docs-build/job/Docs-build-Cloudant/


## Travis

Travis is used to keep github.com and github.ibm.com repositories in sync.
The setup is managed by Cloudant infra team.

https://travis.ibm.com/Bluemix-Docs

## Documentation

Please use https://github.ibm.com/cloud-docs/Cloudant for contributions to the documentation. Pushes to https://github.com/ibm-cloud-docs/Cloudant are only allowed by members of the documentation team. See [Documentation Update Process](https://github.ibm.com/cloud-docs/Cloudant/wiki/Documentation-Update-Process) for instructions. 

If you are not an IBM employee and want to make a documentation contribution, go to the [IBM Cloudant documentation](https://cloud.ibm.com/docs/services/Cloudant?topic=cloudant-getting-started-with-cloudant#getting-started-with-cloudant) and click `Feedback` on the page where you want to comment. 

# 🔐 Detect Secrets Enforcement

This repository uses [`detect-secrets`](https://github.com/IBM/detect-secrets-stream) to prevent committing sensitive information like API keys, tokens, and passwords.

## 🚀 How It Works

Secrets are tracked using a `.secrets.baseline` file. This file contains a hash of detected secret patterns and is version-controlled.

On every pull request, GitHub Actions will:
- Scan the codebase using the committed baseline.
- Fail the build if new untracked secrets are found.

## 🛠 Update the Baseline

If your PR is failing due to newly detected secrets (false positives or intentional additions), follow the steps below to update the baseline:

### ✅ One-Command Update

Use the provided `Makefile` to automatically install and run `detect-secrets`, then clean up:

```bash
make update-secrets