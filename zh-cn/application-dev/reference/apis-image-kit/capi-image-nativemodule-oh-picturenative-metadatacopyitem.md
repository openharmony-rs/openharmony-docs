# OH_PictureNative_MetadataCopyItem
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_PictureNative_MetadataCopyItem {...} OH_PictureNative_MetadataCopyItem
```

## 概述

此结构体用于在创建PictureNative对象的深拷贝时指定元数据的拷贝规则。描述如何将元数据从一种类型拷贝到另一种类型。

**起始版本：** 26.0.0

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [picture_native.h](capi-picture-native-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Image_MetadataType](capi-image-common-h.md#image_metadatatype) srcType | 源元数据类型，指定要从源图片中拷贝的元数据类型。<br>**起始版本：** 26.0.0 |
| [Image_MetadataType](capi-image-common-h.md#image_metadatatype) dstType | 目标元数据类型，指定拷贝的元数据在目标图片中存储的类型。<br>**起始版本：** 26.0.0 |


