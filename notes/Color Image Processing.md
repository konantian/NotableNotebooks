---
title: Color Image Processing
tags: [Notebooks/Cmput206]
created: '2019-02-05T18:05:22.638Z'
modified: '2019-02-05T20:47:57.422Z'
---

# Color Image Processing

## Human Eye and color
  * Color is the visible manifestation of light's wavelength
  * The light is visible to human eyes if its wavelength is between 380-780 nm.
  * For human eye
    * approximately 65% of all cone are sensitive to red light
    * 33% are sensitive to green light
    * 2% are sensitive to blue light
  * Blue cons are the most sensitive
  
  
## Brightness and Chromaticity
**Brightness**
`Decreasing brightness with depth (underwater photo as example)
Brightness is an attribute of visual perception in which a source appears to be radiating or reflecting light.[1] In other words, brightness is the perception elicited by the luminance of a visual target. It is not necessarily proportional to luminance. `

**Chromaticity**
`Chromaticity is an objective specification of the quality of a color regardless of its luminance. Chromaticity consists of two independent parameters, often specified as hue (h) and colorfulness (s)`

  * White and gray shade have same chromaticity, but different brightness values
 
 
## Color Models
  * Color models facilitate the specification of colors in some standards
  * RGB: for color monitor
  * CMY: for color printing
  ![RGB to CMY](@attachment/cmput206/rgb_to_cmy.png)
  * HSI: decouples color and gray-scale information
    * Human describes color in terms of hue, saturation and brightness or intensity
    ![HSI Color Models](@attachment/cmput206/hsi_model.png)
  * CIE LAB: derived from CIE xyY space
  * CMYK model is used in color printers
  
## Pseudocolor Image Processing
  * Pseudocolor image processing consists of assigning colors to gray level values based on some specific criterion
  * Goal and Motivation
    * Improve human visualization
    * Attract attention
  * Major techniques
    * Intensity slicing
    * gray level to color transformation
    
 
## Full-color image processing
  * Two categories:
    * Process each component individually and then form a composite processed color image from the components.
    * Work with color pixels directly. In RGB system, each color point can be interpreted as a vector.
   ![Full color](@attachment/cmput206/full_color.png)
   
## Histogram processing
  * Equalized the histogram of each component will results in erroneous color
  * Spread the intensity uniformly, leaving the colors(hue and saturation) unchanged.
  * Equalizaing the intensity histogram affects the relative appearance of colors in an image.
  * Increasing the image's saturation component after the intensity histogram equalization.
  
## Decorrelating Data
  * Suppose X and Y have linear relationship, but increase in X does not result in increase or decrease in Y => X and Y are not correlated. We use rotation to correlated data.
  ![Decorrelating Data](@attachment/cmput206/decorrelating_data.png)
  * Stretching Decorrelated Data
  ![Decorrelating Data](@attachment/cmput206/stretching_data.png)

## Bayer Pattern
  * A very common filter pattern used for the matrix of CCD or CMOS sensors in a digital camera. More pixels are dedicated to green than to red and blue, because the human eye is more sensitive to green. When only one array of sensors is used, the additional green pixels produce a better color image. In a three-chip digital camera, the image is sent to three separate sensors, one each for red, green and blue. Bryce Bayer invented the pattern at Kodak.
  ![Bayer Pattern](@attachment/cmput206/bayer_pattern.png)
