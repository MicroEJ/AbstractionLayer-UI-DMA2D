
# Overview

MicroEJ C Component: `com.microej.clibrary.llimpl#display-dma2d`.

This component implements some Low-Level API (LLAPI) of MicroUI-3.x over the STM32 DMA2D (Chrom-ART Graphics Accelerator). 
Refer to the VEE Porting Guide > Graphics User Interface > C Module to have more information on this module.

## UI Pack Compatibility

This compoment is MicroEJ UI Pack dependent: it is compatible with one or several MicroEJ UI Pack versions. The following table illustrates the compatibility:

| Component     | MicroEJ UI Pack   |
| ------------- | ----------------- |
| 5.0.0         | [14.0.0 - 15.0.0[ | 
| [4.1.0-4.1.1] | [13.7.0 - 14.0.0[ |
| 4.0.0         | [13.5.0 - 13.7.0[ |
| [3.0.0-3.1.0] | [13.3.0 - 13.5.0[ |
| [2.0.0-2.1.0] | [13.1.0 - 13.2.0[ |
| [1.0.0-1.0.8] | [13.0.0 - 14.0.0[ |

> Note: this component is useless (and not compatible) for the MicroEJ UI Packs before version 13.0.0.

# Usage

1. Add the following line to your `module.ivy`:

    <dependency org="com.microej.clibrary.llimpl" name="microui-dma2d" rev="6.0.0"/>

2. Follow the **Usage** chapters of each component part (see VEE Porting Guide > Graphics User Interface > C Module)

# Migration Guide

The migration guides are described in the VEE Porting Guide > Graphical User Interface > Migration Guide. 

# Requirements

N/A

# Dependencies

_All dependencies are retrieved transitively by MicroEJ Module Manager_.

# Source

N/A

# Restrictions

None.

---
_Copyright 2019-2024 MicroEJ Corp. All rights reserved._  
_Use of this source code is governed by a BSD-style license that can be found with this software._  
