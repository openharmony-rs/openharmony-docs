# isFloatViewEnabled

## Modules to Import

```TypeScript
import { floatView } from '@kit.ArkUI';
```

## isFloatViewEnabled

```TypeScript
function isFloatViewEnabled(): boolean
```

Checks whether the device supports the float view.

| Type| Description|  
|------------|------------|  
| boolean | Whether the device supports the float view. **true** to support; **false** otherwise.|

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| boolean | true if the float view is enabled, otherwise false. |

**Examples**

```TypeScript
// Check whether the current device supports the float view feature.
let enable: boolean = floatView.isFloatViewEnabled();
console.info('Float view enabled is: ' + enable);
```
