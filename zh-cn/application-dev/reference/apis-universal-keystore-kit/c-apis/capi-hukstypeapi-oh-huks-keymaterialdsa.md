# OH_Huks_KeyMaterialDsa

```c
typedef struct OH_Huks_KeyMaterialDsa {...} OH_Huks_KeyMaterialDsa
```

## 概述

定义DSA密钥的结构体类型。

<!--Device-struct OH_Huks_KeyMaterialDsa {...}--><!--Device-struct OH_Huks_KeyMaterialDsa {...}-End-->

**系统能力：** SystemCapability.Security.Huks.Core

**起始版本：** 9

**相关模块：** [HuksTypeApi](capi-universal-keystore-kit-hukstypeapi.md)

**所在头文件：** [native_huks_type.h](capi-native-huks-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| enum [OH_Huks_KeyAlg](capi-native-huks-type-h.md#oh_huks_keyalg) keyAlg | 密钥的算法类型。<br><!--Device-enum OH_Huks_KeyAlg keyAlg--><!--Device-enum OH_Huks_KeyAlg keyAlg-End--> |
| uint32_t keySize | 密钥的长度，单位：Bit。<br><!--Device-uint32_t keySize--><!--Device-uint32_t keySize-End--> |
| uint32_t xSize | x值的长度，单位：Byte。<br><!--Device-uint32_t xSize--><!--Device-uint32_t xSize-End--> |
| uint32_t ySize | y值的长度，单位：Byte。<br><!--Device-uint32_t ySize--><!--Device-uint32_t ySize-End--> |
| uint32_t pSize | p值的长度，单位：Byte。<br><!--Device-uint32_t pSize--><!--Device-uint32_t pSize-End--> |
| uint32_t qSize | q值的长度，单位：Byte。<br><!--Device-uint32_t qSize--><!--Device-uint32_t qSize-End--> |
| uint32_t gSize | g值的长度，单位：Byte。<br><!--Device-uint32_t gSize--><!--Device-uint32_t gSize-End--> |


