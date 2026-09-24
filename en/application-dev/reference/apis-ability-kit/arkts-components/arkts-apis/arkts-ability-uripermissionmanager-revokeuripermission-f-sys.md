# revokeUriPermission (System API)

## Modules to Import

```TypeScript
import { uriPermissionManager } from '@kit.AbilityKit';
```

## revokeUriPermission

```TypeScript
function revokeUriPermission(uri: string, targetBundleName: string, callback: AsyncCallback<number>): void
```

Revokes the URI permission from an application. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> - This API can be used to revoke the URI permission of another application obtained by this application or URI permission granted by this application.
> 
> - URI processing involves encoding and decoding. Therefore, the input URI must be obtained through the [getUriFromPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md) API. For URIs combined by the application, the system cannot guarantee their functions.

**Since:** 10

**Required permissions:** 
- API version 12 and later: N/A
- API versions 10 to 11: ohos.permission.PROXY_AUTHORIZATION_URI

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the file. The scheme has a fixed value of **file**. For details, see [FileUri](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-fileuri-c.md#constructor). |
| targetBundleName | string | Yes | Bundle name of the application, from which the permission is revoked. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **0** is returned; otherwise, **-1** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 10 - 11 |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. Interface caller is not a system app. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000059](../errorcode-ability.md#16000059-specified-uri-type-is-invalid) | Invalid URI type. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 19 and later |

**Examples**

```TypeScript
import { uriPermissionManager } from '@kit.AbilityKit';

let targetBundleName = 'com.example.test_case2';
let uri = "file://com.example.test_case1/data/storage/el2/base/haps/entry_test/files/newDir";

// Revoke the URI permission of the specified application.
uriPermissionManager.revokeUriPermission(uri, targetBundleName, (error) => {
  if (error && error.code !== 0) {
    console.error(`revokeUriPermission failed. Code: ${error.code}, message: ${error.message}.`);
    return;
  }
  console.info('revokeUriPermission success');
});
```


<a id="revokeuripermission-2"></a>

## revokeUriPermission

```TypeScript
function revokeUriPermission(uri: string, targetBundleName: string): Promise<number>
```

Revokes the URI permission from an application. This API uses a promise to return the result.

> **NOTE:** 
> 
> - This API can be used to revoke the URI permission of another application obtained by this application or URI permission granted by this application.
> 
> - URI processing involves encoding and decoding. Therefore, the input URI must be obtained through the [getUriFromPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md) API. For URIs combined by the application, the system cannot guarantee their functions.

**Since:** 10

**Required permissions:** 
- API version 12 and later: N/A
- API versions 10 to 11: ohos.permission.PROXY_AUTHORIZATION_URI

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the file. The scheme has a fixed value of **file**. For details, see [FileUri](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-fileuri-c.md#constructor). |
| targetBundleName | string | Yes | Bundle name of the target application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the result. If the operation is successful, **0** is returned; otherwise, **-1** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 10 - 11 |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. Interface caller is not a system app. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000059](../errorcode-ability.md#16000059-specified-uri-type-is-invalid) | Invalid URI type. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 19 and later |

**Examples**

```TypeScript
import { uriPermissionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let targetBundleName = 'com.example.test_case2';
let uri = 'file://com.example.test_case1/data/storage/el2/base/haps/entry_test/files/newDir';

// Revoke the URI permission of the specified application.
uriPermissionManager.revokeUriPermission(uri, targetBundleName)
  .then((data) => {
    console.info(`Verification success, data: ${JSON.stringify(data)}.`);
  }).catch((error: BusinessError) => {
  console.error(`Verification failed, err code: ${error.code}, err msg: ${error.message}.`);
});
```


<a id="revokeuripermission-4"></a>

## revokeUriPermission

```TypeScript
function revokeUriPermission(uri: string, targetBundleName: string, appCloneIndex: number): Promise<void>
```

Revokes the URI permission from an application. This API uses a promise to return the result.

> **NOTE:** 
> 
> - This API can be used to revoke the URI permission of another application obtained by this application or URI permission granted by this application.
> 
> - This API can be used to revoke the URI permissions granted to a cloned application. You need to specify the application bundle name and index of the cloned application.
> 
> - URI processing involves encoding and decoding. Therefore, the input URI must be obtained through the [getUriFromPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md) API. For URIs combined by the application, the system cannot guarantee their functions.

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the file. The scheme has a fixed value of **file**. For details, see [FileUri](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-fileuri-c.md#constructor). |
| targetBundleName | string | Yes | Bundle name of the target application. |
| appCloneIndex | number | Yes | Index of the cloned application. The value range is [0, 1000]. The value **0** indicates the application itself. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. Interface caller is not a system app. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000059](../errorcode-ability.md#16000059-specified-uri-type-is-invalid) | Invalid URI type. |
| [16000081](../errorcode-ability.md#16000081-failed-to-obtain-the-target-application-information) | Failed to obtain the target application information. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 19 and later |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want, wantConstant, uriPermissionManager } from '@kit.AbilityKit';
import { fileUri } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
  }

  onForeground(): void {
    let targetBundleName: string = 'com.example.demo1';
    let filePath: string = this.context.filesDir + "/test.txt";
    let uri: string = fileUri.getUriFromPath(filePath);
    // Revoke the URI permission of the main application.
    try {
      let appCloneIndex: number = 0;
      uriPermissionManager.revokeUriPermission(uri, targetBundleName, appCloneIndex)
        .then(() => {
          console.info('revokeUriPermission succeeded.');
        }).catch((error: BusinessError) => {
        console.error(`revokeUriPermission failed. error: ${JSON.stringify(error)}.`);
      });
    } catch (error) {
      console.error(`revokeUriPermission failed. error: ${JSON.stringify(error)}.`);
    }

    // Revoke the URI permission of the clone application.
    try {
      let appCloneIndex: number = 1;
      uriPermissionManager.revokeUriPermission(uri, targetBundleName, appCloneIndex)
        .then(() => {
          console.info('revokeUriPermission succeeded.');
        }).catch((error: BusinessError) => {
        console.error(`revokeUriPermission failed. error: ${JSON.stringify(error)}.`);
      });
    } catch (error) {
      console.error(`revokeUriPermission failed. error: ${JSON.stringify(error)}.`);
    }
  }
}
```
