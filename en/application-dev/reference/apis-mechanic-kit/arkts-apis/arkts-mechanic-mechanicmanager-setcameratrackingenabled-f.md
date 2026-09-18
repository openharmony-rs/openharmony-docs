# setCameraTrackingEnabled

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## setCameraTrackingEnabled

```TypeScript
function setCameraTrackingEnabled(isEnabled: boolean): void
```

Enables or disables camera tracking.

**Since:** 20

**System capability:** SystemCapability.Mechanic.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnabled | boolean | Yes | Whether to enable camera tracking. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [33300001](../errorcode-mechanic.md#33300001-system-error) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-device-not-connected) | Device not connected. |
| [33300003](../errorcode-mechanic.md#33300003-function-not-supported) | Feature not supported. |

**Examples**

```TypeScript
console.info('Enable tracing');
// Call the setCameraTrackingEnabled method. The value true indicates enabling camera tracking.
mechanicManager.setCameraTrackingEnabled(true);
console.info('Succeeded in enabling tracking.');
```
