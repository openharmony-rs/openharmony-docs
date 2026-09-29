# TaskStatistic (System API)

```TypeScript
interface TaskStatistic
```

Statistics Related to AI Image Generation Tasks.

@interface TaskStatistic

**Since:** 23

<!--Device-imageGeneration-interface TaskStatistic--><!--Device-imageGeneration-interface TaskStatistic-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## generationTime

```TypeScript
generationTime: number
```

Time taken for AI image generation task in seconds.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-TaskStatistic-generationTime: double--><!--Device-TaskStatistic-generationTime: double-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## imageCount

```TypeScript
imageCount: number
```

Number of images used for AI image generation tasks.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-TaskStatistic-imageCount: int--><!--Device-TaskStatistic-imageCount: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## isSticker

```TypeScript
isSticker: boolean
```

Whether the image AI generation task is a sticker generation task.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-TaskStatistic-isSticker: boolean--><!--Device-TaskStatistic-isSticker: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## style

```TypeScript
style: string
```

The style used in AI image generation tasks.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-TaskStatistic-style: string--><!--Device-TaskStatistic-style: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
