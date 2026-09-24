# encapsulate

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## encapsulate

```TypeScript
function encapsulate(keyAlias: string, params: HuksParam[],
      sharedKeyAlias?: string, sharedKeyParams?: HuksParam[]): Promise<HuksReturnResult>
```

Post-Quantum Cryptography key encapsulation operation, supporting key management by HUKS or by the application itself. If the application chooses to manage the key, the symmetric key is carried in the outData field of HuksReturnResult.

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Huks.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyAlias | string | Yes | indicates the name of the key for the Post-Quantum Cryptography algorithm. |
| params | [HuksParam](arkts-universalkeystore-huks-huksparam-i.md)[] | Yes | indicates the encapsulation properties. |
| sharedKeyAlias | string | No | indicates the key alias of the encapsulated key. If HUKS is used for key management, this parameter must be specified. If the application manages the key itself, this parameter is ignored. |
| sharedKeyParams | [HuksParam](arkts-universalkeystore-huks-huksparam-i.md)[] | No | indicates the properties of the encapsulated key. If HUKS is used for key management, this parameter must be specified. If the application manages the key itself, this parameter is ignored. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksReturnResult](arkts-universalkeystore-huks-huksreturnresult-i.md)&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000001](../errorcode-huks.md#12000001-feature-not-supported) | Algorithm mode is not supported |
| [12000002](../errorcode-huks.md#12000002-missing-key-algorithm-parameter) | Algorithm parameters are missing, please check the algorithm parameters. |
| [12000003](../errorcode-huks.md#12000003-invalid-key-algorithm-parameter) | The algorithm parameters are invalid, please check the algorithm parameters. |
| [12000004](../errorcode-huks.md#12000004-file-error) | File operation failed. |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | IPC communication failed. |
| [12000006](../errorcode-huks.md#12000006-algorithm-library-operation-failed) | The algorithm engine reported an error, please check the input parameters. |
| [12000011](../errorcode-huks.md#12000011-the-entity-does-not-exist) | The queried key does not exist, please check the key-related parameters. |
| [12000012](../errorcode-huks.md#12000012-external-error) | Device environment or input parameters are abnormal. |
| [12000013](../errorcode-huks.md#12000013-the-credential-does-not-exist) | Queried credential does not exist |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | Memory is insufficient. |
| [12000015](../errorcode-huks.md#12000015-failed-to-invoke-other-system-services) | Failed to obtain the security information via UserIAM. |
| 12000016 | The screen lock password is not set. |
| [12000017](../errorcode-huks.md#12000017-duplicate-key-alias) | The key with the same alias already exists. |
| [12000018](../errorcode-huks.md#12000018-invalid-input-parameter) | The input parameter is invalid. |
