# GifMetadata

Gif metadata.

**Since:** 26.0.0

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## canvasHeight

```TypeScript
readonly canvasHeight?: number
```

Canvas height. Unit: px, The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## canvasWidth

```TypeScript
readonly canvasWidth?: number
```

Canvas width. Unit: px, The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## delayTime

```TypeScript
readonly delayTime?: number
```

Delay of each frame in milliseconds. Unit: ms, The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## disposalType

```TypeScript
readonly disposalType?: number
```

Disposal type of each frame in the image. 0 - No disposal specified. 1 - Do not dispose. 2 - Restore to background color. 3 - Restore to previous. The value range is all integers.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## hasGlobalColorMap

```TypeScript
readonly hasGlobalColorMap?: boolean
```

whether the GIF image has a global color map.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## loopCount

```TypeScript
readonly loopCount?: number
```

Loop count. The value range is all integers.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## unclampedDelayTime

```TypeScript
readonly unclampedDelayTime?: number
```

Unclamped delay of each frame in milliseconds. Unit: ms, The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core
