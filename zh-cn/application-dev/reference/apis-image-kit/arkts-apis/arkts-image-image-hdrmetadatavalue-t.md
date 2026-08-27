# HdrMetadataValue

```TypeScript
type HdrMetadataValue = HdrMetadataType | HdrStaticMetadata | ArrayBuffer | HdrGainmapMetadata
```

PixelMap使用的HDR元数据值类型，与[HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md)关键字对应。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

| 类型 | 说明 |
| --- | --- |
| [HdrMetadataType](arkts-image-image-hdrmetadatatype-e.md) | Metadata value corresponding to the **HDR_METADATA_TYPE** key in [HdrMetadataKey]{ |
| [HdrStaticMetadata](arkts-image-image-hdrstaticmetadata-i.md) | Metadata value corresponding to the **HDR_STATIC_METADATA** key in [HdrMetadataKey]{ |
| ArrayBuffer | Metadata value corresponding to the **HDR_DYNAMIC_METADATA** key in [HdrMetadataKey]{ |
| [HdrGainmapMetadata](arkts-image-image-hdrgainmapmetadata-i.md) | Metadata value corresponding to the **HDR_GAINMAP_METADATA** key in [HdrMetadataKey]{ |
