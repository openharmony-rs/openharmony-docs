# JSVM_CallbackInfo__*
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct JSVM_CallbackInfo__* JSVM_CallbackInfo
```

## 概述

表示传递给回调函数的不透明数据类型。可用于获取调用该函数的上下文的附加信息。

**使用场景：** 在Native API开发中，当需要实现JavaScript回调函数时使用该类型。例如，在JSVM模块中注册回调函数后，通过该类型获取回调调用的参数信息和执行上下文。

**解决的问题：** 提供了Native层访问JavaScript回调函数调用上下文的能力，解决了Native代码无法获取回调函数参数和执行环境的问题。

**带来的收益：** 简化了Native层与JavaScript层的交互流程，使开发者能够在Native回调函数中灵活地访问和处理JavaScript传入的参数，提升了Native与JavaScript互操作的灵活性和开发效率。

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 11

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

