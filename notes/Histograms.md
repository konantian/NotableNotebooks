---
title: Histograms
tags: [Notebooks/Cmput206]
---

# Histograms

## Histograms
   ![Histograms](@attachment/cmput206/histograms.png)
  * Not unique,different images may have same histograms

## Cumulative Histograms
 ![Formula](@attachment/cmput206/cumulative_formula.png)
 ![Cumulative Histograms](@attachment/cmput206/cumulative_histogram.png)
 
## Normalized Histogram
  ![Formula](@attachment/cmput206/normalized_formula.png)
  * Probability mass funciton:p(i) means the probability of a pixel value to be i
  
## Normalized cumulative histogram
  * **H(i)/(MN)**
  
## Binning for histogram
  $$range = 2^k$$ k is bit of image
  * Example, a 8 bit image has range of 2^8 = 256 bins
  
## Histogram Matching
  * Image segmentation
  * Tracking
  * Content-based image retrieval
  * Find out images in database by looking for images has similar histograms
  * Procedures
    1. Convert into normalized histograms
    2. Calculating Bhattacharya coefficient
      ![Bhattacharya coefficient](@attachment/cmput206/bhattacharya_coefficient.png)
      * For a perfect match BC is 1, for a complete mismatch BC is 0
      * A higher BC value implies a better match
      
## Histogram equalization(histogram flattening)
**Definition**:
```
Histogram equalization is a technique for adjusting image intensities to enhance contrast.
```
**Local(Adaptive)**:
  * Histogram equalization does not work well when the distribution of pixel values varies a lot over local windows in an image
  * Doing histogram equalization within a sliding window is often more useful than the global histogram equalization
