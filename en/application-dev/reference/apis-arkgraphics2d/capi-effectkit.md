# effectKit

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanamaru-->
<!--Designer: @chensiyi_CE-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=244626bd3ee350522bab6ea45e122f80881abd5e translatedAt=2026-07-13T11:26:26.921Z pushedAt=2026-07-15T10:18:57.311Z -->

## Overview

Provides basic image processing capabilities, including brightness adjustment, blurring, and grayscale conversion of the current image. It is suitable for scenarios where image filter effects need to be quickly implemented within an app, such as image editing, photo beautification, and camera filters. This helps developers quickly implement image effect processing without focusing on the underlying algorithm implementation, reducing development complexity.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

## Files

| Name| Description|
| -- | -- |
| [effect_filter.h](capi-effect-filter-h.md) | Declares the APIs for filter effects. Supports creating and managing various filter effects, including frosted glass blur, brightness adjustment, grayscale conversion, and color inversion. It also supports implementing rich image processing effects through custom matrices, suitable for scenarios such as image editing, photo beautification, and visual effects. |
| [effect_types.h](capi-effect-types-h.md) | Declares the data types for filter effects, used to define matrices, status codes, and tile modes for filter effects. It supports scenarios such as creating custom filter effects and processing image shader tiling. |