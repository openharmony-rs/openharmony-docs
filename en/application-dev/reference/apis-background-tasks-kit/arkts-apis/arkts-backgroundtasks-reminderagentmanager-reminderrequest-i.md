# ReminderRequest

```TypeScript
interface ReminderRequest
```

Defines the request for publishing a reminder.

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## Modules to Import

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## actionButton

```TypeScript
actionButton?: [ActionButton?, ActionButton?, ActionButton?]
```

Buttons displayed for the reminder notification.

For third-party applications, a maximum of two buttons are supported.

For system applications, a maximum of three buttons are supported in API version 10 and later versions, and a maximum of two buttons are supported in versions earlier than API version 10.

**Type:** [ActionButton?, ActionButton?, ActionButton?]

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## autoDeletedTime

```TypeScript
autoDeletedTime?: number
```

Time when the notification is automatically cleared.

The data format is timestamp, in milliseconds. For details, please refer to [NotificationRequest.autoDeletedTime](../../apis-notification-kit/arkts-apis/arkts-notification-notificationrequest-notificationrequest-i.md#autodeletedtime)

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Notification.ReminderAgent

## content

```TypeScript
content?: string
```

Reminder content.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## contentResourceId

```TypeScript
contentResourceId?: number
```

Resource ID of the reminder content, which can be obtained through $r(*resource-name*).id.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.Notification.ReminderAgent

## customRingUri

```TypeScript
customRingUri?: string
```

URI of the custom prompt tone. The prompt tone file must be stored in the **resources/rawfile** directory and supports formats such as M4A, AAC, MP3, OGG, WAV, FLAC, and AMR.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Notification.ReminderAgent

## expiredContent

```TypeScript
expiredContent?: string
```

Content to be displayed after the reminder expires.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## expiredContentResourceId

```TypeScript
expiredContentResourceId?: number
```

Resource ID of the content to be displayed after the reminder expires, which can be obtained through $r(*resource -name*).id.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.Notification.ReminderAgent

## fixedTimeZone

```TypeScript
fixedTimeZone?: TimeZoneType
```

Time zone type. The default value is **TimeZoneType.DEFAULT**.

**Type:** [TimeZoneType](arkts-backgroundtasks-reminderagentmanager-timezonetype-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.ReminderAgent

## groupId

```TypeScript
groupId?: string
```

Group ID used for the reminder. If "Don't ask again" or similar information is selected for the reminder, other reminders with the same group ID are also canceled.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Notification.ReminderAgent

## maxScreenWantAgent

```TypeScript
maxScreenWantAgent?: MaxScreenWantAgent
```

Information about the ability that is started automatically and displayed in full-screen mode when the reminder arrives. If the device is in use, only a notification banner is displayed.

This API is reserved.

**Type:** [MaxScreenWantAgent](arkts-backgroundtasks-reminderagentmanager-maxscreenwantagent-i.md)

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## notificationId

```TypeScript
notificationId?: number
```

Notification ID used by the reminder. You must pass in a notification ID. If there are reminders with the same notification ID, the later one will overwrite the earlier one. The default value is **0**.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## notificationRequestProxy

```TypeScript
notificationRequestProxy?: NotificationRequestProxy
```

Notification request message. This parameter is left empty by default.

**Type:** [NotificationRequestProxy](arkts-backgroundtasks-reminderagentmanager-notificationrequestproxy-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.ReminderAgent

## reminderType

```TypeScript
reminderType: ReminderType
```

Type of the reminder.

**Type:** [ReminderType](arkts-backgroundtasks-reminderagentmanager-remindertype-e.md)

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## ringChannel

```TypeScript
ringChannel?: RingChannel
```

Audio channel of the custom prompt tone. The default channel is the alarm channel.

**Type:** [RingChannel](arkts-backgroundtasks-reminderagentmanager-ringchannel-e.md)

**Since:** 20

**System capability:** SystemCapability.Notification.ReminderAgent

## ringDuration

```TypeScript
ringDuration?: number
```

Ringing duration.

The value ranges from 0 to1800, in seconds. The default value is **1**.

If the value is **0**, the system notification tone is used.

If the value is greater than 0 and [ReminderRequest.customRingUri](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md) is set, the reminder rings on the specified channel [ReminderRequest.ringChannel](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md). Otherwise, the custom notification tone of the agent-powered reminder is used.

The device vibrates when the reminder rings. Since API version 26.0.0, long vibration is supported, and the vibration duration is the same as the ring duration. In versions earlier than API 26.0.0, the device vibrates once quickly when the reminder rings.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## slotType

```TypeScript
slotType?: notification.SlotType
```

Type of the slot used by the reminder.

**Type:** [notification.SlotType](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager.md)

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## snoozeContent

```TypeScript
snoozeContent?: string
```

Content to be displayed when the reminder is snoozing. (It is not applicable to countdown reminders.)

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## snoozeContentResourceId

```TypeScript
snoozeContentResourceId?: number
```

Resource ID of the content to be displayed when the reminder is snoozing, which can be obtained through $r(*resource-name*).id.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.Notification.ReminderAgent

## snoozeSlotType

```TypeScript
snoozeSlotType?: notification.SlotType
```

Type of the slot used by the snoozed reminder. (It is not applicable to countdown reminders.)

**Type:** [notification.SlotType](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager.md)

**Since:** 11

**System capability:** SystemCapability.Notification.ReminderAgent

## snoozeTimes

```TypeScript
snoozeTimes?: number
```

Number of reminder snooze times. The default value is **0**. (It is not applicable to countdown reminders.)

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## tapDismissed

```TypeScript
tapDismissed?: boolean
```

Whether the reminder is automatically cleared. The default value is **true**. For details, see [NotificationRequest.tapDismissed](../../apis-notification-kit/arkts-apis/arkts-notification-notificationrequest-notificationrequest-i.md#tapdismissed)

- **true** (default): The reminder is automatically cleared after the notification or button is tapped.  
- **false**: The reminder is retained after the notification or button is tapped.

**Type:** boolean

**Since:** 10

**System capability:** SystemCapability.Notification.ReminderAgent

## timeInterval

```TypeScript
timeInterval?: number
```

Reminder snooze interval,

in seconds. The minimum value is 30s. (It is not applicable to countdown reminders.)

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## title

```TypeScript
title?: string
```

Reminder title.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## titleResourceId

```TypeScript
titleResourceId?: number
```

Resource ID of the reminder title, which can be obtained through $r(*resource-name*).id.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.Notification.ReminderAgent

## wantAgent

```TypeScript
wantAgent?: WantAgent
```

Information about the ability that is redirected to when the reminder is clicked.

**Type:** [WantAgent](arkts-backgroundtasks-reminderagentmanager-wantagent-i.md)

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent
