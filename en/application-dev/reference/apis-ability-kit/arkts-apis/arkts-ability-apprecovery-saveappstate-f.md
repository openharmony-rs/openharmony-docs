# saveAppState

## Modules to Import

```TypeScript
import { appRecovery } from '@kit.AbilityKit';
```

## saveAppState

```TypeScript
function saveAppState(): boolean
```

Saves the application state. This API can be used together with the APIs of [errorManager](arkts-ability-app-ability-errormanager.md).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the application state is saved. **true** if saved, **false** otherwise. |

**Examples**

```TypeScript
import { appRecovery, errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: errorManager.ErrorObserver = {
  onUnhandledException(errorMsg) {
    console.error('onUnhandledException, errorMsg: ', errorMsg);
    appRecovery.saveAppState();
  }
};

try {
  errorManager.on('error', observer);
} catch (paramError) {
  console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
}
```


<a id="saveappstate-1"></a>

## saveAppState

```TypeScript
function saveAppState(context?: UIAbilityContext): boolean
```

Saves the ability state, which will be used for recovery. This API can be used together with the APIs of [errorManager](arkts-ability-app-ability-errormanager.md).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [UIAbilityContext](arkts-ability-uiabilitycontext-c.md) | No | Context of the target ability. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the application state is saved. **true** if saved, **false** otherwise. |

**Examples**

```TypeScript
import { appRecovery, errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: errorManager.ErrorObserver = {
  onUnhandledException(errorMsg) {
    console.error('onUnhandledException, errorMsg: ', errorMsg);
    // context is the context of the UIAbility instance. Use an arrow function or save it in advance outside the callback.
    appRecovery.saveAppState(this.context);
  }
};

try {
  errorManager.on('error', observer);
} catch (paramError) {
  console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
}
```
