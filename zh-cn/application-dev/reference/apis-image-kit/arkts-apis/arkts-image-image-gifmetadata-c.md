# GifMetadata

Gif metadata.

**起始版本：** 26.0.0

<!--Device-image-class GifMetadata--><!--Device-image-class GifMetadata-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## canvasHeight

```TypeScript
readonly canvasHeight?: number
```

Canvas height.Unit: px, The value should be an integer.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GifMetadata-readonly canvasHeight?: int--><!--Device-GifMetadata-readonly canvasHeight?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## canvasWidth

```TypeScript
readonly canvasWidth?: number
```

Canvas width.Unit: px, The value should be an integer.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GifMetadata-readonly canvasWidth?: int--><!--Device-GifMetadata-readonly canvasWidth?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## delayTime

```TypeScript
readonly delayTime?: number
```

Delay of each frame in milliseconds.Unit: ms, The value should be an integer.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GifMetadata-readonly delayTime?: int--><!--Device-GifMetadata-readonly delayTime?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## disposalType

```TypeScript
readonly disposalType?: number
```

Disposal type of each frame in the image.0 - No disposal specified.1 - Do not dispose.2 - Restore to background color.3 - Restore to previous.The value range is all integers.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GifMetadata-readonly disposalType?: int--><!--Device-GifMetadata-readonly disposalType?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## hasGlobalColorMap

```TypeScript
readonly hasGlobalColorMap?: boolean
```

whether the GIF image has a global color map.

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GifMetadata-readonly hasGlobalColorMap?: boolean--><!--Device-GifMetadata-readonly hasGlobalColorMap?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## loopCount

```TypeScript
readonly loopCount?: number
```

Loop count.The value range is all integers.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GifMetadata-readonly loopCount?: int--><!--Device-GifMetadata-readonly loopCount?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## unclampedDelayTime

```TypeScript
readonly unclampedDelayTime?: number
```

Unclamped delay of each frame in milliseconds.Unit: ms, The value should be an integer.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GifMetadata-readonly unclampedDelayTime?: int--><!--Device-GifMetadata-readonly unclampedDelayTime?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

