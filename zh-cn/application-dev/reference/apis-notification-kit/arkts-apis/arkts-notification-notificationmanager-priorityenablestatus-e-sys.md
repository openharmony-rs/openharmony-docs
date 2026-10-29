# PriorityEnableStatus（系统接口）

```TypeScript
export enum PriorityEnableStatus
```

描述应用通知的优先级开关状态。

**起始版本：** 23

<!--Device-notificationManager-export enum PriorityEnableStatus--><!--Device-notificationManager-export enum PriorityEnableStatus-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## DISABLE

```TypeScript
DISABLE = 0
```

应用通知的优先级开关为关闭状态。

**起始版本：** 23

<!--Device-PriorityEnableStatus-DISABLE = 0--><!--Device-PriorityEnableStatus-DISABLE = 0-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## ENABLE

```TypeScript
ENABLE = 2
```

应用通知均设置为优先通知。

**起始版本：** 23

<!--Device-PriorityEnableStatus-ENABLE = 2--><!--Device-PriorityEnableStatus-ENABLE = 2-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## ENABLE_BY_INTELLIGENT

```TypeScript
ENABLE_BY_INTELLIGENT = 1
```

应用通知的优先级开关为智能识别状态。允许经智能识别、用户关键词匹配、应用规则匹配等方式设置为[优先通知](../../../notification/notification-glossary.md#priority-notification优先通知)。

**起始版本：** 23

<!--Device-PriorityEnableStatus-ENABLE_BY_INTELLIGENT = 1--><!--Device-PriorityEnableStatus-ENABLE_BY_INTELLIGENT = 1-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。
