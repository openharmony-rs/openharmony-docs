# NotificationInfo

通知订阅扩展能力中[onReceiveMessage](arkts-notification-application-notificationsubscriberextensionability-notificationsubscriberextensionability-c.md#onreceivemessage-1)回调的通知信息。

> **说明：**  
>  
> 本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 22

<!--Device-unnamed-export interface NotificationInfo--><!--Device-unnamed-export interface NotificationInfo-End-->

**系统能力：** SystemCapability.Notification.Notification

## appIndex

```TypeScript
readonly appIndex: number
```

创建通知的应用包的分身索引标识，仅在分身应用中生效。

**类型：** number

**起始版本：** 22

<!--Device-NotificationInfo-readonly appIndex: int--><!--Device-NotificationInfo-readonly appIndex: int-End-->

**系统能力：** SystemCapability.Notification.Notification

## appName

```TypeScript
readonly appName?: string
```

创建通知的应用程序名称。

**类型：** string

**起始版本：** 22

<!--Device-NotificationInfo-readonly appName?: string--><!--Device-NotificationInfo-readonly appName?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## bundleName

```TypeScript
readonly bundleName: string
```

创建通知的包名。

**类型：** string

**起始版本：** 22

<!--Device-NotificationInfo-readonly bundleName: string--><!--Device-NotificationInfo-readonly bundleName: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## content

```TypeScript
readonly content: NotificationExtensionContent
```

通知内容。

**类型：** NotificationExtensionContent

**起始版本：** 22

<!--Device-NotificationInfo-readonly content: NotificationExtensionContent--><!--Device-NotificationInfo-readonly content: NotificationExtensionContent-End-->

**系统能力：** SystemCapability.Notification.Notification

## deliveryTime

```TypeScript
readonly deliveryTime?: number
```

通知发布的时间戳（毫秒数）。

**类型：** number

**起始版本：** 22

<!--Device-NotificationInfo-readonly deliveryTime?: long--><!--Device-NotificationInfo-readonly deliveryTime?: long-End-->

**系统能力：** SystemCapability.Notification.Notification

## groupName

```TypeScript
readonly groupName?: string
```

通知组名称。默认情况下此参数为空。

**类型：** string

**起始版本：** 22

<!--Device-NotificationInfo-readonly groupName?: string--><!--Device-NotificationInfo-readonly groupName?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## hashCode

```TypeScript
readonly hashCode: string
```

通知的唯一标识符。

**类型：** string

**起始版本：** 22

<!--Device-NotificationInfo-readonly hashCode: string--><!--Device-NotificationInfo-readonly hashCode: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## notificationSlotType

```TypeScript
readonly notificationSlotType: notificationManager.SlotType
```

通知渠道类型。

**类型：** notificationManager.SlotType

**起始版本：** 22

<!--Device-NotificationInfo-readonly notificationSlotType: notificationManager.SlotType--><!--Device-NotificationInfo-readonly notificationSlotType: notificationManager.SlotType-End-->

**系统能力：** SystemCapability.Notification.Notification

