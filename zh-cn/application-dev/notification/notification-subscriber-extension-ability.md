# 通知订阅拓展能力概述
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @cheerful_ricky-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
## NotificationSubscriberExtensionAbility 开发概述

### 功能简介

[NotificationSubscriberExtensionAbility](../reference/apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md)提供扩展能力，允许第三方应用接收系统通知并将其同步到穿戴设备。该能力主要用于支持手机与第三方穿戴设备之间的通知协同。一定时间内无通知发布或通知取消时[NotificationSubscriberExtensionAbility](../reference/apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md)会被销毁。

### 前提条件
- 用户已通过手机中与穿戴设备配套的应用程序连接穿戴设备。
- 用户已在手机中的穿戴应用中，开启"允许获取本机通知"开关与"已获取的本机通知"通知开关。
### 应用场景
<!--Del-->
- [生态诉求]：支持第三方穿戴接收系统通知
<!--DelEnd-->
- [使用场景]：手机通知同步到穿戴设备
- [传输方式]：支持低功耗蓝牙(BLE)和传统蓝牙两种同步方式

### 约束条件
- [授权方式]：系统授权
- [权限级别]：系统基础应用
- [分布式支持]：false (不支持分布式场景)
- [设备类型]：手机和平板
- [版本约束]：API Version 从 22 开始支持
- [协同设备]：支持将通知协同到已连接的第三方智能手表

### 核心接口
- [NotificationSubscriberExtensionAbility](../reference/apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md) - 扩展能力基类
- [NotificationSubscriberExtensionContext](../reference/apis-notification-kit/js-apis-notificationSubscriberExtensionContext.md) - 扩展上下文
- [NotificationInfo](../reference/apis-notification-kit/js-apis-inner-notification-notificationInfo.md) - 通知信息
- [NotificationExtensionContent](../reference/apis-notification-kit/js-apis-inner-notification-notificationExtensionContent.md) - 通知内容

### 运作机制
<img src="figures/notification_subscription_extension_ability.png" alt="notification_sibscriber_extension_ability" width="50%" height="50%">