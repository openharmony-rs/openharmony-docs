# NotificationCheckResult (System API)

Describes the result of check notifications.

**Since:** 10

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

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
