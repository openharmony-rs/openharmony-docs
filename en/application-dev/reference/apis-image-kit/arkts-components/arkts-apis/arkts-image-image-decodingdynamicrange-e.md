# DecodingDynamicRange

Enumerates the desired dynamic range of an image during decoding.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## AUTO

```TypeScript
AUTO = 0
```

The image is decoded based on the format. If the image is in HDR format, it is decoded based on the HDR content; otherwise, it is decoded based on the SDR content. The image source created by calling [CreateIncrementalSource](arkts-image-image-createincrementalsource-f.md) is decoded into SDR content.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SDR

```TypeScript
SDR = 1
```

The image is decoded according to the standard dynamic range.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## HDR

```TypeScript
HDR = 2
```

The image is decoded according to the high dynamic range. The image source created by calling [CreateIncrementalSource](arkts-image-image-createincrementalsource-f.md) is decoded into SDR content.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core
