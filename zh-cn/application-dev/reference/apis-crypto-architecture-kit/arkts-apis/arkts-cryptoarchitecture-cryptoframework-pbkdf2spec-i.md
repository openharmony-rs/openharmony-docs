# PBKDF2Spec

密钥派生函数参数[KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md)的子类，作为PBKDF2密钥派生函数进行密钥派生时的输入。

> **说明：**  
>  
> password 是原始密码。如果使用 string 类型，需直接传入用于密钥派生的数据，而不是 HexString 或 base64 等字符串类型，并确保该字符串  
> 为 UTF-8 编码，否则派生结果会有差异。

**继承/实现关系：** PBKDF2Spec extends [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md)

**起始版本：** 11

<!--Device-cryptoFramework-interface PBKDF2Spec extends KdfSpec--><!--Device-cryptoFramework-interface PBKDF2Spec extends KdfSpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Kdf
- API版本11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## iterations

```TypeScript
iterations: number
```

迭代次数，需要为正整数。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PBKDF2Spec-iterations: int--><!--Device-PBKDF2Spec-iterations: int-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Kdf
- API版本11：SystemCapability.Security.CryptoFramework

## keySize

```TypeScript
keySize: number
```

派生得到的密钥字节长度，单位为bytes。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PBKDF2Spec-keySize: int--><!--Device-PBKDF2Spec-keySize: int-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Kdf
- API版本11：SystemCapability.Security.CryptoFramework

## password

```TypeScript
password: string | Uint8Array
```

用户输入的原始密码。

**类型：** string | Uint8Array

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PBKDF2Spec-password: string | Uint8Array--><!--Device-PBKDF2Spec-password: string | Uint8Array-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Kdf
- API版本11：SystemCapability.Security.CryptoFramework

## salt

```TypeScript
salt: Uint8Array
```

盐值。

**类型：** Uint8Array

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PBKDF2Spec-salt: Uint8Array--><!--Device-PBKDF2Spec-salt: Uint8Array-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Kdf
- API版本11：SystemCapability.Security.CryptoFramework

