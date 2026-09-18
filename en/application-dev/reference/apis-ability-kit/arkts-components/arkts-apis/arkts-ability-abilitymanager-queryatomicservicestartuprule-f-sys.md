# queryAtomicServiceStartupRule (System API)

## Modules to Import

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## queryAtomicServiceStartupRule

```TypeScript
function queryAtomicServiceStartupRule(context: Context, appId: string): Promise<AtomicServiceStartupRule>
```

Obtains the rule for launching an [EmbeddableUIAbility](arkts-ability-app-ability-embeddableuiability-embeddableuiability-c.md) in embedded mode. This API uses a promise to return the result. This API can be properly called only on phones and tablets. On other devices, it returns the error code 801.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](arkts-ability-context-c.md) | Yes | Context of the caller.<br>Note: Currently, only [UIAbilityContext](arkts-ability-uiabilitycontext-c.md) is supported. |
| appId | string | Yes | Unique ID of the application, which is allocated by the cloud. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AtomicServiceStartupRule](arkts-ability-abilitymanager-atomicservicestartuprule-i-sys.md)&gt; | Promise used to return the rule for launching the embedded atomic service. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { abilityManager, UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    // Unique identifier of the application.
    let appId: string = '6918661953712445909';
    try {
      abilityManager.queryAtomicServiceStartupRule(this.context, appId).then((data: abilityManager.AtomicServiceStartupRule) => {
        console.info(`queryAtomicServiceStartupRule data: ${JSON.stringify(data)}`);
      }).catch((err: BusinessError) => {
        console.error(`queryAtomicServiceStartupRule failed, code is ${err.code}, message is ${err.message}`);
      });
    } catch (err) {
      // Process input parameter errors.
      console.error(`param is invalid, code is ${err.code}, message is ${err.message}`);
    }
  }
}
```
