# getSupportedProcessCachePids (System API)

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## getSupportedProcessCachePids

```TypeScript
function getSupportedProcessCachePids(bundleName : string): Promise<Array<number>>
```

Obtains the PIDs of processes that support quick startup after caching in a specified application. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API can only be used to obtain the PIDs of the system account to which the caller belongs.

**Since:** 14

**Required permissions:** ohos.permission.GET_RUNNING_INFO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return an array containing the PIDs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName = 'ohos.samples.processcache';
  appManager.getSupportedProcessCachePids(bundleName).then((pids: Array<number>) => {
      hilog.info(0x0000, 'testTag', `pids: ${JSON.stringify(pids)}`);
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', `get pids error, code: ${err.code}, msg:${err.message}`);
    })
} catch (err) {
  hilog.error(0x0000, 'testTag', `get pids error, code: ${(err as BusinessError).code}, msg:${(err as BusinessError).message}`);
}
```
