# isEmbeddedUIExtensionSupported

## Modules to Import

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## isEmbeddedUIExtensionSupported

```TypeScript
function isEmbeddedUIExtensionSupported(): boolean
```

Indicates whether the current device supports EmbeddedUIExtensionAbility.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if EmbeddedUIExtensionAbility is supported, returns `false` otherwise. |

**Examples**

```TypeScript
import { abilityManager, UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    // Determine whether the current device supports EmbeddedUIExtensionAbility.
    let isSupported: boolean = abilityManager.isEmbeddedUIExtensionSupported();
    console.info(`isEmbeddedUIExtensionSupported is ${isSupported}`);
  }
}
```
