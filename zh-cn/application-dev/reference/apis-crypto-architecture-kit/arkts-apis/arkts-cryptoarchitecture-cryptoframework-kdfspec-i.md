# KdfSpec

密钥派生函数参数，使用密钥派生函数进行密钥派生时，需要构建其子类对象并作为输入。

**起始版本：** 11

<!--Device-cryptoFramework-interface KdfSpec--><!--Device-cryptoFramework-interface KdfSpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Kdf
- API版本11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## algName

```TypeScript
algName: string
```

指明密钥派生函数的算法名，如"PBKDF2"。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KdfSpec-algName: string--><!--Device-KdfSpec-algName: string-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Kdf
- API版本11：SystemCapability.Security.CryptoFramework

