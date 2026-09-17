# OperationInfo (System API)

Defines cross-device collaborative operation information.

**Since:** 18

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { notificationSubscribe } from '@kit.NotificationKit';
```

## actionName

```TypeScript
actionName?: string
```

Operation button displayed in the notification. The value must be the same as that of **title** in [NotificationActionButton](arkts-notification-notificationactionbutton-notificationactionbutton-i.md).

**Type:** string

**Since:** 18

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## buttonIndex

```TypeScript
buttonIndex?: number
```

Index of the non-live view button or live view auxiliary area that the user taps.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## operationType

```TypeScript
operationType?: number
```

Operation type.

- **0**: The user taps the non-live view.  
- **1**: The user taps the non-live view button.  
- **32**: The user taps the live view.  
- **33**: The user taps the live view auxiliary area.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## userInput

```TypeScript
userInput?: string
```

User input, used to apply quick reply across devices. The value must be the same as that of **inputKey** in [NotificationUserInput](arkts-notification-notificationuserinput-notificationuserinput-i.md).

**Type:** string

**Since:** 18

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
