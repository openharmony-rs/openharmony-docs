# PositionArea

```TypeScript
interface PositionArea
```

Describes area information in an image.

**Since:** 7

<!--Device-image-interface PositionArea--><!--Device-image-interface PositionArea-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## offset

```TypeScript
offset: number
```

Offset for data reading, in bytes.

**Type:** number

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 12.

<!--Device-PositionArea-offset: int--><!--Device-PositionArea-offset: int-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

## pixels

```TypeScript
pixels: ArrayBuffer
```

Pixels of the image. Only pixel data in BGRA_8888 format is supported.

**Type:** ArrayBuffer

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 12.

<!--Device-PositionArea-pixels: ArrayBuffer--><!--Device-PositionArea-pixels: ArrayBuffer-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

## region

```TypeScript
region: Region
```

Region to read or write. The width of the region to write plus the X coordinate cannot be greater than the width of the original image. The height of the region to write plus the Y coordinate cannot be greater than the height of the original image.

**Type:** [Region](arkts-image-image-region-i.md)

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 12.

<!--Device-PositionArea-region: Region--><!--Device-PositionArea-region: Region-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

## stride

```TypeScript
stride: number
```

Number of bytes from one row of pixels in memory to the next row of pixels in memory. The value of **stride** must be greater than or equal to the value of **region.size.width** multiplied by 4.

**Type:** number

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 12.

<!--Device-PositionArea-stride: int--><!--Device-PositionArea-stride: int-End-->

**System capability:** SystemCapability.Multimedia.Image.Core
