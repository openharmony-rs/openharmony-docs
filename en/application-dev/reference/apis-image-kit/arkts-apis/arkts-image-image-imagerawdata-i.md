# ImageRawData

```TypeScript
interface ImageRawData
```

Describes raw data in an image.

**Since:** 24

<!--Device-image-interface ImageRawData--><!--Device-image-interface ImageRawData-End-->

**System capability:** SystemCapability.Multimedia.Image.ImageSource

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## bitsPerPixel

```TypeScript
bitsPerPixel: number
```

Number of bits that each pixel actually occupies in the buffer data.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-ImageRawData-bitsPerPixel: int--><!--Device-ImageRawData-bitsPerPixel: int-End-->

**System capability:** SystemCapability.Multimedia.Image.ImageSource

## buffer

```TypeScript
buffer: ArrayBuffer
```

Binary data of the raw image.

**Type:** ArrayBuffer

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-ImageRawData-buffer: ArrayBuffer--><!--Device-ImageRawData-buffer: ArrayBuffer-End-->

**System capability:** SystemCapability.Multimedia.Image.ImageSource
