# NotificationSlot
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @wangsen1994-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=1ded46b3f2c6157598c112b16f192beb1f37cf1d translatedAt=2026-10-08T02:20:34.985Z pushedAt=2026-10-08T09:28:21.319Z -->

Describes the [notification slot](../../notification/notification-glossary.md#notification-slot). Different notification slots have different [notification reminder modes](../../notification/notification-glossary.md#notification-reminder-mode).

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## NotificationSlot

**System capability**: SystemCapability.Notification.Notification

| Name                | Type                | Read-Only| Optional| Description                  |
| -------------------- | ---------------------|---- | --- |----------------------|
| notificationType<sup>11+</sup>                 | [notificationManager.SlotType](js-apis-notificationManager.md#slottype) | No | Yes  | Slot type. Different slot types have different [notification reminder modes](../../notification/notification-glossary.md#notification-reminder-mode). |
| enabled<sup>9+</sup> | boolean               | Yes | Yes  | Whether to allow publishing notifications of this [notification slot](../../notification/notification-glossary.md#notification-slot) type.<br> - **true**: publishing notifications is allowed.<br> - **false**: publishing notifications is prohibited.   |
| notificationLevel<sup>20+</sup>                 | [notificationManager.SlotLevel](js-apis-notificationManager.md#slotlevel) | No | Yes  | Notification level, which is used to describe the display priority and alert intensity of notifications of this slot type.           |
| desc                 | string                | No | Yes  | Description of the notification slot. The size cannot exceed 243 bytes, and the excess part will be truncated. |
| badgeFlag            | boolean               | No | Yes  | Whether to display the badge. The default value is **true**.<br> - **true**: Display the badge.<br> - **false**: Do not display the badge.              |
| bypassDnd            | boolean               | No | Yes  | Whether to bypass [Do Not Disturb mode](../../notification/notification-glossary.md#do-not-disturb-mode) in the system. The default value is **false**.<br> - **true**: bypasses Do Not Disturb mode, and notifications are still reminded in Do Not Disturb mode.<br> - **false**: does not bypass Do Not Disturb mode, and notifications are not reminded in Do Not Disturb mode.      |
| vibrationEnabled     | boolean               | No | Yes  | Whether to enable vibration. The default value is **false**.<br> - **true**: yes.<br> - **false**: no.                  |
| sound                | string                | No | Yes  | File name of the [customized ringtone](../../notification/notification-glossary.md#customized-ringtone) for notifications of this slot. The file is stored in the resources/rawfile directory and supports formats such as m4a, aac, mp3, ogg, wav, flac, and amr. The size cannot exceed 243 bytes, and the excess part is truncated. |
| lightEnabled         | boolean               | No | Yes  | Whether to enable the light. The default value is **false**.<br> - **true**: yes.<br> - **false**: no.                        |
| type<sup>(deprecated)</sup> | [notification.SlotType](js-apis-notification.md#slottype) | No | Yes  | Slot type.<br> This parameter is supported since API version 7 and deprecated since API version 11. It is recommended to use **notificationType** instead.        |
| level<sup>(deprecated)</sup> | [notification.SlotLevel](js-apis-notification.md#slotlevel) | No | Yes | Notification level.<br>This parameter is supported since API version 7 and deprecated since API version 20. It is recommended to use **notificationLevel** instead. |
| lockscreenVisibility | number                | No| Yes | Mode for displaying the notification on the lock screen. This is a reserved capability and is not supported currently.      |
| lightColor           | number                | No| Yes | Indicator color of the notification. This is a reserved capability and is not supported currently.              |
| vibrationValues      | Array\<number\>       | No| Yes | Vibration mode of the notification. This is a reserved capability and is not supported currently.             |
