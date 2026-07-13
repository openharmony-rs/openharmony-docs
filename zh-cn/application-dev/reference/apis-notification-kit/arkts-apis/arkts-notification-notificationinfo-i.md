# NotificationInfo

通知订阅扩展能力中
[onReceiveMessage](arkts-notification-notificationsubscriberextensionability-c.md#onreceivemessage-1)
回调的通知信息。

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Notification

## appIndex

```TypeScript
readonly appIndex: number
```

创建通知的应用包的分身索引标识，仅在分身应用中生效。

**类型：** number

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Notification

## appName

```TypeScript
readonly appName?: string
```

创建通知的应用程序名称。

**类型：** string

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Notification

## bundleName

```TypeScript
readonly bundleName: string
```

创建通知的包名。

**类型：** string

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Notification

## content

```TypeScript
readonly content: NotificationExtensionContent
```

通知内容。

**类型：** NotificationExtensionContent

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Notification

## deliveryTime

```TypeScript
readonly deliveryTime?: number
```

通知发布的时间戳（毫秒数）。

**类型：** number

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Notification

## groupName

```TypeScript
readonly groupName?: string
```

通知组名称。默认情况下此参数为空。

**类型：** string

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Notification

## hashCode

```TypeScript
readonly hashCode: string
```

通知的唯一标识符。

**类型：** string

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Notification

## notificationSlotType

```TypeScript
readonly notificationSlotType: notificationManager.SlotType
```

通知渠道类型。

**类型：** notificationManager.SlotType

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Notification

