# SystemLiveViewSubscriber (System API)

Subscriber of the system live view notification.

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## onResponse

```TypeScript
onResponse?: (notificationId: number, buttonOptions: ButtonOptions) => void
```

Callback when the button is touched.

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| notificationId | number | Yes |  |
| buttonOptions | [ButtonOptions](arkts-notification-notificationmanager-buttonoptions-i-sys.md) | Yes |  |
