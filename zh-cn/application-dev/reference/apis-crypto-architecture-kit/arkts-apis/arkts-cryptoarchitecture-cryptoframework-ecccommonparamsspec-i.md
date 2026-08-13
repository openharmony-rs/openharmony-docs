# ECCCommonParamsSpec

密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md#AsyKeySpec)的子类，用于指定ECC算法中公私钥包含的公共参数，随机生成公/私钥。 &lt;br&gt;在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createAsyKeyGeneratorBySpec) 方法创建密钥生成器。

**继承/实现关系：** ECCCommonParamsSpec extends [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md#AsyKeySpec)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-cryptoFramework-interface ECCCommonParamsSpec--><!--Device-cryptoFramework-interface ECCCommonParamsSpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## a

```TypeScript
a: bigint
```

指定椭圆曲线的第一个系数a。

**类型：** bigint

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ECCCommonParamsSpec-a: bigint--><!--Device-ECCCommonParamsSpec-a: bigint-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## b

```TypeScript
b: bigint
```

指定椭圆曲线的第二个系数b。

**类型：** bigint

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ECCCommonParamsSpec-b: bigint--><!--Device-ECCCommonParamsSpec-b: bigint-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## field

```TypeScript
field: ECField
```

指定椭圆曲线的域（当前只支持Fp域）。

**类型：** [ECField](arkts-cryptoarchitecture-cryptoframework-ecfield-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ECCCommonParamsSpec-field: ECField--><!--Device-ECCCommonParamsSpec-field: ECField-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## g

```TypeScript
g: Point
```

指定基点g。

**类型：** Point

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ECCCommonParamsSpec-g: Point--><!--Device-ECCCommonParamsSpec-g: Point-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## h

```TypeScript
h: int
```

指定余因子h。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ECCCommonParamsSpec-h: int--><!--Device-ECCCommonParamsSpec-h: int-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## n

```TypeScript
n: bigint
```

ECC算法中基点g的阶n。

**类型：** bigint

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ECCCommonParamsSpec-n: bigint--><!--Device-ECCCommonParamsSpec-n: bigint-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

