# NotificationExtensionSubscriptionInfo

用于描述通知扩展订阅的信息。

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Notification

## addr

```TypeScript
addr: string
```

表示设备的唯一标识符。 当type为`SubscribeType.BLUETOOTH`时，指定对应的蓝牙设备地址。例如："11:22:33:AA:BB:FF"。

**类型：** string

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Notification

## type

```TypeScript
type: notificationExtensionSubscription.SubscribeType
```

订阅的类型，指定通知扩展的订阅方式。当前仅支持`SubscribeType.BLUETOOTH`，表示通过蓝牙订阅通知。

**类型：** notificationExtensionSubscription.SubscribeType

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Notification
