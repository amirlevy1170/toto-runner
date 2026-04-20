# toto-runner

Lightweight public repo that runs the TotoGenerator forms pipeline daily via GitHub Actions (free tier).

The actual code lives in the private `orgreens21/TotoGenerator` repo — this repo just triggers the workflow.

## Setup

1. Create a GitHub PAT with `repo` scope that can access `orgreens21/TotoGenerator`
2. Add these secrets to this repo (Settings → Secrets → Actions):
   - `TOTO_PAT` — the PAT from step 1
   - `API_SPORTS_KEY` — API-Football key
   - `TABPFN_TOKEN` — TabPFN token

## How it works

Every day at 10AM Israel time (7AM UTC), the workflow:
1. Clones the private TotoGenerator repo
2. Installs dependencies
3. Runs the forms walk-forward pipeline
4. Pushes updated DB and predictions back to the private repo
