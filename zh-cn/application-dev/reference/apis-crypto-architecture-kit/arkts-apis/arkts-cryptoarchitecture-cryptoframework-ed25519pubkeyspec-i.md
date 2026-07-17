# ED25519PubKeySpec

密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定Ed25519算法中公钥包含的参数。

在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。

**继承/实现关系：** ED25519PubKeySpec extends [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)

**起始版本：** 11

<!--Device-cryptoFramework-interface ED25519PubKeySpec extends AsyKeySpec--><!--Device-cryptoFramework-interface ED25519PubKeySpec extends AsyKeySpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## pk

```TypeScript
pk: bigint
```

Ed25519算法中的公钥pk。

**类型：** bigint

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ED25519PubKeySpec-pk: bigint--><!--Device-ED25519PubKeySpec-pk: bigint-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

