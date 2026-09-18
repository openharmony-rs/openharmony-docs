# ParamsSpec

Encapsulates the parameters used for encryption or decryption. You need to construct its child class object and pass it to [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init) for symmetric encryption or decryption.

<br>It applies to the symmetric block cipher modes that require parameters such as the initialization vector (IV). If the IV is not required (for example, the ECB mode), pass in **null** to [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init).

> **NOTE:** 
> 
> An initialization vector (IV) is a byte sequence used to introduce randomness or uniqueness in symmetric
> encryption modes (such as CBC, CTR, OFB, CFB, GCM, CCM, and ChaCha20-Poly1305). It ensures that different
> ciphertexts are generated for the same plaintext under the same key.

> **NOTE:** 
> 
> The **params** parameter in
> [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init) is of the
> **ParamsSpec** type (parent class). However, a child class object (such as
> [IvParamsSpec](arkts-cryptoarchitecture-cryptoframework-ivparamsspec-i.md)) needs to be passed in. When constructing the child class
> object, you must set **algName** for its parent class **ParamsSpec** to specify the child class object to be
> passed to **init()**.

**Since:** 9

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## algName

```TypeScript
algName: string
```

Algorithm for symmetric encryption or decryption. The value can be:

- **IvParamsSpec**: applicable to the CBC, CTR, OFB, and CFB modes.  
- **GcmParamsSpec**: applicable to the GCM mode.  
- **CcmParamsSpec**: applicable to the CCM mode.  
- **AeadParamsSpec**: applicable to the AES-GCM, AES-CCM, SM4-GCM and ChaCha20-Poly1305 algorithm.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 9 to 11: SystemCapability.Security.CryptoFramework
