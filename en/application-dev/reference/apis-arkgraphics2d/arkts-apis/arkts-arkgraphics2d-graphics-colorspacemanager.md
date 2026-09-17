# @ohos.graphics.colorSpaceManager(Color Space Management)

This module provides basic capabilities for managing abstract color space objects, including creating criterion color space objects (such as sRGB, DCI-P3, and BT2020) and custom color space objects, as well as obtaining attributes such as the color space type, white point value, and gamma value. It is suitable for scenarios where color consistency needs to be ensured, such as image processing, video rendering, and cross-device color display. It helps you implement accurate color management and conversion, improving user experience in color display.

**Since:** 9

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## Modules to Import

```TypeScript
import { colorSpaceManager } from '@kit.ArkGraphics2D';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [create](arkts-arkgraphics2d-colorspacemanager-create-f.md) | Creates a standard color space object. |
| [create](arkts-arkgraphics2d-colorspacemanager-create-f.md) | Creates a custom color space object. |

### Interfaces

| Name | Description |
| --- | --- |
| [ColorSpaceManager](arkts-arkgraphics2d-colorspacemanager-colorspacemanager-i.md) | Implements management of color space objects. |
| [ColorSpacePrimaries](arkts-arkgraphics2d-colorspacemanager-colorspaceprimaries-i.md) | The three primary colors (red, green, blue) and white as defined by the color space standard, whose positions in the color space are represented by (x, y) coordinates based on real-world chromaticity. |

### Enums

| Name | Description |
| --- | --- |
| [ColorSpace](arkts-arkgraphics2d-colorspacemanager-colorspace-e.md) | Enumerates the color space types. |
