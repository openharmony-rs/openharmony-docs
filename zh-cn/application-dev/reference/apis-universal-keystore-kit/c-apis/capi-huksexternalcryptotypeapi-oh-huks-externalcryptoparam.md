# OH_Huks_ExternalCryptoParam

```c
typedef struct OH_Huks_ExternalCryptoParam {...} OH_Huks_ExternalCryptoParam
```

## 概述

定义参数集合中单个参数的结构体。

**起始版本：** 22

**相关模块：** [HuksExternalCryptoTypeApi](capi-huksexternalcryptotypeapi.md)

**所在头文件：** [native_huks_external_crypto_type.h](capi-native-huks-external-crypto-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t tag | 标签值。<br>**起始版本：** 22 |
| union | 标签内容。<br>**起始版本：** 22 |
| bool boolParam | 布尔类型参数。<br>**起始版本：** 22 |
| int32_t int32Param | int32_t类型参数。<br>**起始版本：** 22 |
| uint32_t uint32Param | uint32_t类型参数。<br>**起始版本：** 22 |
| uint64_t uint64Param | uint64_t类型参数。<br>**起始版本：** 22 |
| struct [OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) blob; } | OH_Huks_Blob类型参数。<br>**起始版本：** 22 |


