## What I built
- Implemented `get_config`, `upload_raw_to_blob`, `write_to_postgres` in `src/pipeline.py`
- Pinned `azure-storage-blob` and `psycopg2-binary` in `requirements.txt`
- Cache-friendly `Dockerfile`
- Deployed as an Azure Container App Job (Task 4-5)
- Execution-history portal screenshot: `docs/execution_history.png`
- AI usage: `AI_ASSIST.md`

## How to review
- Code: read `src/pipeline.py` (blob upload + Postgres upsert).
- Azure result: see `docs/execution_history.png` (the Container App Job execution history).
- AI usage: `AI_ASSIST.md`.

## How to run
From a clean clone, with your own Azure Blob + Postgres access:

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env      # fill in your own Blob + Postgres connection strings
set -a && source .env && set +a
python -m src.pipeline
```

> Data dependency: this needs your own Blob container and Postgres connection strings. A reviewer without them relies on the committed execution-history screenshot as the canonical evidence.

## What reviewers should see (expected results)
Fill in what your run actually produces:
- Rows written to Postgres: <e.g. ~57k>
- Blob(s) written (name / count): <e.g. one raw JSON blob per run>
- Container App Job status in the screenshot: <e.g. Succeeded>

## Known limitations / out of scope
- <e.g. schedule set to daily; retries not configured>
- Write "none" if everything in the assignment is done and working.

## Extra completed
- [ ] Any bonus / stretch items from the chapter

## Self-check
- [ ] `bash .hyf/test.sh` passes
- [ ] No credentials committed (no connection strings in code, `.env` is gitignored)
- [ ] `docs/execution_history.png` shows a successful job execution
