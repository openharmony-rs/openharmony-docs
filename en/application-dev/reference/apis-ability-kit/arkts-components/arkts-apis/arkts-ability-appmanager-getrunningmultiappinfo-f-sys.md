# getRunningMultiAppInfo (System API)

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## getRunningMultiAppInfo

```TypeScript
function getRunningMultiAppInfo(bundleName: string): Promise<RunningMultiAppInfo>
```

Obtains the information about running applications in multi-app mode. The multi-app mode means that an application can be simultaneously logged in with different accounts on the same device. This API uses a promise to return the result.

**Since:** 12

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
| Promise&lt;[RunningMultiAppInfo](arkts-ability-appmanager-runningmultiappinfo-t-sys.md)&gt; | Promise used to return the information about running applications with multi- app mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported. |
| [18500001](../errorcode-ability.md#18500001-invalid-bundle-name) | The bundle does not exist or no patch has been applied. |

**Examples**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName = 'ohos.samples.etsclock';
  appManager.getRunningMultiAppInfo(bundleName).then((info: appManager.RunningMultiAppInfo) => {
      hilog.info(0x0000, 'testTag', `getRunningMultiAppInfo success`);
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', `getRunningMultiAppInfo error, code: ${err.code}, msg:${err.message}`);
    })
} catch (err) {
  hilog.error(0x0000, 'testTag', `getRunningMultiAppInfo error, code: ${(err as BusinessError).code}, msg:${(err as BusinessError).message}`);
}
```
