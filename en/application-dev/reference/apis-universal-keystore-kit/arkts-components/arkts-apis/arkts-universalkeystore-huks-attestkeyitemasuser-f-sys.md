# attestKeyItemAsUser (System API)

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## attestKeyItemAsUser

```TypeScript
function attestKeyItemAsUser(userId: number, keyAlias: string, huksOptions: HuksOptions): Promise<HuksReturnResult>
```

Attests a key for the specified user. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** 
- API version 26 and later: (ohos.permission.ATTEST_KEY and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS) or (ohos.permission.ENTERPRISE_ATTEST_KEY and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)
- API version 11 and later: ohos.permission.ATTEST_KEY and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Security.Huks.Extension

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. |
| keyAlias | string | Yes | Alias of the key. The certificate to be obtained stores the key. |
| huksOptions | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Options for attesting the key. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksReturnResult](arkts-universalkeystore-huks-huksreturnresult-i.md)&gt; | Promise used to return the result. If the operation is successful, **certChains** in **HuksReturnResult** is the certificate chain obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed: call the attestKeyItemAsUser API, missing Permission: ohos.permission.ATTEST_KEY, or the system has not been unlocked by user, or the user does not exist. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | non-system applications are not allowed to use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000001](../errorcode-huks.md#12000001-feature-not-supported) | Feature is not supported. Possible causes: 1. The algorithm mode is not supported. 2. The group key is not supported. 3. The crypto extension key is not supported. |
| [12000002](../errorcode-huks.md#12000002-missing-key-algorithm-parameter) | algorithm param is missing |
| [12000003](../errorcode-huks.md#12000003-invalid-key-algorithm-parameter) | algorithm param is invalid |
| [12000004](../errorcode-huks.md#12000004-file-error) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-algorithm-library-operation-failed) | error occurred in crypto engine |
| [12000011](../errorcode-huks.md#12000011-the-entity-does-not-exist) | queried entity does not exist |
| [12000012](../errorcode-huks.md#12000012-external-error) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | memory is insufficient |

**Examples**

```TypeScript
Prerequisites: see Example of generateKeyItemAsUser.
```
