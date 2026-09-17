# isAutoStartupSupported

## Modules to Import

```TypeScript
import { autoStartupManager } from '@kit.AbilityKit';
```

## isAutoStartupSupported

```TypeScript
function isAutoStartupSupported(): boolean
```

Check whether the current device supports auto startup on this device.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | `true`: Device supports auto startup.   - `false`: Device do not support auto startup. |

**Examples**

```TypeScript
import { autoStartupManager, UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    // Check whether the current device supports auto-start on boot.
    const isSupported: boolean = autoStartupManager.isAutoStartupSupported();
    console.info(`isAutoStartupSupported: ${isSupported}.`);
  }
}
```
