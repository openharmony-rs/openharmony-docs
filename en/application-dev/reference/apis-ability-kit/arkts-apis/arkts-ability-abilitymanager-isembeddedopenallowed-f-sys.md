# isEmbeddedOpenAllowed (System API)

## Modules to Import

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## isEmbeddedOpenAllowed

```TypeScript
function isEmbeddedOpenAllowed(context: Context, appId: string): Promise<boolean>
```

Checks whether the [EmbeddableUIAbility](arkts-ability-app-ability-embeddableuiability-embeddableuiability-c.md) can be started in embedded mode. This API uses a promise to return the result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](arkts-ability-context-c.md) | Yes | Context of the caller. |
| appId | string | Yes | Unique ID of the application, which is allocated by the cloud. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. **true** if embedded startup is allowed, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
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
      abilityManager.isEmbeddedOpenAllowed(this.context, appId).then((data) => {
        console.info(`isEmbeddedOpenAllowed data: ${JSON.stringify(data)}`);
      }).catch((err: BusinessError) => {
        console.error(`isEmbeddedOpenAllowed failed, code is ${err.code}, message is ${err.message}`);
      });
    } catch (err) {
      // Process input parameter errors.
      console.error(`param is invalid, code is ${err.code}, message is ${err.message}`);
    }
  }
}
```
