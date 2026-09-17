# createKem

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## createKem

```TypeScript
function createKem(algNameId: KemAlgNameId): Kem
```

Creates a Kem instance for key encapsulation and decapsulation operations.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| algNameId | [KemAlgNameId](arkts-cryptoarchitecture-cryptoframework-kemalgnameid-e.md) | Yes | The algorithm name ID of the KEM. |

**Return value:**

| Type | Description |
| --- | --- |
| [Kem](arkts-cryptoarchitecture-cryptoframework-kem-i.md) | Returns the **Kem** instance corresponding to the specified algorithm. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

function createKem() {
  try {
    let kem = cryptoFramework.createKem(cryptoFramework.KemAlgNameId.ML_KEM_768);
    console.info('create kem success');
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`create kem failed: errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```
