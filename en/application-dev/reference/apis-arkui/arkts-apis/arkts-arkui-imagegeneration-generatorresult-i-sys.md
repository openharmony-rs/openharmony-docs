# GeneratorResult (System API)

The result of AI-generated images

@interface GeneratorResult

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## image

```TypeScript
image?: image.PixelMap
```

Decoded data of AI-generated images.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## statistic

```TypeScript
statistic: TaskStatistic
```

Statistics of AI-generated image tasks.

**Type:** [TaskStatistic](arkts-arkui-imagegeneration-taskstatistic-i-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## url

```TypeScript
url?: string
```

The path information of AI-generated images.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
