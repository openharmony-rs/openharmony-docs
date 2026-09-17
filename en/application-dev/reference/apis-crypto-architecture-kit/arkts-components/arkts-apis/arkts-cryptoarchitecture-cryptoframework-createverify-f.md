# createVerify

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## createVerify

```TypeScript
function createVerify(algName: string): Verify
```

Creates a **Verify** instance.

<br>For details about the supported specifications, see [Signing and Signature Verification Overview and Algorithm Specifications](../../../security/CryptoArchitectureKit/crypto-sign-sig-verify-overview.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Signature
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| algName | string | Yes | Signature verification algorithm to use. Currently, RSA, ECC, DSA, SM2&lt;sup&gt;10+&lt;/sup&gt;, Ed25519&lt;sup&gt;11+&lt;/sup&gt; and ML-DSA&lt;sup&gt;26.0.0+&lt;/sup&gt; are supported. <br>If RSA PKCS1 is used, you must set the digest. If RSA PSS is used, you must set the digest and mask digest. When the RSA algorithm is used for signature verification, you can use **recover** to verify and recover the signed data. <br>For details about the supported specifications, see [Signing and Signature Verification Overview and Algorithm Specifications](../../../security/CryptoArchitectureKit/crypto-sign-sig-verify-overview.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [Verify](arkts-cryptoarchitecture-cryptoframework-verify-i.md) | Returns the **Verify** instance corresponding to the specified algorithm. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | This operation is not supported. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let verifier1 = cryptoFramework.createVerify('RSA1024|PKCS1|SHA256');

let verifier2 = cryptoFramework.createVerify('RSA1024|PSS|SHA256|MGF1_SHA256');

let verifier3 = cryptoFramework.createVerify('RSA1024|PKCS1|SHA256|Recover');
```
