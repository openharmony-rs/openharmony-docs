# KeyEncodingConfig

```TypeScript
interface KeyEncodingConfig
```

Represents the RSA private key encoding parameters. You can use it to generate an encoded private key string with the specified algorithm and password.

> **NOTE:** 
> 
> - **password** specifies the password used for encoding the private key. It is mandatory.
> 
> - **cipherName** specifies the algorithm used for encoding. It is mandatory. Currently, only **AES-128-CBC**,
> **AES-192-CBC**, **AES-256-CBC**, and **DES-EDE3-CBC** are supported.

**Since:** 18

**System capability:** SystemCapability.Security.CryptoFramework.Key.AsymKey

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## cipherName

```TypeScript
cipherName: string
```

Symmetric cipher algorithm used for encoding the private key.

**Type:** string

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.CryptoFramework.Key.AsymKey

## password

```TypeScript
password: string
```

Password used for encoding the private key.

**Type:** string

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.CryptoFramework.Key.AsymKey
