# HdrGainmapMetadata

Describes the metadata keys used by a gain map, that is, the values available for **HDR_GAINMAP_METADATA** in [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md). For details, see ISO 21496-1.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## alternateHeadroom

```TypeScript
alternateHeadroom: number
```

The alternate hdr headroom.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## baseHeadroom

```TypeScript
baseHeadroom: number
```

The baseline hdr headroom.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## channels

```TypeScript
channels: Array<GainmapChannel>
```

The per-channel metadata.

**Type:** Array&lt;[GainmapChannel](arkts-image-image-gainmapchannel-i.md)&gt;

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## gainmapChannelCount

```TypeScript
gainmapChannelCount: number
```

The number of gain map channels, with a value of 1 or 3.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## miniVersion

```TypeScript
miniVersion: number
```

The minimum version a parser needs to understand.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## useBaseColorFlag

```TypeScript
useBaseColorFlag: boolean
```

Indicate whether to use the color space of the base image.

**Type:** boolean

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## writerVersion

```TypeScript
writerVersion: number
```

The version used by the writer.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core
