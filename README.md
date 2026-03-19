# ISIC Skin Lesion Segmentation under Partial Supervision

## Overview
Segmentation experiment on the ISIC 2018 skin lesion dataset using U-Net with EfficientNet-B0 encoder under sparse pixel supervision, implemented in PyTorch.

## Key Results
| Drop Rate | IoU | Dice | Precision | Recall |
|-----------|-----|------|-----------|--------|
| 0.2 | 0.762 | 0.846 | 0.959 | 0.807 |
| 0.4 | 0.763 | 0.849 | 0.952 | 0.812 |
| 0.5 | 0.760 | 0.844 | 0.957 | 0.807 |
| 0.7 | **0.769** | **0.851** | 0.952 | 0.820 |

## Methodology
- **Model:** U-Net with EfficientNet-B0 encoder (ImageNet pretrained)
- **Loss:** Custom Spatial Focal Loss with pixel-level supervision mask
- **Training:** 3-Fold Cross Validation, Early Stopping, AMP, Dual T4 GPU
- **Supervision:** Random and Class-Balanced pixel sampling strategies
- **Evaluation:** Global pixel-wise (Precision, Recall, F1) + Per-image spatial (IoU, Dice)

## Key Findings
- Best IoU achieved at drop=0.7, contrary to expectations
- Random sampling outperforms balanced sampling on large diverse datasets
- Model detects high-contrast lesion cores well but struggles with low-contrast boundaries
- Hair artifacts introduce noise across all drop rates

## Files
- `notebook.ipynb` — Full training pipeline
- `ISIC_segmentation.pdf` — Detailed experiment report
