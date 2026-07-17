# RSACommonParamsSpec

密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定RSA算法中公私钥包含的公共参数，随机生成公/私钥。

在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。

**继承/实现关系：** RSACommonParamsSpec extends [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)

**起始版本：** 10

<!--Device-cryptoFramework-interface RSACommonParamsSpec extends AsyKeySpec--><!--Device-cryptoFramework-interface RSACommonParamsSpec extends AsyKeySpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## n

```TypeScript
n: bigint
```

指定模数n。

**类型：** bigint

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RSACommonParamsSpec-n: bigint--><!--Device-RSACommonParamsSpec-n: bigint-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

