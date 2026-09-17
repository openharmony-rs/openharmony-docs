# isFloatingBallEnabled

## Modules to Import

```TypeScript
import { floatingBall } from '@kit.ArkUI';
```

## isFloatingBallEnabled

```TypeScript
function isFloatingBallEnabled(): boolean
```

Checks whether the device supports floating balls.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of floating balls. **true** if supported, **false** otherwise. |

**Examples**

```TypeScript
// Check whether the current device supports the floating ball feature.
let enable: boolean = floatingBall.isFloatingBallEnabled();
console.info('Floating ball enabled is: ' + enable);
```
