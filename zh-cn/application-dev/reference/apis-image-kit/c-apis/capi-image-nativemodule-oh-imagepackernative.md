# OH_ImagePackerNative

```c
struct OH_ImagePackerNative
```

## 概述

OH_ImagePackerNative用于将ImageSource、PixelMap、Picture或PixelMap序列编码为图片数据或文件。<br>使用 {@link OH_ImagePackerNative_Create}函数创建OH_ImagePackerNative对象。<br>使用{@link OH_ImagePackerNative_Release}<br>函数释放OH_ImagePackerNative对象。<br>资源管理：OH_ImagePackerNative使用完成后，应调用{@link OH_ImagePackerNative_Release}释放。<br>释放OH_ImagePackerNative对象不会释放OH_PackingOptions、OH_PackingOptionsForSequence、OH_ImageSourceNative、<br>OH_PixelmapNative或OH_PictureNative对象。<br>OH_ImagePackerNative支持的编码方式如下：<br>\| 输入对象 \| 输出位置 \| 编码函数 \| 描述 \|\| -- \| -- \| --<br>\| -- \|\| {@link OH_ImageSourceNative} \| 数据缓冲区 \| {@link OH_ImagePackerNative_PackToDataFromImageSource} \|<br>将ImageSource编码为指定格式的数据。 \|\| {@link OH_PixelmapNative} \| 数据缓冲区 \| {@link OH_ImagePackerNative_PackToDataFromPixelmap} \|<br>将PixelMap编码为指定格式的数据。 \|\| {@link OH_PictureNative} \| 数据缓冲区 \| {@link OH_ImagePackerNative_PackToDataFromPicture} \|<br>将Picture编码为指定格式的数据，仅支持JPEG和HEIF。 \|\| OH_PixelmapNative数组 \| 数据缓冲区 \|<br>{@link OH_ImagePackerNative_PackToDataFromPixelmapSequence} \| 将PixelMap序列编码为GIF格式数据。 \|\| {@link OH_ImageSourceNative}<br>\| 文件描述符 \| {@link OH_ImagePackerNative_PackToFileFromImageSource} \| 将ImageSource编码到文件中。 \|\| {@link OH_PixelmapNative} \|<br> 文件描述符 \| {@link OH_ImagePackerNative_PackToFileFromPixelmap} \| 将PixelMap编码到文件中。 \|\| {@link OH_PictureNative} \| 文件描述符 \|<br> {@link OH_ImagePackerNative_PackToFileFromPicture} \| 将Picture编码到文件中，仅支持JPEG和HEIF。 \|\| OH_PixelmapNative数组 \| 文件描述符 \|<br> {@link OH_ImagePackerNative_PackToFileFromPixelmapSequence} \| 将PixelMap序列编码为GIF格式并写入文件。 \|<br>获取支持编码的图片格式使用<br>{@link OH_ImagePackerNative_GetSupportedFormats}函数。

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_packer_native.h](capi-image-packer-native-h.md)

