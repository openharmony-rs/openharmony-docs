# Types
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

> **说明：**
>
> 本模块首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## ImageType

type ImageType = image.Image | image.Picture

图片容器类型，用于获取全质量图和未压缩图(YUV)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

| 类型      | 说明                                                            |
|---------|---------------------------------------------------------------|
| [image.Image](../apis-image-kit/arkts-apis-image-Image.md) | 图片容器类型，用于获取全质量图。 |
| [image.Picture](../apis-image-kit/arkts-apis-image-Picture.md) | 图片容器类型，用于获取未压缩图(YUV)。|

## NotificationInfo

type NotificationInfo = DefocusFromProximityNotificationInfo

通知信息类型，用于获取微距缩放场景下对焦物体距离镜头过近导致对焦模糊的事件。

> **说明：**
>
> 该通知仅在微距模式下且缩放倍率大于等于 4 倍时触发。
> 可以通过[enableMacro](../apis-camera-kit/arkts-apis-camera-Macro.md#enablemacro19)设置微距能力，并使用[setZoomRatio](../apis-camera-kit/arkts-apis-camera-Zoom.md#setzoomratio11)设置缩放倍率。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

| 类型      | 说明                                                            |
|---------|---------------------------------------------------------------|
| [DefocusFromProximityNotificationInfo](arkts-apis-camera-i.md#defocusfromproximitynotificationinfo) | 通知事件类型，对焦物体和镜头距离过近导致对焦模糊事件的通知对象。 |