# setKeepAliveForAppServiceExtension (System API)

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## setKeepAliveForAppServiceExtension

```TypeScript
function setKeepAliveForAppServiceExtension(bundleName: string, enabled: boolean): Promise<void>
```

Sets or cancels the keep-alive status for an AppServiceExtensionAbility. This API uses a promise to return the result. This API can be properly called on PCs/2-in-1 devices. If it is called on other devices, error code 801 is returned.

> **NOTE:** 
> 
> - This API takes effect only when the application is installed under the user with **userId** of 1 and the
> **mainElement** field in the **module.json5** file of the entry HAP is set to **AppServiceExtensionAbility**.

**Since:** 20

**Required permissions:** ohos.permission.MANAGE_APP_KEEP_ALIVE

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| enabled | boolean | Yes | Whether to keep the application alive or cancel its keep-alive status. **true** to keep, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000081](../errorcode-ability.md#16000081-failed-to-obtain-the-target-application-information) | Failed to obtain the target application information. |
| [16000202](../errorcode-ability.md#16000202-keep-alive-can-be-set-only-for-an-extensionability-of-the-appservice-type) | Invalid main element type. |
| [16000203](../errorcode-ability.md#16000203-cannot-change-the-keep-alive-status-of-an-appserviceextensionability) | Cannot change the keep-alive status. |
| [16000204](../errorcode-ability.md#16000204-application-is-not-installed-for-the-user-with-userid-of-1) | The target bundle is not in u1. |

**Examples**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName = 'ohos.samples.keepaliveapp';
  appManager.setKeepAliveForAppServiceExtension(bundleName, true).then(() => {
    console.info(`setKeepAliveForAppServiceExtension success`);
  }).catch((err: BusinessError) => {
    console.error(`setKeepAliveForAppServiceExtension fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] setKeepAliveForAppServiceExtension error: ${code}, ${message}`);
}
```
