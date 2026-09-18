# PackingDynamicRange

Enumerates the desired dynamic range of an image during encoding.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## AUTO

```TypeScript
AUTO = 0
```

Adaptive. The [pixelmap](arkts-image-image-pixelmap-i.md) is encoded based on the format. If the PixelMap is in HDR format, it is encoded based on the HDR content; otherwise, it is encoded based on the SDR content.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SDR

```TypeScript
SDR = 1
```

The image is decoded according to the standard dynamic range.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core
