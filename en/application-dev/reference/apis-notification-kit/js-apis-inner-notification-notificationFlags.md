# NotificationFlags

<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=50e734d278c25dbb71273705da516c218b3754a1 translatedAt=2026-06-29T02:36:24.620Z pushedAt=2026-06-30T10:57:37.000Z -->

The **NotificationFlags** module implements a **NotificationFlags** instance.

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
| TYPE_NONE      | 0   | Default flag, which has the same effect as **TYPE_OPEN**.         |
| TYPE_OPEN      | 1   | The notification flag is opened.                    |
| TYPE_CLOSE     | 2   | The notification flag is closed.                    |