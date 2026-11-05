# isActive

## Modules to Import

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## isActive

```TypeScript
function isActive(): boolean
```

Checks whether the current device is active.

- A device with a screen is active when the screen is on and inactive when the screen is off.  
- A device without a screen is active when it exits the sleep mode and inactive when it enters the sleep mode.

**Since:** 9

<!--Device-power-function isActive(): boolean--><!--Device-power-function isActive(): boolean-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | The value true is returned for the active state, and false is returned for the inactive state or failure to obtain the device active state. |

**Examples**

```TypeScript
let isActive = power.isActive();
console.info('power is active: ' + isActive);
```
