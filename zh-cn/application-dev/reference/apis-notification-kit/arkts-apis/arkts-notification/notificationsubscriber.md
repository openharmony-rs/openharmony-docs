# notification/notificationSubscriber

## 汇总

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BadgeEnabledChangedCallback](notificationsubscriber-badgeenabledchangedcallback-i-sys.md) | 注册应用角标使能状态变化的回调函数类型。 type BadgeEnabledChangedCallback = (data: EnabledNotificationCallbackData) => void |
| [BadgeNumberCallbackData](notificationsubscriber-badgenumbercallbackdata-i-sys.md) | 应用角标数量变化的回调函数类型。 |
| [EnabledNotificationCallbackData](notificationsubscriber-enablednotificationcallbackdata-i-sys.md) | 应用使能状态变化的回调函数类型。 |
| [EnabledPriorityNotificationByBundleCallbackData](notificationsubscriber-enabledprioritynotificationbybundlecallbackdata-i-sys.md) | 应用通知优先级开关状态。 |
| [EnabledPriorityNotificationCallbackData](notificationsubscriber-enabledprioritynotificationcallbackdata-i-sys.md) | 通知优先级总开关状态。 |
| [EnabledSilentReminderCallbackData](notificationsubscriber-enabledsilentremindercallbackdata-i-sys.md) | 应用通知静默提醒开关状态的回调函数类型。 |
| [NotificationClassification](notificationsubscriber-notificationclassification-i-sys.md) | 通知分类信息。 |
| [NotificationSubscriber](notificationsubscriber-notificationsubscriber-i-sys.md) | 提供订阅者接收到新通知、取消通知等的回调方法。 |
| [NotificationSwitchChangedCallbackData](notificationsubscriber-notificationswitchchangedcallbackdata-i-sys.md) | 通知开关状态变化的回调函数类型。 |
| [SubscribeCallbackData](notificationsubscriber-subscribecallbackdata-i-sys.md) | 返回携带系统属性值的通知信息。 |
| [VoiceContent](notificationsubscriber-voicecontent-i-sys.md) | 通知语音播报内容。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BadgeEnabledChangedCallback](arkts-notification-badgeenabledchangedcallback-t-sys.md) | type BadgeEnabledChangedCallback = (data: EnabledNotificationCallbackData) => void 注册应用角标使能状态变化的回调函数类型。 |
| [EnabledSilentReminderChangedCallback](arkts-notification-enabledsilentreminderchangedcallback-t-sys.md) | 注册应用通知静默提醒使能状态变化的回调函数类型。 type EnabledSilentReminderChangedCallback = (callbackData: EnabledSilentReminderCallbackData) => void |
| [NotificationSwitchChangedCallback](arkts-notification-notificationswitchchangedcallback-t-sys.md) | 注册由[notificationManager.setNotificationSwitch]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_接口设置的通知开关状态变化的回调函数类型。 |
| [SystemUpdateCallback](arkts-notification-systemupdatecallback-t-sys.md) | type SystemUpdateCallback = (data: SubscribeCallbackData) => void 返回携带系统属性值通知信息的回调函数类型。 |
<!--DelEnd-->

