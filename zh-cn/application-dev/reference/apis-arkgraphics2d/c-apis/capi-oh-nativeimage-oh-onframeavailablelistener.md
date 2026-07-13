# OH_OnFrameAvailableListener

```c
typedef struct OH_OnFrameAvailableListener {...} OH_OnFrameAvailableListener
```

## 概述

一个OH_NativeImage的监听者，通过OH_NativeImage_SetOnFrameAvailableListener接口注册该监听结构体，当有buffer可获取时，将触发回调给用户。

**起始版本：** 11

**相关模块：** [OH_NativeImage](capi-oh-nativeimage.md)

**所在头文件：** [native_image.h](capi-native-image-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| void *context | 用户自定义的上下文信息，会在回调触发时返回给用户 |
| [OH_OnFrameAvailable](capi-native-image-h.md#oh_onframeavailable) onFrameAvailable | 有buffer可获取时触发的回调函数 |


