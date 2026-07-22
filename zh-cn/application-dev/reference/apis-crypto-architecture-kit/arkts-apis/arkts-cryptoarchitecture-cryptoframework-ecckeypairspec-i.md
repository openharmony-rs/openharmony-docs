# ECCKeyPairSpec

密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定ECC算法中公私钥包含的全量参数。

在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec)方法创建密钥生成器。

**继承/实现关系：** ECCKeyPairSpec extends [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)

**起始版本：** 10

<!--Device-cryptoFramework-interface ECCKeyPairSpec extends AsyKeySpec--><!--Device-cryptoFramework-interface ECCKeyPairSpec extends AsyKeySpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## params

```TypeScript
params: ECCCommonParamsSpec
```

指定ECC算法中公私钥都包含的公共参数。

**类型：** ECCCommonParamsSpec

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ECCKeyPairSpec-params: ECCCommonParamsSpec--><!--Device-ECCKeyPairSpec-params: ECCCommonParamsSpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## pk

```TypeScript
pk: Point
```

指定ECC算法的公钥pk。

**类型：** Point

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ECCKeyPairSpec-pk: Point--><!--Device-ECCKeyPairSpec-pk: Point-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## sk

```TypeScript
sk: bigint
```

ECC算法中的私钥sk。

**类型：** bigint

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ECCKeyPairSpec-sk: bigint--><!--Device-ECCKeyPairSpec-sk: bigint-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

