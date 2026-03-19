# ISIC Skin Lesion Segmentation under Partial Supervision

Segmentation experiment on the ISIC 2018 dataset using U-Net with EfficientNet-B0 encoder, trained under sparse pixel supervision using a custom Spatial Focal Loss.

## Results

| Strategy | Drop Rate | IoU | Dice | Precision | Recall |
|----------|-----------|-----|------|-----------|--------|
| Random   | 0.7       | **0.769** | **0.851** | 0.952 | 0.820 |
| Random   | 0.4       | 0.763 | 0.849 | 0.952 | 0.812 |
| Balanced | 0.5       | 0.760 | 0.842 | 0.956 | 0.805 |

## Key Findings
- Model maintained ~95% precision across all drop rates
- Contrary to expectations, drop=0.7 achieved the best IoU and Dice
- Random sampling outperforms balanced sampling on large diverse datasets
- All models detected high-contrast lesion cores but struggled with low-contrast boundaries

## Architecture
- **Model:** U-Net
- **Encoder:** EfficientNet-B0 (ImageNet pretrained)
- **Loss:** Custom Spatial Focal Loss (masked)
- **Training:** 3-Fold Cross Validation, Early Stopping
- **Hardware:** Dual T4 GPUs with AMP

## Dataset
ISIC 2018 Skin Lesion Segmentation — 2,596 images

## Files
- `isic-segmentation.ipynb` — Full training pipeline
- `ISIC segmentation.pdf` — Detailed experiment report
