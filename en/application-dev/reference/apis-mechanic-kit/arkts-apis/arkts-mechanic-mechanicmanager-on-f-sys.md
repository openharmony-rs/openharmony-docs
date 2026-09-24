# on (System API)

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## on('rotationAxesStatusChange')

```TypeScript
function on(type: 'rotationAxesStatusChange', callback: Callback<RotationAxesStateChangeInfo>): void
```

Register a listener for axis state changes. The status of the rotation axis changes dynamically, which needs to be monitored.

**Since:** 20

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'rotationAxesStatusChange' | Yes | Event type. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RotationAxesStateChangeInfo](arkts-mechanic-mechanicmanager-rotationaxesstatechangeinfo-i-sys.md)&gt; | Yes | Rotate axis state changes callback. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-system-error) | Service exception. |

**Examples**

```TypeScript
console.info('Register Axis Status listener');
mechanicManager.on("rotationAxesStatusChange", (result: mechanicManager.RotationAxesStateChangeInfo) => {
  console.info(`'result:' ${result}`);
});
console.info('Successful registration');
```
