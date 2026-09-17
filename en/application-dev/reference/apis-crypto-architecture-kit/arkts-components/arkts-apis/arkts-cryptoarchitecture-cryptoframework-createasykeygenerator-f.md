# createAsyKeyGenerator

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## createAsyKeyGenerator

```TypeScript
function createAsyKeyGenerator(algName: string): AsyKeyGenerator
```

Creates an **AsyKeyGenerator** instance based on the specified algorithm.

<br>For details about the supported specifications, see [Asymmetric Key Generation and Conversion Specifications](../../../security/CryptoArchitectureKit/crypto-key-generation-conversion.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| algName | string | Yes | Algorithm used by the asymmetric keys. For details, see the string parameters in [Asymmetric Key Generation and Conversion Specifications](../../../security/CryptoArchitectureKit/crypto-key-generation-conversion.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [AsyKeyGenerator](arkts-cryptoarchitecture-cryptoframework-asykeygenerator-i.md) | Returns the **AsyKeyGenerator** instance corresponding to the specified algorithm. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | This operation is not supported. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ECC256');
```
