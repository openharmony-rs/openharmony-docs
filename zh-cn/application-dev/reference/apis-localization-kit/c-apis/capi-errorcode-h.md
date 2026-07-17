# errorcode.h

## 概述

i18n错误码。

**库：** libohi18n.so

**系统能力：** SystemCapability.Global.I18n

**起始版本：** 22

**相关模块：** [i18n](capi-i18n.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [I18n_ErrorCode](#i18n_errorcode) | I18n_ErrorCode | i18n错误码 |

## 枚举类型说明

### I18n_ErrorCode

```c
enum I18n_ErrorCode
```

**描述**

i18n错误码

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| SUCCESS = 0 | @error 成功 |
| ERROR_INVALID_PARAMETER = 8900001 | @error 当接口传入非法的参数值时，系统会产生此错误码。 |
| UNEXPECTED_ERROR = 8900050 | @error 预期之外的错误，例如内存错误 |


