
# Overview

## Aim

This CCO uses the STM32 DMA2D
- to fill rectangles (see `ui_drawing.h`, function `UI_DRAWING_fillRectangle`),
- to draw some images (see `ui_drawing.h`, function `UI_DRAWING_drawImage`),
- to copy the content of a buffer to another buffer.

## UI Pack Compatibility

It is compatible with the UI-pack [13.1.0-14.0.0[.

## Images Compatibility

The DMA2D is used to render the images in RAW formats:
- RGB565
- RGB888
- ARGB8888
- ARGB4444
- ARGB1555
- A4 (1)
- A8

> (1) The first and last odd columns are drawn in software (GPU memory alignment constraints).

## Copy Buffer

The functions `DRAWING_DMA2D_configure_memcpy()` and `DRAWING_DMA2D_start_memcpy()` can be used to copy the content of a frame buffer to another frame buffer. See chapter Usage.

# Usage

## Declaration

Add the following line to your `module.ivy`:

    <dependency org="com.microej.clibrary.llimpl" name="display-dma2d" rev="3.0.2"/>
    
## Initialization

The function `DRAWING_DMA2D_initialize()` must be called from the implementation of `LLUI_DISPLAY_IMPL_initialize()` (during MicroUI startup).
    
## Drawings
    
The functions `UI_DRAWING_drawImage()` and `UI_DRAWING_fillRectangle()` are automatically called to fill the rectangles and to draw some images (for more details, see Platform Developer Guide, chapter Graphical User Interface).

## Flush

To use the DMA2D to copy the content of a frame buffer to another frame buffer, 
- the function `DRAWING_DMA2D_configure_memcpy()` must be called from the implementation of `LLUI_DISPLAY_IMPL_flush()`,
- the function `DRAWING_DMA2D_start_memcpy()` must be call from the LCD controller IRQ routine,
- the function `DRAWING_DMA2D_IRQHandler` must be call from the DMA2D IRQ routine.

Example of implementation:

```c
uint8_t* LLUI_DISPLAY_IMPL_flush(MICROUI_GraphicsContext* gc, uint8_t* srcAddr, uint32_t xmin, uint32_t ymin, uint32_t xmax, uint32_t ymax) {
	uint8_t* destAddr = (srcAddr == (uint8_t*)BACK_BUFFER) ? (uint8_t*)FRAME_BUFFER : (uint8_t*)BACK_BUFFER;
	HAL_LTDC_SetAddress(&hLtdcHandler, (uint32_t)srcAddr, LTDC_ACTIVE_LAYER);
	DRAWING_DMA2D_configure_memcpy(srcAddr, destAddr, xmin, ymin, xmax, ymax, RK043FN48H_WIDTH, &dma2d_memcpy);
	lcd_enable_interrupt();
	return destAddr;
}

void DMA2D_IRQHandler(void) {
	DRAWING_DMA2D_IRQHandler();
}

void HAL_LTDC_ReloadEventCallback(LTDC_HandleTypeDef *hltdc) {
	// LTDC register reload
	__HAL_LTDC_ENABLE_IT(hltdc, LTDC_IT_RR);

	// launch the copy from backbuffer to lcd buffer
	DRAWING_DMA2D_start_memcpy(&dma2d_memcpy);
}

```

## Cache

Some STM32 CPU use a cache. 

This cache must be cleared before using the DMA2D: 
- before the call to `HAL_DMA2D_Start_IT()` (2 iterations),
- before the call to `HAL_DMA2D_BlendingStart_IT()`.

> For the STM32 CPU without cache, this call has no effect. 

# Requirements

N/A

# Dependencies

_All dependencies are retrieved transitively by MicroEJ Module Manager_.

# Source

N/A

# Restrictions

None.

---
_Copyright 2019-2022 MicroEJ Corp. All rights reserved._  
_Use of this source code is governed by a BSD-style license that can be found with this software._
