# OH_Pixelmap_ImageInfo

```c
struct OH_Pixelmap_ImageInfo
```

## 概述

OH_Pixelmap_ImageInfo是Native层封装的图像像素信息结构体，保存图像像素的宽高、行跨距、像素格式、透明度类型、是否为HDR等信息，适用于在Native层查询Pixelmap属性的场景。<br>创建OH_Pixelmap_ImageInfo对象使用[OH_PixelmapImageInfo_Create](capi-pixelmap-native-h.md#oh_pixelmapimageinfo_create)函数，使用完成后需调用[OH_PixelmapImageInfo_Release](capi-pixelmap-native-h.md#oh_pixelmapimageinfo_release)函数释放资源，两者需配对使用，否则会导致内存泄漏。

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [pixelmap_native.h](capi-pixelmap-native-h.md)

