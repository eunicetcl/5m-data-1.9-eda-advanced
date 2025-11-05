## Copilot / AI Agent instructions for this repository

Purpose: Help an AI code assistant be productive quickly in this educational EDA repo (notebooks, small scripts, and sample data).

- Big picture
  - This is a lesson/assignment repository for "EDA Advanced". Primary artifacts:
    - `notebooks/eda_advanced_lesson.ipynb` — the live lesson notebook (code-along).
    - `visualisations/` — example scripts that produce figures and interactive HTMLs (see `correlation_vs_covariance.py`).
    - `data/` — example CSVs (e.g. `tips.csv`) and some notebook cells expect pickled Yahoo data (`../data/yahoo_price.pkl`, `../data/yahoo_volume.pkl`).
  - Typical intent: create/modify notebook cells for lessons and assignment answers, or update small scripts that generate visuals.

- Developer workflow & environment (explicit)
  - Kernel / environment: the lesson uses a conda env named `pds`. Open the notebook in VSCode and select the `pds` kernel before running cells (see `lesson.md`).
  - Notebooks are authoritative for lesson content; prefer edits in `notebooks/eda_advanced_lesson.ipynb` for lesson code. Scripts in `visualisations/` are runnable with `python`.

- Important, discoverable patterns and examples
  - Standard imports: expect `import pandas as pd` and `import numpy as np` in notebooks and scripts (see top of `notebooks/eda_advanced_lesson.ipynb` and `visualisations/correlation_vs_covariance.py`).
  - Data loading in notebooks uses relative paths: e.g. `price = pd.read_pickle("../data/yahoo_price.pkl")` — confirm that required pickle files exist; if missing, fall back to available CSVs such as `data/tips.csv` or mock small DataFrames for examples.
  - Visualisation scripts sometimes save to absolute paths (example: `plt.savefig('/Users/.../visualisations/correlation_vs_covariance.png', ...)`). When changing scripts, prefer repository-relative paths (e.g. `visualisations/output.png`) to keep them portable.

- Code style & project conventions
  - Keep examples concise and reproducible inside notebooks: small, deterministic seeds are used in example scripts (`np.random.seed(42)` in `visualisations/correlation_vs_covariance.py`).
  - When adding runnable Python scripts, ensure they work outside the notebook (guard notebook-only code) and do not rely on interactive kernel state.

- Integration points & external deps
  - No network services are used by default. The main external requirement is Python scientific stack (pandas, numpy, matplotlib, possibly plotly). The lesson explicitly mentions the `pds` conda environment — inspect the environment or ask the maintainer for an environment.yml if you need exact pins.

- Quick actionable checklist for edits
  1. Open `notebooks/eda_advanced_lesson.ipynb` in VSCode, select `pds` kernel, run top cells to confirm imports.
 2. If a notebook cell reads `../data/*.pkl` and files are missing, either add a small synthetic DataFrame for examples or switch to `data/tips.csv` when semantically appropriate.
 3. For scripts in `visualisations/`, run via `python visualisations/<script>.py`; change any absolute save paths to relative paths under `visualisations/` or `visualisations/output/`.

- When to ask the human
  - If you need exact dependency pins (versions) or access to missing pickle files (`yahoo_price.pkl`), ask the repo owner instead of guessing.
  - If you plan large refactors of lesson content, confirm with the course maintainer to avoid breaking planned lesson flow.

If anything in this file is unclear, tell me which section and I will expand with more precise examples or run a quick verification (e.g., run a notebook cell or a script) based on your preference.
