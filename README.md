# pricewatch-data

  Private data and hourly schedule for [pricewatch](https://github.com/jkhaynes/pricewatch).

  ## What's where

  | Where | What | Who writes it |
  |---|---|---|
  | `main` | `export.csv`, `expansions.csv`, `.github/workflows/pricewatch.yml` | you |
  | `db` | `pricewatch.db`, the price history | the workflow, every hour |

  ## Rules

  - **Never merge `db`.** The workflow overwrites it with a single commit every hour. Ignore
    GitHub's "Compare & pull request" banner for it.
  - **Keep `main` as the default branch.** Scheduled workflows only run from the default branch.
  - **Don't run `pricewatch run` locally.** The copy on `db` is the source of truth, and a local
    run would spend the same daily API budget.
  - The `POKEWALLET_API_KEY` secret lives in Settings → Secrets and variables → Actions.

  ## Common tasks

  - **New collection export:** replace `export.csv`, commit to `main`, then Actions →
    pricewatch → Run workflow → `import`.
  - **Look at the data:** download `pricewatch.db` from the `db` branch and open it in any
    SQLite viewer.
  - **Run now instead of waiting:** Actions → pricewatch → Run workflow → `run`.