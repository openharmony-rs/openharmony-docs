# OH_ImageReceiverOptions

```c
typedef struct OH_ImageReceiverOptions OH_ImageReceiverOptions
```

## 概述

用于定义OH_ImageReceiverOptions数据类型名称。<br>OH_ImageReceiverOptions是native层封装的图片接收器选项设置器结构体，用于创建OH_ImageReceiverNative时传入设置参数。OH_ImageReceiverOptions结构体不可直接操作，而是采用函数调用方式创建、释放结构体以及操作具体字段。<br>创建OH_ImageReceiverOptions对象使用[OH_ImageReceiverOptions_Create](capi-image-receiver-native-h.md#oh_imagereceiveroptions_create)函数。<br>释放OH_ImageReceiverOptions对象使用[OH_ImageReceiverOptions_Release](capi-image-receiver-native-h.md#oh_imagereceiveroptions_release)函数。<br>OH_ImageReceiverOptions结构体内容和操作方式如下：

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_receiver_native.h](capi-image-receiver-native-h.md)

