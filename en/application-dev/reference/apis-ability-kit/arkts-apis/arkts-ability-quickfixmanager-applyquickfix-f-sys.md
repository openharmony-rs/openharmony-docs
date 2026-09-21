# applyQuickFix (System API)

## Modules to Import

```TypeScript
import { quickFixManager } from '@kit.AbilityKit';
```

## applyQuickFix

```TypeScript
function applyQuickFix(hapModuleQuickFixFiles: Array<string>, callback: AsyncCallback<void>): void
```

Applies a quick fix patch. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.INSTALL_BUNDLE

**System capability:** SystemCapability.Ability.AbilityRuntime.QuickFix

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hapModuleQuickFixFiles | Array&lt;string&gt; | Yes | Quick fix patch files, each of which must contain a valid file path. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the quick fix patch is installed, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [18500002](../errorcode-ability.md#18500002-invalid-patch-package) | Invalid patch package. |
| [18500008](../errorcode-ability.md#18500008-internal-error) | Internal error. |

**Examples**

```TypeScript
import { quickFixManager } from '@kit.AbilityKit';

try {
  let hapModuleQuickFixFiles = ['/data/storage/el2/base/entry.hqf'];
  quickFixManager.applyQuickFix(hapModuleQuickFixFiles, (error) => {
    if (error) {
      console.error( `applyQuickFix failed with error: ${error}`);
    } else {
      console.info(`applyQuickFix success`);
    }
  });
} catch (paramError) {
  console.error(`error.code: ${paramError.code}, error.message: ${paramError.message}`);
}
```


<a id="applyquickfix-1"></a>

## applyQuickFix

```TypeScript
function applyQuickFix(hapModuleQuickFixFiles: Array<string>): Promise<void>
```

Applies a quick fix patch. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.INSTALL_BUNDLE

**System capability:** SystemCapability.Ability.AbilityRuntime.QuickFix

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hapModuleQuickFixFiles | Array&lt;string&gt; | Yes | Quick fix patch files, each of which must contain a valid file path. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [18500002](../errorcode-ability.md#18500002-invalid-patch-package) | Invalid patch package. |
| [18500008](../errorcode-ability.md#18500008-internal-error) | Internal error. |

**Examples**

```TypeScript
import { quickFixManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let hapModuleQuickFixFiles = ['/data/storage/el2/base/entry.hqf'];

try {
  quickFixManager.applyQuickFix(hapModuleQuickFixFiles).then(() => {
    console.info(`applyQuickFix success`);
  }).catch((error: BusinessError) => {
    console.error(`applyQuickFix err: ${error}`);
  });
} catch (paramError) {
  console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
}
```
