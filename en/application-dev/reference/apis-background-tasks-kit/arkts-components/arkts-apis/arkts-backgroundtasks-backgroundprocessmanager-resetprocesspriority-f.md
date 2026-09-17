# resetProcessPriority

## Modules to Import

```TypeScript
import { backgroundProcessManager } from '@kit.BackgroundTasksKit';
```

## resetProcessPriority

```TypeScript
function resetProcessPriority(pid: number): Promise<void>
```

Unsuppresses the child process. In this case, the child process follows the scheduling policy of the main process. If the scheduling policy of the main process changes, for example, from the background to the foreground, the child process changes with the main process. The effect is the same as calling **resetProcessPriority**.

**Since:** 17

**System capability:** SystemCapability.Resourceschedule.BackgroundProcessManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pid | number | Yes | ID of the child process, which is the **pid** parameter of the [OH_Ability_StartNativeChildProcess](../../../reference/apis-ability-kit/c-apis/capi-native-child-process-h.md#oh_ability_startnativechildprocess) API. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { backgroundProcessManager } from '@kit.BackgroundTasksKit';

let childProcessPid = 33333;
try {
    backgroundProcessManager.resetProcessPriority(childProcessPid); 
} catch (error) {
    console.error(`resetProcessPriority failed, errCode: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
