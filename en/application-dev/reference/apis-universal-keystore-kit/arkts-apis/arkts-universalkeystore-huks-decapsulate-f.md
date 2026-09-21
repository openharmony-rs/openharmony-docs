# decapsulate

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## decapsulate

```TypeScript
function decapsulate(keyAlias: string, params: HuksParam[], encapData: Uint8Array,
      sharedKeyAlias?: string, sharedKeyParams?:  HuksParam[]): Promise<HuksReturnResult>
```

Decapsulates a post-quantum cryptography key. This operation can be managed by HUKS or the app itself. If the app chooses to manage the key, the symmetric key is contained in the outData field of HuksReturnResult.

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Security.Huks.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyAlias | string | Yes | Alias of the post-quantum cryptography key. |
| params | [HuksParam](arkts-universalkeystore-huks-huksparam-i.md)[] | Yes | Decapsulation properties. |
| encapData | Uint8Array | Yes | Encapsulated shared key. |
| sharedKeyAlias | string | No | Alias of the key used for decapsulation. This parameter must be specified if HUKS is used for key management. If the app manages the key by itself, ignore this parameter. |
| sharedKeyParams | [HuksParam](arkts-universalkeystore-huks-huksparam-i.md)[] | No | Properties of the decapsulated key. This parameter must be specified if HUKS is used for key management. If the app manages the key by itself, ignore this parameter. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksReturnResult](arkts-universalkeystore-huks-huksreturnresult-i.md)&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000001](../errorcode-huks.md#12000001-feature-not-supported) | Algorithm mode is not supported |
| [12000002](../errorcode-huks.md#12000002-missing-key-algorithm-parameter) | The algorithm parameter is missing. Check the algorithm parameter. |
| [12000003](../errorcode-huks.md#12000003-invalid-key-algorithm-parameter) | The algorithm parameter is invalid. Check the algorithm parameter. |
| [12000004](../errorcode-huks.md#12000004-file-error) | The file operation failed. |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | IPC communication failed. |
| [12000006](../errorcode-huks.md#12000006-algorithm-library-operation-failed) | The algorithm engine reports an error. Check the input parameters. |
| [12000011](../errorcode-huks.md#12000011-the-entity-does-not-exist) | The queried key does not exist. Check the key-related parameters. |
| [12000012](../errorcode-huks.md#12000012-external-error) | The device environment or input parameter is abnormal. |
| [12000013](../errorcode-huks.md#12000013-the-credential-does-not-exist) | Queried credential does not exist |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | Insufficient memory. |
| [12000015](../errorcode-huks.md#12000015-failed-to-invoke-other-system-services) | Failed to obtain the security information using UserIAM. |
| 12000016 | The lock screen password is not set. |
| [12000017](../errorcode-huks.md#12000017-duplicate-key-alias) | A key with the same alias already exists. |
| [12000018](../errorcode-huks.md#12000018-invalid-input-parameter) | Invalid input parameter. |
