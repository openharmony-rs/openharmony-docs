# JSVM_CallbackStruct*
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef JSVM_CallbackStruct* JSVM_Callback
```

## 概述

用户提供的native函数的函数指针类型，这些函数通过JSVM-API接口暴露给JavaScript。

**起始版本：** 11

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)