# turnBySpeed (System API)

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## turnBySpeed

```TypeScript
function turnBySpeed(mechId: number, angleSpeed: number, duration: number): Promise<Result>
```

Rotate in place according to the speed.

**Since:** 26.0.0

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mechId | number | Yes | ID of the mechanical device.<br>The value should be an integer. |
| angleSpeed | number | Yes | angular velocity. |
| duration | number | Yes | Duration of movement, unit ms.<br>The value should be an integer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-mechanic-mechanicmanager-result-e-sys.md)&gt; | Promise that returns the execution result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-system-error) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-device-not-connected) | Device not connected. |
| [33300003](../errorcode-mechanic.md#33300003-function-not-supported) | Feature not supported. |
