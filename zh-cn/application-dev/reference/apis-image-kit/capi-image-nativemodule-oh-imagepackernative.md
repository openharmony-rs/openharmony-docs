# OH_ImagePackerNative
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_ImagePackerNative OH_ImagePackerNative
```

## 概述

OH_ImagePackerNative用于将ImageSource、PixelMap、Picture或PixelMap序列编码为图片数据或文件。

使用[OH_ImagePackerNative_Create](capi-image-packer-native-h.md#oh_imagepackernative_create)函数创建OH_ImagePackerNative对象。

使用[OH_ImagePackerNative_Release](capi-image-packer-native-h.md#oh_imagepackernative_release)函数释放OH_ImagePackerNative对象。

资源管理：OH_ImagePackerNative使用完成后，应调用[OH_ImagePackerNative_Release](capi-image-packer-native-h.md#oh_imagepackernative_release)释放。释放OH_ImagePackerNative对象不会释放OH_PackingOptions、OH_PackingOptionsForSequence、OH_ImageSourceNative、OH_PixelmapNative或OH_PictureNative对象。

OH_ImagePackerNative支持的编码方式如下：

| 输入对象 | 输出位置 | 编码函数 | 描述 |
| -- | -- | -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) | 数据缓冲区 | [OH_ImagePackerNative_PackToDataFromImageSource](capi-image-packer-native-h.md#oh_imagepackernative_packtodatafromimagesource) | 将ImageSource编码为指定格式的数据。 |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) | 数据缓冲区 | [OH_ImagePackerNative_PackToDataFromPixelmap](capi-image-packer-native-h.md#oh_imagepackernative_packtodatafrompixelmap) | 将PixelMap编码为指定格式的数据。 |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) | 数据缓冲区 | [OH_ImagePackerNative_PackToDataFromPicture](capi-image-packer-native-h.md#oh_imagepackernative_packtodatafrompicture) | 将Picture编码为指定格式的数据，仅支持JPEG和HEIF。 |
| OH_PixelmapNative数组 | 数据缓冲区 | [OH_ImagePackerNative_PackToDataFromPixelmapSequence](capi-image-packer-native-h.md#oh_imagepackernative_packtodatafrompixelmapsequence) | 将PixelMap序列编码为GIF格式数据。 |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) | 文件描述符 | [OH_ImagePackerNative_PackToFileFromImageSource](capi-image-packer-native-h.md#oh_imagepackernative_packtofilefromimagesource) | 将ImageSource编码到文件中。 |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) | 文件描述符 | [OH_ImagePackerNative_PackToFileFromPixelmap](capi-image-packer-native-h.md#oh_imagepackernative_packtofilefrompixelmap) | 将PixelMap编码到文件中。 |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) | 文件描述符 | [OH_ImagePackerNative_PackToFileFromPicture](capi-image-packer-native-h.md#oh_imagepackernative_packtofilefrompicture) | 将Picture编码到文件中，仅支持JPEG和HEIF。 |
| OH_PixelmapNative数组 | 文件描述符 | [OH_ImagePackerNative_PackToFileFromPixelmapSequence](capi-image-packer-native-h.md#oh_imagepackernative_packtofilefrompixelmapsequence) | 将PixelMap序列编码为GIF格式并写入文件。 |

获取支持编码的图片格式使用[OH_ImagePackerNative_GetSupportedFormats](capi-image-packer-native-h.md#oh_imagepackernative_getsupportedformats)函数。

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_packer_native.h](capi-image-packer-native-h.md)
