# NotificationFlags
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @michael_woo888-->
<!--Designer: @dongqingran; @wulong158-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

The **NotificationFlags** module implements a **NotificationFlags** instance.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## NotificationFlags

Defines the notification flags.

**System capability**: SystemCapability.Notification.Notification

| Name            | Type                   | Read Only| Optional| Description                                        |
| ---------------- | ---------------------- | ---- | -----|-------------------------------------------- |
| soundEnabled     | [NotificationFlagStatus](#notificationflagstatus11) | No | Yes| Settings of sound for the notification. This parameter becomes writable starting from API version 23. Only [TYPE_CLOSE](#notificationflagstatus11) takes effect.   |
| vibrationEnabled | [NotificationFlagStatus](#notificationflagstatus11) | No | Yes| Settings of vibration for the notification. This parameter becomes writable starting from API version 23. Only [TYPE_CLOSE](#notificationflagstatus11) takes effect.|
| bannerEnabled<sup>23+</sup> | [NotificationFlagStatus](#notificationflagstatus11) | No | Yes| Settings of banner for the notification. Only [TYPE_CLOSE](#notificationflagstatus11) takes effect.|
| lockScreenEnabled<sup>23+</sup> | [NotificationFlagStatus](#notificationflagstatus11) | No | Yes| Settings of screen lock for the notification. Only [TYPE_CLOSE](#notificationflagstatus11) takes effect.|


## NotificationFlagStatus<sup>11+</sup>

Enumerates the notification flag states.

**System capability**: SystemCapability.Notification.Notification

| Name          | Value | Description                              |
| -------------- | --- | --------------------------------- |
| TYPE_NONE      | 0   | The default flag is used. The effect is the same as that of **TYPE_OPEN**.         |
| TYPE_OPEN      | 1   | The notification flag is enabled.                    |
| TYPE_CLOSE     | 2   | The notification flag is disabled.                    |
