# HdrMetadataValue

```TypeScript
type HdrMetadataValue = HdrMetadataType | HdrStaticMetadata | ArrayBuffer | HdrGainmapMetadata
```

PixelMap使用的HDR元数据值类型，与[HdrMetadataKey]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_关键字对应。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-image-type HdrMetadataValue = HdrMetadataType | HdrStaticMetadata | ArrayBuffer | HdrGainmapMetadata--><!--Device-image-type HdrMetadataValue = HdrMetadataType | HdrStaticMetadata | ArrayBuffer | HdrGainmapMetadata-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

| 类型 | 说明 |
| --- | --- |
| HdrMetadataType | Metadata value corresponding to the **HDR\_METADATA\_TYPE** key in [HdrMetadataKey]{ |
| HdrStaticMetadata | Metadata value corresponding to the **HDR\_STATIC\_METADATA** key in [HdrMetadataKey]{ |
| ArrayBuffer | Metadata value corresponding to the **HDR\_DYNAMIC\_METADATA** key in [HdrMetadataKey]{ |
| HdrGainmapMetadata | Metadata value corresponding to the **HDR\_GAINMAP\_METADATA** key in [HdrMetadataKey]{ |

