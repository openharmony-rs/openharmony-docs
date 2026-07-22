# NotificationExtensionSubscriptionInfo

用于描述通知扩展订阅的信息。
> **说明：**  
>  
> 本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 22

<!--Device-unnamed-export interface NotificationExtensionSubscriptionInfo--><!--Device-unnamed-export interface NotificationExtensionSubscriptionInfo-End-->

**系统能力：** SystemCapability.Notification.Notification

## addr

```TypeScript
addr: string
```

表示设备的唯一标识符。例如："11:22:33:AA:BB:FF"

**类型：** string

**起始版本：** 22

<!--Device-NotificationExtensionSubscriptionInfo-addr: string--><!--Device-NotificationExtensionSubscriptionInfo-addr: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## type

```TypeScript
type: notificationExtensionSubscription.SubscribeType
```

表示订阅的类型，包括通过蓝牙订阅通知。

**类型：** notificationExtensionSubscription.SubscribeType

**起始版本：** 22

<!--Device-NotificationExtensionSubscriptionInfo-type: notificationExtensionSubscription.SubscribeType--><!--Device-NotificationExtensionSubscriptionInfo-type: notificationExtensionSubscription.SubscribeType-End-->

**系统能力：** SystemCapability.Notification.Notification

