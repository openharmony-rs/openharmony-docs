# getRotationAxesStatus (System API)

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## getRotationAxesStatus

```TypeScript
function getRotationAxesStatus(mechId: number): RotationAxesStatus
```

Obtains the status of the rotation axes.

**Since:** 20

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mechId | number | Yes | ID of the mechanical device. |

**Return value:**

| Type | Description |
| --- | --- |
| [RotationAxesStatus](arkts-mechanic-mechanicmanager-rotationaxesstatus-i-sys.md) | Rotation axis status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-system-error) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-device-not-connected) | Device not connected. |

**Examples**

```TypeScript
console.info('Query the rotation axis status');
let axisStatus: mechanicManager.RotationAxesStatus = mechanicManager.getRotationAxesStatus(0);
console.info(`'Query the rotation axis status successfully, axis state:' ${axisStatus}`);
```
