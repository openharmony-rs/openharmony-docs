# HdrMetadataValue

```TypeScript
type HdrMetadataValue = HdrMetadataType | HdrStaticMetadata | ArrayBuffer | HdrGainmapMetadata
```

PixelMap使用的HDR元数据值类型，与[HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md)关键字对应。

**起始版本：** 12

<!--Device-image-type HdrMetadataValue = HdrMetadataType | HdrStaticMetadata | ArrayBuffer | HdrGainmapMetadata--><!--Device-image-type HdrMetadataValue = HdrMetadataType | HdrStaticMetadata | ArrayBuffer | HdrGainmapMetadata-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

| 类型 | 说明 |
| --- | --- |
| [HdrMetadataType](arkts-image-image-hdrmetadatatype-e.md) | Metadata value corresponding to the **HDR_METADATA_TYPE** key in [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md) [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md)中HDR_METADATA_TYPE关键字对应的元数据值类型，用于表示HDR元数据的类型。不同取值对应不同类型的HDR元数据，需根据HDR图像的实际元数据类型选择合适的值，并填充对应类型的元数据成员字段。 |
| [HdrStaticMetadata](arkts-image-image-hdrstaticmetadata-i.md) | Metadata value corresponding to the **HDR_STATIC_METADATA** key in [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md) [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md)中HDR_STATIC_METADATA关键字对应的元数据值类型，用于存储HDR静态元数据。 |
| ArrayBuffer | Metadata value corresponding to the **HDR_DYNAMIC_METADATA** key in [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md) [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md)中HDR_DYNAMIC_METADATA关键字对应的元数据值类型，用于存储HDR动态元数据，格式遵循相关HDR动态元数据标准。 |
| [HdrGainmapMetadata](arkts-image-image-hdrgainmapmetadata-i.md) | Metadata value corresponding to the **HDR_GAINMAP_METADATA** key in [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md) [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md)中HDR_GAINMAP_METADATA关键字对应的元数据值类型，用于存储HDR增益图元数据，参考ISO 21496-1。 |
