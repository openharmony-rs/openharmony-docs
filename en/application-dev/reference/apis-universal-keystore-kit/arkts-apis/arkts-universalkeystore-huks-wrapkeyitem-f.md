# wrapKeyItem

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## wrapKeyItem

```TypeScript
function wrapKeyItem(keyAlias: string, params: HuksOptions): Promise<HuksReturnResult>
```

Wraps a key. This API uses a promise to return the result.

> **NOTE:** 
> 
> Wrapping SE security level keys that defined in [HuksKeySecurityLevel](arkts-universalkeystore-huks-hukskeysecuritylevel-e.md)
> requires the ohos.permission.ACCESS_SE_KEY permission.

<!--Del-->This feature is not supported currently.<!--DelEnd-->

**Since:** 20

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Huks.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyAlias | string | Yes | Key alias, which must be the same as the alias used when the key was generated. |
| params | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Encryption type of the key to be exported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksReturnResult](arkts-universalkeystore-huks-huksreturnresult-i.md)&gt; | Promise that returns the operation result. If the operation is successful, **outData** in **HuksReturnResult** is the exported key ciphertext. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed: call the wrapKeyItem API, missing Permission: ohos.permission.ACCESS_SE_KEY.<br>**Applicable version:** 26.0.0 and later |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000004](../errorcode-huks.md#12000004-file-error) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | IPC communication failed |
| [12000011](../errorcode-huks.md#12000011-the-entity-does-not-exist) | queried entity does not exist |
| [12000012](../errorcode-huks.md#12000012-external-error) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | memory is insufficient |
| [12000018](../errorcode-huks.md#12000018-invalid-input-parameter) | the input parameter is invalid |
| [12000026](../errorcode-huks.md#12000026-secure-element-fault) | the secure element is not available<br>**Applicable version:** 26.0.0 and later |
