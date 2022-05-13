# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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
_Copyright 2019-2022 MicroEJ Corp. All rights reserved._  
_Use of this source code is governed by a BSD-style license that can be found with this software._  

