# AsyKeyDataItem

```TypeScript
enum AsyKeyDataItem
```

Enumerates the asymmetric key data types.

**Since:** 26.0.0

<!--Device-cryptoFramework-enum AsyKeyDataItem--><!--Device-cryptoFramework-enum AsyKeyDataItem-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ML_DSA_PRIVATE_SEED

```TypeScript
ML_DSA_PRIVATE_SEED = 0
```

Indicates the private seed of the ML-DSA private key.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-AsyKeyDataItem-ML_DSA_PRIVATE_SEED = 0--><!--Device-AsyKeyDataItem-ML_DSA_PRIVATE_SEED = 0-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ML_DSA_PRIVATE_RAW

```TypeScript
ML_DSA_PRIVATE_RAW = 1
```

Indicates the raw private key data of the ML-DSA private key.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-AsyKeyDataItem-ML_DSA_PRIVATE_RAW = 1--><!--Device-AsyKeyDataItem-ML_DSA_PRIVATE_RAW = 1-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ML_DSA_PUBLIC_RAW

```TypeScript
ML_DSA_PUBLIC_RAW = 2
```

Indicates the raw public key data of the ML-DSA public key.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-AsyKeyDataItem-ML_DSA_PUBLIC_RAW = 2--><!--Device-AsyKeyDataItem-ML_DSA_PUBLIC_RAW = 2-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ML_KEM_PRIVATE_SEED

```TypeScript
ML_KEM_PRIVATE_SEED = 3
```

Indicates the private seed of the ML-KEM private key.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-AsyKeyDataItem-ML_KEM_PRIVATE_SEED = 3--><!--Device-AsyKeyDataItem-ML_KEM_PRIVATE_SEED = 3-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ML_KEM_PRIVATE_RAW

```TypeScript
ML_KEM_PRIVATE_RAW = 4
```

Indicates the raw private key data of the ML-KEM private key.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-AsyKeyDataItem-ML_KEM_PRIVATE_RAW = 4--><!--Device-AsyKeyDataItem-ML_KEM_PRIVATE_RAW = 4-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Key.AsymKey

## ML_KEM_PUBLIC_RAW

```TypeScript
ML_KEM_PUBLIC_RAW = 5
```

Indicates the raw public key data of the ML-KEM public key.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-AsyKeyDataItem-ML_KEM_PUBLIC_RAW = 5--><!--Device-AsyKeyDataItem-ML_KEM_PUBLIC_RAW = 5-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Key.AsymKey

## EC_PRIVATE_K

```TypeScript
EC_PRIVATE_K = 6
```

Private key scalar **k** on the elliptic curve (EC).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-AsyKeyDataItem-EC_PRIVATE_K = 6--><!--Device-AsyKeyDataItem-EC_PRIVATE_K = 6-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Key.AsymKey

## EC_PRIVATE_04_X_Y_K

```TypeScript
EC_PRIVATE_04_X_Y_K = 7
```

Indicates the composite encoding 04||X||Y||K of the EC key, where 04||X||Y is the uncompressed public key point and K is the private key scalar.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-AsyKeyDataItem-EC_PRIVATE_04_X_Y_K = 7--><!--Device-AsyKeyDataItem-EC_PRIVATE_04_X_Y_K = 7-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Key.AsymKey

## EC_PUBLIC_X_Y

```TypeScript
EC_PUBLIC_X_Y = 8
```

Indicates the X||Y format encoded data representing an EC public key

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-AsyKeyDataItem-EC_PUBLIC_X_Y = 8--><!--Device-AsyKeyDataItem-EC_PUBLIC_X_Y = 8-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Key.AsymKey

## EC_PUBLIC_04_X_Y

```TypeScript
EC_PUBLIC_04_X_Y = 9
```

Indicates the 04||X||Y format encoded data representing an EC public key

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-AsyKeyDataItem-EC_PUBLIC_04_X_Y = 9--><!--Device-AsyKeyDataItem-EC_PUBLIC_04_X_Y = 9-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Key.AsymKey

## EC_PUBLIC_COMPRESS_X

```TypeScript
EC_PUBLIC_COMPRESS_X = 10
```

Indicates the 02||X or 03||X format encoded data representing an EC public key

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-AsyKeyDataItem-EC_PUBLIC_COMPRESS_X = 10--><!--Device-AsyKeyDataItem-EC_PUBLIC_COMPRESS_X = 10-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Key.AsymKey
