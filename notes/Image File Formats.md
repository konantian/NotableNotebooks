---
title: Image File Formats
tags: [Notebooks/Cmput206]
---

# Image File Formats

**Image file formats**
  * A raster format means "matrix format" of digital image
  * Vector format means representing geometric objects by **continuous** coordinates
  * While displaying a vector image, the display devise/software has to convert it to a raster image
  * Photoshop has both these capabilities to represent images
  * Some image formats, such as CGM, SVG, PS, EPS, PDF have the capability to store both raster and vector image data
  
**Indexed color image**
  ![Index Image](@attachment/cmput206/index_image.png)
  
  
**BMP(bit map) and PGM(portable bitmap)**
  * Supports indexed, true color, grayscale and binary images
  * PGM store files in a human readable text format
  ![PGM](@attachment/cmput206/pgm.png)
  
**TIFF(Tagged image file format**
  * Supports grayscale, indexed and true color images
 
**GIF(Graphics interchange format)**
  * Was popular for web images
  * Indexed file format with a maximum depth of 8 bits
  * Does not support true color images
  * Use **lossless** compressions
  
**PNG(Portable network graphics)**
  * Supports true color, grayscale, indexed
  * Superior to GIF in many ways
  * Supports lossless compression

**JPEG(Joint photographic experts group**
  * Jpeg is a compression method for color and grayscale images
  * Goal was to achieve a data compression of 1:16
  * It is the most used image format today
  
  
| Formats | Indexed | True color | Grayscale | Compression |
|:---:|:-----:| :--------: |:----------:|:---:|
|BMP|Yes|Yes|Yes|Uncompressed|
|TIFF|Yes|Yes|Yes|Uncompressed|
|GIF|Yes|No|Yes|Loseless|
|PNG|Yes|Yes|Yes|Loseless|
|JPEG|No|Yes|Yes|Lose|
