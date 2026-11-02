# createKdf

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## createKdf

```TypeScript
function createKdf(algName: string): Kdf
```

Creates a KDF instance.

<br>For details about the supported specifications, see [Key Derivation Function Specifications](../../../security/CryptoArchitectureKit/crypto-key-derivation-overview.md).

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-cryptoFramework-function createKdf(algName: string): Kdf--><!--Device-cryptoFramework-function createKdf(algName: string): Kdf-End-->

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Kdf
- API version 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| algName | string | Yes | Key derivation algorithm (including the hash function for the HMAC). Currently, only PBKDF2, HKDF, SCRYPT and X963KDF are supported. For example, **PBKDF2&#124;SHA256**, **HKDF&#124;SHA256**, **SCRYPT**, or **X963KDF&#124;SHA256**.<br>For details about the supported specifications, see [Key Derivation Overview and Algorithm Specifications](../../../security/CryptoArchitectureKit/crypto-key-derivation-overview.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [Kdf](arkts-cryptoarchitecture-cryptoframework-kdf-i.md) | **Kdf** instance of the corresponding algorithm. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | [Sync] Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | This operation is not supported. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |

**Examples**

PBKDF2

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let kdf = cryptoFramework.createKdf('PBKDF2|SHA256');
```
