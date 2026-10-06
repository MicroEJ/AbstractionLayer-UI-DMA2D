# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [8.0.2] - 2026-10-06

### Changed

- Compatible with MicroEJ UI Pack 14.5.5.
- Complete the Doxygen documentation of the headers, and align the README with the other MicroEJ Abstraction Layers.

## [8.0.1] - 2026-08-04

### Fixed

- Fix incorrect Doxygen comments in the DMA2D drawing header.

## [8.0.0] - 2025-10-07

- Compatible with MicroEJ UI Pack 14.5.0.

### Changed

- Use the UI Pack 14.5.0 options convention.

### Fixed

- Fix the copyright headers.

## [7.0.1] - 2025-05-26

### Fixed

- Fix the implementation of `UI_DRAWING_DMA2D_copyImage()` to use the right software algorithm.

## [7.0.0] - 2024-10-09

- Compatible with MicroEJ UI Pack 14.1.0.

### Changed

- Fetch the MicroUI Abstraction Layer 14.1.0.

## [6.0.1] - 2024-10-01

- Compatible with MicroEJ UI Pack 14.0.3.

### Changed

- Fetch the MicroUI Abstraction Layer 14.0.3.

## [6.0.0] - 2024-07-19

### Changed

- Rename this module to `com.microej.clibrary.llimpl#microui-dma2d`.
- Rename `ui_drawing_dma2d_configuration.h` to `ui_dma2d_configuration.h`.
- Install the files in the `ui_dma2d` directory.

## [5.0.1] - 2024-04-09

- Compatible with MicroEJ UI Pack 14.0.x.

### Changed

- Homogenize the notions of back and front buffers.

## [5.0.0] - 2024-02-14

- Compatible with MicroEJ UI Pack 14.0.x.

### Added

- Add the function `UI_DRAWING_DMA2D_memcpy_callback()` to be notified about the end of the memory copy.
- Add the support of the display Buffer Refresh Strategies (BRS) `PREDRAW` and `SINGLE`.
- Add the configuration version (`1`).

### Changed

- Make the Abstraction Layer compatible with the UI Pack 14.0.0 (MicroUI Abstraction Layer 4.0.0).

## [4.1.1] - 2023-10-25

- Compatible with MicroEJ UI Pack 13.7.x.

### Changed

- Update the license file.

## [4.1.0] - 2023-10-23

- Compatible with MicroEJ UI Pack 13.7.x.

### Changed

- Fetch Abstraction Layer com.microej.clibrary.llimpl#microui#3.1.0 (compatibility with UI Pack 13.7.0).

### Fixed

- Fix some comments.

## [4.0.0] - 2023-05-03

- Compatible with MicroEJ UI Pack 13.5.x and 13.6.x

### Added

- Add the dependency to the MicroUI Abstraction Layer 3.0.0 (automatically fetched by transitivity).
- Add the compatibility with multiple Graphics Context output formats (UI Pack 13.5.0).

### Changed

- Make the Abstraction Layer compatible with UI pack 13.5.0 and higher.

### Fixed

- Fix an include directive for case-sensitive filesystems.

## [3.1.0] - 2023-04-13

- Compatible with MicroEJ UI Pack 13.3.x and 13.4.x.

### Added

- Add the configuration file `drawing_dma2d_configuration.h` to enable or not the cache management (cache invalidate and clean).

### Fixed

- Fix the problems with reading memory back after a DMA2D transfer on cache-enabled CPUs.

## [3.0.2] - 2023-02-02

- Compatible with MicroEJ UI Pack 13.3.x and 13.4.x.

### Fixed

- Fix the flush bounds when drawing an image: must be set before calling `LLUI_DISPLAY_notifyAsynchronousDrawingEnd()`.

## [3.0.1] - 2022-12-16

- Compatible with MicroEJ UI Pack 13.3.x and 13.4.x.

### Fixed

- Fix the flush bounds when drawing an image.

## [3.0.0] - 2022-08-31

- Compatible with MicroEJ UI Pack 13.3.x and 13.4.x.

### Added

- Add the implementation of `UI_DRAWING_drawRegion`.

### Changed

- Make the Abstraction Layer compatible UI pack 13.3 and higher.
- Simplify the implementation of `UI_DRAWING_drawImage`: new specification ensures the overlapping is not possible (not backward compatible).

### Removed

- Remove the software implementation of "image overlap": already available in UI Pack 13.3.0.

## [2.1.0] - 2022-07-20

- Compatible with MicroEJ UI Pack 13.1.x and 13.2.x.

### Added

- Add the compatibility with the STM32H7 series.

### Changed

- Manage the overlapping (draw an image on the same image)
	- by using a fast software algorithm when the opacity is fully opaque (alpha == 0xff),
	- by using the DMA2D otherwise (block per block).

## [2.0.1] - 2022-06-16

- Compatible with MicroEJ UI Pack 13.1.x and 13.2.x.

### Fixed

- Fix the limitation of UI Pack 13.x in checking the MicroUI GraphicsContext clip before filling a rectangle.

## [2.0.0] - 2022-05-13

- Compatible with MicroEJ UI Pack 13.1.x and 13.2.x.

### Changed

- Make the Abstraction Layer compatible UI pack 13.1 and higher (specification `LLUI_DISPLAY_setDrawingLimits()` has changed).

## [1.0.8] - 2022-05-13

- Compatible with MicroEJ UI Pack 13.0.x.

### Fixed

- Fix the use of returned code when drawing images with the DMA2D.
- Clean cache before each DMA2D transfer (no-op on STM32 CPU without cache).

## [1.0.7] - 2022-04-28

- Compatible with MicroEJ UI Pack 13.0.x.

### Fixed

- Fix the license and copyrights: use BSD License.
- Fix Misra rules.

## [1.0.6] - 2020-12-08

- Compatible with MicroEJ UI Pack 13.0.x.

### Fixed

- Fix missing license file.

## [1.0.5] - 2020-09-23

- Compatible with MicroEJ UI Pack 13.0.x.

### Fixed

- De-init the DMA2D before re-initializing it, to reset the context at HAL level.
- Manipulate drawing limits after being sure the DMA2D is finished.

## [1.0.4] - 2020-09-15

- Compatible with MicroEJ UI Pack 13.0.x.

### Fixed

- Draw an image on same image is not supported by DMA2D when destination region overlaps source region.

## [1.0.3] - 2020-09-02

- Compatible with MicroEJ UI Pack 13.0.x.

### Fixed

- Fix artifact organization

## [1.0.2] - 2020-07-28

- Compatible with MicroEJ UI Pack 13.0.x.

### Fixed

- Fix file names
- Remove/replace notion of `LLDISPLAY`

## [1.0.1] - 2020-04-24

- Compatible with MicroEJ UI Pack 13.0.x.

### Fixed

- Fix UI3 function names

## [1.0.0] - 2020-04-09

- Compatible with MicroEJ UI Pack 13.0.x.

### Added

- Initial revision.
- Implements `LLDISPLAY_EXTRA_IMPL_doFillRect()` and `LLDISPLAY_EXTRA_IMPL_drawImage()`.
- Supported image formats: ARGB8888, RGB888, ARGB1555, ARGB4444, RGB565, A8 and A4.
- Features a function to perform a memory copy between two pixels buffers (useful after a flush).
- Requires defines `LLDISPLAY_BPP` and `STM32F4XX` or `STM32F7XX` (see `lldisplay_dma2d.h`)


---
_Copyright 2019-2026 MicroEJ Corp._\
_Use of this source code is governed by a BSD-style license that can be found with this software._\
_Build: 7E4D1F7C_
