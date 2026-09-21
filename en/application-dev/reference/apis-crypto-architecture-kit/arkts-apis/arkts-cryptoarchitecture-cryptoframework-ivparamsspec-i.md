# IvParamsSpec

```TypeScript
interface IvParamsSpec extends ParamsSpec
```

Encapsulates the parameters for encryption or decryption using a block cipher mode that requires an IV. It is a child class of [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md) and used as a parameter in [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-3) for symmetric encryption or decryption.

<br>This is applicable to block cipher modes that require an IV, such as CBC, CTR, OFB, and CFB.

> **NOTE:** 
> 
> Before passing a value to
> [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-3), specify
> **algName** for its parent class [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md).

**Inheritance/Implementation:** IvParamsSpec extends [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)

**Since:** 9

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## iv

```TypeScript
iv: DataBlob
```

IV parameter for encryption/decryption. Common lengths are listed below:

- In the CBC, CTR, OFB, or CFB mode of AES: The IV length is 16 bytes.  
- In the CBC, OFB, or CFB mode of 3DES: The IV length is 8 bytes.  
- In the CBC, CTR, OFB, or CFB mode of SM4&lt;sup&gt;10+&lt;/sup&gt;: The IV length is 16 bytes.

**Type:** [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 9 to 11: SystemCapability.Security.CryptoFramework
