# JSVM_ExtendedErrorInfo

## 概述

扩展的异常信息。

**起始版本：** 11

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char* errorMessage | UTF8编码的字符串，包含异常信息描述。 |
| void* engineReserved | 特定于VM的详细异常信息。目前尚未为任何VM实现此功能。 |
| uint32_t engineErrorCode | 特定于VM的异常代码。目前尚未为任何VM实现此功能。 |
| JSVM_Status errorCode | 源自最后一个异常的JSVM-API状态代码。 |


