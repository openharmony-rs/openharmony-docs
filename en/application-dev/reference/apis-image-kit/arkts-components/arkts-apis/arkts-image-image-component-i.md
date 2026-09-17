# Component

Describes the color components of an image.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## byteBuffer

```TypeScript
readonly byteBuffer: ArrayBuffer
```

Component buffer.

**Type:** ArrayBuffer

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.Core

## componentType

```TypeScript
readonly componentType: ComponentType
```

Color component type.

**Type:** [ComponentType](arkts-image-image-componenttype-e.md)

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.Core

## pixelStride

```TypeScript
readonly pixelStride: number
```

Pixel stride.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.Core

## rowStride

```TypeScript
readonly rowStride: number
```

Row stride. The camera preview stream data needs to be read by stride. For details, see [Solution to Screen Artifacts During Camera Preview](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-deal-stride-solution).

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.Core
