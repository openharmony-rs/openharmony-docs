# revokeQuickFix (System API)

## Modules to Import

```TypeScript
import { quickFixManager } from '@kit.AbilityKit';
```

## revokeQuickFix

```TypeScript
function revokeQuickFix(bundleName: string, callback: AsyncCallback<void>): void
```

Revokes quick fix. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED and ohos.permission.INSTALL_BUNDLE

**System capability:** SystemCapability.Ability.AbilityRuntime.QuickFix

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Name of the bundle for which the patch needs to be revoked. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If quick fix is revoked, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [18500001](../errorcode-ability.md#18500001-invalid-bundle-name) | The bundle does not exist or no patch has been applied. |
| [18500009](../errorcode-ability.md#18500009-application-has-a-quick-fix-task-being-processed) | The application has an ongoing quick fix task. |

**Examples**

```TypeScript
import { quickFixManager } from '@kit.AbilityKit';

let bundleName = 'com.example.myapplication';

quickFixManager.revokeQuickFix(bundleName, (err) => {
  if (err.code) {
    console.error(`revokeQuickFix ${bundleName} failed, err code: ${err.code}, err msg: ${err.message}.`);
  }
});
```


<a id="revokequickfix-1"></a>

## revokeQuickFix

```TypeScript
function revokeQuickFix(bundleName: string): Promise<void>
```

Revokes quick fix. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED and ohos.permission.INSTALL_BUNDLE

**System capability:** SystemCapability.Ability.AbilityRuntime.QuickFix

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Name of the bundle for which the patch needs to be revoked. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [18500001](../errorcode-ability.md#18500001-invalid-bundle-name) | The bundle does not exist or no patch has been applied. |
| [18500009](../errorcode-ability.md#18500009-application-has-a-quick-fix-task-being-processed) | The application has an ongoing quick fix task. |

**Examples**

```TypeScript
import { quickFixManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.example.myapplication';

quickFixManager.revokeQuickFix(bundleName).then(() => {
  console.info(`revokeQuickFix ${bundleName} success.`);
}).catch((err: BusinessError) => {
  console.error(`revokeQuickFix ${bundleName} failed, err code: ${err.code}, err msg: ${err.message}.`);
});
```
