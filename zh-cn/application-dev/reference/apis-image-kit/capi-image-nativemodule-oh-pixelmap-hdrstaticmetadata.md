# OH_Pixelmap_HdrStaticMetadata
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_Pixelmap_HdrStaticMetadata {...} OH_Pixelmap_HdrStaticMetadata
```

## 概述

表示HDR_STATIC_METADATA关键字对应的静态元数据值，用于描述HDR显示设备的能力信息（如三基色坐标、白点坐标、最值亮度等），在调用[OH_PixelmapNative_SetMetadata](capi-pixelmap-native-h.md#oh_pixelmapnative_setmetadata)和[OH_PixelmapNative_GetMetadata](capi-pixelmap-native-h.md#oh_pixelmapnative_getmetadata)时作为[OH_Pixelmap_HdrMetadataValue](capi-image-nativemodule-oh-pixelmap-hdrmetadatavalue.md)的成员使用。

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [pixelmap_native.h](capi-pixelmap-native-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| float displayPrimariesX[3] | 归一化后显示设备三基色的X坐标，数组的长度为3，按R、G、B顺序存储（索引0为R，1为G，2为B），以0.00002为单位，范围[0.0, 1.0]。 |
| float displayPrimariesY[3] | 归一化后显示设备三基色的Y坐标，数组的长度为3，按R、G、B顺序存储（索引0为R，1为G，2为B），以0.00002为单位，范围[0.0, 1.0]。 |
| float whitePointX | 归一化后白点值的X坐标，以0.00002为单位，范围[0.0, 1.0]。 |
| float whitePointY | 归一化后白点值的Y坐标，以0.00002为单位，范围[0.0, 1.0]。 |
| float maxLuminance | 图像主监视器最大亮度。以1为单位，取值范围为[0, 65535]。 |
| float minLuminance | 图像主监视器最小亮度。以0.0001为单位，取值范围为[0, 6.55535]。 |
| float maxContentLightLevel | 显示内容的最大亮度。以1为单位，取值范围为[0, 65535]。 |
| float maxFrameAverageLightLevel | 显示内容的最大平均亮度。以1为单位，取值范围为[0, 65535]。 |


