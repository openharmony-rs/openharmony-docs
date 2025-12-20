# OH_Huks_ExternalCryptoParam

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

```c
typedef struct {...} OH_Huks_ExternalCryptoParam
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
| uint32_t tag | 标签值。 |
| union {<br>  bool boolParam; <br>  int32_t int32Param; <br> uint32_t uint32Param; <br>    uint64_t uint64Param; <br>    [struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) blob; <br> } | 标签内容。<br>boolParam：布尔类型参数。<br>int32Param：int32_t类型参数。<br>uint32Param：uint32_t类型参数。<br>uint64Param：uint64_t类型参数。<br>blob：OH_Huks_Blob类型参数。  |


