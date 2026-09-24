# OH_Pixelmap_HdrStaticMetadata

```c
typedef struct OH_Pixelmap_HdrStaticMetadata {...} OH_Pixelmap_HdrStaticMetadata
```

## 概述

表示HDR_STATIC_METADATA关键字对应的静态元数据值，用于描述HDR显示设备的能力信息及内容亮度特征 （如三基色坐标、白点坐标、最值亮度、内容最大亮度等），在调用{@link OH_PixelmapNative_SetMetadata}和<br>{@link OH_PixelmapNative_GetMetadata}时作为{@link OH_Pixelmap_HdrMetadataValue}的成员使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [pixelmap_native.h](capi-pixelmap-native-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| float displayPrimariesX[3] | 归一化后显示设备三基色的X坐标。数组的长度为3，按R、G、B顺序存储，以0.00002为单位，取值范围是[0.0, 0.99998]。 |
| float displayPrimariesY[3] | 归一化后显示设备三基色的Y坐标。数组的长度为3，按R、G、B顺序存储，以0.00002为单位，取值范围是[0.0, 0.99998]。 |
| float whitePointX | 归一化后白点值的X坐标。以0.00002为单位，取值范围是[0.0, 0.99998]。 |
| float whitePointY | 归一化后白点值的Y坐标。以0.00002为单位，取值范围是[0.0, 0.99998]。 |
| float maxLuminance | 图像主监视器的最大亮度。以1为单位，取值范围是[0, 65535]。单位：尼特（nit）。 |
| float minLuminance | 图像主监视器的最小亮度。以0.0001为单位，取值范围是[0, 6.5535]。单位：尼特（nit）。 |
| float maxContentLightLevel | 显示内容的最大亮度。以1为单位，取值范围是[0, 65535]。单位：尼特（nit）。 |
| float maxFrameAverageLightLevel | 显示内容的最大平均亮度。以1为单位，取值范围是[0, 65535]。单位：尼特（nit）。 |


