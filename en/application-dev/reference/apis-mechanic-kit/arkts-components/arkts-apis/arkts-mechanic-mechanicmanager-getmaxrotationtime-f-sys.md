# getMaxRotationTime (System API)

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## getMaxRotationTime

```TypeScript
function getMaxRotationTime(mechId: number): number
```

Obtains the maximum continuous rotation duration of a mechanical device.

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
| number | Maximum rotation duration. Unit: millisecond. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-system-error) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-device-not-connected) | Device not connected. |

**Examples**

```TypeScript
console.info('Query maximum rotation time');
let maxTime = mechanicManager.getMaxRotationTime(0);
console.info(`'Query maximum rotation time successful, maximum time:' ${maxTime}`);
```
