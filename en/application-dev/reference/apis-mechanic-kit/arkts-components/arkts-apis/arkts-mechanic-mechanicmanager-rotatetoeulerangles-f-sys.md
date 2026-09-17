# rotateToEulerAngles (System API)

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## rotateToEulerAngles

```TypeScript
function rotateToEulerAngles(mechId: number, angles: EulerAngles, duration: number): Promise<Result>
```

Rotates a mechanical device to the absolute angles.

**Since:** 20

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mechId | number | Yes | ID of the mechanical device. |
| angles | [EulerAngles](arkts-mechanic-mechanicmanager-eulerangles-i-sys.md) | Yes | Absolute angles. |
| duration | number | Yes | Rotation duration. Unit: millisecond. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-mechanic-mechanicmanager-result-e-sys.md)&gt; | Promise that return the execution result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-system-error) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-device-not-connected) | Device not connected. |

**Examples**

```TypeScript
let degree: mechanicManager.EulerAngles = {
  yaw: 0.9 * Math.PI,
  roll: 0.9 * Math.PI,
  pitch: 0.9 * Math.PI
}
mechanicManager.rotateToEulerAngles(0, degree, 500)
  .then((result: mechanicManager.Result) => {
    console.info(`'Rotate result:' ${result}`);
  });
console.info('End rotation');
```
