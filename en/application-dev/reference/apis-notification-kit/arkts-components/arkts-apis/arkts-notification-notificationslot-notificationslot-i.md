# NotificationSlot

The **NotificationSlot** module provides APIs for defining the notification slots. The notification reminder modes vary according to notification slots.

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## badgeFlag

```TypeScript
badgeFlag?: boolean
```

Whether to display the badge. The default value is **true**.

- **true**: Display the badge.  
- **false**: Do not display the badge.

**Type:** boolean

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## bypassDnd

```TypeScript
bypassDnd?: boolean
```

Whether to bypass Do Not Disturb mode in the system. The default value is **false**.

- **true**: Bypass Do Not Disturb mode, and notifications will still be alerted in Do Not Disturb mode.  
- **false**: Do not bypass Do Not Disturb mode, and notifications will not be alerted in Do Not Disturb mode.

**Type:** boolean

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## desc

```TypeScript
desc?: string
```

Description of the notification channel. The size cannot exceed 243 bytes, and the excess part will be truncated.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## enabled

```TypeScript
readonly enabled?: boolean
```

Whether to allow notifications of this slot type to be published.

- **true**: yes.  
- **false**: no.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

## level

```TypeScript
level?: notification.SlotLevel
```

Notification level.

**Type:** [notification.SlotLevel](arkts-notification-notification-slotlevel-depr-e.md)

**Since:** 7

**Deprecated since:** 20

**Substitutes:** [notificationLevel](#notificationlevel)

**System capability:** SystemCapability.Notification.Notification

## lightColor

```TypeScript
lightColor?: number
```

Indicator color of the notification. This is a reserved capability and is not supported currently.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## lightEnabled

```TypeScript
lightEnabled?: boolean
```

Whether to enable the light. The default value is **false**.

- **true**: yes.  
- **false**: no.

**Type:** boolean

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## lockscreenVisibility

```TypeScript
lockscreenVisibility?: number
```

Mode for displaying the notification on the lock screen. This is a reserved capability and is not supported currently.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## notificationLevel

```TypeScript
notificationLevel?: notificationManager.SlotLevel
```

Notification level, which is used to describe the display priority and alert intensity of notifications of this channel type.

**Type:** [notificationManager.SlotLevel](arkts-notification-notificationmanager-slotlevel-e.md)

**Since:** 20

**System capability:** SystemCapability.Notification.Notification

## notificationType

```TypeScript
notificationType?: notificationManager.SlotType
```

Slot type. Different slot types have different notification reminder types.

**Type:** [notificationManager.SlotType](arkts-notification-notificationmanager-slottype-e.md)

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## sound

```TypeScript
sound?: string
```

File name of the custom ringtone for notifications from this channel. The file is placed in the **resources/rawfile** directory, and formats such as M4A, AAC, MP3, OGG, WAV, FLAC, and AMR are supported. The size cannot exceed 243 bytes, and the excess part will be truncated.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## type

```TypeScript
type?: notification.SlotType
```

Channel type.

**Type:** [notification.SlotType](arkts-notification-notification-slottype-depr-e.md)

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [notificationType](#notificationtype)

**System capability:** SystemCapability.Notification.Notification

## vibrationEnabled

```TypeScript
vibrationEnabled?: boolean
```

Whether to enable vibration. The default value is **false**.

- **true**: yes.  
- **false**: no.

**Type:** boolean

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## vibrationValues

```TypeScript
vibrationValues?: Array<number>
```

Vibration mode of the notification. This is a reserved capability and is not supported currently.

**Type:** Array&lt;number&gt;

**Since:** 7

**System capability:** SystemCapability.Notification.Notification
