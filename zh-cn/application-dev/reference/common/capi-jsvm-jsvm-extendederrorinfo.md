# JSVM_ExtendedErrorInfo
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} JSVM_ExtendedErrorInfo
```

## 概述

扩展的异常信息。

**使用场景：** 在JSVM API调用失败时获取详细的异常信息，调试和排查JavaScript运行时错误，日志记录和错误上报。

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 11

**支持设备类型：** Phone | PC/2in1 | Tablet | Wearable。具体支持情况可通过对应的API接口进行判断。

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char* errorMessage | UTF-8编码的字符串，包含异常信息。 |
| void* engineReserved | 特定于VM的详细异常信息。目前尚未为任何VM实现此功能。 |
| uint32_t engineErrorCode | 特定于VM的异常代码。目前尚未为任何VM实现此功能。 |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) errorCode | 源自最后一个异常的JSVM-API状态码。 |


