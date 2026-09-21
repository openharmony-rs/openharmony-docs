# image_receiver_native.h

## 概述

声明从native层获取图片数据的方法。

**库：** libimage_receiver.so

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md) | - | OH_ImageReceiverNative是native层封装的图片接收器结构体，OH_ImageReceiverNative结构体不可直接操作，而是采用函数调用方式创建、释放结构体以及操作具体字段。<br> 创建OH_ImageReceiverNative对象使用{@link OH_ImageReceiverNative_Create}函数。<br>释放OH_ImageReceiverNative对象使用<br>{@link OH_ImageReceiverNative_Release}函数。<br>OH_ImageReceiverNative结构体内容和操作方式如下： |
| [OH_ImageReceiverOptions](capi-image-nativemodule-oh-imagereceiveroptions.md) | - | 用于定义OH_ImageReceiverOptions数据类型名称。<br>OH_ImageReceiverOptions是native层封装的图片接收器选项设置器结构体， 用于创建OH_ImageReceiverNative时传入设置参数。OH_ImageReceiverOptions结构体不可直接操作，而是采用函数调用方式创建、释放结构体以及操作具体字段。<br> 创建OH_ImageReceiverOptions对象使用{@link OH_ImageReceiverOptions_Create}函数。<br>释放OH_ImageReceiverOptions对象使用<br>{@link OH_ImageReceiverOptions_Release}函数。<br>OH_ImageReceiverOptions结构体内容和操作方式如下： |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_ImageReceiver_OnCallback)(OH_ImageReceiverNative *receiver)](#oh_imagereceiver_oncallback) | OH_ImageReceiver_OnCallback | 定义native层图片的回调方法。 |
| [typedef void (\*OH_ImageReceiver_ImageArriveCallback)(OH_ImageReceiverNative *receiver, void *userData)](#oh_imagereceiver_imagearrivecallback) | OH_ImageReceiver_ImageArriveCallback | ImageArrive事件的回调方法。 |
| [Image_ErrorCode OH_ImageReceiverOptions_Create(OH_ImageReceiverOptions **options)](#oh_imagereceiveroptions_create) | - | Creates an OH_ImageReceiverOptions object at the application layer. |
| [Image_ErrorCode OH_ImageReceiverOptions_GetSize(OH_ImageReceiverOptions* options, Image_Size* size)](#oh_imagereceiveroptions_getsize) | - | 获取OH_ImageReceiverOptions对象的Image_Size。 |
| [Image_ErrorCode OH_ImageReceiverOptions_SetSize(OH_ImageReceiverOptions* options, Image_Size size)](#oh_imagereceiveroptions_setsize) | - | 设置OH_ImageReceiverOptions对象的Image_Size。 |
| [Image_ErrorCode OH_ImageReceiverOptions_GetCapacity(OH_ImageReceiverOptions* options, int32_t* capacity)](#oh_imagereceiveroptions_getcapacity) | - | 获取OH_ImageReceiverOptions对象的图片缓存容量。 |
| [Image_ErrorCode OH_ImageReceiverOptions_SetCapacity(OH_ImageReceiverOptions* options, int32_t capacity)](#oh_imagereceiveroptions_setcapacity) | - | 设置OH_ImageReceiverOptions对象的图片缓存容量。 |
| [Image_ErrorCode OH_ImageReceiverOptions_Release(OH_ImageReceiverOptions* options)](#oh_imagereceiveroptions_release) | - | 释放OH_ImageReceiverOptions对象。 |
| [Image_ErrorCode OH_ImageReceiverNative_Create(OH_ImageReceiverOptions* options, OH_ImageReceiverNative** receiver)](#oh_imagereceivernative_create) | - | 创建应用层OH_ImageReceiverNative对象。 |
| [Image_ErrorCode OH_ImageReceiverNative_GetReceivingSurfaceId(OH_ImageReceiverNative* receiver, uint64_t* surfaceId)](#oh_imagereceivernative_getreceivingsurfaceid) | - | 通过OH_ImageReceiverNative获取SurfaceId。 |
| [Image_ErrorCode OH_ImageReceiverNative_ReadLatestImage(OH_ImageReceiverNative* receiver, OH_ImageNative** image)](#oh_imagereceivernative_readlatestimage) | - | 通过OH_ImageReceiverNative获取最新的一张图片。 |
| [Image_ErrorCode OH_ImageReceiverNative_ReadNextImage(OH_ImageReceiverNative* receiver, OH_ImageNative** image)](#oh_imagereceivernative_readnextimage) | - | 通过OH_ImageReceiverNative获取下一张图片。 |
| [Image_ErrorCode OH_ImageReceiverNative_On(OH_ImageReceiverNative* receiver, OH_ImageReceiver_OnCallback callback)](#oh_imagereceivernative_on) | - | 注册一个[OH_ImageReceiver_OnCallback](capi-image-receiver-native-h.md#oh_imagereceiver_oncallback)回调事件。 <br>每当接收到新的图片，该回调事件就会响应。 |
| [Image_ErrorCode OH_ImageReceiverNative_Off(OH_ImageReceiverNative* receiver)](#oh_imagereceivernative_off) | - | 关闭[OH_ImageReceiver_OnCallback](capi-image-receiver-native-h.md#oh_imagereceiver_oncallback)回调事件。 <br>关闭被[OH_ImageReceiverNative_On](capi-image-receiver-native-h.md#oh_imagereceivernative_on)开启的回调事件。 |
| [Image_ErrorCode OH_ImageReceiverNative_GetSize(OH_ImageReceiverNative* receiver, Image_Size* size)](#oh_imagereceivernative_getsize) | - | 通过OH_ImageReceiverNative获取ImageReceiver的大小。 |
| [Image_ErrorCode OH_ImageReceiverNative_GetCapacity(OH_ImageReceiverNative* receiver, int32_t* capacity)](#oh_imagereceivernative_getcapacity) | - | 通过OH_ImageReceiverNative获取ImageReceiver的容量。 |
| [Image_ErrorCode OH_ImageReceiverNative_Release(OH_ImageReceiverNative* receiver)](#oh_imagereceivernative_release) | - | 释放Native OH_ImageReceiverNative对象。 |
| [Image_ErrorCode OH_ImageReceiverNative_OnImageArrive(OH_ImageReceiverNative* receiver, OH_ImageReceiver_ImageArriveCallback callback, void *userData)](#oh_imagereceivernative_onimagearrive) | - |  |
| [Image_ErrorCode OH_ImageReceiverNative_OffImageArrive(OH_ImageReceiverNative* receiver, OH_ImageReceiver_ImageArriveCallback callback)](#oh_imagereceivernative_offimagearrive) | - |  |
| [Image_ErrorCode OH_ImageReceiverNative_SetMemoryName(const OH_ImageReceiverNative* receiver, const char *name, uint32_t size)](#oh_imagereceivernative_setmemoryname) | - | 设置OH_ImageReceiverNative对象的内存名称。<br> 仅支持可见ASCII字符，空格、换行、制表符及其他控制字符将被过滤掉。 如果过滤后的结果完全由数字组成，将自动添加前缀"ImageReceiver:"。 过滤后的名称长度（包括结束符'\0'）不得超过256字节。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| void (*OH_ImageReceiver_OnCallback)(OH_ImageReceiverNative *receiver) | 定义native层图片的回调方法。<br>**起始版本：** 12 |
| void (*OH_ImageReceiver_ImageArriveCallback)(OH_ImageReceiverNative *receiver, void *userData) | ImageArrive事件的回调方法。<br>**起始版本：** 20 |

## 函数说明

### OH_ImageReceiver_OnCallback()

```c
typedef void (*OH_ImageReceiver_OnCallback)(OH_ImageReceiverNative *receiver)
```

**描述：**

定义native层图片的回调方法。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 12

### OH_ImageReceiver_ImageArriveCallback()

```c
typedef void (*OH_ImageReceiver_ImageArriveCallback)(OH_ImageReceiverNative *receiver, void *userData)
```

**描述：**

ImageArrive事件的回调方法。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 20

### OH_ImageReceiverOptions_Create()

```c
Image_ErrorCode OH_ImageReceiverOptions_Create(OH_ImageReceiverOptions **options)
```

**描述：**

Creates an OH_ImageReceiverOptions object at the application layer.

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageReceiverOptions](capi-image-nativemodule-oh-imagereceiveroptions.md) **options | Double pointer to the OH_ImageReceiverOptions object created. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if bad parameter.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_ALLOC_FAILED - if alloc failed. |

### OH_ImageReceiverOptions_GetSize()

```c
Image_ErrorCode OH_ImageReceiverOptions_GetSize(OH_ImageReceiverOptions* options, Image_Size* size)
```

**描述：**

获取OH_ImageReceiverOptions对象的Image_Size。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageReceiverOptions](capi-image-nativemodule-oh-imagereceiveroptions.md)* options | 表示OH_ImageReceiverOptions对象的指针。 |
| Image_Size* size | 表示作为获取结果的Image_Size对象的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_BAD_PARAMETER：参数错误。 |

### OH_ImageReceiverOptions_SetSize()

```c
Image_ErrorCode OH_ImageReceiverOptions_SetSize(OH_ImageReceiverOptions* options, Image_Size size)
```

**描述：**

设置OH_ImageReceiverOptions对象的Image_Size。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageReceiverOptions](capi-image-nativemodule-oh-imagereceiveroptions.md)* options | 表示OH_ImageReceiverOptions对象的指针。 |
| Image_Size size | 表示Image_Size对象的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_BAD_PARAMETER：参数错误。 |

### OH_ImageReceiverOptions_GetCapacity()

```c
Image_ErrorCode OH_ImageReceiverOptions_GetCapacity(OH_ImageReceiverOptions* options, int32_t* capacity)
```

**描述：**

获取OH_ImageReceiverOptions对象的图片缓存容量。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageReceiverOptions](capi-image-nativemodule-oh-imagereceiveroptions.md)* options | 表示OH_ImageReceiverOptions对象的指针。 |
| int32_t* capacity | 表示作为获取结果的图片缓存容量对象的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_BAD_PARAMETER：参数错误。 |

### OH_ImageReceiverOptions_SetCapacity()

```c
Image_ErrorCode OH_ImageReceiverOptions_SetCapacity(OH_ImageReceiverOptions* options, int32_t capacity)
```

**描述：**

设置OH_ImageReceiverOptions对象的图片缓存容量。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageReceiverOptions](capi-image-nativemodule-oh-imagereceiveroptions.md)* options | 表示OH_ImageReceiverOptions对象的指针。 |
| int32_t capacity | 表示图片缓存容量值。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_BAD_PARAMETER：参数错误。 |

### OH_ImageReceiverOptions_Release()

```c
Image_ErrorCode OH_ImageReceiverOptions_Release(OH_ImageReceiverOptions* options)
```

**描述：**

释放OH_ImageReceiverOptions对象。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageReceiverOptions](capi-image-nativemodule-oh-imagereceiveroptions.md)* options | 表示OH_ImageReceiverOptions对象的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_BAD_PARAMETER：参数错误。 |

**参考：**

[OH_ImageReceiverOptions](capi-image-nativemodule-oh-imagereceiveroptions.md)


### OH_ImageReceiverNative_Create()

```c
Image_ErrorCode OH_ImageReceiverNative_Create(OH_ImageReceiverOptions* options, OH_ImageReceiverNative** receiver)
```

**描述：**

创建应用层OH_ImageReceiverNative对象。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageReceiverOptions](capi-image-nativemodule-oh-imagereceiveroptions.md)* options | 表示OH_ImageReceiverOptions对象的指针。 |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)** receiver | 表示作为获取结果的OH_ImageReceiverNative对象的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_BAD_PARAMETER：参数错误。      <br>IMAGE_ALLOC_FAILED：申请内存失败。 |

### OH_ImageReceiverNative_GetReceivingSurfaceId()

```c
Image_ErrorCode OH_ImageReceiverNative_GetReceivingSurfaceId(OH_ImageReceiverNative* receiver, uint64_t* surfaceId)
```

**描述：**

通过OH_ImageReceiverNative获取SurfaceId。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | 表示OH_ImageReceiverNative对象的指针。 |
| uint64_t* surfaceId | 表示作为获取结果的id对象的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_BAD_PARAMETER：参数错误。      <br>IMAGE_UNKNOWN_ERROR：未知原因错误。 |

**参考：**

[OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)


### OH_ImageReceiverNative_ReadLatestImage()

```c
Image_ErrorCode OH_ImageReceiverNative_ReadLatestImage(OH_ImageReceiverNative* receiver, OH_ImageNative** image)
```

**描述：**

通过OH_ImageReceiverNative获取最新的一张图片。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | 表示OH_ImageReceiverNative对象的指针。 |
| OH_ImageNative** image | 获取到的应用层的OH_ImageNative指针对象。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_BAD_PARAMETER：参数错误。      <br>IMAGE_UNKNOWN_ERROR：未知原因错误。      <br>IMAGE_ALLOC_FAILED：申请内存失败。 |

**参考：**

OH_ImageReceiverNative, OH_ImageNative


### OH_ImageReceiverNative_ReadNextImage()

```c
Image_ErrorCode OH_ImageReceiverNative_ReadNextImage(OH_ImageReceiverNative* receiver, OH_ImageNative** image)
```

**描述：**

通过OH_ImageReceiverNative获取下一张图片。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | 表示OH_ImageReceiverNative对象的指针。 |
| OH_ImageNative** image | 获取到的应用层的OH_ImageNative指针对象。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_BAD_PARAMETER：参数错误。      <br>IMAGE_UNKNOWN_ERROR：未知原因错误。      <br>IMAGE_ALLOC_FAILED：申请内存失败。 |

**参考：**

OH_ImageReceiverNative, OH_ImageNative


### OH_ImageReceiverNative_On()

```c
Image_ErrorCode OH_ImageReceiverNative_On(OH_ImageReceiverNative* receiver, OH_ImageReceiver_OnCallback callback)
```

**描述：**

注册一个[OH_ImageReceiver_OnCallback](capi-image-receiver-native-h.md#oh_imagereceiver_oncallback)回调事件。 <br>每当接收到新的图片，该回调事件就会响应。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | 表示OH_ImageReceiverNative对象的指针。 |
| [OH_ImageReceiver_OnCallback](capi-image-receiver-native-h.md#oh_imagereceiver_oncallback) callback | 表示OH_ImageReceiver_OnCallback事件的回调函数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_BAD_PARAMETER：参数错误。 |

**参考：**

OH_ImageReceiverNative, OH_ImageReceiver_OnCallback


### OH_ImageReceiverNative_Off()

```c
Image_ErrorCode OH_ImageReceiverNative_Off(OH_ImageReceiverNative* receiver)
```

**描述：**

关闭[OH_ImageReceiver_OnCallback](capi-image-receiver-native-h.md#oh_imagereceiver_oncallback)回调事件。 <br>关闭被[OH_ImageReceiverNative_On](capi-image-receiver-native-h.md#oh_imagereceivernative_on)开启的回调事件。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | 表示OH_ImageReceiverNative对象的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_BAD_PARAMETER：参数错误。 |

**参考：**

OH_ImageReceiverNative, OH_ImageReceiverNative_On


### OH_ImageReceiverNative_GetSize()

```c
Image_ErrorCode OH_ImageReceiverNative_GetSize(OH_ImageReceiverNative* receiver, Image_Size* size)
```

**描述：**

通过OH_ImageReceiverNative获取ImageReceiver的大小。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | 表示OH_ImageReceiverNative对象的指针。 |
| Image_Size* size | 表示作为获取结果的Image_Size对象的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_BAD_PARAMETER：参数错误。 |

**参考：**

OH_ImageReceiverNative, Image_Size


### OH_ImageReceiverNative_GetCapacity()

```c
Image_ErrorCode OH_ImageReceiverNative_GetCapacity(OH_ImageReceiverNative* receiver, int32_t* capacity)
```

**描述：**

通过OH_ImageReceiverNative获取ImageReceiver的容量。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | 表示OH_ImageReceiverNative对象的指针。 |
| int32_t* capacity | 表示作为获取结果的图片缓存容量对象的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_BAD_PARAMETER：参数错误。 |

**参考：**

[OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)


### OH_ImageReceiverNative_Release()

```c
Image_ErrorCode OH_ImageReceiverNative_Release(OH_ImageReceiverNative* receiver)
```

**描述：**

释放Native OH_ImageReceiverNative对象。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | 表示OH_ImageReceiverNative对象的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_BAD_PARAMETER：参数错误。 |

**参考：**

[OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)


### OH_ImageReceiverNative_OnImageArrive()

```c
Image_ErrorCode OH_ImageReceiverNative_OnImageArrive(OH_ImageReceiverNative* receiver, OH_ImageReceiver_ImageArriveCallback callback, void *userData)
```

**描述：**

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | 处理回调的OH_ImageReceiverNative对象。 |
| [OH_ImageReceiver_ImageArriveCallback](capi-image-receiver-native-h.md#oh_imagereceiver_imagearrivecallback) callback | 要注册的OH_ImageReceiver_ImageArriveCallback回调方法。 |
| void *userData | 用户自定义数据指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：操作成功。      <br>IMAGE_RECEIVER_INVALID_PARAMETER：参数错误。 |

### OH_ImageReceiverNative_OffImageArrive()

```c
Image_ErrorCode OH_ImageReceiverNative_OffImageArrive(OH_ImageReceiverNative* receiver, OH_ImageReceiver_ImageArriveCallback callback)
```

**描述：**

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | 处理回调的OH_ImageReceiverNative对象。 |
| [OH_ImageReceiver_ImageArriveCallback](capi-image-receiver-native-h.md#oh_imagereceiver_imagearrivecallback) callback | 要注销的OH_ImageReceiver_ImageArriveCallback回调。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：操作成功。      <br>IMAGE_RECEIVER_INVALID_PARAMETER：参数错误，receiver或callback未注册。 |

### OH_ImageReceiverNative_SetMemoryName()

```c
Image_ErrorCode OH_ImageReceiverNative_SetMemoryName(const OH_ImageReceiverNative* receiver, const char *name, uint32_t size)
```

**描述：**

设置OH_ImageReceiverNative对象的内存名称。<br> 仅支持可见ASCII字符，空格、换行、制表符及其他控制字符将被过滤掉。 如果过滤后的结果完全由数字组成，将自动添加前缀"ImageReceiver:"。 过滤后的名称长度（包括结束符'\0'）不得超过256字节。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | [in] 指向OH_ImageReceiverNative对象的指针，不能为NULL。 |
| const char *name | [in] 指向要设置的内存名称字符串的指针，不能为NULL。字符串必须以'\0'结尾。 |
| uint32_t size | [in] 名称字符串的字节大小，包括结束符'\0'。必须大于0。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | <ul>          <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) 操作成功。</li>          <li>[IMAGE_RECEIVER_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) receiver或name为NULL，或size为0，              或name过滤后无可视字符，或过滤后大小超过256字节。</li>          </ul> |


