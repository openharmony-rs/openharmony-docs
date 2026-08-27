# OH_PixelmapNative

```c
typedef struct OH_PixelmapNative OH_PixelmapNative
```

## 概述

OH_PixelmapNative是Native层封装的图像解码后无压缩的位图格式结构体，支持像素数据读写、不透明度设置、缩放、平移、旋转、翻转、裁剪等操作，适用于需要在Native层对Pixelmap进行像素级处理与变换的场景。<br>创建OH_PixelmapNative需要使用{@link OH_PixelmapNative_CreatePixelmap}系列函数，该函数在未指定源像素格式时，会默认按BGRA_8888格式解析源像素数据。使用完毕后，必须调用{@link OH_PixelmapNative_Release}函数释放资源，两者需配对使用，否则会导致内存泄漏。<br>OH_PixelmapNative结构体的部分相关函数和操作方式如下：

**起始版本：** 13

**相关模块：** [ImageProcessing](capi-imageprocessing.md)

**所在头文件：** [image_processing_types.h](capi-image-processing-types-h.md)

