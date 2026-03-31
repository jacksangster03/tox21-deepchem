# Molecular Toxicity Prediction with DeepChem

Multi-task toxicity prediction on the **Tox21** dataset using DeepChem, built as part of my GSoC 2026 application for the [DeepChem](https://github.com/deepchem/deepchem) project.

## Overview

This notebook trains a `MultitaskClassifier` to predict 12 toxicity assay endpoints simultaneously from molecular structure (ECFP fingerprints). Tox21 is a benchmark dataset of ~8,000 compounds tested across nuclear receptor signalling and stress response pathways by the NIH, EPA, and FDA.

## What's Covered

- Loading and exploring the Tox21 dataset via DeepChem's MoleculeNet
- ECFP featurisation and scaffold splitting
- Training a multi-task neural network (hidden layers [512, 256])
- Per-task ROC-AUC evaluation (mean test ROC-AUC: **0.693**)
- Comparison against a Random Forest baseline
- Prediction analysis: true positives vs false negatives on the androgen receptor assay
- Custom molecule predictions (aspirin, caffeine, BPA, DDT, etc.)
- Molecular property analysis (LogP, MW, TPSA vs predicted toxicity)

## Key Results

| Metric | Value |
|--------|-------|
| Mean test ROC-AUC (MultitaskClassifier) | 0.6933 |
| Mean test ROC-AUC (Random Forest baseline) | 0.7040 |
| Best assay | NR-AR-LBD (0.7982) |
| Worst assay | NR-PPAR-gamma (0.5817) |

The model correctly identifies known toxic compounds (Bisphenol A, DDT) as high-risk and common drugs (caffeine, aspirin) as low-risk, validating biological plausibility.

## Setup

Requires Python 3.11+.

```bash
pip install -r requirements.txt
jupyter notebook tox21_deepchem.ipynb
```

## Author

Jack Sangster, Imperial College London / IE University
