# miRNA-target-pairs

Prediction of miRNA–target-site binding pairs on the Hejret 2023 dataset
(miRBench `AGO2_CLASH_Hejret2023`, [Zenodo 20540907](https://zenodo.org/records/20540907)).
Group project for ML Course 2026 (Exercise 10), by two students.

Starting point: the course example (2D CNN),
[exercise_10.ipynb](https://github.com/palexiou/ML_Course_2026/blob/main/exercise_10.ipynb).
Our goal is to compare **different representations and models** (Random Forest / XGBoost, 1D CNN, 2D CNN variants)
with one shared evaluation system.

## Data
- Inputs: `noncodingRNA` (miRNA), `gene` (50-nt target site). Label: `label` (1 = observed pair, 0 = synthetic negative).
- **Never use other columns (especially `Nunique`) – it leaks the label.**
- 20% of the official training file (stratified by label, seed 42) is the validation set.
- The official test file is used **once**, at the very end.

## Repository layout
```
src/         python scripts (data loading, models, evaluation)
notebooks/   short notebooks for exploration / result plots
results/     predictions + answers CSVs and metrics per model
data/        downloaded data (not committed)
docs/        report material
NOTES.md     decision / experiment log (both members write here)
WORKFLOW.md  how we collaborate with git
REPORT.md    final report (written at the end)
```

## Prediction / answer file format (shared by all models)
- `results/<model>/validation_predictions.csv`: `sample_id,probability`
- `results/<model>/validation_answers.csv`: `sample_id,label`
- same for `test_*`. `sample_id` = `train_<row>` / `test_<row>` (original file row).

## Reproduce
```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
# commands for training / evaluation will be added here as scripts are written
```

## Team
| Member | GitHub | Main responsibility |
|---|---|---|
| Vasilis Karouanas | @vasiliskarouanas | TBD |
| (classmate) | TBD | TBD |
