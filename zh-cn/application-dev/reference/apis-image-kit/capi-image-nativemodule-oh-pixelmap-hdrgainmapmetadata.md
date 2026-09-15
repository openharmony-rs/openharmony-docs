# OH_Pixelmap_HdrGainmapMetadata
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_Pixelmap_HdrGainmapMetadata {...} OH_Pixelmap_HdrGainmapMetadata
```

## 概述

表示HDR_GAINMAP_METADATA关键字对应的增益图相关元数据值，参考ISO 21496-1。用于描述HDR增益图的版本、通道数、提亮比、偏移量及各通道增益曲线等参数，在调用[OH_PixelmapNative_SetMetadata](capi-pixelmap-native-h.md#oh_pixelmapnative_setmetadata)和[OH_PixelmapNative_GetMetadata](capi-pixelmap-native-h.md#oh_pixelmapnative_getmetadata)时作为[OH_Pixelmap_HdrMetadataValue](capi-image-nativemodule-oh-pixelmap-hdrmetadatavalue.md)的成员使用，适用于HDR图像增益映射元数据的设置与获取场景。

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [pixelmap_native.h](capi-pixelmap-native-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint16_t writerVersion | 元数据编写器的版本。 |
| uint16_t miniVersion | 元数据解析所需的最小版本。 |
| uint8_t gainmapChannelNum | 增益图的颜色通道数。取值为1或3，值为3时RGB通道的元数据值不同，值为1时各通道元数据值相同，参考ISO 21496-1。 |
| bool useBaseColorFlag | 是否使用基础图的色彩空间。true表示使用，false表示不使用，参考ISO 21496-1。 |
| float baseHeadroom | 基础图的提亮比。取值范围是[1.0, +∞)，参考ISO 21496-1。 |
| float alternateHeadroom | 可选择图像的提亮比。取值范围是[1.0, +∞)，参考ISO 21496-1。 |
| float gainmapMax[3] | 增益图的最大值。按R、G、B三通道存储，取值范围是(0, +∞)且必须大于gainmapMin的对应通道，参考ISO 21496-1。 |
| float gainmapMin[3] | 增益图的最小值。按R、G、B三通道存储，取值可以为0或负值但必须小于gainmapMax的对应通道，参考ISO 21496-1。 |
| float gamma[3] | 增益曲线的Gamma校正值。按R、G、B三通道存储，取值范围是(0, +∞)，参考ISO 21496-1。 |
| float baselineOffset[3] | 基础图的偏移量。按R、G、B三通道存储，参考ISO 21496-1。 |
| float alternateOffset[3] | 可选择图像的偏移量。按R、G、B三通道存储，参考ISO 21496-1。 |


