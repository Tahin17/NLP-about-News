# CSE440 organized notebook guide

## What changed

The notebook is now organized for speed and repeatability.

### 1. Three preprocessing versions are stored separately
The notebook saves these files automatically:

- `project_cache/preprocessed/train_none.csv`
- `project_cache/preprocessed/train_extreme.csv`
- `project_cache/preprocessed/train_optimum.csv`
- `project_cache/preprocessed/test_none.csv`
- `project_cache/preprocessed/test_extreme.csv`
- `project_cache/preprocessed/test_optimum.csv`

Each file contains:
- `News Headline` = original raw text
- `text` = preprocessed text for that version
- `News Topic` = label

### 2. One fixed validation split is reused everywhere
The notebook creates and saves one duplicate-aware split:
- `project_cache/splits/group_split_seed42_val15.csv`

This keeps every model on the same train/validation rows and avoids leakage from duplicate headlines.

### 3. Expensive artifacts are cached
The notebook also caches:
- TF-IDF vectorizers and sparse matrices
- SVD-reduced dense features for the DNN
- Skip-gram tokenizer, sequences, and embedding matrix
- Model checkpoints and training histories

### 4. Seed and rerun behavior
The notebook uses:
- `SEED = 42`

This gives reproducible splits, initialization, and training order as much as TensorFlow allows.

A seed does **not** remove the need to train a model.  
To avoid rerunning all epochs, the notebook now uses:
- checkpoint saving
- best-weight reloading
- training history logs

## Main control flags

At the top of the notebook you can change these:

- `FORCE_REBUILD_PREPROCESSED = False`
- `FORCE_NEW_SPLIT = False`
- `FORCE_REBUILD_FEATURES = False`
- `FORCE_REBUILD_SKIPGRAM = False`
- `FORCE_RETRAIN = False`

Keep them `False` for normal use.

Set one of them to `True` only when you intentionally want to rebuild that stage.

## Recommended usage

1. Run the notebook once from top to bottom to create all caches.
2. On later runs, keep all force flags as `False`.
3. Rerun only the cells for the specific model you want to continue testing.
4. The neural models will load saved checkpoints when available instead of retraining from scratch.
