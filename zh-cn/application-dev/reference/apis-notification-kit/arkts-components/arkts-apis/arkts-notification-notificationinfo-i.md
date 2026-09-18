# NotificationInfo

通知订阅扩展能力中[onReceiveMessage](arkts-notification-application-notificationsubscriberextensionability-notificationsubscriberextensionability-c.md#onreceivemessage)回调的通知信息。

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Notification

## appIndex

```TypeScript
readonly appIndex: number
```

创建通知的应用的分身索引标识，仅在分身应用中生效。

**类型：** number

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Notification

## appName

```TypeScript
readonly appName?: string
```

创建通知的应用名称。

**类型：** string

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Notification

## bundleName

```TypeScript
readonly bundleName: string
```

创建通知的应用包名。

**类型：** string

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Notification

## content

```TypeScript
readonly content: NotificationExtensionContent
```

通知内容。包含通知的标题和正文。

**类型：** [NotificationExtensionContent](arkts-notification-notificationextensioncontent-i.md)

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Notification

## deliveryTime

```TypeScript
readonly deliveryTime?: number
```

通知发布的时间戳。数据格式：时间戳。单位：毫秒。

**类型：** number

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Notification

## groupName

```TypeScript
readonly groupName?: string
```

通知组名称。

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

通知渠道类型，标识通知所属的渠道分类（如社交通讯、服务提醒等）。不同渠道类型对应不同的提醒方式。

**类型：** [notificationManager.SlotType](arkts-notification-notificationmanager-slottype-e.md)

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Notification
