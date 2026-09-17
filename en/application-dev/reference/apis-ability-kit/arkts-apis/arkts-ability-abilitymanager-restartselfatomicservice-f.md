# restartSelfAtomicService

## Modules to Import

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## restartSelfAtomicService

```TypeScript
function restartSelfAtomicService(context: Context): void
```

Restarts the current atomic service.

> **NOTE:** 
> 
> - Currently, atomic services can be started only in an independent window.
> 
> - If you call this API,ApplicationContext.restartApp(), or [UIAbilityContext.restartApp()](arkts-ability-uiabilitycontext-c.md#restartapp) within 3 seconds after a successful call to this API, the system returns error code 16000064.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](arkts-ability-context-c.md) | Yes | Context of the ability.<br>Note: Currently, only [UIAbilityContext](arkts-ability-uiabilitycontext-c.md) is supported.<br> |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Connect to system service failed; 2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000064](../errorcode-ability.md#16000064-frequent-application-restart) | Restart too frequently. Try again at least 3s later. |
| [16000086](../errorcode-ability.md#16000086-context-is-not-a-uiabilitycontext) | The context is not UIAbilityContext. |
| [16000090](../errorcode-ability.md#16000090-caller-is-not-an-atomic-service) | The caller is not an atomic service. |

**Examples**

```TypeScript
import { AbilityConstant, EmbeddableUIAbility, Want, abilityManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends EmbeddableUIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      // Restart the current atomic service.
      abilityManager.restartSelfAtomicService(this.context);
    } catch (e) {
      console.error(`restartSelfAtomicService error: ${JSON.stringify(e as BusinessError)}`);
    }
  }
}
```
