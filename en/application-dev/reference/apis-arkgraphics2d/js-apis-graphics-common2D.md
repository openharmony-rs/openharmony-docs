# @ohos.graphics.common2D (Common Data Types of 2D Graphics)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=4e50217bab17d31bea74ffd285654969c1ffbf06 translatedAt=2026-08-24T09:21:40.390Z pushedAt=2026-08-31T12:03:42.238Z -->

This module defines some common data types in the 2D graphics field, including color, rectangular area, and coordinate point, which are applicable to scenarios such as 2D graphics drawing. It provides developers with common graphics data structures to facilitate graphics computation and rendering operations.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This module uses the physical pixel unit, px.

## Modules to Import

```ts
import { common2D } from '@kit.ArkGraphics2D';
```

## Color

Describes a color in ARGB format.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

| Name | Type  | Read-Only| Optional| Description                                    |
| ----- | ------ | ---- | ---- | ---------------------------------------- |
| alpha | number | No  | No  | Alpha component of the color. The value is an integer ranging from 0 to 255.|
| red   | number | No  | No  | Red component of the color. The value is an integer ranging from 0 to 255.|
| green | number | No  | No  | Green component of the color. The value is an integer ranging from 0 to 255.|
| blue  | number | No  | No  | Blue component of the color. The value is an integer ranging from 0 to 255.|

## Rect

Defines a rectangular area by two coordinate points: the upper-left corner point and the lower-right corner point.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

| Name  | Type  | Read-Only| Optional| Description                          |
| ------ | ------ | ---- | ---- | ------------------------------ |
| left   | number | No   | No   | X-coordinate of the upper left corner of the rectangular area, a floating-point number. The unit is physical pixel px. |
| top    | number | No   | No   | Y-coordinate of the upper left corner of the rectangular area, a floating-point number. The unit is physical pixel px. |
| right  | number | No   | No   | X-coordinate of the lower right corner of the rectangular area, a floating-point number. The unit is physical pixel px. |
| bottom | number | No   | No   | Y-coordinate of the lower right corner of the rectangular area, a floating-point number. The unit is physical pixel px. |

## Point<sup>12+</sup>

Describes a coordinate point.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

| Name  | Type  | Read-Only| Optional| Description                          |
| ------ | ------ | ---- | ---- | ------------------------------ |
| x      | number | No   | No   | Horizontal coordinate, which is a floating-point value in physical pixels (px).               |
| y      | number | No   | No   | Vertical coordinate, which is a floating-point value in physical pixels (px).               |

## Color4f<sup>20+</sup>

Describes a color in ARGB format, where each color component is a floating-point number ranging from 0.0 to 1.0.

**System capability**: SystemCapability.Graphics.Drawing

| Name | Type  | Read-Only| Optional| Description                                    |
| ----- | ------ | ---- | ---- | ---------------------------------------- |
| alpha | number | No  | No  | Alpha component of the color. The value is a floating point number ranging from 0.0 to 1.0.|
| red   | number | No  | No  | Red component of the color. The value is a floating point number ranging from 0.0 to 1.0.|
| green | number | No  | No  | Green component of the color. The value is a floating point number ranging from 0.0 to 1.0.|
| blue  | number | No  | No  | Blue component of the color. The value is a floating point number ranging from 0.0 to 1.0.|

## Point3d<sup>12+</sup>

Describes a 3D coordinate point. It inherits from [Point](#point12).

**System capability**: SystemCapability.Graphics.Drawing

| Name  | Type  | Read-Only| Optional| Description                          |
| ------ | ------ | ---- | ---- | ------------------------------ |
| z      | number | No   | No   | z-coordinate, a floating-point number. The unit is physical pixel px.               |