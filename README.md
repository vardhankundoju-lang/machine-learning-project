# PCB Defect Patch Classification

An end-to-end notebook for classifying six types of PCB defects from image patches. It crops defect regions from YOLO bounding-box labels, compares classical machine-learning models, tunes a Random Forest classifier, and evaluates it on a held-out test split.

The notebook reports **93.79% test accuracy** and a **93.76% macro F1 score** for its tuned Random Forest model.

## Project contents

- `ml project 8 - patch classification.ipynb` — data preparation, visualizations, model comparison, tuning, and evaluation.
- `requirements.txt` — Python packages used by the notebook.
- `pcb-defect-dataset/` — expected local input data; not included in this repository.
- `pcb-defect-patches/` — generated crops and metadata; created by the notebook and not included in this repository.

## Setup

Use Python 3.10 or newer. From the project directory, create and activate a virtual environment, then install the dependencies:

```powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

On macOS or Linux, use `python3 -m venv .venv` and `source .venv/bin/activate` instead.

## Data

The source dataset is not stored in this repository. Obtain it separately and place it in `pcb-defect-dataset/` with this layout:

```text
pcb-defect-dataset/
  train/
    images/
    labels/
  val/
    images/
    labels/
  test/
    images/
    labels/
```

Labels must use YOLO format, with one bounding box per line: class ID, normalized center coordinates, width, and height. The notebook expects the class IDs in this order: `mouse_bite`, `spur`, `missing_hole`, `short`, `open_circuit`, `spurious_copper`.

Check the source dataset's license and usage terms before obtaining or redistributing it. The notebook creates the `pcb-defect-patches/` directory and its metadata when run.

## Run

Start Jupyter from the project directory so the relative dataset paths resolve:

```powershell
jupyter notebook "ml project 8 - patch classification.ipynb"
```
