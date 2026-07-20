# @ohos.notificationExtensionSubscription

本模块提供管理通知扩展的能力，具体包括：打开通知扩展订阅设置界面、订阅和取消订阅通知扩展、获取和设置通知授权状态。

> **说明：**  
>  
> 本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 22

<!--Device-unnamed-declare namespace notificationExtensionSubscription--><!--Device-unnamed-declare namespace notificationExtensionSubscription-End-->

**系统能力：** SystemCapability.Notification.Notification

## 导入模块

```TypeScript
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getSubscribeInfo](arkts-notification-notificationextensionsubscription-getsubscribeinfo-f.md#getsubscribeinfo) | 获取当前应用的通知扩展订阅信息。使用Promise异步回调。 |
| [getUserGrantedEnabledBundles](arkts-notification-notificationextensionsubscription-getusergrantedenabledbundles-f.md#getusergrantedenabledbundles-1) | 获取指定应用中“已获取的本机通知”通知开关开启的应用列表。使用Promise异步回调。 |
| [isUserGranted](arkts-notification-notificationextensionsubscription-isusergranted-f.md#isusergranted) | 查询“允许获取本机通知”的开关状态。使用Promise异步回调。 |
| [openSubscriptionSettings](arkts-notification-notificationextensionsubscription-opensubscriptionsettings-f.md#opensubscriptionsettings) | 打开应用的通知扩展订阅授权页面，以半模态弹窗形式显示。用户可在该页面授权“允许获取本机通知”开关与“已获取的本机通知”应用开关。使用Promise异步回调。 |
| [openSubscriptionSettingsWithResult](arkts-notification-notificationextensionsubscription-opensubscriptionsettingswithresult-f.md#opensubscriptionsettingswithresult) | 打开应用的通知扩展订阅授权页面，以半模态弹窗形式显示。用户可在该页面授权“允许获取本机通知”开关与“已获取的本机通知”应用开关。使用Promise异步回调，当半模态窗口关闭时返回用户设置的授权的结果。 |
| [subscribe](arkts-notification-notificationextensionsubscription-subscribe-f.md#subscribe) | 订阅通知扩展。使用蓝牙模块相关接口获取蓝牙设备的唯一地址后方可订阅。使用Promise异步回调。 |
| [unsubscribe](arkts-notification-notificationextensionsubscription-unsubscribe-f.md#unsubscribe) | 取消通知扩展的订阅。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getAllSubscriptionBundles](arkts-notification-notificationextensionsubscription-getallsubscriptionbundles-f-sys.md#getallsubscriptionbundles) | 获取所有具有ohos.permission.SUBSCRIBE_NOTIFICATION权限并且实现了[NotificationSubscriberExtensionAbility](arkts-notification-application-notificationsubscriberextensionability-notificationsubscriberextensionability-c.md)的应用列表。使用Promise异步回调。 |
| [getUserGrantedEnabledBundles](arkts-notification-notificationextensionsubscription-getusergrantedenabledbundles-f-sys.md#getusergrantedenabledbundles) | 获取指定应用中“已获取的本机通知”通知开关开启的应用列表。使用Promise异步回调。 |
| [getUserGrantedState](arkts-notification-notificationextensionsubscription-getusergrantedstate-f-sys.md#getusergrantedstate) | 查询指定应用的“允许获取本机通知”的开关状态。使用Promise异步回调。 |
| [setUserGrantedBundleState](arkts-notification-notificationextensionsubscription-setusergrantedbundlestate-f-sys.md#setusergrantedbundlestate) | 设置指定应用中“已获取的本机通知”的应用通知开关状态。使用Promise异步回调。 |
| [setUserGrantedState](arkts-notification-notificationextensionsubscription-setusergrantedstate-f-sys.md#setusergrantedstate) | 设置指定应用的“允许获取本机通知”的开关状态。使用Promise异步回调。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SubscribeType](arkts-notification-notificationextensionsubscription-subscribetype-e.md) | 表示通知扩展订阅的类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [BundleOption](arkts-notification-notificationextensionsubscription-bundleoption-t.md) | 指定应用的包信息。 |
| [GrantedBundleInfo](arkts-notification-notificationextensionsubscription-grantedbundleinfo-t.md) | 授权应用的包信息。 |
| [NotificationExtensionSubscriptionInfo](arkts-notification-notificationextensionsubscription-notificationextensionsubscriptioninfo-t.md) | 用于描述通知扩展订阅的信息。 |
| [NotificationInfo](arkts-notification-notificationextensionsubscription-notificationinfo-t.md) | 通知订阅扩展能力中[onReceiveMessage](arkts-notification-application-notificationsubscriberextensionability-notificationsubscriberextensionability-c.md#onreceivemessage-1)回调的通知信息。 |
| [UserGrantSetting](arkts-notification-notificationextensionsubscription-usergrantsetting-t.md) | 用户授权的设置信息。 |

