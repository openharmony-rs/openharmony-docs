# OH_Huks_Result

```c
typedef struct OH_Huks_Result {...} OH_Huks_Result
```

## 概述

表示状态返回数据，包括返回码和消息。

**系统能力：** SystemCapability.Security.Huks.Core

**起始版本：** 9

**相关模块：** [HuksTypeApi](capi-hukstypeapi.md)

**所在头文件：** [native_huks_type.h](capi-native-huks-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t errorCode | 状态返回码，参考{@link OH_Huks_ErrCode}。 |
| const char *errorMsg | 对状态返回码的说明信息。 |
| uint8_t *data | 其他返回数据。 |


