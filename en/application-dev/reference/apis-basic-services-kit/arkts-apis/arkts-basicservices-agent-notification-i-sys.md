# Notification

```TypeScript
interface Notification
```

Describes the custom information of the notification bar.

**Since:** 15

<!--Device-agent-interface Notification--><!--Device-agent-interface Notification-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## disable

```TypeScript
disable?: boolean
```

Disables the notification. If the value is false, a notification will be displayed, otherwise nothing will be displayed. If not specified, the value is false.

**Type:** boolean

**Since:** 20

<!--Device-Notification-disable?: boolean--><!--Device-Notification-disable?: boolean-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

**System API:** This is a system API.
