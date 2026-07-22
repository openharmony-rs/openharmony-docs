# HKDFSpec

密钥派生函数参数[KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md)的子类，作为HKDF密钥派生函数进行密钥派生时的输入。
> **说明：**  
>  
> key指的是用户输入的最初的密钥材料。根据模式的不同info与salt可以传空，但是不可不传。  
>  
> 例如：EXTRACT_AND_EXPAND模式需要输入全部的值，EXTRACT_ONLY模式info可以为空，在构建HKDFSpec的时候，info传入null值。  
>  
> 默认的模式为EXTRACT_AND_EXPAND，"HKDF|SHA256|EXTRACT_AND_EXPAND"等价于"HKDF|SHA256"。

**继承/实现关系：** HKDFSpec extends [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md)

**起始版本：** 12

<!--Device-cryptoFramework-interface HKDFSpec extends KdfSpec--><!--Device-cryptoFramework-interface HKDFSpec extends KdfSpec-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## info

```TypeScript
info: Uint8Array
```

拓展信息。

**类型：** Uint8Array

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HKDFSpec-info: Uint8Array--><!--Device-HKDFSpec-info: Uint8Array-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

## key

```TypeScript
key: string | Uint8Array
```

密钥材料。

**类型：** string \| Uint8Array

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HKDFSpec-key: string | Uint8Array--><!--Device-HKDFSpec-key: string | Uint8Array-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

## keySize

```TypeScript
keySize: number
```

派生得到的密钥字节长度，单位为bytes。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HKDFSpec-keySize: int--><!--Device-HKDFSpec-keySize: int-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

## salt

```TypeScript
salt: Uint8Array
```

盐值。

**类型：** Uint8Array

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HKDFSpec-salt: Uint8Array--><!--Device-HKDFSpec-salt: Uint8Array-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

