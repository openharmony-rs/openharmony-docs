# DHCommonParamsSpec

密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定DH算法中公私钥包含的公共参数。

在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。

**继承/实现关系：** DHCommonParamsSpec extends [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)

**起始版本：** 11

<!--Device-cryptoFramework-interface DHCommonParamsSpec extends AsyKeySpec--><!--Device-cryptoFramework-interface DHCommonParamsSpec extends AsyKeySpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## g

```TypeScript
g: bigint
```

DH算法中的参数g。

**类型：** bigint

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DHCommonParamsSpec-g: bigint--><!--Device-DHCommonParamsSpec-g: bigint-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

## l

```TypeScript
l: number
```

DH算法中私钥长度，单位为bits。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DHCommonParamsSpec-l: int--><!--Device-DHCommonParamsSpec-l: int-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

## p

```TypeScript
p: bigint
```

指定DH算法中大素数p。

**类型：** bigint

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DHCommonParamsSpec-p: bigint--><!--Device-DHCommonParamsSpec-p: bigint-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

