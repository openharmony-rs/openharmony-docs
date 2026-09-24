# NotificationCapsule

```TypeScript
export interface NotificationCapsule
```

Describes the notification capsule, which is used to display the capsule form in the live view.

> **NOTE:** 
> 
> The actual display effect depends on the device capabilities and the notification center UI style.

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## capsuleButtons

```TypeScript
capsuleButtons?: Array<NotificationIconButton>
```

Buttons of the notification capsule of an instant task. A maximum of two buttons are supported. This parameter is left empty by default.

**Type:** Array&lt;[NotificationIconButton](arkts-notification-notificationcontent-notificationiconbutton-i-sys.md)&gt;

**Since:** 18

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## content

```TypeScript
content?: string
```

Extended text of the capsule. This parameter is left empty by default.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## time

```TypeScript
time?: number
```

Display duration of the notification capsule of an instant task. The default value is **0**. Unit: second.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
