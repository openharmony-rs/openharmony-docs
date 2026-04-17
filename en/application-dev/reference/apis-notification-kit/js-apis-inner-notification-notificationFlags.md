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
| soundEnabled     | [NotificationFlagStatus](#notificationflagstatus11) | Yes | Yes| Settings of the sound alert for the notification.   |
| vibrationEnabled | [NotificationFlagStatus](#notificationflagstatus11) | Yes | Yes| Settings of vibration for the notification.|


## NotificationFlagStatus<sup>11+</sup>

Enumerates the notification flag states.

**System capability**: SystemCapability.Notification.Notification

| Name          | Value | Description                              |
| -------------- | --- | --------------------------------- |
| TYPE_NONE      | 0   | Default flag, which has the same effect as **TYPE_OPEN**.         |
| TYPE_OPEN      | 1   | The notification flag is enabled.                    |
| TYPE_CLOSE     | 2   | The notification flag is disabled.                    |
