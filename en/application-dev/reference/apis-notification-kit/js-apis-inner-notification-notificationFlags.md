# NotificationFlags

<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=9aa812250f4e9aa6e205822b2fc097b3c5b2a47d translatedAt=2026-07-21T01:08:31.066Z pushedAt=2026-07-21T09:31:51.864Z -->

The **NotificationFlags** module describes the notification flags. An application can use **NotificationFlags** to reduce the notification reminder types as needed.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## NotificationFlags

Defines the notification flags.

**System capability**: SystemCapability.Notification.Notification

| Name            | Type                   | Read Only| Optional| Description                                        |
| ---------------- | ---------------------- | ---- | -----|-------------------------------------------- |
| soundEnabled     | [NotificationFlagStatus](#notificationflagstatus11) | No | Yes| Settings of sound for the notification. The default value is **TYPE_NONE**. This parameter becomes writable starting from API version 23. Only [TYPE_CLOSE](#notificationflagstatus11) takes effect.   |
| vibrationEnabled | [NotificationFlagStatus](#notificationflagstatus11) | No | Yes| Settings of vibration for the notification. The default value is **TYPE_NONE**. This parameter becomes writable starting from API version 23. Only [TYPE_CLOSE](#notificationflagstatus11) takes effect.|
| bannerEnabled<sup>23+</sup> | [NotificationFlagStatus](#notificationflagstatus11) | No | Yes| Settings of banner for the notification. The default value is **TYPE_NONE**. Only [TYPE_CLOSE](#notificationflagstatus11) takes effect.|
| lockScreenEnabled<sup>23+</sup> | [NotificationFlagStatus](#notificationflagstatus11) | No | Yes| Settings of screen lock for the notification. The default value is **TYPE_NONE**. Only [TYPE_CLOSE](#notificationflagstatus11) takes effect.|

## NotificationFlagStatus<sup>11+</sup>

Enumerates the notification flag states.

**System capability**: SystemCapability.Notification.Notification

| Name          | Value | Description                              |
| -------------- | --- | --------------------------------- |
| TYPE_NONE      | 0   | Default flag when no flag is set. It has the same effect as **TYPE_OPEN**.     |
| TYPE_OPEN      | 1   | The notification flag is opened.                    |
| TYPE_CLOSE     | 2   | The notification flag is closed.                    |