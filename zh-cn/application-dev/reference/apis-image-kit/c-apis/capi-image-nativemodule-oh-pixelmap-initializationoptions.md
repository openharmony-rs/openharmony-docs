# OH_Pixelmap_InitializationOptions

```c
struct OH_Pixelmap_InitializationOptions
```

## 概述

OH_Pixelmap_InitializationOptions是Native层封装的初始化选项结构体，用于在创建Pixelmap时指定其属性， 可配置图片宽高、像素格式、透明度类型等参数，适用于需要在Native层创建Pixelmap并自定义其初始化属性的场景。 <br>使用{@link OH_PixelmapInitializationOptions_Create}函数创建OH_Pixelmap_InitializationOptions对象；<br>使用完成后需调用{@link OH_PixelmapInitializationOptions_Release}函数释放资源，两者需配对使用，否则会导致内存泄漏。

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [pixelmap_native.h](capi-pixelmap-native-h.md)

