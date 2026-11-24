# errorcode.h

## 概述

提供国际化接口返回的错误码。

**库：** libohi18n.so

**系统能力：** SystemCapability.Global.I18n

**起始版本：** 22

**相关模块：** [i18n](capi-localization-kit-i18n.md)

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

**描述：**

i18n错误码

<!--Device-enum I18n_ErrorCode--><!--Device-enum I18n_ErrorCode-End-->

**系统能力：** SystemCapability.Global.I18n

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| SUCCESS = 0 | &nbsp;成功<br><!--Device-SUCCESS = 0--><!--Device-SUCCESS = 0-End--> |
| ERROR_INVALID_PARAMETER = 8900001 | &nbsp;当接口传入非法的参数值时，系统会产生此错误码。<br><!--Device-ERROR_INVALID_PARAMETER = 8900001--><!--Device-ERROR_INVALID_PARAMETER = 8900001-End--> |
| UNEXPECTED_ERROR = 8900050 | &nbsp;预期之外的错误，例如内存错误<br><!--Device-UNEXPECTED_ERROR = 8900050--><!--Device-UNEXPECTED_ERROR = 8900050-End--> |


