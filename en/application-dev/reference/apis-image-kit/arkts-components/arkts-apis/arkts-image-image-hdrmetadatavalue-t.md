# HdrMetadataValue

```TypeScript
type HdrMetadataValue = HdrMetadataType | HdrStaticMetadata | ArrayBuffer | HdrGainmapMetadata
```

Describes the HDR metadata values used by a PixelMap, which corresponds to the values available for [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md).

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

| Type | Description |
| --- | --- |
| [HdrMetadataType](arkts-image-image-hdrmetadatatype-e.md) | Metadata value corresponding to the **HDR_METADATA_TYPE** key in [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md). |
| [HdrStaticMetadata](arkts-image-image-hdrstaticmetadata-i.md) | Metadata value corresponding to the **HDR_STATIC_METADATA** key in [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md). |
| ArrayBuffer | Metadata value corresponding to the **HDR_DYNAMIC_METADATA** key in [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md). |
| [HdrGainmapMetadata](arkts-image-image-hdrgainmapmetadata-i.md) | Metadata value corresponding to the **HDR_GAINMAP_METADATA** key in [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md). |
