# disconnectDevice (System API)

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## disconnectDevice

```TypeScript
function disconnectDevice(mechId: number): Promise<Result>
```

Disconnect a device with mechanic id.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CONNECT_MECHANIC_HARDWARE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mechId | number | Yes | mechanic device id.<br>The value should be an integer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-mechanic-mechanicmanager-result-e-sys.md)&gt; | Promise used to return the execution result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-system-error) | Service exception. |
