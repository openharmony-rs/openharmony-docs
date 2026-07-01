# OH_Pixelmap_HdrDynamicMetadata
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_Pixelmap_HdrDynamicMetadata {...} OH_Pixelmap_HdrDynamicMetadata
```

## 概述

表示HDR_DYNAMIC_METADATA关键字对应的动态元数据值，用于存储HDR图像的动态元数据，在调用[OH_PixelmapNative_SetMetadata](capi-pixelmap-native-h.md#oh_pixelmapnative_setmetadata)和[OH_PixelmapNative_GetMetadata](capi-pixelmap-native-h.md#oh_pixelmapnative_getmetadata)时作为[OH_Pixelmap_HdrMetadataValue](capi-image-nativemodule-oh-pixelmap-hdrmetadatavalue.md)的成员使用。

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [pixelmap_native.h](capi-pixelmap-native-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t *data | 动态元数据值的指针，指向存储动态元数据的二进制数据缓冲区，缓冲区长度由length成员指定。 |
| uint32_t length | 动态元数据值的长度，单位：字节（Byte），取值需与data指向的数据缓冲区实际长度一致。 |


