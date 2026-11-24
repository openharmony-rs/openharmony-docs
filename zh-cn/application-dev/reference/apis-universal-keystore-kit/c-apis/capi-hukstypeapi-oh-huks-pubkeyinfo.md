# OH_Huks_PubKeyInfo

```c
typedef struct OH_Huks_PubKeyInfo {...} OH_Huks_PubKeyInfo
```

## 概述

定义公钥信息的结构体类型。

<!--Device-struct OH_Huks_PubKeyInfo {...}--><!--Device-struct OH_Huks_PubKeyInfo {...}-End-->

**系统能力：** SystemCapability.Security.Huks.Core

**起始版本：** 9

**相关模块：** [HuksTypeApi](capi-universal-keystore-kit-hukstypeapi.md)

**所在头文件：** [native_huks_type.h](capi-native-huks-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| enum [OH_Huks_KeyAlg](capi-native-huks-type-h.md#oh_huks_keyalg) keyAlg | 公钥的算法类型。<br><!--Device-enum OH_Huks_KeyAlg keyAlg--><!--Device-enum OH_Huks_KeyAlg keyAlg-End--> |
| uint32_t keySize | 公钥的长度，单位：Bit。<br><!--Device-uint32_t keySize--><!--Device-uint32_t keySize-End--> |
| uint32_t nOrXSize | n或X值的长度，单位：Byte。<br><!--Device-uint32_t nOrXSize--><!--Device-uint32_t nOrXSize-End--> |
| uint32_t eOrYSize | e或Y值的长度，单位：Byte。<br><!--Device-uint32_t eOrYSize--><!--Device-uint32_t eOrYSize-End--> |
| uint32_t placeHolder | 占位符的大小，用于对齐内存或为未来的算法扩展提供预留空间，单位：Byte。<br><!--Device-uint32_t placeHolder--><!--Device-uint32_t placeHolder-End--> |


