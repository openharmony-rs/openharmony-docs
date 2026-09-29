# OH_Huks_KeyMaterial25519

```c
struct OH_Huks_KeyMaterial25519 {...}
```

## 概述

定义25519类型密钥的结构体类型。

**系统能力：** SystemCapability.Security.Huks.Core

**起始版本：** 9

**相关模块：** [HuksTypeApi](capi-hukstypeapi.md)

**所在头文件：** [native_huks_type.h](capi-native-huks-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| enum OH_Huks_KeyAlg keyAlg | 密钥的算法类型。 |
| uint32_t keySize | 25519类型密钥的长度，单位：Bit。 |
| uint32_t pubKeySize | 公钥的长度，单位：Byte。 |
| uint32_t priKeySize | 私钥的长度，单位：Byte。 |
| uint32_t reserved | 保留字段。 |


