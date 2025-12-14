# Astronomical Catalogue Cross-Matching

## Overview
This project implements an automated algorithm to align multiple astronomical catalogues derived from consecutive optical telescope observations of the same sky patch. Due to mechanical inaccuracies in telescope pointing, sequential images often exhibit spatial shifts that must be corrected for multi-epoch analysis.

## Key Features & Methodology:
* **Data Parsing:** extracts $(x, y)$ source coordinates from raw ASCII catalogue files (image*.asc).
* **Shift Detection:** Calculates pairwise relative shifts between images by computing the distance vectors between all sources in two catalogues. A 2D histogram of these difference vectors is used to identify the peak, which corresponds to the true physical shift between the exposures.
* **Global Alignment:** Solves a system of linear relationships derived from the pairwise shifts to determine the absolute offset of each image relative to a reference frame.
* **Visualization:** Verifies the alignment by plotting the cross-matched sources, ensuring that stars from different exposures overlap correctly.

## Tools: 
* **Python**
* **NumPy** (vectorized calculations)
* **Matplotlib** (visualization)
