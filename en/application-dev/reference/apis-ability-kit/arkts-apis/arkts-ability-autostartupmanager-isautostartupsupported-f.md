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

> **NOTE:** 
> 
> It is recommended that you call this API to check the device capability before calling
> [autoStartupManager.getAutoStartupStatusForSelf](arkts-ability-autostartupmanager-getautostartupstatusforself-f.md).
> If false is returned, the current device does not support auto-start on boot.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-autoStartupManager-function isAutoStartupSupported(): boolean--><!--Device-autoStartupManager-function isAutoStartupSupported(): boolean-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the current device supports auto-start on boot. The value true means that auto-start on boot is supported, and false means the opposite. |

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
