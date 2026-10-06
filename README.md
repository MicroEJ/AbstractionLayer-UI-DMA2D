![ARCH](https://shields.microej.com/endpoint?url=https://repository.microej.com/packages/badges/arch_7.16.json)

# Overview

This Abstraction Layer implements a part of the drawings of the MicroUI Low Level API, described in [LLUI_DISPLAY: Display](https://docs.microej.com/en/latest/VEEPortingGuide/appendix/llapi.html#llui-display-display), over the STM32 DMA2D (Chrom-ART Graphics Accelerator).
It provides the drawing functions of `ui_drawing.h` that the DMA2D can perform: the rectangle filling and the image drawings.
When the DMA2D cannot perform a drawing, the software drawing of the Graphics Engine performs it.
See the [MicroUI Over DMA2D](https://docs.microej.com/en/latest/VEEPortingGuide/uiCco.html#section-ui-c-module-microui-dma2d) section of the MicroEJ documentation.

This Abstraction Layer is tied to the MicroEJ UI Pack: the versions it is compatible with are listed in the [compatibility](https://docs.microej.com/en/latest/VEEPortingGuide/uiReleaseNotes.html#section-ui-releasenotes-cmodule-extended) tables of the documentation.
The badge above gives the oldest MicroEJ Architecture it supports, not the latest one: the [MicroEJ Architecture Compatibility Version](https://docs.microej.com/en/latest/VEEPortingGuide/uiReleaseNotes.html#microej-architecture-compatibility-version) tables list the Architectures of each UI Pack version.

# Usage

1. Add the sources of this Abstraction Layer to the BSP of the VEE Port, in either of these two ways:

   - From the MicroEJ repository: install the `.cco` archive of the version the VEE Port needs, as the [installation guide](https://docs.microej.com/en/latest/VEEPortingGuide/appendix/cmodules.html) describes.
     The headers land in `bsp/vee/port/ui_dma2d/inc` and the sources in `bsp/vee/port/ui_dma2d/src`.
   - From GitHub: add the [GitHub repository](https://github.com/MicroEJ/AbstractionLayer-UI-DMA2D) to the BSP of the VEE Port as a git submodule, at the tag of the version the VEE Port needs.
     The VEE Port chooses the folder of the submodule, and either of these two layouts works.
     A flat folder sits beside the other components of the BSP:

     ```sh
     git submodule add https://github.com/MicroEJ/AbstractionLayer-UI-DMA2D.git bsp/vee/port/ui_dma2d
     git -C bsp/vee/port/ui_dma2d checkout <version>
     ```

     A folder grouped by domain sits under the folder of the other components of the same domain:

     ```sh
     git submodule add https://github.com/MicroEJ/AbstractionLayer-UI-DMA2D.git bsp/vee/port/ui/UI-DMA2D
     git -C bsp/vee/port/ui/UI-DMA2D checkout <version>
     ```

     The headers then sit in `<folder>/src/main/c/inc` and the sources in `<folder>/src/main/c/src`, where `<folder>` is the folder of the submodule.
     A copy of these sources in the VEE Port repository works as well.

   Then add the folder of the headers to the include paths of the BSP project, and the files of the folder of the sources to its sources.

2. The configuration file [ui_dma2d_configuration.h](src/main/c/inc/ui_dma2d_configuration.h) stores the default values of the Abstraction Layer options.
   To change an option, define it in the file `veeport_configuration.h` of the VEE Port, which `ui_dma2d_configuration.h` includes first through `ui_configuration.h`.

3. When the VEE Port moves to another version of this Abstraction Layer, follow the [MicroUI migration guide](https://docs.microej.com/en/latest/VEEPortingGuide/uiMigrationGuide.html).

# Requirements

None.

# Validation

This Abstraction Layer is tested on the following boards:

- STM32F429I-EVAL, with the STM32F4xx HAL driver 1.7.12.

# MISRA Compliance

This Abstraction Layer is MISRA-compliant (MISRA C:2012) with some noted exceptions.
It has been verified with Cppcheck v2.13.
Here is the list of deviations from the MISRA standard:

| Deviation  | Category  | Justification                                                                                          |
|:----------:|:---------:|:------------------------------------------------------------------------------------------------------ |
| Rule 2.5   | Advisory  | A macro can be defined at API level and not used by the application.                                   |
| Rule 8.4   | Required  | The compatible declarations are the UI Pack's functions.                                               |
| Rule 8.7   | Advisory  | The LLAPI functions require external linkage, but cppcheck cannot detect their invocation by the Pack. |
| Rule 11.4  | Advisory  | The DMA2D driver functions of the STM32 HAL take the source and destination addresses as `uint32_t`.   |
| Rule 18.4  | Advisory  | Adding an offset to a buffer address is required to target a pixel.                                    |

# Dependencies

- The MicroUI Abstraction Layer.
- The STM32 HAL of the MCU: STM32F4, STM32F7 or STM32H7.

# Changelog

The changes of this Abstraction Layer are listed in the [public changelog of the MicroEJ UI Pack](https://docs.microej.com/en/latest/VEEPortingGuide/uiChangeLog.html), section `C Module DMA2D`.

# Source

- `ui_dma2d_configuration.h`: the options of the Abstraction Layer.
- `ui_drawing_dma2d.h`, `ui_drawing_dma2d.c`: the drawing functions of `ui_drawing.h` over the DMA2D.

# Restrictions

None.

---
_Copyright 2019-2026 MicroEJ Corp._\
_Use of this source code is governed by a BSD-style license that can be found with this software._\
_Build: 7E4D1F7C_
