# Types
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

本模块定义了图像处理相关的类型别名，主要包括PixelMap HDR元数据相关的值类型，与HdrMetadataKey关键字配合使用，用于规范HDR图像处理中元数据的表达与传递。

> **说明：**
>
> 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## HdrMetadataValue<sup>12+</sup>

type HdrMetadataValue = HdrMetadataType | HdrStaticMetadata | ArrayBuffer | HdrGainmapMetadata

PixelMap使用的HDR元数据值类型，与[HdrMetadataKey](arkts-apis-image-e.md#hdrmetadatakey12)关键字对应。

**系统能力：** SystemCapability.Multimedia.Image.Core

| 类型                | 说明                                            |
| ------------------- | ----------------------------------------------- |
| [HdrMetadataType](arkts-apis-image-e.md#hdrmetadatatype12) | [HdrMetadataKey](arkts-apis-image-e.md#hdrmetadatakey12)中HDR_METADATA_TYPE关键字对应的元数据值类型，用于表示HDR元数据的类型。不同取值对应不同类型的HDR元数据，需根据HDR图像的实际元数据类型选择合适的值，并填充对应类型的元数据成员字段。 |
| [HdrStaticMetadata](arkts-apis-image-i.md#hdrstaticmetadata12) | [HdrMetadataKey](arkts-apis-image-e.md#hdrmetadatakey12)中HDR_STATIC_METADATA关键字对应的元数据值类型，用于存储HDR静态元数据。 |
| ArrayBuffer | [HdrMetadataKey](arkts-apis-image-e.md#hdrmetadatakey12)中HDR_DYNAMIC_METADATA关键字对应的元数据值类型，用于存储HDR动态元数据，格式遵循相关HDR动态元数据标准。 |
| [HdrGainmapMetadata](arkts-apis-image-i.md#hdrgainmapmetadata12) | [HdrMetadataKey](arkts-apis-image-e.md#hdrmetadatakey12)中HDR_GAINMAP_METADATA关键字对应的元数据值类型，用于存储HDR增益图元数据，参考ISO 21496-1。 |
