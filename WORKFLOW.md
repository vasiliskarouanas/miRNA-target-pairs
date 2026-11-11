# Collaboration workflow (2 people)

1. `main` is always working. Nobody pushes directly to `main`.
2. One branch per task: `rf-xgboost`, `cnn-1d`, `evaluator`, `data-loading`, ...
   ```bash
   git checkout main && git pull
   git checkout -b rf-xgboost
   # work, then
   git add <files> && git commit -m "Add random forest baseline on k-mer features"
   git push -u origin rf-xgboost
   ```
3. Open a Pull Request on GitHub. The **other** person reviews and merges (squash or merge commit).
4. Small, meaningful commits with clear messages. Both members commit regularly (this shows each contribution).
5. Every experiment gets an entry in `NOTES.md`: date, who, what changed, validation metrics, conclusion.
6. Fixed seed (42) and the same train/validation split for every model (`src/data.py`).
7. Test set: touched once, together, after the final model is frozen. Never tune on it.
8. Don't commit data or model weights.
