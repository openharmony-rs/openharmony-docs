# NotificationInfo

通知订阅扩展能力中 [onReceiveMessage]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 回调的通知信息。 > **说明：** > > 本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export interface NotificationInfo--><!--Device-unnamed-export interface NotificationInfo-End-->

**系统能力：** SystemCapability.Notification.Notification

## appIndex

```TypeScript
readonly appIndex: int
```

创建通知的应用的分身索引标识，仅在分身应用中生效。

**类型：** int

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-NotificationInfo-readonly appIndex: int--><!--Device-NotificationInfo-readonly appIndex: int-End-->

**系统能力：** SystemCapability.Notification.Notification

## appName

```TypeScript
readonly appName?: string
```

创建通知的应用名称。

**类型：** string

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-NotificationInfo-readonly appName?: string--><!--Device-NotificationInfo-readonly appName?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## bundleName

```TypeScript
readonly bundleName: string
```

创建通知的应用包名。

**类型：** string

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-NotificationInfo-readonly bundleName: string--><!--Device-NotificationInfo-readonly bundleName: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## content

```TypeScript
readonly content: NotificationExtensionContent
```

通知内容。包含通知的标题和正文。

**类型：** NotificationExtensionContent

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-NotificationInfo-readonly content: NotificationExtensionContent--><!--Device-NotificationInfo-readonly content: NotificationExtensionContent-End-->

**系统能力：** SystemCapability.Notification.Notification

## deliveryTime

```TypeScript
readonly deliveryTime?: long
```

通知发布的时间戳。 数据格式：时间戳。 单位：毫秒。

**类型：** long

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-NotificationInfo-readonly deliveryTime?: long--><!--Device-NotificationInfo-readonly deliveryTime?: long-End-->

**系统能力：** SystemCapability.Notification.Notification

## groupName

```TypeScript
readonly groupName?: string
```

通知组名称。

**类型：** string

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-NotificationInfo-readonly groupName?: string--><!--Device-NotificationInfo-readonly groupName?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## hashCode

```TypeScript
readonly hashCode: string
```

通知的唯一标识符。

**类型：** string

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-NotificationInfo-readonly hashCode: string--><!--Device-NotificationInfo-readonly hashCode: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## notificationSlotType

```TypeScript
readonly notificationSlotType: notificationManager.SlotType
```

通知渠道类型，标识通知所属的渠道分类（如社交通讯、服务提醒等）。 不同渠道类型对应不同的提醒方式。

**类型：** notificationManager.SlotType

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-NotificationInfo-readonly notificationSlotType: notificationManager.SlotType--><!--Device-NotificationInfo-readonly notificationSlotType: notificationManager.SlotType-End-->

**系统能力：** SystemCapability.Notification.Notification

