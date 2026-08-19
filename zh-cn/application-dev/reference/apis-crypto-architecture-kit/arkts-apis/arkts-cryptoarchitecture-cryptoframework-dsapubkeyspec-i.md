# DSAPubKeySpec

密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定DSA算法中公钥包含的参数。 <br>在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md) 方法创建密钥生成器。

**继承/实现关系：** DSAPubKeySpec extends [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)

**起始版本：** 23

<!--Device-cryptoFramework-interface DSAPubKeySpec--><!--Device-cryptoFramework-interface DSAPubKeySpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## params

```TypeScript
params: DSACommonParamsSpec
```

指定DSA算法中公私钥包含的公共参数。

**类型：** [DSACommonParamsSpec](arkts-cryptoarchitecture-cryptoframework-dsacommonparamsspec-i.md)

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DSAPubKeySpec-params: DSACommonParamsSpec--><!--Device-DSAPubKeySpec-params: DSACommonParamsSpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## pk

```TypeScript
pk: bigint
```

DSA算法的公钥pk。

**类型：** bigint

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DSAPubKeySpec-pk: bigint--><!--Device-DSAPubKeySpec-pk: bigint-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

