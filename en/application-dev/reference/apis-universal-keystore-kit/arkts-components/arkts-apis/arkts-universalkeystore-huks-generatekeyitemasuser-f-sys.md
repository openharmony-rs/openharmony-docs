# generateKeyItemAsUser (System API)

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## generateKeyItemAsUser

```TypeScript
function generateKeyItemAsUser(userId: number, keyAlias: string, huksOptions: HuksOptions): Promise<void>
```

Generates a key for the specified user. This API uses a promise to return the result. Based on the principle that the key cannot be transferred out of [Trusted Execution Environment (TEE)](../../../security/UniversalKeystoreKit/huks-concepts.md#tee), the key material content is not returned through the promise and is only used to indicate whether the call is successful.

**Since:** 12

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Security.Huks.Extension

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. |
| keyAlias | string | Yes | Key alias. The value can contain up to 128 bytes and should not include sensitive data such as personal information. |
| huksOptions | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | [Attribute tags](../../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#enums) of the key to generate. The algorithm, key purpose, and key length are mandatory. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed: call the generateKeyItemAsUser API, missing Permission: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS, or the system has not been unlocked by user, or the user does not exist. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | non-system applications are not allowed to use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000001](../errorcode-huks.md#12000001-feature-not-supported) | Feature is not supported. Possible causes: 1. The algorithm mode is not supported. 2. The group key is not supported. 3. The crypto extension key is not supported. |
| [12000002](../errorcode-huks.md#12000002-missing-key-algorithm-parameter) | algorithm param is missing |
| [12000003](../errorcode-huks.md#12000003-invalid-key-algorithm-parameter) | algorithm param is invalid |
| [12000004](../errorcode-huks.md#12000004-file-error) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-algorithm-library-operation-failed) | error occurred in crypto engine |
| [12000012](../errorcode-huks.md#12000012-external-error) | Device environment or input parameter abnormal |
| [12000013](../errorcode-huks.md#12000013-the-credential-does-not-exist) | queried credential does not exist |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | memory is insufficient |
| [12000015](../errorcode-huks.md#12000015-failed-to-invoke-other-system-services) | Failed to obtain the security information via UserIAM |
| [12000017](../errorcode-huks.md#12000017-duplicate-key-alias) | The key with the same alias already exists<br>**Applicable version:** 20 and later |

**Examples**

```TypeScript
Prerequisites:

The caller must be a system application running under user 0 to user 99 (inclusive) and must have the ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission. For details, see [singleton](../../../../device-dev/subsystems/subsys-app-privilege-config-guide.md#device-specific-application-privileges).
```
