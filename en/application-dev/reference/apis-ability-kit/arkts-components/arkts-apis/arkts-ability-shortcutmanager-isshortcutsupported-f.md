# isShortcutSupported

## Modules to Import

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
```

## isShortcutSupported

```TypeScript
function isShortcutSupported(): boolean
```

Checks whether the current device supports shortcuts.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Indicates whether the current device supports shortcuts. The return value true indicates that the current device supports shortcuts; the return value false indicates that the current device does not support shortcuts. |

**Examples**

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = shortcutManager.isShortcutSupported();
  console.info('isShortcutSupported data is' + JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  console.error(`isShortcutSupported errData is errCode:${err.code}  message:${err.message}`);
}
```
