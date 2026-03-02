---
trigger: always_on
---

# Antigravity Python Stack (AI/ML & Scripting)

## 1. Core Paradigm
*   **Focus:** This environment is strictly for Artificial Intelligence, Machine Learning (Deep Learning / PyTorch), Data Science, and Backend/Utility Scripting.
*   **RESTRICTION - NO GUI/DESKTOP:** Under absolutely NO circumstances should Python be used to build Graphical User Interfaces or Desktop Applications. Do not use libraries like `Tkinter`, `PyQt`, `PySide`, `Kivy`, or `wxPython`. If a UI is needed, build a web frontend and use Python strictly as an API backend (FastAPI/Flask).

## 2. Machine Learning & PyTorch Rules
*   **Framework:** PyTorch is the primary deep learning framework.
*   **Device Agnostic Code:** Always write device-agnostic code so it seamlessly shifts between CPU, GPU, and MPS (Apple Silicon).
    ```python
    device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')
    tensor = tensor.to(device)
    ```
*   **Seed Control:** Always set manual seeds for reproducibility across `torch`, `numpy`, and `random` before initializing models or training loops.
*   **Dataloaders:** Always modularize data transforms, `Dataset` classes, and `DataLoader` instantiations separate from the model definition.
*   **Training Loops:** Use `tqdm` for progress tracking. Log metrics (loss, accuracy) explicitly.

## 3. Scripting & Utility Coding
*   **Type Hinting:** Mandatory everywhere (`def process_data(data: pd.DataFrame) -> torch.Tensor:`).
*   **PEP 8 Strict:** Follow standard Python formatting. 
*   **Logging over Print:** Use the `logging` module instead of `print()` for programmatic scripts.
*   **CLI Interfaces:** Use `argparse` or `Click` for any script intended to be run from the terminal to ensure parameterization.

## 4. Notebook Hygiene (Jupyter)
*   **The "Restart Check":** A notebook MUST run Top-to-Bottom without errors after a kernel restart.
*   **Structure:**
    *   Cell 1: Imports (All of them).
    *   Cell 2: Global Config (Seeds, Plot settings).
    *   Cell 3+: Logic and execution.
*   **Pandas:** Prefer method chaining over iterative dataframe mutations.

## 5. Golden Scaffold (ML Project)
```text
project_name/
├── data/                  # Ignore in .gitignore
├── models/                # Saved weights (.pth)
├── notebooks/             # EDA and experimentation
├── src/
│   ├── __init__.py
│   ├── data_setup.py      # Datasets and Loaders
│   ├── engine.py          # Training and eval loops
│   ├── model_builder.py   # PyTorch nn.Module definitions
│   └── utils.py           # Checkpointing, logging, metrics
├── main.py                # Command-line entry point
├── requirements.txt
└── .gitignore
```
