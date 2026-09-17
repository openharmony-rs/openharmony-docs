# createKeyAgreement

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## createKeyAgreement

```TypeScript
function createKeyAgreement(algName: string): KeyAgreement
```

Creates a **KeyAgreement** instance.

<br>For details about the supported specifications, see[Key Agreement Overview and Algorithm Specifications](../../../security/CryptoArchitectureKit/crypto-key-agreement-overview.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.KeyAgreement
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| algName | string | Yes | Key agreement algorithm to use. In addition to ECDH, X25519 and DH are supported since API version 11.<br>For details about the supported specifications, see [Key Agreement Overview and Algorithm Specifications](../../../security/CryptoArchitectureKit/crypto-key-agreement-overview.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [KeyAgreement](arkts-cryptoarchitecture-cryptoframework-keyagreement-i.md) | Returns the **KeyAgreement** instance corresponding to the specified algorithm. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | This operation is not supported. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let keyAgreement = cryptoFramework.createKeyAgreement('ECC256');
```
