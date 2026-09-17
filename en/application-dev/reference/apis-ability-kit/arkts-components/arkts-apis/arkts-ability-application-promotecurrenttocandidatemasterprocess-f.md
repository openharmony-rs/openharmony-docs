# promoteCurrentToCandidateMasterProcess

## Modules to Import

```TypeScript
import { application } from '@kit.AbilityKit';
```

## promoteCurrentToCandidateMasterProcess

```TypeScript
export function promoteCurrentToCandidateMasterProcess(insertToHead: boolean): Promise<void>
```

Adds the current process into the [candidate master process](../../../application-models/ability-terminology.md#candidate-master-process) list. This API uses a promise to return the result. When the [master process](../../../application-models/ability-terminology.md#master-process) is destroyed and a UIAbility or UIExtensionAbility with **isolationProcess** set to **true** is restarted, the system takes corresponding actions based on whether there is a candidate master process.

- If a candidate master process exists, the system sets the process at the head of the candidate master process  
list as the new master process and triggers the [onNewProcessRequest](arkts-ability-app-ability-abilitystage-abilitystage-c.md#onnewprocessrequest) callback.  
- If no candidate master process exists, the system performs the following operations based on the component type:  
- For a UIAbility, the system creates an empty process as the master process.  
- For a UIExtensionAbility, the system first tries to reuse an existing UIExtensionAbility process as the new  
master process. If no available process exists, it creates an empty process as the master process. This API can be properly called on PCs/2-in-1 devices and tablets. If it is called on other devices, error code 801 is returned.

> **NOTE:** 
> 
> If the current process is already the
> [master process](../../../application-models/ability-terminology.md#master-process), calling this API has no
> effect and does not generate an error code.
> 
> A process can be set as a candidate master process only if it is currently running a component with
> **isolationProcess** set to **true** or has previously as the main process.
> 
> 
> The **isolationProcess** field can be set to **true** in the
> [module.json5](../../../quick-start/module-configuration-file.md) file, but only for the UIExtensionAbility of
> the sys/commonUI type.

<!--DelEnd-->

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| insertToHead | boolean | Yes | Whether to add the current process to the head of the candidate master process list. **true** to add the current process to the head of the list, **false** to add the current process to the tail of the list. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [16000115](../errorcode-ability.md#16000115-current-process-cannot-be-set-as-candidate-master-process) | The current process cannot be set as a candidate master process. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, application, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      application.promoteCurrentToCandidateMasterProcess(true)
        .then(() => {
          console.info('promote succeed');
        })
        .catch((err: BusinessError) => {
          console.error(`promote failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (error) {
      let code: number = (error as BusinessError).code;
      let message: string = (error as BusinessError).message;
      console.error(`promoteCurrentToCandidateMasterProcess failed, error.code: ${code}, error.message: ${message}`);
    }
  }
}
```
