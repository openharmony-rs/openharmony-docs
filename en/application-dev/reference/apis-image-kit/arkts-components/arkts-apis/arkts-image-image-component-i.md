# Component

```TypeScript
interface Component
```

Describes the color components of an image.

**Since:** 9

<!--Device-image-interface Component--><!--Device-image-interface Component-End-->

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

<!--Device-Component-readonly byteBuffer: ArrayBuffer--><!--Device-Component-readonly byteBuffer: ArrayBuffer-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

## componentType

```TypeScript
readonly componentType: ComponentType
```

Color component type.

**Type:** [ComponentType](arkts-image-image-componenttype-e.md)

**Since:** 9

<!--Device-Component-readonly componentType: ComponentType--><!--Device-Component-readonly componentType: ComponentType-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

## pixelStride

```TypeScript
readonly pixelStride: number
```

Pixel stride.

**Type:** number

**Since:** 9

<!--Device-Component-readonly pixelStride: int--><!--Device-Component-readonly pixelStride: int-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

## rowStride

```TypeScript
readonly rowStride: number
```

Row stride. The camera preview stream data needs to be read by stride. For details, see [Solution to Screen Artifacts During Camera Preview](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-deal-stride-solution).

**Type:** number

**Since:** 9

<!--Device-Component-readonly rowStride: int--><!--Device-Component-readonly rowStride: int-End-->

**System capability:** SystemCapability.Multimedia.Image.Core
