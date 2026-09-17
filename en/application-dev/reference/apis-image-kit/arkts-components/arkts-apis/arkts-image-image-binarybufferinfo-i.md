# BinaryBufferInfo

Describes binary buffer info.

**Since:** 26.0.0

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## bytesPerRow

```TypeScript
bytesPerRow?: number
```

Bytes per row.If it is not specified, it will be calculated as (width + 7) / 8. The value range is all integers.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## data

```TypeScript
data: ArrayBuffer
```

Describes binary buffer.

**Type:** ArrayBuffer

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## size

```TypeScript
size: Size
```

Describes binary buffer size.

**Type:** Size

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.ImagePacker
