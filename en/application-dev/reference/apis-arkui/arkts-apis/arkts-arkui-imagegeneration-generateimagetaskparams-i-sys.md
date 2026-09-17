# GenerateImageTaskParams (System API)

Configuration parameter options for AI-generated image tasks.

@interface GenerateImageTaskParams

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## imageCount

```TypeScript
imageCount?: number
```

the number of AI-generated image in one task.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## images

```TypeScript
images: Array<ImageItem>
```

image information used for AI-generated image tasks.

**Type:** Array&lt;[ImageItem](arkts-arkui-imagegeneration-imageitem-i-sys.md)&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## imageSize

```TypeScript
imageSize: image.Size
```

the size information of AI-generated image in one task.

**Type:** [image.Size](../../apis-image-kit/arkts-apis/arkts-image-image-size-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## positionImage

```TypeScript
positionImage?: image.PixelMap
```

Location reference map for multi-image generated tasks.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## prompt

```TypeScript
prompt: string
```

Description information for AI-generated image tasks.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## selectPath

```TypeScript
selectPath?: Array<common2D.Point>
```

Path information for lasso selection in AI-generated image tasks.

**Type:** Array&lt;[common2D.Point](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-common2d-point-i.md)&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## style

```TypeScript
style?: string
```

the style of AI-generated image in one task.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
