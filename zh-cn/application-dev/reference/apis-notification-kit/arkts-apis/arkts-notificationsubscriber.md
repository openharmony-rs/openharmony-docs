# notificationSubscriber

## 汇总

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BadgeEnabledChangedCallback](arkts-notification-badgeenabledchangedcallback-i-sys.md) | 注册应用角标使能状态变化的回调函数类型。type BadgeEnabledChangedCallback = (data: EnabledNotificationCallbackData) =&gt; void |
| [BadgeNumberCallbackData](arkts-notification-badgenumbercallbackdata-i-sys.md) | 应用通知角标数量状态变化的回调函数类型。 |
| [EnabledNotificationCallbackData](arkts-notification-enablednotificationcallbackdata-i-sys.md) | 应用角标使能状态变化。 |
| [EnabledPriorityNotificationByBundleCallbackData](arkts-notification-enabledprioritynotificationbybundlecallbackdata-i-sys.md) | 应用通知优先级开关状态 |
| [EnabledPriorityNotificationCallbackData](arkts-notification-enabledprioritynotificationcallbackdata-i-sys.md) | 通知优先级总开关状态。 |
| [EnabledSilentReminderCallbackData](arkts-notification-enabledsilentremindercallbackdata-i-sys.md) | 应用通知静默提醒使能状态变化。 |
| [NotificationClassification](arkts-notification-notificationclassification-i-sys.md) | 描述通知分类信息。 |
| [NotificationSubscriber](arkts-notification-notificationsubscriber-i-sys.md) | 提供订阅者接收到新通知、取消通知等的回调方法。 |
| [NotificationSwitchChangedCallbackData](arkts-notification-notificationswitchchangedcallbackdata-i-sys.md) | 描述通知开关状态变化的回调数据。 |
| [SubscribeCallbackData](arkts-notification-subscribecallbackdata-i-sys.md) | 返回携带系统属性值的通知信息。 |
| [VoiceContent](arkts-notification-voicecontent-i-sys.md) | 通知消息中语音播报内容定义 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [EnabledSilentReminderChangedCallback](arkts-notification-enabledsilentreminderchangedcallback-t-sys.md) | 注册应用通知静默提醒使能状态变化的回调函数类型。type EnabledSilentReminderChangedCallback = (callbackData: EnabledSilentReminderCallbackData) =&gt; void |
| [NotificationSwitchChangedCallback](arkts-notification-notificationswitchchangedcallback-t-sys.md) | 注册由[notificationManager.setNotificationSwitch]{@link../@ohos.notificationManager:notificationManager.setNotificationSwitch}接口设置的通知开关状态变化的回调函数类型。 |
| [SystemUpdateCallback](arkts-notification-systemupdatecallback-t-sys.md) | type SystemUpdateCallback = (data: SubscribeCallbackData) =&gt; void |
<!--DelEnd-->

