# OH_Huks_Result

```c
typedef struct OH_Huks_Result {...} OH_Huks_Result
```

## 概述

表示状态返回数据，包括返回码和消息。

<!--Device-struct OH_Huks_Result {...}--><!--Device-struct OH_Huks_Result {...}-End-->

**系统能力：** SystemCapability.Security.Huks.Core

**起始版本：** 9

**相关模块：** [HuksTypeApi](capi-universal-keystore-kit-hukstypeapi.md)

**所在头文件：** [native_huks_type.h](capi-native-huks-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t errorCode | 状态返回码，参考[OH_Huks_ErrCode](capi-native-huks-type-h.md#oh_huks_errcode)。<br><!--Device-int32_t errorCode--><!--Device-int32_t errorCode-End--> |
| const char *errorMsg | 对状态返回码的说明信息。<br><!--Device-const char *errorMsg--><!--Device-const char *errorMsg-End--> |
| uint8_t *data | 其他返回数据。<br><!--Device-uint8_t *data--><!--Device-uint8_t *data-End--> |


