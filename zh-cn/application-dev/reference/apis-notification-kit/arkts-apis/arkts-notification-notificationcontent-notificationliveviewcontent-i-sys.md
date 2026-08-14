# NotificationLiveViewContent（系统接口）

描述普通实况通知。继承自[NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md#NotificationBasicContent)。

**继承/实现关系：** NotificationLiveViewContent extends [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md#NotificationBasicContent)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface NotificationLiveViewContent--><!--Device-unnamed-export interface NotificationLiveViewContent-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## extensionWantAgent

```TypeScript
extensionWantAgent?: WantAgent
```

点击辅助区的跳转动作。默认为空。

**类型：** [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-depr-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-NotificationLiveViewContent-extensionWantAgent?: WantAgent--><!--Device-NotificationLiveViewContent-extensionWantAgent?: WantAgent-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## extraInfo

```TypeScript
extraInfo?: Record<string, RecordData>
```

实况通知附加内容。默认为空。

**类型：** Record&lt;string, [RecordData](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-NotificationLiveViewContent-extraInfo?: Record<string, RecordData>--><!--Device-NotificationLiveViewContent-extraInfo?: Record<string, RecordData>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## isLocalUpdateOnly

```TypeScript
isLocalUpdateOnly?: boolean
```

实况窗是否只在本地更新。默认为false。 - true：是。 - false：否。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-NotificationLiveViewContent-isLocalUpdateOnly?: boolean--><!--Device-NotificationLiveViewContent-isLocalUpdateOnly?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## pictureInfo

```TypeScript
pictureInfo?: Record<string, Array<image.PixelMap>>
```

实况通知附加内容中的图片信息。默认为空。

**类型：** Record&lt;string, Array&lt;image.PixelMap&gt;&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-NotificationLiveViewContent-pictureInfo?: Record<string, Array<image.PixelMap>>--><!--Device-NotificationLiveViewContent-pictureInfo?: Record<string, Array<image.PixelMap>>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## status

```TypeScript
status: LiveViewStatus
```

通知状态。

**类型：** [LiveViewStatus](arkts-notification-notificationcontent-liveviewstatus-e-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-NotificationLiveViewContent-status: LiveViewStatus--><!--Device-NotificationLiveViewContent-status: LiveViewStatus-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## version

```TypeScript
version?: int
```

通知版本号（如果数据库存储版本号为0xffffffff，则本次更新和结束不校验版本号大小，否则需要校验本次版本号>数据库存储版本号）。不填默认为0xffffffff。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-NotificationLiveViewContent-version?: int--><!--Device-NotificationLiveViewContent-version?: int-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

