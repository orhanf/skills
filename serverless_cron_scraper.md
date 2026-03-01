---
description: How to set up a serverless cron scraper using GitHub Actions that commits data back to the repository
---

This workflow is useful when building automated daily data pipelines (like scraped newsletters, bots, or aggregators) using a completely free, serverless architecture via GitHub Actions.

### 1. Set up the Python Environment
Create a Python script that will act as the data processor.

// turbo
1. Create a `backend/` directory.
2. Inside, create a `requirements.txt` listing your dependencies.
3. Create a `main.py` that fetches data, processes it (e.g., using Gemini API), and saves the final output as a JSON file (e.g., to `frontend/data.json`).

### 2. Create the GitHub Action Workflow
We will use GitHub Actions to run the script on a schedule (cron) and commit the results.

// turbo
4. Create the directory `.github/workflows/` if it does not exist.
5. Create a `.github/workflows/daily-run.yml` file.
6. Populate it with the following template:

```yaml
name: Daily Serverless Scraper

on:
  schedule:
    - cron: '0 3 * * *' # Runs every day at 3:00 AM UTC
  workflow_dispatch: # Allows manual triggering from the GitHub UI

permissions:
  contents: write

jobs:
  run-pipeline:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.11'
          cache: 'pip'

      - name: Install dependencies
        run: pip install -r backend/requirements.txt

      - name: Run Extraction Script
        env:
          # Map GitHub Secrets to environment variables if your script needs them
          # API_KEY: ${{ secrets.API_KEY }}
        run: python backend/main.py

      - name: Commit and Push Data
        run: |
          git config --global user.name "github-actions[bot]"
          git config --global user.email "github-actions[bot]@users.noreply.github.com"
          
          # Add the generated data/JSON files here
          git add frontend/data.json
          
          git commit -m "Automated update: new data [skip ci]" || echo "No changes to commit"
          git push
```

### 3. Setup Secrets
If the Python script requires external API keys:
7. Instruct the user to go to their GitHub repository **Settings -> Secrets and variables -> Actions**.
8. Add the required repository secrets (e.g., `API_KEY`).

### 4. Hosting the Frontend (Optional)
If this scraper powers a frontend application (like a static Web App or PWA), pushing the updated `data.json` to the `main` branch will automatically trigger deployments if you use platforms linked to your repository.
9. Recommend linking the repository to Vercel or Netlify for free private-repository static hosting, pointing the "Root Directory" to the `frontend/` directory.
