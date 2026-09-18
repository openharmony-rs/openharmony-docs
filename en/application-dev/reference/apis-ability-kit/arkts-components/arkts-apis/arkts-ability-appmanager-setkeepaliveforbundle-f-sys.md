# setKeepAliveForBundle (System API)

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## setKeepAliveForBundle

```TypeScript
function setKeepAliveForBundle(bundleName: string, userId: number, enable: boolean): Promise<void>
```

Sets or cancels the keep-alive status for an application that belongs to a specified user. This API uses a promise to return the result. Starting from API version 18, this API can be properly called only on 2-in-1 devices and wearables. For versions earlier than API version 18, this API can be properly called only on 2-in-1 devices. If it is called on other device types, error code 801 is returned.

> **NOTE:** 
> 
> - To support keep-alive, **mainElement** in the [module.json5](../../../quick-start/module-configuration-file.md) file of the application must be a UIAbility.The system initiates the keep-alive operation only when this mainElement has been launched.
> 
> - On 2-in-1 devices, the application must appear in the status bar within 5 seconds of launch. Otherwise, the system revokes the application's keep-alive status and terminate the restarted process.
> 
> - When the kept-alive application process exits, the system attempts to restart it. If three consecutive restart attempts fail, the system stops restarting the process.

**Since:** 14

**Required permissions:** ohos.permission.MANAGE_APP_KEEP_ALIVE

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| userId | number | Yes | User ID. |
| enable | boolean | Yes | Whether to keep the application alive or cancel its keep-alive status. **true** to keep the application alive, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16300005](../errorcode-ability.md#16300005-bundle-information-does-not-exist) | The target bundle does not exist. |
| [16300008](../errorcode-ability.md#16300008-specified-package-does-not-have-a-main-uiability) | The target bundle has no MainAbility. |
| [16300009](../errorcode-ability.md#16300009-specified-package-does-not-have-a-status-bar) | The target bundle has no status-bar ability. |
| [16300010](../errorcode-ability.md#16300010-running-application-is-not-attached-to-a-status-bar) | The target application is not attached to the status bar. |

**Examples**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName = 'ohos.samples.keepaliveapp';
  let userId = 100;
  appManager.setKeepAliveForBundle(bundleName, userId, true).then(() => {
    console.info(`setKeepAliveForBundle success`);
  }).catch((err: BusinessError) => {
    console.error(`setKeepAliveForBundle fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] setKeepAliveForBundle error: ${code}, ${message}`);
}
```
