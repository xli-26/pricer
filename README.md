# Pricer

Estimating retail prices from product descriptions, comparing frontier LLMs against Jev, a System One decision model from TypeSafe.

The work happens in `lab.ipynb`. The `pricer` package holds the dataset loading, preprocessing and the evaluation harness.

## Setup

1. Install [uv](https://docs.astral.sh/uv/getting-started/installation/) if you don't have it:

   ```bash
   curl -LsSf https://astral.sh/uv/install.sh | sh
   ```

2. Install dependencies (this also creates the virtual environment and installs Python 3.12):

   ```bash
   uv sync
   ```

3. Create a `.env` file in the project root:

   ```
   OPENROUTER_API_KEY=...
   HF_TOKEN=...
   ```

   `OPENROUTER_API_KEY` reaches Jev through OpenRouter's Decisions API, and `HF_TOKEN` loads the dataset from Hugging Face.

4. Open `lab.ipynb`, select the `.venv` kernel, and run the cells from the top.

## Notes

Predictors passed to `evaluate` take an `Item` and return `(estimate, inference_cost)`. The harness scores 200 items by default, and reports average error, cost per call and latency.
