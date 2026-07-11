# NotificationSlot

<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=50e734d278c25dbb71273705da516c218b3754a1 translatedAt=2026-06-29T02:36:49.026Z pushedAt=2026-06-30T10:57:37.004Z -->

The **NotificationSlot** module provides APIs for defining the notification slots. The notification reminder modes vary according to notification slots.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## NotificationSlot

**System capability**: SystemCapability.Notification.Notification

| Name                | Type                | Read-Only| Optional| Description                  |
| -------------------- | ---------------------|---- | --- |----------------------|
| notificationType<sup>11+</sup>                 | [notificationManager.SlotType](js-apis-notificationManager.md#slottype) | No | Yes  | Channel type. |
| enabled<sup>9+</sup> | boolean               | Yes | Yes  | Whether to allow notifications to be published from this notification channel.<br> - **true**: yes.<br> - **false**: no.   |
| notificationLevel<sup>20+</sup>                 | [notificationManager.SlotLevel](js-apis-notificationManager.md#slotlevel) | No | Yes  | Notification level, which is used to describe the display priority and alert intensity of notifications of this channel type.           |
| desc                 | string                | No | Yes  | Description of the notification channel. The size cannot exceed 243 bytes, and the excess part will be truncated. |
| badgeFlag            | boolean               | No | Yes  | Whether to display the badge. The default value is **true**.<br> - **true**: Display the badge.<br> - **false**: Do not display the badge.              |
| bypassDnd            | boolean               | No | Yes  | Whether to bypass Do Not Disturb mode in the system. The default value is **false**.<br> - **true**: Bypass Do Not Disturb mode, and notifications will still be alerted in Do Not Disturb mode.<br> - **false**: Do not bypass Do Not Disturb mode, and notifications will not be alerted in Do Not Disturb mode.      |
| vibrationEnabled     | boolean               | No | Yes  | Whether to enable vibration. The default value is **false**.<br> - **true**: yes.<br> - **false**: no.                  |
| sound                | string                | No | Yes  | File name of the custom ringtone for notifications from this channel. The file is placed in the **resources/rawfile** directory, and formats such as M4A, AAC, MP3, OGG, WAV, FLAC, and AMR are supported. The size cannot exceed 243 bytes, and the excess part will be truncated. |
| lightEnabled         | boolean               | No | Yes  | Whether to enable the light. The default value is **false**.<br> - **true**: yes.<br> - **false**: no.                        |
| type<sup>(deprecated)</sup> | [notification.SlotType](js-apis-notification.md#slottype) | No | Yes  | Channel type.<br> This parameter is supported since API version 7 and deprecated since API version 11. It is recommended to use **notificationType** instead.        |
| level<sup>(deprecated)</sup> | [notification.SlotLevel](js-apis-notificationManager.md#slotlevel) | No| Yes | Notification level.<br>This parameter is supported since API version 7 and deprecated since API version 20. It is recommended to use **notificationLevel** instead.|
| lockscreenVisibility | number                | No| Yes | Mode for displaying the notification on the lock screen. This is a reserved capability and is not supported currently.      |
| lightColor           | number                | No| Yes | Indicator color of the notification. This is a reserved capability and is not supported currently.              |
| vibrationValues      | Array\<number\>       | No| Yes | Vibration mode of the notification. This is a reserved capability and is not supported currently.             |