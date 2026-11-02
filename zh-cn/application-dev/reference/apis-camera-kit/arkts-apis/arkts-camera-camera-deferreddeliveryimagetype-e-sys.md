# DeferredDeliveryImageType（系统接口）

```TypeScript
enum DeferredDeliveryImageType
```

枚举，分段式投递图像类型。在分段式投递中，拍照和录像分为两个阶段。第一阶段以较快的速度向用户输出图像或视频。第二阶段在优化处理之后，再次输出更高分辨率的图像或视频。

**起始版本：** 11

<!--Device-camera-enum DeferredDeliveryImageType--><!--Device-camera-enum DeferredDeliveryImageType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## NONE

```TypeScript
NONE = 0
```

不支持分段式投递。

**起始版本：** 11

<!--Device-DeferredDeliveryImageType-NONE = 0--><!--Device-DeferredDeliveryImageType-NONE = 0-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## PHOTO

```TypeScript
PHOTO = 1
```

拍照的分段式投递。

**起始版本：** 11

<!--Device-DeferredDeliveryImageType-PHOTO = 1--><!--Device-DeferredDeliveryImageType-PHOTO = 1-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## VIDEO

```TypeScript
VIDEO = 2
```

录像的分段式投递。

**起始版本：** 11

<!--Device-DeferredDeliveryImageType-VIDEO = 2--><!--Device-DeferredDeliveryImageType-VIDEO = 2-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。
