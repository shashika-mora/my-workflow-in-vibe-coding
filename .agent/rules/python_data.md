# Antigravity Data Science Stack (Python)

## 1. Notebook Hygiene
*   **The "Restart Check":** A notebook MUST run Top-to-Bottom without errors after a kernel restart.
*   **Structure:**
    *   Cell 1: Imports (All of them).
    *   Cell 2: Global Config (Seeds, Plot settings).
    *   Cell 3+: Logic.

## 2. Coding Rules
*   **Style:** PEP 8 strict.
*   **Type Hinting:** Mandatory (`def func(x: int) -> int:`).
*   **Pandas:** Prefer method chaining.
    ```python
    df = (df.dropna(subset=['id']).query('value > 0'))
    ```
*   **Loops:** Use `tqdm` for long operations.

## 3. Golden Scaffold (Python Tool)
```text
project_name/
├── src/
│   ├── __init__.py
│   ├── main.py            # Entry point
│   ├── utils.py           # Helper functions
│   └── core_logic.py      # The heavy lifting
├── tests/
│   └── test_core.py       # Pytest files
├── notebooks/             # Exploration (if applicable)
├── requirements.txt
├── README.md
└── .gitignore
```

## 4. Visualization Aesthetics
*   **Tools:** Seaborn or Plotly.
*   **Theme:**
    ```python
    sns.set_theme(style="whitegrid", context="talk") # Clean and readable
    ```
*   **Despine:** `sns.despine()` to remove top/right borders.
