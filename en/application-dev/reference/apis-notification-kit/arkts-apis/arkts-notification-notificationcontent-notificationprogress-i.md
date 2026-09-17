# NotificationProgress

Describes the notification progress, which is used to display progress bar information in the live view.

> **NOTE:** 
> 
> The actual display effect depends on the device capabilities and the notification center UI style.

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## currentValue

```TypeScript
currentValue?: number
```

Current value of the progress.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## isPercentage

```TypeScript
isPercentage?: boolean
```

Whether to display the progress as a percentage. The value defaults to **false**.

- **true**: The progress is displayed as a percentage.  
- **false**: The progress is displayed as an absolute value.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## maxValue

```TypeScript
maxValue?: number
```

Maximum value of the progress.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Notification.Notification
