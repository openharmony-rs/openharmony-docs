# OH_ImageReceiverNative

```c
typedef struct OH_ImageReceiverNative OH_ImageReceiverNative
```

## 概述

OH_ImageReceiverNative是native层封装的图片接收器结构体，OH_ImageReceiverNative结构体不可直接操作，而是采用函数调用方式创建、释放结构体以及操作具体字段。<br>创建OH_ImageReceiverNative对象使用[OH_ImageReceiverNative_Create](capi-image-receiver-native-h.md#oh_imagereceivernative_create)函数。<br>释放OH_ImageReceiverNative对象使用[OH_ImageReceiverNative_Release](capi-image-receiver-native-h.md#oh_imagereceivernative_release)函数。<br>OH_ImageReceiverNative结构体内容和操作方式如下：

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_receiver_native.h](capi-image-receiver-native-h.md)

