# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [4.0.0] - 2023-05-03

### Added

  - Add the dependency to the CCO MicroUI 3.0.0 (automatically fetched by transitivity).
  - Add the compatibility with multiple Graphics Context output formats (UI Pack 13.5.0).

### Changed

  - Make the CCO compatible with UI pack 13.5.0 and higher.

### Fixed

  - Fix an include directive for case-sensitive filesystems.
  
### Migration Guide

  - Follow the migration steps of CCO MicroUI 3.0.0
  - [VEE Port configuration project] 
  		- CCO Display-DMA2D 4.0.0.
  - [BSP project] 
  		- Delete the properties file `cco_display-dma2d.properties`.
  		- Delete the C files `drawing_dma2d.h` and  `drawing_dma2d.c` and remove them from the C project configuration.
  		- In the C project configuration, include the new C file `ui_drawing_dma2d.c`.
  		- Replace the import `drawing_dma2d.h` by `ui_drawing_dma2d.h`.
  		- Replace the calls to functions `DRAWING_DMA2D_xxx()` by `UI_DRAWING_DMA2D_xxx()`.
  - Build the VEE Port and the BSP.

## [3.1.0] - 2023-04-13

### Added

  - Add the configuration file `drawing_dma2d_configuration.h` to enable or not the cache management (cache invalidate and clean).

### Fixed

  - Fix the problems with reading memory back after a DMA2D transfer on cache-enabled CPUs.
  
### Migration Guide

  1. Read the comments about the cache in `drawing_dma2d_configuration.h`.
  2. Uncomment the expected define `DRAWING_DMA2D_CACHE_MANAGEMENT` (enable or disable the cache management).
  

## [3.0.2] - 2023-02-02

### Fixed

  - Fix the flush bounds when drawing an image: must be set before calling `LLUI_DISPLAY_notifyAsynchronousDrawingEnd()`.
  
## [3.0.1] - 2022-12-16

### Fixed

  - Fix the flush bounds when drawing an image.

## [3.0.0] - 2022-08-31

### Added

  - Add the implementation of `UI_DRAWING_drawRegion`.

### Changed

  - Make CCO compatible UI pack 13.3 and higher.
  - Simplify the implementation of `UI_DRAWING_drawImage`: new specification ensures the overlapping is not possible (not backward compatible).

### Removed

  - Remove the software implementation of "image overlap": already available in UI Pack 13.3.0.

## [2.1.0] - 2022-07-20

### Added

  - Add the compatibility with the STM32H7 series.

### Changed

  - Manage the overlapping (draw an image on the same image) 
  		- by using a fast software algorithm when the opacity is fully opaque (alpha == 0xff),
  		- by using the DMA2D otherwise (block per block).  

## [2.0.1] - 2022-06-16

### Fixed

  - Fix the limitation of UI Pack 13.x in checking the MicroUI GraphicsContext clip before filling a rectangle.

## [2.0.0] - 2022-05-13

### Changed

  - Make CCO compatible UI pack 13.1 and higher (specification `LLUI_DISPLAY_setDrawingLimits()` has changed).
  
## [1.0.8] - 2022-05-13

### Fixed

  - Fix the use of returned code when drawing images with the DMA2D.
  - Clean cache before each DMA2D transfer (no-op on STM32 CPU without cache).
  
## [1.0.7] - 2022-04-28

### Fixed

  - Fix the license and copyrights: use BSD License.
  - Fix Misra rules.

## [1.0.6] - 2020-12-08

### Fixed

  - Fix missing license file.

## [1.0.5] - 2020-09-23

### Fixed

  - De-init the DMA2D before re-initializing it, to reset the context at HAL level.
  - Manipulate drawing limits after being sure the DMA2D is finished.

## [1.0.4] - 2020-09-15

### Fixed

  - Draw an image on same image is not supported by DMA2D when destination region overlaps source region.

## [1.0.3] - 2020-09-02

### Fixed

  - Fix artifact organization

## [1.0.2] - 2020-07-28

### Fixed

- Fix file names
- Remove/replace notion of `LLDISPLAY` 

## [1.0.1] - 2020-04-24

### Fixed

- Fix UI3 function names 

## [1.0.0] - 2020-04-09

### Added

- Initial revision.
- Implements `LLDISPLAY_EXTRA_IMPL_doFillRect()` and `LLDISPLAY_EXTRA_IMPL_drawImage()`.
- Supported image formats: ARGB8888, RGB888, ARGB1555, ARGB4444, RGB565, A8 and A4.
- Features a function to perform a memory copy between two pixels buffers (useful after a flush).
- Requires defines `LLDISPLAY_BPP` and `STM32F4XX` or `STM32F7XX` (see `lldisplay_dma2d.h`)  


---
_Copyright 2019-2023 MicroEJ Corp. All rights reserved._  
_Use of this source code is governed by a BSD-style license that can be found with this software._  

