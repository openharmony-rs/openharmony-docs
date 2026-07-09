# OH_PixelmapNative
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
struct OH_PixelmapNative
```

## 概述

OH_PixelmapNative结构体是Native层封装的图像解码后无压缩的位图格式结构体，支持像素数据读写、透明度设置、缩放、平移、旋转、翻转、裁剪等操作，适用于需要在Native层对Pixelmap进行像素级处理与变换的场景。

创建OH_PixelmapNative使用[OH_PixelmapNative_CreatePixelmap](capi-pixelmap-native-h.md#oh_pixelmapnative_createpixelmap)函数，当未指定源像素格式时，默认采用BGRA_8888格式处理数据。使用完毕后，必须调用[OH_PixelmapNative_Release](capi-pixelmap-native-h.md#oh_pixelmapnative_release)函数释放资源，两者需配对使用，否则会导致内存泄漏。

OH_PixelmapNative结构体内容和操作方式如下：

| 字段类型 | 字段名称 | 字段描述 | 操作函数 | 函数描述 |
| -------- | -------- | -------- | -------- | -------- |
| uint8_t | data | 图像像素数据，当未指定源像素格式时，默认按BGRA_8888格式处理。 | [OH_PixelmapNative_ReadPixels](capi-pixelmap-native-h.md#oh_pixelmapnative_readpixels) | 读取Pixelmap的像素数据，结果写入缓冲区中。|
| uint8_t | data | 图像像素数据，当未指定源像素格式时，默认按BGRA_8888格式处理。 | [OH_PixelmapNative_WritePixels](capi-pixelmap-native-h.md#oh_pixelmapnative_writepixels) | 将缓冲区中的像素数据写入Pixelmap。 |
| [OH_Pixelmap_ImageInfo](capi-image-nativemodule-oh-pixelmap-imageinfo.md) | imageInfo | 图像像素信息，参考[OH_Pixelmap_ImageInfo](capi-image-nativemodule-oh-pixelmap-imageinfo.md)。 | [OH_PixelmapNative_GetImageInfo](capi-pixelmap-native-h.md#oh_pixelmapnative_getimageinfo) | 获取图像像素信息。 |
| float | alphaRate | 不透明度，取值范围(0.0, 1.0]，1.0表示完全不透明。 | [OH_PixelmapNative_Opacity](capi-pixelmap-native-h.md#oh_pixelmapnative_opacity) | 设置透明比率，使Pixelmap达到对应的透明效果。 |
|float, float | scaleX, scaleY | scaleX为沿X轴的缩放比例、scaleY为沿Y轴的缩放比例，取值需大于0，1.0表示不缩放。 | [OH_PixelmapNative_Scale](capi-pixelmap-native-h.md#oh_pixelmapnative_scale) | 根据输入的缩放比例对图片进行缩放。 |
| float, float| x, y | x平移量、y平移量，单位：像素。 | [OH_PixelmapNative_Translate](capi-pixelmap-native-h.md#oh_pixelmapnative_translate) | 根据输入的平移距离对图片进行位置变换。 |
| float | angle | 旋转角度，单位：角度（°）。 |[OH_PixelmapNative_Rotate](capi-pixelmap-native-h.md#oh_pixelmapnative_rotate) | 根据输入的角度对图片进行旋转。 |
| bool, bool | shouldFlipHorizontally, shouldFlipVertically | 是否水平翻转图像（true表示水平翻转图像，false表示不水平翻转图像）、是否垂直翻转图像（true表示垂直翻转图像，false表示不垂直翻转图像）。 | [OH_PixelmapNative_Flip](capi-pixelmap-native-h.md#oh_pixelmapnative_flip) | 根据输入的水平/垂直翻转标志对图片进行翻转。 |
| [Image_Region](capi-image-nativemodule-image-region.md) | region | 裁剪区间，包含起始坐标(x,y)和宽高，宽高需为正值且裁剪区域需在图像范围内，参考[Image_Region](capi-image-nativemodule-image-region.md)。 | [OH_PixelmapNative_Crop](capi-pixelmap-native-h.md#oh_pixelmapnative_crop) | 根据输入的区域信息对图片进行裁剪。 |

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [pixelmap_native.h](capi-pixelmap-native-h.md)