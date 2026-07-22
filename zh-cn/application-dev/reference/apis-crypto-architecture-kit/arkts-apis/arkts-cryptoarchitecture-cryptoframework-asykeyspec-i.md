# AsyKeySpec

指定非对称密钥参数的基本接口，用于创建密钥生成器。在指定非对称密钥参数时需要构造其子类对象，并将子类对象传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec)方法创建密钥生成器。构造子类对象时，除了RSA密钥采用小端写法外，其他bigint类型的密钥参数均采用大端写法，并使用正数。

**起始版本：** 10

<!--Device-cryptoFramework-interface AsyKeySpec--><!--Device-cryptoFramework-interface AsyKeySpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## algName

```TypeScript
algName: string
```

指定非对称密钥的算法名称，比如"RSA"、"DSA"、"ECC"、"SM2"、"Ed25519"、"X25519"、"DH"。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeySpec-algName: string--><!--Device-AsyKeySpec-algName: string-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## specType

```TypeScript
specType: AsyKeySpecType
```

指定密钥参数类型，用于区分公/私钥参数。

**类型：** AsyKeySpecType

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeySpec-specType: AsyKeySpecType--><!--Device-AsyKeySpec-specType: AsyKeySpecType-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

