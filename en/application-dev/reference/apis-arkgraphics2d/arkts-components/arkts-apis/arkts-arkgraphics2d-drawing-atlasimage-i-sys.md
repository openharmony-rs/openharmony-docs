# AtlasImage (System API)

```TypeScript
interface AtlasImage
```

Defines the atlas frame parameters for sprite sheet frame animation.

**Since:** 26.0.1

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## atlasImage

```TypeScript
atlasImage: image.PixelMap
```

Sprite sheet atlas image. Created through the image module as a PixelMap instance.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## cols

```TypeScript
cols: number
```

Number of columns in the sprite sheet atlas. The value range is [1, totalFrame]; out-of-range values will be clamped internally.

> **NOTE:** 
> 
> cols * (frameWidth + 2 * padding) must not exceed the atlas image width.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## frameHeight

```TypeScript
frameHeight: number
```

Height of a single frame in pixels. The value range is [1, 8192]; out-of-range values will be clamped internally.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## frameIndex

```TypeScript
frameIndex: number
```

Current frame index in the atlas. The value range is [0, totalFrame - 1]; out-of-range values will be clamped internally.

> **NOTE:** 
> 
> This field is animated by [animateTo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#animateto)

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## frameWidth

```TypeScript
frameWidth: number
```

Width of a single frame in pixels. The value range is [1, 8192]; out-of-range values will be clamped internally.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## mode

```TypeScript
mode: AtlasInterpolationMode
```

Interpolation mode for frame animation. NONE (0): no interpolation; each frame is displayed independently. FRAME_BLEND (1): frame interpolation; smooth transition between adjacent frames.

**Type:** [AtlasInterpolationMode](arkts-arkgraphics2d-drawing-atlasinterpolationmode-e-sys.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## padding

```TypeScript
padding: number
```

Padding between frames in pixels, used to prevent texture bleeding at frame boundaries. The value range is [0, 64]; out-of-range values will be clamped internally.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## rows

```TypeScript
rows: number
```

Number of rows in the sprite sheet atlas. The value range is [1, totalFrame]; out-of-range values will be clamped internally.

> **NOTE:** 
> 
> rows * (frameHeight + 2 * padding) must not exceed the atlas image height.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## totalFrame

```TypeScript
totalFrame: number
```

Total number of frames in the atlas. The value range is [1, rows * cols]; out-of-range values will be clamped internally.

> **NOTE:** 
> 
> Must not exceed rows * cols.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.
