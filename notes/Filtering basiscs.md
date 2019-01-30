---
title: Filtering basiscs
tags: [Notebooks/Cmput206]
created: '2019-01-24T04:20:22.722Z'
modified: '2019-01-30T21:51:56.709Z'
---

# Filtering basiscs

## Filter
> It refers to accepting/rejection **frequency** components

> Filtering is a technique for modifying or enhancing an image. For example, you can filter an image to emphasize certain features or remove other features.

> Filtering is a neighborhood operation, in which the value of any given pixel in the output image is determined by applying some algorithm to the values of the pixels in the neighborhood of the corresponding input pixel. A pixel's neighborhood is some set of pixels, defined by their locations relative to that pixel.

## Handing image borders
  * Take on the value of the closest border pixel
  * Mirrored at the image boundaries
  * Repreat periodically along the coordinate axes
  

## Filter size
  * Typically is oldd matrix size(2k+1) by (2k+1), for center the filter on a pixel and equal number of pixels on all sides
  * Computational complexity increases with filter size

## Types of filters

**Linear(smoothing) filters**
  * Smoothing filters application
    * Noise reduction
      * Median filter works better than an averageing filter
        * a single very unrepresentative pixel in a neighborhood will not affect the median value significantly.
        * the median filter does not create new unrealistic pixel values
    * Segmentation
    * Blurring
  * Difference filters
    * Edge detection
    * Image sharpening
  * Box filter
  ```
  Box filter is basically an average-of-surrounding-pixel kind of image filtering
  ```
 ![Box filter](@attachment/cmput206/box_filter.png)
  * Gaussian filter 
  ```
  The Gaussian smoothing operator is a 2-D convolution operator that is used to `blur' images and remove detail and noise.
  ```
 ![Gaussian filter](@attachment/cmput206/gaussian_filter.png)
  * Laplace filter
  ```
  The Laplacian of an image highlights regions of rapid intensity change and is therefore often used for edge detection
  ```
 ![Laplace filter](@attachment/cmput206/laplace_filter.png)
 
  * Convolution(Spatial linear filter)
    * convolution is a general purpose filter effect for images
    * the output is a new modified filtered image
  ![Convolution](@attachment/cmput206/convolution.png)
  ![Convolution](@attachment/cmput206/convolution_example.png)
  * Correlation
    * correlations and convolutions give same results when at least one of f and w is symmetric
    ![Correlation](@attachment/cmput206/correlation.png)
  * Properties
    * Commutative 
    ```
    I * H = H * I
    ```
    * Linear
    ```
    (s * I)*H = I * (s*H)
    (I1 + I2)*H = (I1*H) + (I2*H)
    ```
    * Associative
    ```
    A*(B*C) = (A*B)*C
    ```
  * Drawbacks
    * It also smoothes out important structures, edges
    * Reduce fine image details
    
**Nonlinear filter**
  * Resulting pixel value is a function of the pixel values in a corresponding neighborhood
  * Non-linear filter operation
  * Median filter
    ![Median filter](@attachment/cmput206/median_filter.png)
  * Weighted median filter
    ![Weighted median filter](@attachment/cmput206/weighted_median_filter.png)
    * Restore some spatialization absent in the traditional median, which generates "moving edges", by better centering the median around the central pixel of the square window. 
    * Allow negative weights, to better mimic not only smoothing filters (positive weights) but also "median-derivative-like" filters.
  
  
  * Sharpening Spatial Filters
    * Purpose: Highlight fine detail
    * Smoothing: pixel averaging = integration
    * Sharpening: differentiation = enhance edges and deepmphasize
    * Isotropic filters
      * Applies equally well in all directions in an image
      * With no particular sensitivity or bias towards one particular set of directions
      ![Laplacian](@attachment/cmput206/laplacian.png)
      
**Unsharp Masking**
  ```
  The unsharp filter is a simple sharpening operator which derives its name from the fact that it enhances edges (and other high frequency components in an image) via a procedure which subtracts an unsharp, or smoothed, version of an image from the original image.
  ```
  * Procedures
    * Blur the image
    * Subtract the blurred image from the original;call this resulting image as mask
    * Mulitply the mask image with a positive constant
    * Add the multiplied mask image to the original image
  * Properties
    * The resulting image, although clearer, may be a less accurate representation of the image's subject
  
**High-boost Filtering**
  * In image processing, it is often desirable to emphasize high frequency components representing the image details without eliminating low frequency components (such as sharpening)
  ![High-boost Filtering](@attachment/cmput206/high_boost.png)
  
**Image Gradient**
  * An image gradient is a directional change in the intensity or color in an image. 
  ![Image Gradient](@attachment/cmput206/image_gradient.png)
