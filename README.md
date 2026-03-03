# SafeMed-SSL: Uncertainty-Guided Semi-Supervised Learning for Safe Medical Image Classification

[![Conference](https://img.shields.io/badge/SASIGD-2026-blue)](https://sasigd.cbit.ac.in/)
[![Framework](https://img.shields.io/badge/PyTorch-2.0-orange)](https://pytorch.org/)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

Official PyTorch implementation of the paper: **"Uncertainty-Guided Semi-Supervised Learning for Safe Medical Image Classification in Low-Resource Settings"**.

Submitted to **SASIGD 2026** 

## Problem Statement
In low-resource healthcare settings, obtaining expert-labeled medical images is expensive and time-consuming. Standard Semi-Supervised Learning (SSL) methods like FixMatch can fail silently, classifying ambiguous images with high confidence but incorrectly.

**Our Solution:** We introduce an **Uncertainty-Guided Safety Filter** that uses MC Dropout to estimate model uncertainty. It rejects ambiguous pseudo-labels even if the model is confident, significantly reducing the **Silent Failure Rate (SFR)**.

## Key Features
- **Dual-Path Architecture:** Combines standard Supervised Learning (20% data) with Uncertainty-Guided SSL (80% data).
- **Safety Mechanism:** Filters unlabeled samples based on both **Confidence (>0.70)** and **Uncertainty (<0.2)**.
- **Low-Resource Optimized:** Designed for lightweight backbones (ResNet-18) suitable for edge deployment.

## Results (Malaria Screening)
| Method | Accuracy | Silent Failure Rate (SFR) |
| :--- | :--- | :--- |
| Supervised Baseline (20% Labels) | 94.12% | 2.50% |
| FixMatch (Standard SSL) | 95.89% | 2.47% |
| **Ours (SafeMed-SSL)** | **96.53%** | **1.77%** |

> **Impact:** We achieved a **29.2% reduction in silent failures** ($p=0.0137$), preventing potentially dangerous misdiagnoses.

## Dataset
We used the **NIH Malaria Cell Images Dataset**, which contains 27,558 images of parasitized and uninfected cells.
- **Download:** [Kaggle Link](https://www.kaggle.com/datasets/iarunava/cell-images-for-detecting-malaria)
- **Structure:**
data/
├── Parasitized/
└── Uninfected/


## Usage

### 1. Installation
```bash
git clone [https://github.com/Latchan-Ch/SafeMed-SSL.git](https://github.com/Latchan-Ch/SafeMed-SSL.git)
cd SafeMed-SSL

```

### 2. Training

To train the model with the Uncertainty-Guided strategy, see our notebook 

## Authors

* **Latchan Chhetri** (Dept. of AI & DS, SMIT)
* **Aman Kumar** (Dept. of AI & DS, SMIT)
* **Hrishikesh Das** (Dept. of CSE, SMIT)

## Citation

If you find this work useful, please cite our paper:

```bibtex
@inproceedings{safemed2026,
  title={Uncertainty-Guided Semi-Supervised Learning for Safe Medical Image Classification in Low-Resource Settings},
  author={Chhetri, Latchan and Kumar, Aman and Das, Hrishikesh},
  booktitle={2026 International Conference on Sustainable AI for Social Impact and Global Development (SASIGD)},
  year={2026}
}
