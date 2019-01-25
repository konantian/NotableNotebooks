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
