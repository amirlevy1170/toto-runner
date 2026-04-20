# toto-runner

Lightweight public repo that runs TotoGenerator pipelines daily via GitHub Actions (free tier).

The actual code lives in the private `orgreens21/TotoGenerator` repo — this repo just hosts the workflows.

## Workflows

| Workflow | Schedule | Description |
|----------|----------|-------------|
| `daily.yml` | 01:00 UTC daily | Main pipeline: fetch data, train models, predict |
| `draw.yml` | After daily completes | Draw predictions pipeline |
| `forms_daily.yml` | 07:00 UTC daily (10AM Israel) | Forms walk-forward validation + predictions |
| `backfill.yml` | Manual only | Backfill historical data |
| `backtest.yml` | Manual only | Walk-forward backtest |

## Setup

Add these secrets (Settings → Secrets → Actions):

| Secret | Required | Description |
|--------|----------|-------------|
| `TOTO_PAT` | ✅ | GitHub PAT with `repo` scope to access TotoGenerator |
| `API_SPORTS_KEY` | ✅ | API-Football key |
| `TABPFN_TOKEN` | ✅ | TabPFN token |
| `EMAIL_SENDER` | ⬜ | Gmail sender for notifications |
| `EMAIL_PASSWORD` | ⬜ | Gmail app password |
| `EMAIL_RECIPIENT` | ⬜ | Notification recipient |
| `GEMINI_API_KEY` | ⬜ | Gemini API key |
| `DASHBOARD_TOKEN` | ⬜ | PAT for toto-dashboard repo sync |
