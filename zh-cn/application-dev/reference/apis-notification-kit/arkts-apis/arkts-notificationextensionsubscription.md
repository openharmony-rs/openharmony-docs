# @ohos.notificationExtensionSubscription

本模块提供管理通知扩展的能力，具体包括：打开通知扩展订阅设置界面、订阅和取消订阅通知扩展、获取和设置通知授权状态。

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Notification

## 导入模块

```TypeScript
import { notificationExtensionSubscription } from '@ohos.notificationExtensionSubscription';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[getAllSubscriptionBundles](arkts-notification-notificationextensionsubscription-getallsubscriptionbundles-f-sys.md#getAllSubscriptionBundles-1) | 获取所有具有ohos.permission.SUBSCRIBE_NOTIFICATION权限并且实现了<br/>[NotificationSubscriberExtensionAbility](arkts-notification-notificationsubscriberextensionability-c.md#NotificationSubscriberExtensionAbility)的应用列表。<br/>使用Promise异步回调。<br/> |
| [getSubscribeInfo](arkts-notification-notificationextensionsubscription-getsubscribeinfo-f.md#getSubscribeInfo-1) | 获取当前应用的通知扩展订阅信息。使用Promise异步回调。<br/> |
| <!--DelRow-->[getUserGrantedEnabledBundles](arkts-notification-notificationextensionsubscription-getusergrantedenabledbundles-f-sys.md#getUserGrantedEnabledBundles-1) | 获取指定应用中“已获取的本机通知”通知开关开启的应用列表。使用Promise异步回调。<br/> |
| [getUserGrantedEnabledBundles](arkts-notification-notificationextensionsubscription-getusergrantedenabledbundles-f.md#getUserGrantedEnabledBundles-2) | 获取指定应用中“已获取的本机通知”通知开关开启的应用列表。使用Promise异步回调。<br/> |
| <!--DelRow-->[getUserGrantedState](arkts-notification-notificationextensionsubscription-getusergrantedstate-f-sys.md#getUserGrantedState-1) | 查询指定应用的“允许获取本机通知”的开关状态。使用Promise异步回调。<br/> |
| [isUserGranted](arkts-notification-notificationextensionsubscription-isusergranted-f.md#isUserGranted-1) | 查询“允许获取本机通知”的开关状态。使用Promise异步回调。<br/> |
| [openSubscriptionSettings](arkts-notification-notificationextensionsubscription-opensubscriptionsettings-f.md#openSubscriptionSettings-1) | 打开应用的通知扩展订阅授权页面，以半模态弹窗形式显示。用户可在该页面授权“允许获取本机通知”开关与“已获取的本机通知”应用开关。<br/>使用Promise异步回调。<br/> |
| [openSubscriptionSettingsWithResult](arkts-notification-notificationextensionsubscription-opensubscriptionsettingswithresult-f.md#openSubscriptionSettingsWithResult-1) | 打开应用的通知扩展订阅授权页面，以半模态弹窗形式显示。用户可在该页面授权“允许获取本机通知”开关与“已获取的本机通知”应用开关。<br/>使用Promise异步回调，当半模态窗口关闭时返回用户设置的授权的结果。<br/> |
| <!--DelRow-->[setUserGrantedBundleState](arkts-notification-notificationextensionsubscription-setusergrantedbundlestate-f-sys.md#setUserGrantedBundleState-1) | 设置指定应用中“已获取的本机通知”的应用通知开关状态。使用Promise异步回调。<br/> |
| <!--DelRow-->[setUserGrantedState](arkts-notification-notificationextensionsubscription-setusergrantedstate-f-sys.md#setUserGrantedState-1) | 设置指定应用的“允许获取本机通知”的开关状态。使用Promise异步回调。<br/> |
| [subscribe](arkts-notification-notificationextensionsubscription-subscribe-f.md#subscribe-1) | 订阅通知扩展。使用[蓝牙模块](../../../../connectivity/connectivity-kit-intro.md#蓝牙简介)相关接口获取蓝牙设备的唯一地址后<br/>方可订阅。使用Promise异步回调。<br/> |
| [unsubscribe](arkts-notification-notificationextensionsubscription-unsubscribe-f.md#unsubscribe-1) | 取消通知扩展的订阅。使用Promise异步回调。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SubscribeType](arkts-notification-notificationextensionsubscription-subscribetype-e.md) | 表示通知扩展订阅的类型。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [BundleOption](arkts-notification-notificationextensionsubscription-bundleoption-t.md) | 指定应用的包信息。<br/> |
| [GrantedBundleInfo](arkts-notification-notificationextensionsubscription-grantedbundleinfo-t.md) | 授权应用的包信息。<br/> |
| [NotificationExtensionSubscriptionInfo](arkts-notification-notificationextensionsubscription-notificationextensionsubscriptioninfo-t.md) | 用于描述通知扩展订阅的信息。<br/> |
| [NotificationInfo](arkts-notification-notificationextensionsubscription-notificationinfo-t.md) | 通知订阅扩展能力中<br/>[onReceiveMessage](arkts-notification-notificationsubscriberextensionability-c.md#onReceiveMessage-1)<br/>回调的通知信息。<br/> |
| [UserGrantSetting](arkts-notification-notificationextensionsubscription-usergrantsetting-t.md) | 用户授权的设置信息。<br/> |

