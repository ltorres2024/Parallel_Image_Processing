# Parallelized Image Processing with Dask – DSC 360 Final Project

This project tackles the challenge of **large-scale image processing** for machine learning applications, using a dataset of artworks categorized by genre. The main goal was to evaluate and compare the performance of **non-parallelized vs. Dask-parallelized** workflows for loading and preprocessing thousands of high-resolution images.

Dataset used:  
[WikiArt Dataset – Creating Art GAN (Kaggle)](https://www.kaggle.com/datasets/ipythonx/wikiart-gangogh-creating-art-gan)

---

## Overview

The pipeline includes:
- Image loading and preprocessing (filtering, error handling, size validation)
- Extraction of image metadata using `Pillow` and `Dask Image`
- Timing and performance benchmarking of:
  - Non-parallelized image loading
  - Parallelized image loading using **Dask**

---

##  Techniques Implemented

### Non-Parallel Processing
- Loops through images directory-by-directory
- Verifies file integrity and size
- Stores processing time for each image

### Dask Parallelization
- Uses `dask.delayed` to parallelize:
  - File discovery across directories
  - Image reading and metadata extraction
- Visualized task dependency graph with `.visualize()`

---

## Key Results

| Method            | Wall Time        | Avg Time per Image |
|------------------|------------------|---------------------|
| Non-Parallelized | ~32 minutes      | ~0.024 seconds      |
| Parallelized      | ~6.5 minutes     | ~0.029 seconds      |

> **Finding:** Despite the shorter total wall time in parallelized execution, average per-image processing time was slightly longer, likely due to Dask's overhead on small tasks. However, parallel execution was vastly more efficient at scale.

---

## Tools & Libraries

- `Pandas`, `NumPy`, `Matplotlib`
- `Pillow` (PIL) – image loading and validation
- `Dask`, `dask_image` – parallel processing and image handling
- `os`, `time`, `pathlib` – file handling and benchmarking

---

## Challenges Addressed

- Managed corrupted or oversized image files
- Skipped unreadable images with meaningful error handling
- Addressed decompression bomb warnings for extremely large images
- Created plots for both overall and zoomed-in processing times

---

## Authors

**Leo Sanchez & Brian Chaffee** 
