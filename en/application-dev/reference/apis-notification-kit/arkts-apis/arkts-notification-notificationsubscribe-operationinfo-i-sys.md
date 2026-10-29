# OperationInfo (System API)

```TypeScript
export interface OperationInfo
```

Describes the [cross-device collaboration](../../../notification/notification-glossary.md#cross-device-collaboration) operation information.

**Since:** 18

<!--Device-notificationSubscribe-export interface OperationInfo--><!--Device-notificationSubscribe-export interface OperationInfo-End-->

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

Operation button displayed in the notification. The value must be the same as that of **title** in [NotificationActionButton](arkts-notification-notificationactionbutton-i.md).

**Type:** string

**Since:** 18

<!--Device-OperationInfo-actionName?: string--><!--Device-OperationInfo-actionName?: string-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## buttonIndex

```TypeScript
buttonIndex?: number
```

Index of the non-live view button or live view auxiliary area that the user taps.

**Type:** number

**Since:** 20

<!--Device-OperationInfo-buttonIndex?: int--><!--Device-OperationInfo-buttonIndex?: int-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## operationType

```TypeScript
operationType?: number
```

Type of the user click operation.

- **0**: The user clicks the non-[live view notification](../../../notification/notification-glossary.md#live-view-notification) body.  
- **1**: The user clicks a non-live-view notification button.  
- **32**: The user clicks the live view notification body.  
- **33**: The user clicks the auxiliary area of the live view notification.

**Type:** number

**Since:** 20

<!--Device-OperationInfo-operationType?: int--><!--Device-OperationInfo-operationType?: int-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## userInput

```TypeScript
userInput?: string
```

User input, used to apply quick reply across devices. The value must be the same as that of **inputKey** in [NotificationUserInput](arkts-notification-notificationuserinput-i.md).

**Type:** string

**Since:** 18

<!--Device-OperationInfo-userInput?: string--><!--Device-OperationInfo-userInput?: string-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
