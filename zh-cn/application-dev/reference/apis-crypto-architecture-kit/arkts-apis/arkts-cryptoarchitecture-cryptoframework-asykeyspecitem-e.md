# AsyKeySpecItem

```TypeScript
enum AsyKeySpecItem
```

表示密钥参数的枚举。

**起始版本：** 10

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## DSA_P_BN

```TypeScript
DSA_P_BN = 101
```

DSA算法的素模数p。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## DSA_Q_BN

```TypeScript
DSA_Q_BN = 102
```

DSA算法中密钥参数q（p-1的素因子）。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## DSA_G_BN

```TypeScript
DSA_G_BN = 103
```

DSA算法的参数g。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## DSA_SK_BN

```TypeScript
DSA_SK_BN = 104
```

DSA算法的私钥sk。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## DSA_PK_BN

```TypeScript
DSA_PK_BN = 105
```

DSA算法的公钥pk。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ECC_FP_P_BN

```TypeScript
ECC_FP_P_BN = 201
```

ECC算法中表示椭圆曲线Fp域的素数p。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ECC_A_BN

```TypeScript
ECC_A_BN = 202
```

ECC算法中椭圆曲线的第一个系数a。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ECC_B_BN

```TypeScript
ECC_B_BN = 203
```

ECC算法中椭圆曲线的第二个系数b。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ECC_G_X_BN

```TypeScript
ECC_G_X_BN = 204
```

ECC算法中基点g的x坐标。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ECC_G_Y_BN

```TypeScript
ECC_G_Y_BN = 205
```

ECC算法中基点g的y坐标。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ECC_N_BN

```TypeScript
ECC_N_BN = 206
```

ECC算法中基点g的阶n。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ECC_H_NUM

```TypeScript
ECC_H_NUM = 207
```

ECC算法中的余因子h。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ECC_SK_BN

```TypeScript
ECC_SK_BN = 208
```

ECC算法中的私钥sk。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ECC_PK_X_BN

```TypeScript
ECC_PK_X_BN = 209
```

ECC算法中，公钥pk（椭圆曲线上的一个点）的x坐标。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ECC_PK_Y_BN

```TypeScript
ECC_PK_Y_BN = 210
```

ECC算法中，公钥pk（椭圆曲线上的一个点）的y坐标。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ECC_FIELD_TYPE_STR

```TypeScript
ECC_FIELD_TYPE_STR = 211
```

ECC算法中，椭圆曲线的域类型（当前只支持Fp域）。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ECC_FIELD_SIZE_NUM

```TypeScript
ECC_FIELD_SIZE_NUM = 212
```

ECC算法中域的大小，单位为bits（注：对于Fp域，域的大小为素数p的bits长度）。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ECC_CURVE_NAME_STR

```TypeScript
ECC_CURVE_NAME_STR = 213
```

ECC算法中的SECG(Standards for Efficient Cryptography Group)曲线名称。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## RSA_N_BN

```TypeScript
RSA_N_BN = 301
```

RSA算法中的模数n。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## RSA_SK_BN

```TypeScript
RSA_SK_BN = 302
```

RSA算法中的私钥sk（即私钥指数d）。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## RSA_PK_BN

```TypeScript
RSA_PK_BN = 303
```

RSA算法中的公钥pk（即公钥指数e）。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## DH_P_BN

```TypeScript
DH_P_BN = 401
```

DH算法中的素数p。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## DH_G_BN

```TypeScript
DH_G_BN = 402
```

DH算法中的参数g。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## DH_L_NUM

```TypeScript
DH_L_NUM = 403
```

DH算法中私钥长度，单位为bits。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## DH_SK_BN

```TypeScript
DH_SK_BN = 404
```

DH算法中的私钥sk。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## DH_PK_BN

```TypeScript
DH_PK_BN = 405
```

DH算法中的公钥pk。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ED25519_SK_BN

```TypeScript
ED25519_SK_BN = 501
```

Ed25519算法中的私钥sk。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ED25519_PK_BN

```TypeScript
ED25519_PK_BN = 502
```

Ed25519算法中的公钥pk。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## X25519_SK_BN

```TypeScript
X25519_SK_BN = 601
```

X25519算法中的私钥sk。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## X25519_PK_BN

```TypeScript
X25519_PK_BN = 602
```

X25519算法中的公钥pk。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

