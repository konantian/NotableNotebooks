---
title: Point operations
tags: [Notebooks/Cmput206]
created: '2019-01-28T21:40:03.818Z'
modified: '2019-01-29T00:02:11.465Z'
---

# Point operations
**Negative images**
  * Denote [0,L-1] intensity levels of the image
  * Image negative is obtained by s = L-1-r
  * Useful for enhancing white or gey detail embedded in dark regions of an image
  
**Global thresholding**
  * Global thresholding is based on the assumption that the image has a bimodal histogram and, therefore, the object can be extracted from the background by a simple operation that compares image values with a threshold value T
  * The object and background pixels have gray levels grouped into two dominant modes. One obvious way to extract the object from the background is to select a threshold T that separates these modes.
  * The thresholded image g(x,y) is defined as g(x, y)
  g(x,y)={1if(x,y)>T0if(x,y)≤T.The result of thresholding is a binary image, where pixels with intensity value of 1 correspond to objects, whereas pixels with value 0 correspond to the background.
  ![Global Thresholding](@attachment/cmput206/global_thresholding.png)
  
 
**Intensity Transformations**
  * The following transformation T produces an image of higher contrast than the original by darkening the levels below k and brightening the level above k in input image
  ![Intensity transformations](@attachment/cmput206/intensity_transformations.png)
  * Linear(Negative/Identity)
  * Logarithmic(Log/Inverse log)
    * The log transformation maps a narrow range of low input grey level values into a wider range of output values
     $$s=c*log(1+r)$$
    * Log transformation compresses the dynamic range of images with large variations in pixel values
    * In the following example the Fourier transform of an image is put through a log transform to reveal more detail
      ![Log transformation](@attachment/cmput206/log_transformation.png)
  * Power law(nth power/nth root)
    * Map a narrow range of dark input values into a wider range of output values or vice versa
    $$ s = c*r^\gamma $$
    * Gamma correction
    ![Gamma correction](@attachment/cmput206/gamma_correction.png)
      * A gamma value gamma < 1is sometimes called an encoding gamma, and the process of encoding with this compressive power-law nonlinearity is called gamma compression; conversely a gamma value gamma >1 is called a decoding gamma and the application of the expansive power-law nonlinearity is called gamma expansion.
      
  * Piecewise linear transformation
    * A complementary approach to the previously discussed methods
    * Principle advantage is that the piecewise linear functions can be arbitrarily complex
    * Principle disadvantage is that their specification requires considerably more user input
    * One of the simplest piecewise linear functions is a contrast-stretching transformation
  
 **Automatic contrast adjustment**
   * Suppose alow and ahigh are the lowest and the highest pixel values in the current image
   ![Automatic Contrast](@attachment/cmput206/automatic_contrast.png)
   ![Automatic Contrast](@attachment/cmput206/automatic_contrastB.png)
   
**Modified automatic contrast adjustment**
  * In practice, the linear mapping function can be affected by a few extreme pixel values (sometimes called outlier values)
  ![Modified Automatic Contrast](@attachment/cmput206/modified_mac.png)
