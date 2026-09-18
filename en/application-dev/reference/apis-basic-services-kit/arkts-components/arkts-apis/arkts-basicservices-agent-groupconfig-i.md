# GroupConfig

Describes group configuration options for download tasks.

**Since:** 15

**System capability:** SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## gauge

```TypeScript
gauge?: boolean
```

Whether to send progress notifications. This parameter applies only to background tasks.

- **true**: The progress, success, and failure notifications are displayed.  
- **false**: Only success and failure notifications are displayed.

The default value is **false**.

**Type:** boolean

**Since:** 15

**System capability:** SystemCapability.Request.FileTransferAgent

## notification

```TypeScript
notification: Notification
```

Custom settings for the notification bar. The default value is **{}**.

**Type:** [Notification](arkts-basicservices-agent-notification-i.md)

**Since:** 15

**System capability:** SystemCapability.Request.FileTransferAgent
