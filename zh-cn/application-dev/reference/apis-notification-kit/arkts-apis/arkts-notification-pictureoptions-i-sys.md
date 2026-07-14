# PictureOptions（系统接口）

实况通知图片配置项。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## preparseLiveViewPicList

```TypeScript
preparseLiveViewPicList?: string[]
```

订阅普通实况类型通知中
[NotificationLiveViewContent](arkts-notification-notificationliveviewcontent-i-sys.md)的extraInfo中的
图片信息。入参为extraInfo中需要解析为pixelMap格式的图片文件名的Key。<br>当应用发布普通实况类型通知时，通过
[onConsume](arkts-notification-notificationsubscriber-i-sys.md#onconsume)将解析后的图片信息回调给订阅者，
解析后的图片信息存放于NotificationLiveViewContent的pictureInfo内。

**类型：** string[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

