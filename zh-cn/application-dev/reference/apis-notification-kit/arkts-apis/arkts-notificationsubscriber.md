# notificationSubscriber

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[BadgeEnabledChangedCallback](arkts-notification-badgeenabledchangedcallback-i-sys.md) | 注册应用角标使能状态变化的回调函数类型。<br/>type BadgeEnabledChangedCallback = (data: EnabledNotificationCallbackData) =&gt; void<br/> |
| <!--DelRow-->[BadgeNumberCallbackData](arkts-notification-badgenumbercallbackdata-i-sys.md) | 应用通知角标数量状态变化的回调函数类型。<br/> |
| <!--DelRow-->[EnabledNotificationCallbackData](arkts-notification-enablednotificationcallbackdata-i-sys.md) | 应用角标使能状态变化。<br/> |
| <!--DelRow-->[EnabledPriorityNotificationByBundleCallbackData](arkts-notification-enabledprioritynotificationbybundlecallbackdata-i-sys.md) | 应用通知优先级开关状态<br/> |
| <!--DelRow-->[EnabledPriorityNotificationCallbackData](arkts-notification-enabledprioritynotificationcallbackdata-i-sys.md) | 通知优先级总开关状态。<br/> |
| <!--DelRow-->[EnabledSilentReminderCallbackData](arkts-notification-enabledsilentremindercallbackdata-i-sys.md) | 应用通知静默提醒使能状态变化。<br/> |
| <!--DelRow-->[NotificationClassification](arkts-notification-notificationclassification-i-sys.md) | 描述通知分类信息。<br/> |
| <!--DelRow-->[NotificationSubscriber](arkts-notification-notificationsubscriber-i-sys.md) | 提供订阅者接收到新通知、取消通知等的回调方法。<br/> |
| <!--DelRow-->[NotificationSwitchChangedCallbackData](arkts-notification-notificationswitchchangedcallbackdata-i-sys.md) | 描述通知开关状态变化的回调数据。<br/> |
| <!--DelRow-->[SubscribeCallbackData](arkts-notification-subscribecallbackdata-i-sys.md) | 返回携带系统属性值的通知信息。<br/> |
| <!--DelRow-->[VoiceContent](arkts-notification-voicecontent-i-sys.md) | 通知消息中语音播报内容定义<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[EnabledSilentReminderChangedCallback](arkts-notification-enabledsilentreminderchangedcallback-t-sys.md) | 注册应用通知静默提醒使能状态变化的回调函数类型。<br/>type EnabledSilentReminderChangedCallback = (callbackData: EnabledSilentReminderCallbackData) =&gt; void<br/> |
| <!--DelRow-->[NotificationSwitchChangedCallback](arkts-notification-notificationswitchchangedcallback-t-sys.md) | 注册由[notificationManager.setNotificationSwitch]{@link<br/>../@ohos.notificationManager:notificationManager.setNotificationSwitch}接口设置的通知开关状态变化的回调函数类型。<br/> |
| <!--DelRow-->[SystemUpdateCallback](arkts-notification-systemupdatecallback-t-sys.md) | type SystemUpdateCallback = (data: SubscribeCallbackData) =&gt; void<br/> |

