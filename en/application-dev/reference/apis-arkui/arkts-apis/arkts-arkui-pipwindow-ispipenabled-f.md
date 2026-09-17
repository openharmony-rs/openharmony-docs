# isPiPEnabled

## Modules to Import

```TypeScript
import { PiPWindow } from '@kit.ArkUI';
```

## isPiPEnabled

```TypeScript
function isPiPEnabled(): boolean
```

Checks whether the current device supports the PiP feature.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the PiP feature is supported. **true** if supported, **false** otherwise. |

**Examples**

```TypeScript
let enable: boolean = PiPWindow.isPiPEnabled(); // Check whether the PiP window is supported.
console.info('isPiPEnabled:' + enable);
```
