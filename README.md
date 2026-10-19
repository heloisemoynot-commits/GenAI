# Trustworthy Generative AI — ESILV, Next-Generation AI module (A4, Data & AI)

Shared repository of **sub-group `<SUB-GROUP NAME>`** for TD 1, TD 2 and TD 3.

## Sub-group and members

| Member | GitHub handle | Role in TD 1 (filled in during the session) |
| ------ | ------------- | ------------------------------------------- |
| `<Name 1>` | `@<handle>` | |
| `<Name 2>` | `@<handle>` | |
| `<Name 3>` | `@<handle>` | |
| `<Name 4>` | `@<handle>` | |
| `<Name 5>` | `@<handle>` | |
| `<Name 6>` | `@<handle>` | |
| `<Name 7>` | `@<handle>` | |
| `<Name 8>` | `@<handle>` | |

## Course pack and data

- Course site: https://storage.googleapis.com/docs.g.quanticfactory.io/ESILV/next-generation-ai/latest/index.html
- Pack version: **2026-10-14-students-1** (14 October 2026), student kit `esilv-student-2026-10-14.zip`, folder `kit-td1`
- `modeles-autorises.json` dated 2026-10-14
- Database `data/boutique.sqlite`, SHA-256
  `0077e235adc2ca647b484e3083c98a6d7cae3ef3655ce366a299caf13398fec2`
  (seed 20260925, identical to `data/manifest.json`; 5 products, 59 customers, 397 order lines). The database is never modified.

## Required models (TD 1 panel)

| Provider | Exact identifier |
| -------- | ---------------- |
| Groq (Free) | `openai/gpt-oss-120b` |
| Groq (Free) | `openai/gpt-oss-20b` |
| Groq (Free) | `qwen/qwen3.8-27b` |
| OpenRouter | `cohere/north-mini-code:free` |
| OpenRouter | `dots-studio/dots-3-note-preview:free` |

Zero-spend constraint: Groq Free plan, OpenRouter without purchased credits, `:free` routes only.

## Environment

Tested on Windows 11, PowerShell, Python 3.14.8, SQLite 3.50.4, `requests` 2.34.2.
Any Python ≥ 3.10 with `requests` works; everything else uses the standard library.

API keys live **only** in environment variables (`GROQ_API_KEY`, `OPENROUTER_API_KEY`) on each member's machine. They are never written to a file in this repository.

## Reproduce

```powershell
# Windows PowerShell, from the repository root
python -m venv .venv
.venv\Scripts\python.exe -m pip install requests
.venv\Scripts\python.exe verify-data.py              # last object must show "ok": true

$env:GROQ_API_KEY = "<your key>"
$env:OPENROUTER_API_KEY = "<your key>"
.venv\Scripts\python.exe check_access.py | Tee-Object ready-for-td1.txt
```

```bash
# macOS / Linux
python3 -m venv .venv && source .venv/bin/activate
python3 -m pip install requests
python3 verify-data.py
export GROQ_API_KEY="<your key>" OPENROUTER_API_KEY="<your key>"
python3 check_access.py | tee ready-for-td1.txt
```

TD 1 runs (commands, `--models`, `--cases`, `--state`, `--out` files) are documented in `reports/td1.md` as they are executed.

## Status

### Preparation (before 21 October 2026)

- [x] Kit extracted, `verify-data.py` → `ok: true`
- [x] `check_access.py` → **5/5 models OK** on 19 October 2026 (output in `ready-for-td1.txt`)
- [ ] All members have run their own access check

### TD 1 (21 October 2026)

| Deliverable | Status |
| ----------- | ------ |
| `reference-td1.csv` (C01–C20, SQL, `revenue_cents`, checker) | to do |
| `traces-td1.jsonl`, `traces-td1.csv` | to do |
| `five-model-summary-en.csv` | to do |
| `model-question-comparison-en.csv` | to do |
| `prompts-en.md` | to do |
| `reports/td1.md` | to do |

### Open blocks

None at the moment.

## AI assistance

AI-assisted work is declared. Prompts used for the experiment are in `prompts-en.md`; prompts used for coding or writing help are kept in `prompts-ai-assistance.md` as they were used.
