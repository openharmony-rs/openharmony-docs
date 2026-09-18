# BundleNotificationStatistics (System API)

Describes the notification statistics of a specified application.

**Since:** 26.0.0

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## bundle

```TypeScript
bundle: BundleOption
```

Bundle information of the application.

**Type:** [BundleOption](arkts-notification-notificationmanager-bundleoption-t.md)

**Since:** 26.0.0

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## lastTime

```TypeScript
lastTime: number
```

Time when the app last published a notification.<br>Data format: timestamp.<br>Unit: millisecond.

**Type:** number

**Since:** 26.0.0

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## recentCount

```TypeScript
recentCount: number
```

Total number of notifications published by the application in the last seven days.

**Type:** number

**Since:** 26.0.0

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
