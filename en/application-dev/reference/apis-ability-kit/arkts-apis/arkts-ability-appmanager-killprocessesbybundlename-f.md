# killProcessesByBundleName

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

<a id="killprocessesbybundlename-1"></a>

## killProcessesByBundleName

```TypeScript
function killProcessesByBundleName(bundleName: string, clearPageStack: boolean, appIndex?: number): Promise<void>
```

Kills a process by bundle name. This API uses a promise to return the result.

**Since:** 14

**Required permissions:** ohos.permission.KILL_APP_PROCESSES or ohos.permission.CLEAN_BACKGROUND_PROCESSES

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| clearPageStack | boolean | Yes | Whether to clear the page stack. **true** to clear, **false** otherwise. |
| appIndex | number | No | ID of an application clone. The default value is **0**. If the value is **0**, all processes of the main application are terminated. If the value is greater than 0, all processes of the specified application clone are terminated. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | If the input parameter is not valid parameter. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';
let isClearPageStack = false;
let appIndex = 1;

try {
  appManager.killProcessesByBundleName(bundleName, isClearPageStack, appIndex).then((data) => {
    console.info('killProcessesByBundleName success.');
  }).catch((err: BusinessError) => {
    console.error(`killProcessesByBundleName fail, code: ${err.code}, msg:${err.message}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```
