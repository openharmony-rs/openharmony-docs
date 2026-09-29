# PackingOptionsForTiff

```TypeScript
interface PackingOptionsForTiff
```

Describes the options for tiff image packing.

**Since:** 26.0.0

<!--Device-image-interface PackingOptionsForTiff--><!--Device-image-interface PackingOptionsForTiff-End-->

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## compression

```TypeScript
compression?: number
```

Compression algorithm type: 3 (CCITT G3), 4 (CCITT G4), 5 (LZW).  
- For binary image: must be 3 (G3) or 4 (G4), automatically uses 4 (G4).  
- For Y8/RGB_888 format: automatically uses LZW (5), user setting is ignored.  
The value should be an integer, Currently, only 3, 4, and 5 are supported.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PackingOptionsForTiff-compression?: int--><!--Device-PackingOptionsForTiff-compression?: int-End-->

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## orientation

```TypeScript
orientation?: Orientation
```

Image orientation.Default value is TOP_LEFT.

**Type:** [Orientation](arkts-image-image-orientation-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PackingOptionsForTiff-orientation?: Orientation--><!--Device-PackingOptionsForTiff-orientation?: Orientation-End-->

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## resolutionUnit

```TypeScript
resolutionUnit?: number
```

Resolution unit: 1 (No unit), 2 (Inch), 3 (Centimeter). Currently, only 1, 2, and 3 are supported.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PackingOptionsForTiff-resolutionUnit?: int--><!--Device-PackingOptionsForTiff-resolutionUnit?: int-End-->

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## xResolution

```TypeScript
xResolution?: number
```

Horizontal resolution. The value must be greater than 0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PackingOptionsForTiff-xResolution?: double--><!--Device-PackingOptionsForTiff-xResolution?: double-End-->

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## yResolution

```TypeScript
yResolution?: number
```

Vertical resolution. The value must be greater than 0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PackingOptionsForTiff-yResolution?: double--><!--Device-PackingOptionsForTiff-yResolution?: double-End-->

**System capability:** SystemCapability.Multimedia.Image.ImagePacker
