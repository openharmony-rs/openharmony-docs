# subscribe (System API)

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## subscribe

```TypeScript
function subscribe(events: MechEventType[], callback: Callback<MechEvent>): void
```

Subscribe to the specified events.

**Since:** 26.0.0

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| events | [MechEventType](arkts-mechanic-mechanicmanager-mecheventtype-e-sys.md)[] | Yes | Events to subscribe to. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MechEvent](arkts-mechanic-mechanicmanager-mechevent-i-sys.md)&gt; | Yes | Callback of event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-system-error) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-device-not-connected) | Device not connected. |
| [33300003](../errorcode-mechanic.md#33300003-function-not-supported) | Feature not supported. |
