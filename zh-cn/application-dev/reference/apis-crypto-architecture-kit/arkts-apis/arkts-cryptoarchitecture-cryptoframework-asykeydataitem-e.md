# AsyKeyDataItem

表示非对称密钥数据项类型的枚举。

**起始版本：** 26.0.0

<!--Device-cryptoFramework-enum AsyKeyDataItem--><!--Device-cryptoFramework-enum AsyKeyDataItem-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ML_DSA_PRIVATE_SEED

```TypeScript
ML_DSA_PRIVATE_SEED = 0
```

ML-DSA私钥的私有种子。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyDataItem-ML_DSA_PRIVATE_SEED = 0--><!--Device-AsyKeyDataItem-ML_DSA_PRIVATE_SEED = 0-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ML_DSA_PRIVATE_RAW

```TypeScript
ML_DSA_PRIVATE_RAW = 1
```

ML-DSA私钥的原始私钥数据。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyDataItem-ML_DSA_PRIVATE_RAW = 1--><!--Device-AsyKeyDataItem-ML_DSA_PRIVATE_RAW = 1-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ML_DSA_PUBLIC_RAW

```TypeScript
ML_DSA_PUBLIC_RAW = 2
```

ML-DSA公钥的原始公钥数据。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyDataItem-ML_DSA_PUBLIC_RAW = 2--><!--Device-AsyKeyDataItem-ML_DSA_PUBLIC_RAW = 2-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ML_KEM_PRIVATE_SEED

```TypeScript
ML_KEM_PRIVATE_SEED = 3
```

ML-KEM私钥的私有种子。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyDataItem-ML_KEM_PRIVATE_SEED = 3--><!--Device-AsyKeyDataItem-ML_KEM_PRIVATE_SEED = 3-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ML_KEM_PRIVATE_RAW

```TypeScript
ML_KEM_PRIVATE_RAW = 4
```

ML-KEM私钥的原始私钥数据。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyDataItem-ML_KEM_PRIVATE_RAW = 4--><!--Device-AsyKeyDataItem-ML_KEM_PRIVATE_RAW = 4-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ML_KEM_PUBLIC_RAW

```TypeScript
ML_KEM_PUBLIC_RAW = 5
```

ML-KEM公钥的原始公钥数据。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyDataItem-ML_KEM_PUBLIC_RAW = 5--><!--Device-AsyKeyDataItem-ML_KEM_PUBLIC_RAW = 5-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## EC_PRIVATE_K

```TypeScript
EC_PRIVATE_K = 6
```

表示椭圆曲线（EC）上的私钥标量k。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyDataItem-EC_PRIVATE_K = 6--><!--Device-AsyKeyDataItem-EC_PRIVATE_K = 6-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## EC_PRIVATE_04_X_Y_K

```TypeScript
EC_PRIVATE_04_X_Y_K = 7
```

表示椭圆曲线（EC）密钥的复合编码04||X||Y||K，其中04||X||Y为非压缩公钥点，K为私钥标量。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyDataItem-EC_PRIVATE_04_X_Y_K = 7--><!--Device-AsyKeyDataItem-EC_PRIVATE_04_X_Y_K = 7-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## EC_PUBLIC_X_Y

```TypeScript
EC_PUBLIC_X_Y = 8
```

表示椭圆曲线（EC）公钥的 X||Y格式编码数据。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyDataItem-EC_PUBLIC_X_Y = 8--><!--Device-AsyKeyDataItem-EC_PUBLIC_X_Y = 8-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## EC_PUBLIC_04_X_Y

```TypeScript
EC_PUBLIC_04_X_Y = 9
```

表示椭圆曲线（EC）公钥的 04||X||Y格式编码数据。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyDataItem-EC_PUBLIC_04_X_Y = 9--><!--Device-AsyKeyDataItem-EC_PUBLIC_04_X_Y = 9-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## EC_PUBLIC_COMPRESS_X

```TypeScript
EC_PUBLIC_COMPRESS_X = 10
```

表示椭圆曲线（EC）公钥的 02||X 或 03||X格式编码数据。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyDataItem-EC_PUBLIC_COMPRESS_X = 10--><!--Device-AsyKeyDataItem-EC_PUBLIC_COMPRESS_X = 10-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

