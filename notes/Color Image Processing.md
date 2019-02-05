---
title: Color Image Processing
tags: [Notebooks/Cmput206]
created: '2019-02-05T18:05:22.638Z'
modified: '2019-02-05T18:53:46.828Z'
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
