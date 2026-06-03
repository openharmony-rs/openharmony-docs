# JSVM_Deferred__*
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct JSVM_Deferred__* JSVM_Deferred
```

## 概述

表示Promise延迟对象。

**使用场景：** 在JSVM Native模块中需要创建Promise对象并延迟处理异步操作结果时，需要在Native层手动控制Promise的resolve或reject时机的场景，将Native层的异步操作结果封装为Promise返回给JavaScript层。

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 11

**支持设备类型：** Phone | PC/2in1 | Tablet | Wearable。具体支持情况可通过对应的API接口进行判断。

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

