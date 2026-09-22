# isControlSupported

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## isControlSupported

```TypeScript
function isControlSupported(mechDeviceType?: MechDeviceType): boolean
```

Checks whether the current device supports embodied control for a specific type of device.

**Since:** 26.0.0

**System capability:** SystemCapability.Mechanic.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mechDeviceType | [MechDeviceType](arkts-mechanic-mechanicmanager-mechdevicetype-e.md) | No | Associated device type.<br>Default: If this parameter is not provided, it represents all device types. As long as one or more types are supported, the result returned will be supported. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns whether embodied control is supported. |

**Examples**

```TypeScript
console.info('Check whether control is supported');
// Call the isControlSupported method and pass MechDeviceType.GIMBAL_DEVICE to check whether gimbal device control is supported.
let isSupported = mechanicManager.isControlSupported(mechanicManager.MechDeviceType.GIMBAL_DEVICE);
console.info(`isSupported: ${isSupported}`);
```
