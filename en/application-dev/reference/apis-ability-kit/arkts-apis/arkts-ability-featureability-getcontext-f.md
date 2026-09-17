# getContext

## Modules to Import

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
```

## getContext

```TypeScript
function getContext(): Context
```

Obtains the application context.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Return value:**

| Type | Description |
| --- | --- |
| [Context](arkts-ability-featureability-context-t.md) | Application context. |

**Examples**

```TypeScript
import { featureAbility } from '@kit.AbilityKit';

// Get the application context.
let context = featureAbility.getContext();
context.getBundleName((error, data) => {
  if (error && error.code !== 0) {
    console.error(`getBundleName fail, error: ${JSON.stringify(error)}`);
  } else {
    console.info(`getBundleName success, data: ${JSON.stringify(data)}`);
  }
});
```
