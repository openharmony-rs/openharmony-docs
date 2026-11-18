# @ohos.graphics.drawing (Drawing Module) (System API)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=216da4264a1ebd8da1fd36c0d74d45c6a0b2968c translatedAt=2026-11-03T13:32:24.839Z pushedAt=2026-11-04T06:40:25.380Z nl=1 -->

The Drawing module provides basic graphics drawing capabilities, including drawing rectangles, circles, points, lines, custom paths, and fonts. This page contains only the system APIs of this module.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs in later versions are marked with a superscript to indicate their starting version.
> - This page contains only the system APIs of this module. For other public APIs, see [@ohos.graphics.drawing (Drawing Module)](arkts-apis-graphics-drawing.md).
> - This module uses the physical pixel unit px of the screen.
> - This module follows a single-thread model policy, and the caller is responsible for managing thread safety and context state switching.

## Modules to Import

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## AtlasInterpolationMode

Enumerates the interpolation modes for the sequence frame animation of a sprite atlas ([Sprite Sheet](../../graphics/graphic-term.md#sprite-sheet)).

**Since:** 26.0.1

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Graphics.Drawing

| Name        | Value | Description                                                         |
| ----------- | ---- | ------------------------------------------------------------ |
| NONE        | 0    | No interpolation. Each frame is displayed independently. |
| FRAME_BLEND | 1    | Inter-frame interpolation. Smooth transition is performed between adjacent frames. |

## AtlasImage

Defines the atlas frame parameters for the sequence frame animation of a sprite atlas ([Sprite Sheet](../../graphics/graphic-term.md#sprite-sheet)).

**Since:** 26.0.1

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Graphics.Drawing

| Name        | Type   | Read-only | Optional | Description   |
| ----------- | ------ | ---- | ---- | ------ |
| atlasImage  | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | No   | No   | Sprite atlas image.|
| rows        | number | No   | No   | Number of rows in the sprite atlas. Value range: [1, totalFrame]. Out of range values are truncated internally.<br>rows * (frameHeight + 2 * padding) must not exceed the height of the atlas image.|
| cols        | number | No   | No   | Number of columns in the sprite atlas. Value range: [1, totalFrame]. Out of range values are truncated internally.<br>cols * (frameWidth + 2 * padding) must not exceed the width of the atlas image.|
| frameWidth  | number | No   | No   | Width of a single frame. Unit: px. Value range: [1, 8192]. Out of range values are truncated internally.|
| frameHeight | number | No   | No   | Height of a single frame. Unit: px. Value range: [1, 8192]. Out of range values are truncated internally.|
| padding     | number | No   | No   | Spacing between frames. Unit: px. Used to prevent texture bleeding at frame boundaries. Value range: [0, 64]. Out of range values are truncated internally.|
| frameIndex  | number | No   | No   | Index of the current frame in the atlas. Value range: [0, totalFrame - 1]. Out of range values are truncated internally.<br>This field can be driven by animation through [animateTo](../apis-arkui/arkts-apis-uicontext-uicontext.md#animateto).|
| totalFrame  | number | No   | No   | Total number of frames in the atlas. Value range: [1, rows * cols]. Out of range values are truncated internally.|
| mode        | [drawing.AtlasInterpolationMode](#atlasinterpolationmode) | No   | No   | Interpolation mode of the frame animation.|
