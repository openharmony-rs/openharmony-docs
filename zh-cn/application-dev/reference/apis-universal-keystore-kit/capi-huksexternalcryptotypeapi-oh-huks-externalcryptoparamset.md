# OH_Huks_ExternalCryptoParamSet

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

```c
typedef struct OH_Huks_ExternalCryptoParamSet {...} OH_Huks_ExternalCryptoParamSet
```

## 概述

定义外部加密参数集合的结构。

**起始版本：** 22

**相关模块：** [HuksExternalCryptoTypeApi](capi-huksexternalcryptotypeapi.md)

**所在头文件：** [native_huks_external_crypto_type.h](capi-native-huks-external-crypto-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t paramSetSize | 参数集合所占内存大小，单位：Byte。<br>**起始版本：** 22 |
| uint32_t paramsCnt | 参数集合中的参数数量。<br>**起始版本：** 22 |
| [OH_Huks_ExternalCryptoParam](capi-huksexternalcryptotypeapi-oh-huks-externalcryptoparam.md) params[] | 参数数组，大小由paramSetSize与paramsCnt决定。<br>**起始版本：** 22 |


