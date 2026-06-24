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
import { notificationSubscribe } from '@ohos.notificationSubscribe';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[distributeOperation](arkts-notification-notificationsubscribe-distributeoperation-f-sys.md#distributeOperation-1) | 触发指定通知的跨设备协同操作（例如通知跨设备点击跳转、通知跨设备快捷回复等）。使用Promise异步回调。<br/> |
| <!--DelRow-->[remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-1) | 根据应用的包信息和通知键值，删除指定通知。使用callback异步回调。<br/> |
| <!--DelRow-->[remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-2) | 根据应用的包信息和通知键值，删除指定通知。使用Promise异步回调。<br/> |
| <!--DelRow-->[remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-3) | 通过通知的唯一ID，删除指定通知。使用callback异步回调。<br/> |
| <!--DelRow-->[remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-4) | 批量删除指定通知。使用callback异步回调。<br/> |
| <!--DelRow-->[remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-5) | 通过通知的唯一ID，删除指定通知。使用Promise异步回调。<br/> |
| <!--DelRow-->[remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-6) | 批量删除指定通知。使用Promise异步回调。<br/> |
| <!--DelRow-->[removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md#removeAll-1) | 删除指定应用的所有通知。使用callback异步回调。<br/> |
| <!--DelRow-->[removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md#removeAll-2) | 删除所有通知。使用callback异步回调。<br/> |
| <!--DelRow-->[removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md#removeAll-3) | 删除指定用户下的所有通知。使用callback异步回调。<br/> |
| <!--DelRow-->[removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md#removeAll-4) | 删除指定用户下的所有通知。使用Promise异步回调。<br/> |
| <!--DelRow-->[removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md#removeAll-5) | 删除指定应用的所有通知。使用Promise异步回调。<br/> |
| <!--DelRow-->[subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md#subscribe-1) | 订阅当前用户下所有应用的通知。使用callback异步回调。<br/> |
| <!--DelRow-->[subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md#subscribe-2) | 订阅通知并指定订阅信息。使用callback异步回调。<br/> |
| <!--DelRow-->[subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md#subscribe-3) | 订阅通知并指定订阅信息。使用Promise异步回调。<br/> |
| <!--DelRow-->[subscribeNotification](arkts-notification-notificationsubscribe-subscribenotification-f-sys.md#subscribeNotification-1) | 订阅通知；订阅后，通过订阅者中的回调函数接收新消息。使用Promise异步回调。<br/> |
| <!--DelRow-->[subscribeNotification](arkts-notification-notificationsubscribe-subscribenotification-f-sys.md#subscribeNotification-2) | 订阅通知；订阅后，通过订阅者中的回调函数接收新消息。使用Promise异步回调。<br/> |
| <!--DelRow-->[subscribeSelf](arkts-notification-notificationsubscribe-subscribeself-f-sys.md#subscribeSelf-1) | 订阅本应用的通知并指定订阅信息。使用Promise异步回调。<br/> |
| <!--DelRow-->[unsubscribe](arkts-notification-notificationsubscribe-unsubscribe-f-sys.md#unsubscribe-1) | 取消订阅。使用callback异步回调。<br/> |
| <!--DelRow-->[unsubscribe](arkts-notification-notificationsubscribe-unsubscribe-f-sys.md#unsubscribe-2) | 取消订阅。使用Promise异步回调。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[NotificationKey](arkts-notification-notificationsubscribe-notificationkey-i-sys.md) | 通知键值。<br/> |
| <!--DelRow-->[OperationInfo](arkts-notification-notificationsubscribe-operationinfo-i-sys.md) | 跨设备协同操作信息。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[RemoveReason](arkts-notification-notificationsubscribe-removereason-e-sys.md) | 通知删除原因。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[BadgeNumberCallbackData](arkts-notification-notificationsubscribe-badgenumbercallbackdata-t-sys.md) | 回调返回监听到的应用信息。<br/> |
| <!--DelRow-->[BundleOption](arkts-notification-notificationsubscribe-bundleoption-t-sys.md) | 描述BundleOption信息，即应用的包信息。<br/> |
| <!--DelRow-->[EnabledNotificationCallbackData](arkts-notification-notificationsubscribe-enablednotificationcallbackdata-t-sys.md) | 回调返回监听到的应用信息。<br/> |
| <!--DelRow-->[EnabledPriorityNotificationByBundleCallbackData](arkts-notification-notificationsubscribe-enabledprioritynotificationbybundlecallbackdata-t-sys.md) | 返回应用通知优先级开关状态。<br/> |
| <!--DelRow-->[EnabledPriorityNotificationCallbackData](arkts-notification-notificationsubscribe-enabledprioritynotificationcallbackdata-t-sys.md) | 返回通知优先级总开关状态。<br/> |
| <!--DelRow-->[EnabledSilentReminderCallbackData](arkts-notification-notificationsubscribe-enabledsilentremindercallbackdata-t-sys.md) | 回调返回监听到的静默提醒使能状态信息。<br/> |
| <!--DelRow-->[EnabledSilentReminderChangedCallback](arkts-notification-notificationsubscribe-enabledsilentreminderchangedcallback-t-sys.md) | 注册应用通知静默提醒使能状态变化的回调函数类型。<br/> |
| <!--DelRow-->[NotificationClassification](arkts-notification-notificationsubscribe-notificationclassification-t-sys.md) | 描述通知分类信息。<br/> |
| <!--DelRow-->[NotificationSubscribeInfo](arkts-notification-notificationsubscribe-notificationsubscribeinfo-t-sys.md) | 通知发布者的信息。<br/> |
| <!--DelRow-->[NotificationSubscriber](arkts-notification-notificationsubscribe-notificationsubscriber-t-sys.md) | 作为订阅通知接口subscribe的入参，提供订阅者接收到新通知、取消通知等的回调方法。<br/> |
| <!--DelRow-->[NotificationSwitchChangedCallback](arkts-notification-notificationsubscribe-notificationswitchchangedcallback-t-sys.md) | 注册由[notificationManager.setNotificationSwitch]{@link<br/>./@ohos.notificationManager:notificationManager.setNotificationSwitch}接口设置的通知开关状态变化的回调函数类型。<br/> |
| <!--DelRow-->[NotificationSwitchChangedCallbackData](arkts-notification-notificationsubscribe-notificationswitchchangedcallbackdata-t-sys.md) | 描述通知开关状态变化的回调数据。<br/> |
| <!--DelRow-->[SubscribeCallbackData](arkts-notification-notificationsubscribe-subscribecallbackdata-t-sys.md) | 携带系统属性值的通知信息。<br/> |
| <!--DelRow-->[VoiceContent](arkts-notification-notificationsubscribe-voicecontent-t-sys.md) | 通知消息中语音播报内容定义。<br/> |
| <!--DelRow-->[VoiceContentOptions](arkts-notification-notificationsubscribe-voicecontentoptions-t-sys.md) | 实况通知语音播报内容配置项。<br/> |

