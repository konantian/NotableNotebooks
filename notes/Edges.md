---
title: Edges
tags: [Notebooks/Cmput206]
---

# Edges

**Edges**
  * Are image positions where local image intensity changes significantly along a particular orientation
  * Human visual system extracts sensitive information from edges
  * An entire image can be decently "reconstructed" from edges, so in that sense edges are the "information packets" in an image
  * Edge detection
    * A dominant approach in edge detection is **gradient-based**
 ![edge_detection](@attachment/cmput206/edge_detection.png)
 
**Image derivative**
 * Derivatives of image
 ![Derivate Functions](@attachment/cmput206/derivative_function.png)
 * Magnitude of image gradient is a good "edge indicator"
 ![Derivatie image](@attachment/cmput206/edge_indicator.png)
 * Calculating image derivate by linear filter
 ![Image derivate by linear filter](@attachment/cmput206/derivative_by_filter.png)
 * Edge detection by image gradient
 ![Image derivate by linear filter](@attachment/cmput206/gradient_edge_detection.png)
 * Prewitt edge operator
 * 
 ![Prewitt operator](@attachment/cmput206/prewitt_operator.png)
 * Sobel edge operator
   * The Sobel–Feldman operator is based on convolving the image with a small, separable, and integer-valued filter in the horizontal and vertical directions and is therefore relatively **inexpensive** in terms of computations. 
   * On the other hand, the gradient approximation that it produces is relatively crude, in particular for high-frequency variations in the image.
   ![Sobel operator](@attachment/cmput206/sobel_operator.png)
 * Edge strength and orientation
 ![Edge strength and orientation](@attachment/cmput206/edge_strength.png)
 
**Canny edge detection**
  * Smooth image with Gaussian filtering
  * Find out edge strength and orientation of the smoothed image.
  * (non-maximum suppression): At each pixel, determine if it has maximum edge strength along the edge orientation.Mark such pixel as edge pixels.
  * Apply a high threshold to the edge strength magnitude to detect a set of edges.
  ![Threshold level](@attachment/cmput206/threshold_level.png)
    * This stage decides which are all edges are really edges and which are not. For this, we need two threshold values, minVal and maxVal. Any edges with intensity gradient more than maxVal are sure to be edges and those below minVal are sure to be non-edges, so discarded. Those who lie between these two thresholds are classified edges or non-edges based on their connectivity. If they are connected to "sure-edge" pixels, they are considered to be part of edges. Otherwise, they are also discarded. 
    ![Threshold](@attachment/cmput206/thresholding.png)
    * You can now use a **single** threshold value to remove some of the non-edge points.
    * But better to use **two** thresholds(low and hight)
    * **How to choose thresholds**: Threshold value can be chosen low enough only when there is no noise in the image, so that all true edges can be detected without miss.
  * Follow the edges perpendicular to the edge orientation. If the pixels survive a low threshold, keep it as an edge pixel.
