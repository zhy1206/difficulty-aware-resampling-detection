# Code Release Plan

Use this checklist when moving the original research code into the repository.

## 1. Data preparation

Add the exact scripts used to:

- Convert KITTI annotations to YOLO format.
- Keep only Car, Pedestrian, and Cyclist.
- Produce the fixed 7:2:1 split.
- Save the original split text files or checksums.

## 2. Difficulty scoring

The public implementation should expose:

- `alpha`: small-object weight.
- `beta`: occlusion weight.
- `gamma`: truncation weight.
- `delta`: hard-category weight.
- `max_repeat = 5`.
- Small-object threshold: bounding-box area below 1024 pixels.
- Occlusion levels: 2 and 3.
- Truncation threshold: greater than 0.5.
- Hard categories: Pedestrian and Cyclist.

## 3. Resampled training source

Add the exact routine that repeats each image path according to its mapped repeat number. Keep validation and test images unmodified.

## 4. Training entry points

Provide separate commands for:

- YOLO11n baseline.
- Random oversampling.
- Class-balanced resampling.
- Fixed all-factor resampling.
- 81-setting grid search.
- High-resolution fine-tuning.

## 5. Reproducibility metadata

Record Python, PyTorch, CUDA and Ultralytics versions, GPU model, random seed, KITTI split hashes, and checkpoint initialization.

## 6. Publication metadata

After the proceedings are online, add the author list, DOI, proceedings link, official BibTeX and a release tag such as `v1.0-prcv2026`.
