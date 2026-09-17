# getCameraTrackingEnabled

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## getCameraTrackingEnabled

```TypeScript
function getCameraTrackingEnabled(): boolean
```

Checks whether camera tracking is enabled for this mechanical device.

**Since:** 20

**System capability:** SystemCapability.Mechanic.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Enabled status. The value true means that camera tracking is enabled, and false means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [33300001](../errorcode-mechanic.md#33300001-system-error) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-device-not-connected) | Device not connected. |

**Examples**

```TypeScript
console.info('Get tracking status');
// Call getCameraTrackingEnabled to obtain whether camera tracking is currently enabled.
let enabled = mechanicManager.getCameraTrackingEnabled();
console.info(`'current tracking status:' ${enabled}`);
```
