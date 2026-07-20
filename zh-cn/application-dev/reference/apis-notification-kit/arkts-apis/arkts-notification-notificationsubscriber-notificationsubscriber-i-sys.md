# NotificationSubscriber（系统接口）

提供订阅者接收到新通知、取消通知等的回调方法。

**起始版本：** 7

<!--Device-unnamed-export interface NotificationSubscriber--><!--Device-unnamed-export interface NotificationSubscriber-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onBadgeChanged

```TypeScript
onBadgeChanged?:(data: BadgeNumberCallbackData) => void
```

回调返回监听到的应用角标数量变化。

**类型：** (data: BadgeNumberCallbackData) =&gt; void

**起始版本：** 10

<!--Device-NotificationSubscriber-onBadgeChanged?:(data: BadgeNumberCallbackData) => void--><!--Device-NotificationSubscriber-onBadgeChanged?:(data: BadgeNumberCallbackData) => void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onBadgeEnabledChanged

```TypeScript
onBadgeEnabledChanged?: BadgeEnabledChangedCallback
```

返回应用角标的使能状态变化。

**类型：** BadgeEnabledChangedCallback

**起始版本：** 12

<!--Device-NotificationSubscriber-onBadgeEnabledChanged?: BadgeEnabledChangedCallback--><!--Device-NotificationSubscriber-onBadgeEnabledChanged?: BadgeEnabledChangedCallback-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onBatchCancel

```TypeScript
onBatchCancel?: (data: Array<SubscribeCallbackData>) => void
```

批量删除的通知信息。

**类型：** (data: Array&lt;SubscribeCallbackData&gt;) =&gt; void

**起始版本：** 11

<!--Device-NotificationSubscriber-onBatchCancel?: (data: Array<SubscribeCallbackData>) => void--><!--Device-NotificationSubscriber-onBatchCancel?: (data: Array<SubscribeCallbackData>) => void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onCancel

```TypeScript
onCancel?:(data: SubscribeCallbackData) => void
```

需要取消的通知信息。

**类型：** (data: SubscribeCallbackData) =&gt; void

**起始版本：** 7

<!--Device-NotificationSubscriber-onCancel?:(data: SubscribeCallbackData) => void--><!--Device-NotificationSubscriber-onCancel?:(data: SubscribeCallbackData) => void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onConnect

```TypeScript
onConnect?:() => void
```

订阅完成的回调。

**类型：** () =&gt; void

**起始版本：** 7

<!--Device-NotificationSubscriber-onConnect?:() => void--><!--Device-NotificationSubscriber-onConnect?:() => void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onConsume

```TypeScript
onConsume?:(data: SubscribeCallbackData) => void
```

新接收到的通知信息。

**类型：** (data: SubscribeCallbackData) =&gt; void

**起始版本：** 7

<!--Device-NotificationSubscriber-onConsume?:(data: SubscribeCallbackData) => void--><!--Device-NotificationSubscriber-onConsume?:(data: SubscribeCallbackData) => void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onDestroy

```TypeScript
onDestroy?:() => void
```

服务失联的回调。

**类型：** () =&gt; void

**起始版本：** 7

<!--Device-NotificationSubscriber-onDestroy?:() => void--><!--Device-NotificationSubscriber-onDestroy?:() => void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onDisconnect

```TypeScript
onDisconnect?:() => void
```

取消订阅的回调。

**类型：** () =&gt; void

**起始版本：** 7

<!--Device-NotificationSubscriber-onDisconnect?:() => void--><!--Device-NotificationSubscriber-onDisconnect?:() => void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onDoNotDisturbChanged

```TypeScript
onDoNotDisturbChanged?: (mode: notificationManager.DoNotDisturbDate) => void
```

回调返回免打扰时间选项变更。

**类型：** (mode: notificationManager.DoNotDisturbDate) =&gt; void

**起始版本：** 11

<!--Device-NotificationSubscriber-onDoNotDisturbChanged?: (mode: notificationManager.DoNotDisturbDate) => void--><!--Device-NotificationSubscriber-onDoNotDisturbChanged?: (mode: notificationManager.DoNotDisturbDate) => void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onDoNotDisturbDateChange

```TypeScript
onDoNotDisturbDateChange?: (mode: notification.DoNotDisturbDate) => void
```

回调返回免打扰时间选项变更。

**类型：** (mode: notification.DoNotDisturbDate) =&gt; void

**起始版本：** 8

**废弃版本：** 11

**替代接口：** [onDoNotDisturbChanged](arkts-notification-notificationsubscriber-notificationsubscriber-i-sys.md#ondonotdisturbchanged)

<!--Device-NotificationSubscriber-onDoNotDisturbDateChange?: (mode: notification.DoNotDisturbDate) => void--><!--Device-NotificationSubscriber-onDoNotDisturbDateChange?: (mode: notification.DoNotDisturbDate) => void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onEnabledNotificationChanged

```TypeScript
onEnabledNotificationChanged?:(callbackData: EnabledNotificationCallbackData) => void
```

回调返回监听到的应用信息。

**类型：** (callbackData: EnabledNotificationCallbackData) =&gt; void

**起始版本：** 8

<!--Device-NotificationSubscriber-onEnabledNotificationChanged?:(callbackData: EnabledNotificationCallbackData) => void--><!--Device-NotificationSubscriber-onEnabledNotificationChanged?:(callbackData: EnabledNotificationCallbackData) => void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onEnabledPriorityByBundleChanged

```TypeScript
onEnabledPriorityByBundleChanged?: (callbackData: EnabledPriorityNotificationByBundleCallbackData) => void
```

返回应用通知优先级开关状态。

**类型：** (callbackData: EnabledPriorityNotificationByBundleCallbackData) =&gt; void

**起始版本：** 23

<!--Device-NotificationSubscriber-onEnabledPriorityByBundleChanged?: (callbackData: EnabledPriorityNotificationByBundleCallbackData) => void--><!--Device-NotificationSubscriber-onEnabledPriorityByBundleChanged?: (callbackData: EnabledPriorityNotificationByBundleCallbackData) => void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onEnabledPriorityChanged

```TypeScript
onEnabledPriorityChanged?: (callbackData: EnabledPriorityNotificationCallbackData) => void
```

返回通知优先级总开关状态。

**类型：** (callbackData: EnabledPriorityNotificationCallbackData) =&gt; void

**起始版本：** 23

<!--Device-NotificationSubscriber-onEnabledPriorityChanged?: (callbackData: EnabledPriorityNotificationCallbackData) => void--><!--Device-NotificationSubscriber-onEnabledPriorityChanged?: (callbackData: EnabledPriorityNotificationCallbackData) => void-End-->

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

<!--Device-NotificationSubscriber-onEnabledSilentReminderChanged?: EnabledSilentReminderChangedCallback--><!--Device-NotificationSubscriber-onEnabledSilentReminderChanged?: EnabledSilentReminderChangedCallback-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onNotificationSwitchChanged

```TypeScript
onNotificationSwitchChanged?: NotificationSwitchChangedCallback
```

返回由[notificationManager.setNotificationSwitch](arkts-notification-notificationmanager-setnotificationswitch-f-sys.md#setnotificationswitch-1)接口设置的通知开关状态变化。

**类型：** NotificationSwitchChangedCallback

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotificationSubscriber-onNotificationSwitchChanged?: NotificationSwitchChangedCallback--><!--Device-NotificationSubscriber-onNotificationSwitchChanged?: NotificationSwitchChangedCallback-End-->

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

<!--Device-NotificationSubscriber-onSystemUpdate?: SystemUpdateCallback--><!--Device-NotificationSubscriber-onSystemUpdate?: SystemUpdateCallback-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onUpdate

```TypeScript
onUpdate?:(data: NotificationSortingMap) => void
```

最新的通知排序列表。

**类型：** (data: NotificationSortingMap) =&gt; void

**起始版本：** 7

<!--Device-NotificationSubscriber-onUpdate?:(data: NotificationSortingMap) => void--><!--Device-NotificationSubscriber-onUpdate?:(data: NotificationSortingMap) => void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

