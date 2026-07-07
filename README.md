# BrainScan AI, détection de tumeurs cérébrales par apprentissage semi-supervisé

Projet d'exploration et de labellisation semi-supervisée sur un jeu d'images IRM
(1506 images au total : 1406 non étiquetées, 100 étiquetées normal/cancer, 50 de chaque).

## Structure
- `notebooks/01_exploration_clustering.ipynb` : import, EDA, extraction de features, clustering
- `notebooks/02_semi_supervised_training.ipynb` : entraînement semi-supervisé et évaluation
- `support/` : support de présentation

## Setup

```bash
uv sync
uv run python -m ipykernel install --user --name=brainscan-ai --display-name="BrainScan AI (uv)"
```

Puis sélectionner le kernel "BrainScan AI (uv)" dans Jupyter ou VS Code.
