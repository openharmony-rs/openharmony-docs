# effectKit

## Overview

Provides basic image processing capabilities, including brightness adjustment, blurring, and grayscale conversion of the current image. It is suitable for scenarios where image filter effects need to be quickly implemented within an app, such as image editing, photo beautification, and camera filters. This helps developers quickly implement image effect processing without focusing on the underlying algorithm implementation, reducing development complexity.

**Since**: 12

## Files

| Name | Description |
| -- | -- |
| [effect_types.h](capi-effect-types-h.md) | Declares the data types for filter effects, used to define the matrices, status codes, and tile modes for filter effects, and supports scenarios such as creating custom filter effects and processing image shader tiling. |
| [effect_filter.h](capi-effect-filter-h.md) | Declares the APIs for filter effects. It supports creating and managing various filter effects, including frosted glass blur, brightness adjustment, grayscale conversion, and color inversion. It also supports implementing rich image processing effects through custom matrices, applicable to scenarios such as image editing, photo beautification, and visual effects.<br> You must call {@link OH_Filter_CreateEffect} and {@link OH_Filter_Release} in pairs to ensure that resources are properly released. None of the APIs in this file support multi-threaded calls. |
