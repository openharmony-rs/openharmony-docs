# NotificationInfo
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @cheerful_ricky-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

通知信息应描述与第三方可穿戴设备共享的内容。

> **说明：**
>
> 本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## NotificationInfo

**系统能力**：SystemCapability.Notification.Notification

| 名称 | 类型 | 只读 | 可选 | 说明 | 
| -------- | -------- | -------- | -------- | -------- |
| hashCode | string | 是 | 否 | 通知的唯一标识符。|
| notificationSlotType | [notificationManager.SlotType](../apis-notification-kit/js-apis-notificationManager.md#slottype)| 是 | 否 | 通知槽位类型。默认值为OTHER。 |
| content | [NotificationExtensionContent](js-apis-inner-notification-notificationExtensionContent.md) | 是 | 否 | 通知内容。 |
| bundleName | string | 是 | 否 | 创建通知的包名。|
| appName | string | 是 | 是 | 创建通知的应用程序名称。|
| deliveryTime | number | 是 | 是 | 通知发布的时间戳（毫秒数）。|
| deliveryTime | long | 是 | 是 | 通知发布时间戳。|
| groupName | string | 是 | 是 | 通知组名称。默认情况下此参数为空。|