# PictureOptions（系统接口）

实况通知图片配置项。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export interface PictureOptions--><!--Device-unnamed-export interface PictureOptions-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## preparseLiveViewPicList

```TypeScript
preparseLiveViewPicList?: string[]
```

订阅普通实况类型通知中 [NotificationLiveViewContent]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的extraInfo中的 图片信息。入参为extraInfo中需要解析为pixelMap格式的图片文件名的Key。\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_当应用发布普通实况类型通知时，通过 [onConsume]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_将解析后的图片信息回调给订阅者， 解析后的图片信息存放于NotificationLiveViewContent的pictureInfo内。

**类型：** string[]

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PictureOptions-preparseLiveViewPicList?: string[]--><!--Device-PictureOptions-preparseLiveViewPicList?: string[]-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

