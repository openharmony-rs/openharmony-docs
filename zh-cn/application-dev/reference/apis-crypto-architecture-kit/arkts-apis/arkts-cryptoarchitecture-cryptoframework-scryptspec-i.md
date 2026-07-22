# ScryptSpec

密钥派生函数参数[KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md)的子类，作为SCRYPT密钥派生函数进行密钥派生时的输入。
> **说明：**  
>  
> passphrase指的是原始密码，如果使用string类型，需要直接传入用于密钥派生的数据，而不是HexString、base64等字符串类型，同时需要确保该  
> 字符串为utf-8编码，否则派生结果会有差异。

**继承/实现关系：** ScryptSpec extends [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md)

**起始版本：** 18

<!--Device-cryptoFramework-interface ScryptSpec extends KdfSpec--><!--Device-cryptoFramework-interface ScryptSpec extends KdfSpec-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## keySize

```TypeScript
keySize: number
```

派生得到的密钥字节长度，需要为正整数，单位为bytes。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ScryptSpec-keySize: int--><!--Device-ScryptSpec-keySize: int-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

## maxMemory

```TypeScript
maxMemory: number
```

最大内存限制参数，需要为正整数，单位为bytes。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ScryptSpec-maxMemory: long--><!--Device-ScryptSpec-maxMemory: long-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

## n

```TypeScript
n: number
```

CPU/内存开销参数，需要为正整数。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ScryptSpec-n: long--><!--Device-ScryptSpec-n: long-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

## p

```TypeScript
p: number
```

并行化参数，需要为正整数。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ScryptSpec-p: long--><!--Device-ScryptSpec-p: long-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

## passphrase

```TypeScript
passphrase: string | Uint8Array
```

用户输入的原始密码。

**类型：** string \| Uint8Array

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ScryptSpec-passphrase: string | Uint8Array--><!--Device-ScryptSpec-passphrase: string | Uint8Array-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

## r

```TypeScript
r: number
```

块大小参数，需要为正整数。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ScryptSpec-r: long--><!--Device-ScryptSpec-r: long-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

## salt

```TypeScript
salt: Uint8Array
```

盐值。

**类型：** Uint8Array

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ScryptSpec-salt: Uint8Array--><!--Device-ScryptSpec-salt: Uint8Array-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

