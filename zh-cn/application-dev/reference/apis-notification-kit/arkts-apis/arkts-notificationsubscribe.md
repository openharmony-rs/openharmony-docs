# @ohos.notificationSubscribe

本模块提供通知订阅、取消订阅、通知移除等，一般情况下，只有系统应用具有这些操作权限。

> **说明：**
>
> 本模块接口均为系统接口。

**起始版本：** 9

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
| [distributeOperation](arkts-notification-distributeoperation-f-sys.md#distributeoperation-1) | 触发指定通知的跨设备协同操作（例如通知跨设备点击跳转、通知跨设备快捷回复等）。使用Promise异步回调。 |
| [remove](arkts-notification-remove-f-sys.md#remove-1) | 根据应用的包信息和通知键值，删除指定通知。使用callback异步回调。 |
| [remove](arkts-notification-remove-f-sys.md#remove-2) | 根据应用的包信息和通知键值，删除指定通知。使用Promise异步回调。 |
| [remove](arkts-notification-remove-f-sys.md#remove-3) | 通过通知的唯一ID，删除指定通知。使用callback异步回调。 |
| [remove](arkts-notification-remove-f-sys.md#remove-4) | 批量删除指定通知。使用callback异步回调。 |
| [remove](arkts-notification-remove-f-sys.md#remove-5) | 通过通知的唯一ID，删除指定通知。使用Promise异步回调。 |
| [remove](arkts-notification-remove-f-sys.md#remove-6) | 批量删除指定通知。使用Promise异步回调。 |
| [removeAll](arkts-notification-removeall-f-sys.md#removeall-1) | 删除指定应用的所有通知。使用callback异步回调。 |
| [removeAll](arkts-notification-removeall-f-sys.md#removeall-2) | 删除所有通知。使用callback异步回调。 |
| [removeAll](arkts-notification-removeall-f-sys.md#removeall-3) | 删除指定用户下的所有通知。使用callback异步回调。 |
| [removeAll](arkts-notification-removeall-f-sys.md#removeall-4) | 删除指定用户下的所有通知。使用Promise异步回调。 |
| [removeAll](arkts-notification-removeall-f-sys.md#removeall-5) | 删除指定应用的所有通知。使用Promise异步回调。 |
| [subscribe](arkts-notification-subscribe-f-sys.md#subscribe-1) | 订阅当前用户下所有应用的通知。使用callback异步回调。 |
| [subscribe](arkts-notification-subscribe-f-sys.md#subscribe-2) | 订阅通知并指定订阅信息。使用callback异步回调。 |
| [subscribe](arkts-notification-subscribe-f-sys.md#subscribe-3) | 订阅通知并指定订阅信息。使用Promise异步回调。 |
| [subscribeNotification](arkts-notification-subscribenotification-f-sys.md#subscribenotification-1) | 订阅通知；订阅后，通过订阅者中的回调函数接收新消息。使用Promise异步回调。 |
| [subscribeNotification](arkts-notification-subscribenotification-f-sys.md#subscribenotification-2) | 订阅通知；订阅后，通过订阅者中的回调函数接收新消息。使用Promise异步回调。 |
| [subscribeSelf](arkts-notification-subscribeself-f-sys.md#subscribeself-1) | 订阅本应用的通知并指定订阅信息。使用Promise异步回调。 |
| [unsubscribe](arkts-notification-unsubscribe-f-sys.md#unsubscribe-1) | 取消订阅。使用callback异步回调。 |
| [unsubscribe](arkts-notification-unsubscribe-f-sys.md#unsubscribe-2) | 取消订阅。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [NotificationKey](arkts-notification-notificationkey-i-sys.md) | 通知键值。 |
| [OperationInfo](arkts-notification-operationinfo-i-sys.md) | 跨设备协同操作信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [RemoveReason](arkts-notification-removereason-e-sys.md) | 通知删除原因。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BadgeNumberCallbackData](arkts-notification-badgenumbercallbackdata-t-sys.md) | 回调返回监听到的应用信息。 |
| [BundleOption](arkts-notification-bundleoption-t-sys.md) | 描述BundleOption信息，即应用的包信息。 |
| [EnabledNotificationCallbackData](arkts-notification-enablednotificationcallbackdata-t-sys.md) | 回调返回监听到的应用信息。 |
| [EnabledPriorityNotificationByBundleCallbackData](arkts-notification-enabledprioritynotificationbybundlecallbackdata-t-sys.md) | 返回应用通知优先级开关状态。 |
| [EnabledPriorityNotificationCallbackData](arkts-notification-enabledprioritynotificationcallbackdata-t-sys.md) | 返回通知优先级总开关状态。 |
| [EnabledSilentReminderCallbackData](arkts-notification-enabledsilentremindercallbackdata-t-sys.md) | 回调返回监听到的静默提醒使能状态信息。 |
| [EnabledSilentReminderChangedCallback](arkts-notification-enabledsilentreminderchangedcallback-t-sys.md) | 注册应用通知静默提醒使能状态变化的回调函数类型。 |
| [NotificationClassification](arkts-notification-notificationclassification-t-sys.md) | 描述通知分类信息。 |
| [NotificationSubscribeInfo](arkts-notification-notificationsubscribeinfo-t-sys.md) | 通知发布者的信息。 |
| [NotificationSubscriber](arkts-notification-notificationsubscriber-t-sys.md) | 作为订阅通知接口subscribe的入参，提供订阅者接收到新通知、取消通知等的回调方法。 |
| [NotificationSwitchChangedCallback](arkts-notification-notificationswitchchangedcallback-t-sys.md) | 注册由[notificationManager.setNotificationSwitch]{@link./@ohos.notificationManager:notificationManager.setNotificationSwitch}接口设置的通知开关状态变化的回调函数类型。 |
| [NotificationSwitchChangedCallbackData](arkts-notification-notificationswitchchangedcallbackdata-t-sys.md) | 描述通知开关状态变化的回调数据。 |
| [SubscribeCallbackData](arkts-notification-subscribecallbackdata-t-sys.md) | 携带系统属性值的通知信息。 |
| [VoiceContent](arkts-notification-voicecontent-t-sys.md) | 通知消息中语音播报内容定义。 |
| [VoiceContentOptions](arkts-notification-voicecontentoptions-t-sys.md) | 实况通知语音播报内容配置项。 |
<!--DelEnd-->

