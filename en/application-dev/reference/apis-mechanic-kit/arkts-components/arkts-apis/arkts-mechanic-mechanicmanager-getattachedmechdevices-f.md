# getAttachedMechDevices

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## getAttachedMechDevices

```TypeScript
function getAttachedMechDevices(): MechInfo[]
```

Obtain the list of connected mechanical devices.

**Since:** 20

**System capability:** SystemCapability.Mechanic.Core

**Return value:**

| Type | Description |
| --- | --- |
| [MechInfo](arkts-mechanic-mechanicmanager-mechinfo-i.md)[] | List of connected mechanical devices. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [33300001](../errorcode-mechanic.md#33300001-system-error) | Service exception. |

**Examples**

```TypeScript
console.info('Query device list');
// Call getAttachedMechDevices to obtain the list of attached mechanic devices.
let mechanicInfos = mechanicManager.getAttachedMechDevices();
console.info(`'device list:' ${mechanicInfos}`);
```
