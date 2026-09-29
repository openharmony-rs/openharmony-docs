# NotificationCheckResult (System API)

```TypeScript
export interface NotificationCheckResult
```

Describes the result of check notifications.

**Since:** 10

<!--Device-notificationManager-export interface NotificationCheckResult--><!--Device-notificationManager-export interface NotificationCheckResult-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## code

```TypeScript
code: number
```

Result code.

**0**: display.

**1**: no display.

**Type:** number

**Since:** 10

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-NotificationCheckResult-code: int--><!--Device-NotificationCheckResult-code: int-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## message

```TypeScript
message: string
```

Result.

**Type:** string

**Since:** 10

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-NotificationCheckResult-message: string--><!--Device-NotificationCheckResult-message: string-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
