# SourceOptions

Defines image source initialization options.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## sourceDensity

```TypeScript
sourceDensity: number
```

Pixel density of the image resource, in ppi.

If **desiredSize** is not set in [DecodingOptions](arkts-image-image-decodingoptions-i.md) and **SourceOptions.sourceDensity** and **DecodingOptions.fitDensity** are not 0, the PixelMap output after decoding will be scaled.

The formula for calculating the width after scaling is as follows (the same applies to the height): (width * fitDensity + (sourceDensity &gt;  
> 1)) / sourceDensity.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## sourcePixelFormat

```TypeScript
sourcePixelFormat?: PixelMapFormat
```

Image pixel format. The default value is **UNKNOWN**.

**Type:** [PixelMapFormat](arkts-image-image-pixelmapformat-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## sourceSize

```TypeScript
sourceSize?: Size
```

Image pixel size. The default value is null.

**Type:** Size

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core
