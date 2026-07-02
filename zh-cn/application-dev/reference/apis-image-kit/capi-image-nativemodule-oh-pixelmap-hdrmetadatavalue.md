# OH_Pixelmap_HdrMetadataValue
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yaozhupeng-->
<!--Designer: @yaozhupeng-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_Pixelmap_HdrMetadataValue {...} OH_Pixelmap_HdrMetadataValue
```

## 概述

Pixelmap使用的HDR元数据值，和OH_Pixelmap_HdrMetadataKey关键字相对应。当传入相应的[OH_Pixelmap_HdrMetadataKey](capi-pixelmap-native-h.md#oh_pixelmap_hdrmetadatakey)关键字作为入参时，可通过本结构体设置或获取对应类型的元数据值，用于[OH_PixelmapNative_SetMetadata](capi-pixelmap-native-h.md#oh_pixelmapnative_setmetadata)及[OH_PixelmapNative_GetMetadata](capi-pixelmap-native-h.md#oh_pixelmapnative_getmetadata)，适用于需要对HDR图像进行元数据管理与渲染处理的场景，帮助应用正确设置和获取HDR元数据以实现高质量的HDR图像显示效果。

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [pixelmap_native.h](capi-pixelmap-native-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_Pixelmap_HdrMetadataType](capi-pixelmap-native-h.md#oh_pixelmap_hdrmetadatatype) type | HDR_METADATA_TYPE关键字对应的HDR元数据类型值。 |
| [OH_Pixelmap_HdrStaticMetadata](capi-image-nativemodule-oh-pixelmap-hdrstaticmetadata.md) staticMetadata | HDR_STATIC_METADATA关键字对应的HDR静态元数据值。 |
| [OH_Pixelmap_HdrDynamicMetadata](capi-image-nativemodule-oh-pixelmap-hdrdynamicmetadata.md) dynamicMetadata | HDR_DYNAMIC_METADATA关键字对应的HDR动态元数据值。 |
| [OH_Pixelmap_HdrGainmapMetadata](capi-image-nativemodule-oh-pixelmap-hdrgainmapmetadata.md) gainmapMetadata | HDR_GAINMAP_METADATA关键字对应的HDR增益映射元数据值。 |
