# Overview

MicroEJ C Component: `com.microej.clibrary.llimpl#display-dma2d`.

This component implements some Low-Level API (LLAPI) of MicroUI-3.x over the STM32 DMA2D (Chrom-ART Graphics Accelerator). 
Refer to the VEE Porting Guide > Graphics User Interface > C Module to have more information on this module.

# UI Pack Compatibility

This compoment is MicroEJ UI Pack dependent: it is compatible with one or several MicroEJ UI Pack versions, listed in the [C Module compatibility](https://docs.microej.com/en/latest/VEEPortingGuide/uiReleaseNotes.html#extended-c-modules) tables in the documentation.

> Note: this component is useless (and not compatible) for the MicroEJ UI Packs before version 13.0.0.

# Usage

1. Add the following line to your `module.ivy`:

    <dependency org="com.microej.clibrary.llimpl" name="microui-dma2d" rev="7.0.1"/>

2. Follow the **Usage** chapters of each component part (see VEE Porting Guide > Graphics User Interface > C Module)

# Migration Guide

The migration guides are described in the VEE Porting Guide > Graphical User Interface > Migration Guide. 

# Requirements

N/A.

# Dependencies

_All dependencies are retrieved transitively by MicroEJ Module Manager_.

# Source

N/A.

# Restrictions

None.

---
_Copyright 2019-2024 MicroEJ Corp. All rights reserved._\
_Use of this source code is governed by a BSD-style license that can be found with this software._
