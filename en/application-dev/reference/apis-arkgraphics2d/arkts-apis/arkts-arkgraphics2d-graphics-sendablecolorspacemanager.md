# @ohos.graphics.sendableColorSpaceManager(Sendable Color Space Management)

This module provides APIs for creating and managing sendable color space objects and obtaining basic attributes of sendable color spaces. It is applicable to scenarios where color space information needs to be transferred between multiple threads. It solves the problem that color management objects cannot be shared across threads, improving the efficiency and consistency of color processing.

**Since:** 12

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## Modules to Import

```TypeScript
import { sendableColorSpaceManager } from '@kit.ArkGraphics2D';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [create](arkts-arkgraphics2d-sendablecolorspacemanager-create-f.md) | Creates a criterion color space management instance that is sendable. |
| [create](arkts-arkgraphics2d-sendablecolorspacemanager-create-f.md) | Creates a custom color space object that is sendable. |

### Interfaces

| Name | Description |
| --- | --- |
| [ColorSpaceManager](arkts-arkgraphics2d-sendablecolorspacemanager-colorspacemanager-i.md) | Implements management of color space objects. ColorSpaceManager is a core class used to manage and operate color space objects. It provides functions such as obtaining the color space type, white point value, and gamma value, and supports transfer between concurrent ArkTS instances. |

### Types

| Name | Description |
| --- | --- |
| [ISendable](arkts-arkgraphics2d-sendablecolorspacemanager-isendable-t.md) | The ISendable type alias is defined to align with the API specifications of the current module. |
