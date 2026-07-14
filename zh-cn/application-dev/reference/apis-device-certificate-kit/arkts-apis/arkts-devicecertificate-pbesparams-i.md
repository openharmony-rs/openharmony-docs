# PbesParams

表示基于密码的加密算法参数，当前仅支持PBES2。

**起始版本：** 21

**系统能力：** SystemCapability.Security.Cert

## encryptionAlgorithm

```TypeScript
encryptionAlgorithm?: PbesEncryptionAlgorithm
```

表示PBES加密算法类型。默认为AES_256_CBC。

**类型：** PbesEncryptionAlgorithm

**默认值：** PbesEncryptionAlgorithm.AES_256_CBC

**起始版本：** 21

**元服务API：** 从API版本21开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## iterations

```TypeScript
iterations?: number
```

表示迭代次数。默认为2048。
取值应为正整数。

**类型：** number

**默认值：** 2048

**起始版本：** 21

**元服务API：** 从API版本21开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## saltLen

```TypeScript
saltLen?: number
```

表示盐值长度。默认为16，最小值为8。
取值应为≥8的整数。

**类型：** number

**默认值：** 16

**起始版本：** 21

**元服务API：** 从API版本21开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

