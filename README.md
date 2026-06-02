# nycu-vrdl-hubmap-vasculature-segmentation
Final project for NYCU Visual Recognition using Deep Learning (VRDL): Microvascular instance segmentation on the HuBMAP dataset using YOLOv11x, spatial validation, ensemble learning, TTA, and state-of-the-art solution reproduction.
# HuBMAP State-of-the-Art Reproduction

## Overview

This repository reproduces the public winning solution for the Kaggle competition:

**HuBMAP – Hacking the Human Vasculature**

The objective of the competition is to accurately detect and segment microvascular structures from high-resolution PAS-stained histopathology images.

This reproduction was performed as part of the Final Project for the course:

**Visual Recognition using Deep Learning (VRDL)**
National Yang Ming Chiao Tung University (NYCU)

---

# Objective

The goal of this work is to:

* Reproduce the public state-of-the-art solution.
* Reconstruct the complete inference environment.
* Resolve dependency and compatibility issues.
* Execute the full ensemble pipeline.
* Generate valid Kaggle submissions.
* Benchmark reproduced performance against competition results.

---

# Competition

**Competition:** HuBMAP – Hacking the Human Vasculature

Task:

Instance segmentation of blood vessels in human tissue slides.

Input:

* PAS-stained Whole Slide Images (WSIs)

Output:

* Pixel-level vessel instance masks

Evaluation Metric:

* Average Precision (AP)

---

# Reproduced Solution

The reproduced solution is based on the public winning ensemble architecture.

The pipeline consists of:

```text
Input Images
      ↓
10 Trained Detection Models
      ↓
Individual Model Predictions
      ↓
Weighted Box Fusion (WBF)
      ↓
Mask Generation
      ↓
Post-processing
      ↓
submission.csv
```

The ensemble combines predictions from:

```text
r0i
r1i
s0i
s1i
m0i
m1i
y0i
y1i
sb0i
sb1i
```

Each model contributes complementary vessel detections that are merged using Weighted Box Fusion.

---

# Environment Reconstruction

One of the major challenges of this reproduction was rebuilding the original competition environment.

Issues resolved:

* MMCV compatibility errors
* MMDetection installation issues
* MMPretrain dependency conflicts
* Missing ensemble dependencies
* Missing configuration files
* Missing inference scripts
* Kaggle submission environment constraints

Packages used:

* Python
* PyTorch
* MMDetection
* MMCV
* MMEngine
* MMPretrain
* OpenCV
* Ensemble Boxes

---

# Inference Pipeline

The reproduction workflow follows:

```text
Checkpoint Loading
        ↓
Model Inference
        ↓
PKL Generation
        ↓
Ensemble Creation
        ↓
Mask Reconstruction
        ↓
Submission Generation
```

Generated intermediate files:

```text
r0i.pkl
r1i.pkl
s0i.pkl
s1i.pkl
m0i.pkl
m1i.pkl
y0i.pkl
y1i.pkl
sb0i.pkl
sb1i.pkl
ensemble.pkl
ensemble_results.pkl
submission.csv
```

---

# Results

Final reproduced performance:

| Metric              | Score |
| ------------------- | ----- |
| Public Leaderboard  | 0.317 |
| Private Leaderboard | 0.589 |

The reproduced model successfully achieved the historical best competition score.

---

# Repository Structure

```text
.
├── notebooks/
│   ├── sota_reproduction.ipynb
│
├── checkpoints/
│   ├── r0i.pth
│   ├── r1i.pth
│   ├── s0i.pth
│   ├── s1i.pth
│   ├── m0i.pth
│   ├── m1i.pth
│   ├── y0i.pth
│   ├── y1i.pth
│   ├── sb0i.pth
│   └── sb1i.pth
│
├── outputs/
│   ├── ensemble.pkl
│   ├── ensemble_results.pkl
│   ├── submission.csv
│   └── score_screenshots/
│
└── README.md
```

---

# Reproduction Contributions

This repository documents:

* Environment reconstruction
* Dependency resolution
* Checkpoint integration
* Ensemble execution
* Kaggle submission generation
* Result verification

The focus of this repository is reproducibility and benchmarking of public state-of-the-art methods.

---

# References

HuBMAP – Hacking the Human Vasculature Competition

Public Winning Solutions

MMDetection Framework

Weighted Box Fusion (WBF)

PyTorch

---

# Author

Basetti Sai Viswas

National Yang Ming Chiao Tung University

Visual Recognition using Deep Learning (VRDL)

2026

