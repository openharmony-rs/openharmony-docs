# NotificationTime

Describes the notification timing information.

> **NOTE:** 
> 
> The actual display effect depends on the device capabilities and the notification center UI style.

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## initialTime

```TypeScript
initialTime?: number
```

Initial time for the timer, which is used to set the starting point of the timer in the live view. The default value is **0**. Unit: ms.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## isCountDown

```TypeScript
isCountDown?: boolean
```

Whether it is countdown mode. The default value is **false**.

- **true**: The time is displayed decreasing from initialTime.  
- **false**: The time is displayed increasing from initialTime.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## isInTitle

```TypeScript
isInTitle?: boolean
```

Whether the time information is displayed in the notification title. The default value is **false**.

- **true**: The timer information will be embedded in the title area.  
- **false**: The timer information is displayed in a separate area.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## isPaused

```TypeScript
isPaused?: boolean
```

Whether the timer is paused. The default value is **false**.

- **true**: The timer is paused at the current value.  
- **false**: The timer runs normally.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.Notification.Notification
