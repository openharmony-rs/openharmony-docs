# KeyEncodingConfig

RSA私钥编码参数，使用获取私钥字符串时，可以添加此参数，生成指定算法、密码的编码后的私钥字符串。
> **说明：**  
>  
> - password是必选参数，表示编码用到的密码。  
>  
> - cipherName是必选参数，指定编码用到的算法。当前仅支持AES-128-CBC、AES-192-CBC、AES-256-CBC、DES-EDE3-CBC。

**起始版本：** 18

<!--Device-cryptoFramework-interface KeyEncodingConfig--><!--Device-cryptoFramework-interface KeyEncodingConfig-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## cipherName

```TypeScript
cipherName: string
```

用于编码私钥的对称密码算法。

**类型：** string

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEncodingConfig-cipherName: string--><!--Device-KeyEncodingConfig-cipherName: string-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## password

```TypeScript
password: string
```

密码。

**类型：** string

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEncodingConfig-password: string--><!--Device-KeyEncodingConfig-password: string-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

