# offBatteryLevelChange (System API)

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## offBatteryLevelChange

```TypeScript
function offBatteryLevelChange(mechId: number, callback?: Callback<BatteryLevelInfo>): void
```

Unsubscribes to device battery level change information.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mechId | number | Yes | ID of the mechanical device. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BatteryLevelInfo](arkts-mechanic-mechanicmanager-batterylevelinfo-i-sys.md)&gt; | No | Callback function that returns the current battery level.<br>If not specified, all callbacks registered for this mechId will be removed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-system-error) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-device-not-connected) | Device not connected. |
| [33300003](../errorcode-mechanic.md#33300003-function-not-supported) | Feature not supported. |
