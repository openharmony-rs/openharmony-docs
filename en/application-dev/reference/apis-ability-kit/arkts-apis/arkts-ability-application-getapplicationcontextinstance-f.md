# getApplicationContextInstance

## Modules to Import

```TypeScript
import { application } from '@kit.AbilityKit';
```

## getApplicationContextInstance

```TypeScript
export function getApplicationContextInstance(): ApplicationContext
```

Obtains the application context. This API provides context access independent of the base class **Context**. Repeated calls to this API obtain the same ApplicationContext instance.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ApplicationContext](arkts-ability-applicationcontext-c.md) | Application context. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: Memory operation error. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, application, Want, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let applicationContext: common.ApplicationContext = application.getApplicationContextInstance();
    } catch (error) {
      let code: number = (error as BusinessError).code;
      let message: string = (error as BusinessError).message;
      console.error(`getApplicationContextInstance failed, error.code: ${code}, error.message: ${message}`);
    }
  }
}
```
