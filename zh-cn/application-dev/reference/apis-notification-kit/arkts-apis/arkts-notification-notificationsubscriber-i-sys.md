# NotificationSubscriber（系统接口）

提供订阅者接收到新通知、取消通知等的回调方法。

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onBadgeChanged

```TypeScript
onBadgeChanged?:(data: BadgeNumberCallbackData) => void
```

回调返回监听到的应用信息。

**类型：** (data: BadgeNumberCallbackData) => void

**起始版本：** 10

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onBadgeEnabledChanged

```TypeScript
onBadgeEnabledChanged?: BadgeEnabledChangedCallback
```

返回应用角标的使能状态变化。

**类型：** BadgeEnabledChangedCallback

**起始版本：** 12

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onBatchCancel

```TypeScript
onBatchCancel?: (data: Array<SubscribeCallbackData>) => void
```

新接收到的通知信息。

**类型：** (data: Array<SubscribeCallbackData>) => void

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onCancel

```TypeScript
onCancel?:(data: SubscribeCallbackData) => void
```

需要取消的通知信息。

**类型：** (data: SubscribeCallbackData) => void

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onConnect

```TypeScript
onConnect?:() => void
```

订阅完成的回调。

**类型：** () => void

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onConsume

```TypeScript
onConsume?:(data: SubscribeCallbackData) => void
```

新接收到的通知信息。

**类型：** (data: SubscribeCallbackData) => void

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onDestroy

```TypeScript
onDestroy?:() => void
```

服务失联的回调。

**类型：** () => void

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onDisconnect

```TypeScript
onDisconnect?:() => void
```

取消订阅的回调。

**类型：** () => void

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onDoNotDisturbChanged

```TypeScript
onDoNotDisturbChanged?: (mode: notificationManager.DoNotDisturbDate) => void
```

回调返回免打扰时间选项变更。

**类型：** (mode: notificationManager.DoNotDisturbDate) => void

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onDoNotDisturbDateChange

```TypeScript
onDoNotDisturbDateChange?: (mode: notification.DoNotDisturbDate) => void
```

回调返回免打扰时间选项变更。

**类型：** (mode: notification.DoNotDisturbDate) => void

**起始版本：** 8

**废弃版本：** 11

**替代接口：** [onDoNotDisturbChanged](arkts-notification-notificationsubscriber-i-sys.md#ondonotdisturbchanged)

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onEnabledNotificationChanged

```TypeScript
onEnabledNotificationChanged?:(callbackData: EnabledNotificationCallbackData) => void
```

回调返回监听到的应用信息。

**类型：** (callbackData: EnabledNotificationCallbackData) => void

**起始版本：** 8

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onEnabledPriorityByBundleChanged

```TypeScript
onEnabledPriorityByBundleChanged?: (callbackData: EnabledPriorityNotificationByBundleCallbackData) => void
```

返回应用通知优先级开关状态。

**类型：** (callbackData: EnabledPriorityNotificationByBundleCallbackData) => void

**起始版本：** 23

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onEnabledPriorityChanged

```TypeScript
onEnabledPriorityChanged?: (callbackData: EnabledPriorityNotificationCallbackData) => void
```

返回通知优先级总开关状态。

**类型：** (callbackData: EnabledPriorityNotificationCallbackData) => void

**起始版本：** 23

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onEnabledSilentReminderChanged

```TypeScript
onEnabledSilentReminderChanged?: EnabledSilentReminderChangedCallback
```

返回应用通知静默提醒的使能状态变化。

**类型：** EnabledSilentReminderChangedCallback

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onNotificationSwitchChanged

```TypeScript
onNotificationSwitchChanged?: NotificationSwitchChangedCallback
```

返回由[notificationManager.setNotificationSwitch](arkts-notification-setnotificationswitch-f-sys.md#setnotificationswitch-1)接口设置的通知开关状态变化。

**类型：** NotificationSwitchChangedCallback

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onSystemUpdate

```TypeScript
onSystemUpdate?: SystemUpdateCallback
```

返回携带系统属性值的通知信息。

**类型：** SystemUpdateCallback

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onUpdate

```TypeScript
onUpdate?:(data: NotificationSortingMap) => void
```

最新的通知排序列表。

**类型：** (data: NotificationSortingMap) => void

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

