# OhosImageReceiverInfo

```c
struct OhosImageReceiverInfo {...}
```

## 概述

定义ImageReceiver的相关信息。

**起始版本：** 10

**相关模块：** [Image](capi-image.md)

**所在头文件：** [image_receiver_mdk.h](capi-image-receiver-mdk-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t width | Default width of the image received by the consumer, in pixels. |
| int32_t height | Default height of the image received by the consumer, in pixels. |
| int32_t format | Image format [OHOS_IMAGE_FORMAT_JPEG](capi-image-mdk-h.md#anonymous enum) created by using the receiver. |
| int32_t capicity | Maximum number of images that can be cached. |


