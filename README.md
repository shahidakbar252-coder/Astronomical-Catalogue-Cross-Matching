# Astronomical Catalogue Cross-Matching

## Overview
This project addresses the problem of precisely aligning multiple astronomical catalogues (lists of star coordinates) derived from consecutive optical telescope exposures of the same sky patch. Since telescope pointing is subject to errors, a computational approach is necessary to determine the correct spatial shift between images for accurate multi-epoch analysis.

## Methodology and Key Features
1.  **Shift Detection (Pairwise Alignment):**
    * The core algorithm calculates the relative $(x, y)$ shift between two catalogues by taking the difference between all possible pairs of object coordinates (one from each catalogue).
    * A 2D histogram of these difference vectors is created; the true offset is identified as the center of the bin containing the maximum number of counts, as it represents the most frequent positional difference between corresponding stars. This technique is robust against measurement errors and non-matching sources (e.g., artifacts or missing objects).
2.  **Global Alignment:**
    * Pairwise shifts are computed for all combinations of the six available catalogues.
    * A system of linear equations is then solved to find the final absolute shift of each catalogue relative to a fixed reference image.
3.  **Analysis:** The project includes an analysis of systematic errors, noting that shifts computed directly between images (e.g., $d_{23}$) may differ slightly from shifts computed indirectly ($d_{21}-d_{31}$) due to accumulation of binning/measurement noise.

## Tools Used
* **Python:**
* **NumPy:** Essential for efficient, vectorized calculation of all pairwise coordinate differences and for manipulating data arrays.
* **Matplotlib:** Used for visualizing the 2D difference histograms and plotting the final shifts of all catalogues.
