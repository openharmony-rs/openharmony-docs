# createMd

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## createMd

```TypeScript
function createMd(algName: string): Md
```

Creates an **Md** instance.

<br>For details about the supported specifications, see [Supported Algorithms and Specifications](../../../security/CryptoArchitectureKit/crypto-generate-message-digest-overview.md#supported-algorithms-and-specifications).

**Since:** 9

**Model restriction:** 
- API version 12 and later: This API can be used in both the stage model and FA model.
- API versions 9 to 11: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.MessageDigest
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| algName | string | Yes | Message digest algorithm to use. For details about the supported algorithms, see [Supported Algorithms and Specifications](../../../security/CryptoArchitectureKit/crypto-generate-message-digest-overview.md#supported-algorithms-and-specifications). |

**Return value:**

| Type | Description |
| --- | --- |
| [Md](arkts-cryptoarchitecture-cryptoframework-md-i.md) | Returns the **Md** instance corresponding to the specified algorithm. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let md = cryptoFramework.createMd('SHA256');
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`sync failed: errCode: ${e.code}, errMsg: ${e.message}`);
}
```
