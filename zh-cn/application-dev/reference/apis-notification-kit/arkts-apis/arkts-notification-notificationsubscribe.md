# @ohos.notificationSubscribe(NotificationSubscribe模块)

本模块提供[通知订阅](../../../notification/notification-glossary.md#notification-subscription通知订阅)、取消订阅、通知移除等，一般情况下，只有系统应用具有这些操作权限。

**起始版本：** 9

<!--Device-unnamed-declare namespace notificationSubscribe--><!--Device-unnamed-declare namespace notificationSubscribe-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { notificationSubscribe } from '@kit.NotificationKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [distributeOperation](arkts-notification-notificationsubscribe-distributeoperation-f-sys.md#distributeoperation-1) | 触发指定通知的[跨设备协同](../../../notification/notification-glossary.md#cross-device-collaboration跨设备协同)操作（例如通知跨设备点击跳转、通知跨设备快捷回复等）。使用Promise异步回调。 |
| [remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-1) | 根据应用的包信息和通知键值，删除指定通知。使用callback异步回调。 |
| [remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-2) | 根据应用的包信息和通知键值，删除指定通知。使用Promise异步回调。 |
| [remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-3) | 通过通知的唯一ID，删除指定通知。使用callback异步回调。 |
| [remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-4) | 批量删除指定通知。使用callback异步回调。 |
| [remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-5) | 通过通知的唯一ID，删除指定通知。使用Promise异步回调。 |
| [remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-6) | 批量删除指定通知。使用Promise异步回调。 |
| [removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md#removeall-1) | 删除指定应用的所有通知。使用callback异步回调。 |
| [removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md#removeall-2) | 删除所有通知。使用callback异步回调。 |
| [removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md#removeall-3) | 删除指定用户下的所有通知。使用callback异步回调。 |
| [removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md#removeall-4) | 删除指定用户下的所有通知。使用Promise异步回调。 |
| [removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md#removeall-5) | 删除指定应用的所有通知。使用Promise异步回调。 |
| [subscribeNotification](arkts-notification-notificationsubscribe-subscribenotification-f-sys.md#subscribenotification-1) | 订阅通知；订阅后，通过订阅者中的回调函数接收新消息。使用Promise异步回调。 |
| [subscribeNotification](arkts-notification-notificationsubscribe-subscribenotification-f-sys.md#subscribenotification-2) | 订阅通知；订阅后，通过订阅者中的回调函数接收新消息。使用Promise异步回调。 |
| [subscribeSelf](arkts-notification-notificationsubscribe-subscribeself-f-sys.md#subscribeself-1) | 订阅本应用的通知。使用Promise异步回调。 |
| [unsubscribe](arkts-notification-notificationsubscribe-unsubscribe-f-sys.md#unsubscribe-1) | 取消订阅。使用callback异步回调。 |
| [unsubscribe](arkts-notification-notificationsubscribe-unsubscribe-f-sys.md#unsubscribe-2) | 取消订阅。使用Promise异步回调。 |
| [subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md#subscribe-1) | 订阅当前用户下所有应用的通知。使用callback异步回调。 |
| [subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md#subscribe-2) | 订阅通知并指定订阅信息。使用callback异步回调。 |
| [subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md#subscribe-3) | 订阅通知并指定订阅信息。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [NotificationKey](arkts-notification-notificationsubscribe-notificationkey-i-sys.md) | 通知键值。 |
| [OperationInfo](arkts-notification-notificationsubscribe-operationinfo-i-sys.md) | [跨设备协同](../../../notification/notification-glossary.md#cross-device-collaboration跨设备协同)操作信息。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BadgeNumberCallbackData](arkts-notification-notificationsubscribe-badgenumbercallbackdata-t-sys.md) | 应用角标数量变化的回调数据。 |
| [BundleOption](arkts-notification-notificationsubscribe-bundleoption-t-sys.md) | 描述BundleOption信息，即应用的包信息。 |
| [EnabledNotificationCallbackData](arkts-notification-notificationsubscribe-enablednotificationcallbackdata-t-sys.md) | 应用角标使能状态变化的回调数据。 |
| [EnabledPriorityNotificationByBundleCallbackData](arkts-notification-notificationsubscribe-enabledprioritynotificationbybundlecallbackdata-t-sys.md) | 应用通知优先级开关状态变化的回调数据。 |
| [EnabledPriorityNotificationCallbackData](arkts-notification-notificationsubscribe-enabledprioritynotificationcallbackdata-t-sys.md) | 通知优先级总开关状态变化的回调数据。 |
| [EnabledSilentReminderCallbackData](arkts-notification-notificationsubscribe-enabledsilentremindercallbackdata-t-sys.md) | 应用通知[静默提醒](../../../notification/notification-glossary.md#silent-reminder静默提醒)开关状态变化的回调数据。 |
| [EnabledSilentReminderChangedCallback](arkts-notification-notificationsubscribe-enabledsilentreminderchangedcallback-t-sys.md) | 注册应用通知[静默提醒](../../../notification/notification-glossary.md#silent-reminder静默提醒)使能状态变化的回调函数类型。 |
| [NotificationClassification](arkts-notification-notificationsubscribe-notificationclassification-t-sys.md) | 通知分类信息。 |
| [NotificationSubscribeInfo](arkts-notification-notificationsubscribe-notificationsubscribeinfo-t-sys.md) | 通知订阅者的信息。 |
| [NotificationSubscriber](arkts-notification-notificationsubscribe-notificationsubscriber-t-sys.md) | 提供订阅者接收到新通知、取消通知等的回调方法。 |
| [NotificationSwitchChangedCallback](arkts-notification-notificationsubscribe-notificationswitchchangedcallback-t-sys.md) | 注册由[notificationManager.setNotificationSwitch](arkts-notification-notificationmanager-setnotificationswitch-f-sys.md)接口设置的通知开关状态变化的回调函数类型。 |
| [NotificationSwitchChangedCallbackData](arkts-notification-notificationsubscribe-notificationswitchchangedcallbackdata-t-sys.md) | 通知开关状态变化的回调数据。 |
| [SubscribeCallbackData](arkts-notification-notificationsubscribe-subscribecallbackdata-t-sys.md) | 返回携带系统属性值的通知信息。 |
| [VoiceContent](arkts-notification-notificationsubscribe-voicecontent-t-sys.md) | 通知语音播报内容。 |
| [VoiceContentOptions](arkts-notification-notificationsubscribe-voicecontentoptions-t-sys.md) | Describes the properties of the voice content options for notification subscription. |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [RemoveReason](arkts-notification-notificationsubscribe-removereason-e-sys.md) | 通知删除原因。 |
<!--DelEnd-->
