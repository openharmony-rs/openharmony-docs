# exitMasterProcessRole

## Modules to Import

```TypeScript
import { application } from '@kit.AbilityKit';
```

## exitMasterProcessRole

```TypeScript
export function exitMasterProcessRole(): Promise<void>
```

Relinquishes the [master-process](../../../application-models/ability-terminology.md#master-process) role from the current process. This API uses a promise to return the result. This API can be properly called only on 2-in-1 devices and tablets. If it is called on other device types, error code 801 is returned.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [16000118](../errorcode-ability.md#16000118-process-is-not-the-master-process) | Not a master process. |
| [16000119](../errorcode-ability.md#16000119-pending-request-exists) | Cannot exit because there is an unfinished request. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, application, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      application.exitMasterProcessRole()
        .then(() => {
          console.info('exitMasterProcessRole succeed');
        })
        .catch((err: BusinessError) => {
          console.error(`exitMasterProcessRole failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (error) {
      let code: number = (error as BusinessError).code;
      let message: string = (error as BusinessError).message;
      console.error(`exitMasterProcessRole failed, error.code: ${code}, error.message: ${message}`);
    }
  }
}
```
