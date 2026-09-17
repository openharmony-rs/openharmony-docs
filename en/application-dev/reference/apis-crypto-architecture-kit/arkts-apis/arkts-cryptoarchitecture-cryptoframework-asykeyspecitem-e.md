# AsyKeySpecItem

Enumerates the asymmetric key parameters.

**Since:** 10

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## DSA_P_BN

```TypeScript
DSA_P_BN = 101
```

Prime modulus **p** in the DSA algorithm.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## DSA_Q_BN

```TypeScript
DSA_Q_BN = 102
```

Parameter **q**, prime factor of (p - 1) in the DSA algorithm.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## DSA_G_BN

```TypeScript
DSA_G_BN = 103
```

Parameter **g** in the DSA algorithm.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## DSA_SK_BN

```TypeScript
DSA_SK_BN = 104
```

Private key **sk** in the DSA algorithm.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## DSA_PK_BN

```TypeScript
DSA_PK_BN = 105
```

Public key **pk** in the DSA algorithm.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## ECC_FP_P_BN

```TypeScript
ECC_FP_P_BN = 201
```

Prime number **p** in the **Fp** field of the elliptic curve in the ECC algorithm.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## ECC_A_BN

```TypeScript
ECC_A_BN = 202
```

First coefficient **a** of the elliptic curve in the ECC algorithm.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## ECC_B_BN

```TypeScript
ECC_B_BN = 203
```

Second coefficient **b** of the elliptic curve in the ECC algorithm.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## ECC_G_X_BN

```TypeScript
ECC_G_X_BN = 204
```

X coordinate of the base point **g** in the ECC algorithm.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## ECC_G_Y_BN

```TypeScript
ECC_G_Y_BN = 205
```

Y coordinate of the base point **g** in the ECC algorithm.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## ECC_N_BN

```TypeScript
ECC_N_BN = 206
```

Order **n** of the base point **g** in the ECC algorithm.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## ECC_H_NUM

```TypeScript
ECC_H_NUM = 207
```

Cofactor **h** in the ECC algorithm.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## ECC_SK_BN

```TypeScript
ECC_SK_BN = 208
```

Private key **sk** in the ECC algorithm.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## ECC_PK_X_BN

```TypeScript
ECC_PK_X_BN = 209
```

X coordinate of the public key **pk** (a point on the elliptic curve) in the ECC algorithm.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## ECC_PK_Y_BN

```TypeScript
ECC_PK_Y_BN = 210
```

Y coordinate of the public key **pk** (a point on the elliptic curve) in the ECC algorithm.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## ECC_FIELD_TYPE_STR

```TypeScript
ECC_FIELD_TYPE_STR = 211
```

Elliptic curve field type in the ECC algorithm. Currently, only the **Fp** field is supported.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## ECC_FIELD_SIZE_NUM

```TypeScript
ECC_FIELD_SIZE_NUM = 212
```

Size of the field in the ECC algorithm, in bits.

Note: The size of the **Fp** field is the length of the prime **p**, in bits.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## ECC_CURVE_NAME_STR

```TypeScript
ECC_CURVE_NAME_STR = 213
```

Standards for Efficient Cryptography Group (SECG) curve name in the ECC algorithm.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## RSA_N_BN

```TypeScript
RSA_N_BN = 301
```

Modulus **n** in the RSA algorithm.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## RSA_SK_BN

```TypeScript
RSA_SK_BN = 302
```

Private key **sk** (private key exponent **d**) in the RSA algorithm.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## RSA_PK_BN

```TypeScript
RSA_PK_BN = 303
```

Public key **pk** (public key exponent **e**) in the RSA algorithm.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## DH_P_BN

```TypeScript
DH_P_BN = 401
```

Prime **p** in the DH algorithm.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API version 11: SystemCapability.Security.CryptoFramework

## DH_G_BN

```TypeScript
DH_G_BN = 402
```

Parameter **g** in the DH algorithm.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API version 11: SystemCapability.Security.CryptoFramework

## DH_L_NUM

```TypeScript
DH_L_NUM = 403
```

Length of the private key in the DH algorithm, in bits.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API version 11: SystemCapability.Security.CryptoFramework

## DH_SK_BN

```TypeScript
DH_SK_BN = 404
```

Private key **sk** in the DH algorithm.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API version 11: SystemCapability.Security.CryptoFramework

## DH_PK_BN

```TypeScript
DH_PK_BN = 405
```

Public key **pk** in the DH algorithm.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API version 11: SystemCapability.Security.CryptoFramework

## ED25519_SK_BN

```TypeScript
ED25519_SK_BN = 501
```

Private key **sk** in the Ed25519 algorithm.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API version 11: SystemCapability.Security.CryptoFramework

## ED25519_PK_BN

```TypeScript
ED25519_PK_BN = 502
```

Public key **pk** in the Ed25519 algorithm.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API version 11: SystemCapability.Security.CryptoFramework

## X25519_SK_BN

```TypeScript
X25519_SK_BN = 601
```

Private key **sk** in the X25519 algorithm.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API version 11: SystemCapability.Security.CryptoFramework

## X25519_PK_BN

```TypeScript
X25519_PK_BN = 602
```

Public key **pk** in the X25519 algorithm.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API version 11: SystemCapability.Security.CryptoFramework
