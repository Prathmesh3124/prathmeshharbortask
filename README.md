# harbor-task-prathmeshbadgujar

Harbor new-hire assignment: a simple **data-processing** task that aggregates JSON invoices into a sorted rollup report.

## Task: `json-invoice-rollup`

The agent must:

1. Read `/app/invoices.json`
2. Keep only invoices with `status == "paid"` and `currency == "USD"`
3. Aggregate customer revenue and SKU totals
4. Write sorted results to `/app/rollup.json`

Difficulty: **easy** · Category: **data-processing**

## Repository layout

```text
harbor_tasks/json-invoice-rollup/
├── task.toml
├── instruction.md
├── environment/
│   ├── Dockerfile
│   └── invoices.json
├── solution/
│   └── solve.sh
└── tests/
    ├── test.sh
    └── test_outputs.py
```

## Prerequisites

- [Docker](https://www.docker.com/products/docker-desktop/)
- [uv](https://docs.astral.sh/uv/)
- Harbor CLI (`uv tool install harbor` or use a Harbor checkout)

## How to run

From this repository root:

```bash
# Oracle (reference solution) — expect Mean 1.000
harbor run --agent oracle --path harbor_tasks/json-invoice-rollup --job-name test-oracle

# NOP (no-op agent) — expect Mean 0.000
harbor run --agent nop --path harbor_tasks/json-invoice-rollup --job-name test-nop

# Lint
uvx ruff check harbor_tasks/json-invoice-rollup
```

## Validation results

### Oracle — reward **1.0**

![Oracle test output showing Mean 1.000](screenshots/oracle.png)

### NOP — reward **0.0**

![NOP test output showing Mean 0.000](screenshots/nop.png)

### Ruff lint — passed

![Ruff lint output showing All checks passed](screenshots/ruff.png)

## Author

Prathmesh Badgujar
