# JSVM_DeserializeResult
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct JSVM_DeserializeResult__* JSVM_DeserializeResult
```

## 概述

与JSVM_COMPILE_BACKGROUND_DESERIALIZE_RESULT一起传递的后台反序列化结果。

**使用场景：** 用于在JSVM后台编译场景中，传递和存储后台反序列化的结果数据。

**特点：** 轻量级的类型定义，与JSVM_COMPILE_BACKGROUND_DESERIALIZE_RESULT配合使用。

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 24

**支持设备类型：** Phone | PC/2in1 | Tablet | Wearable。具体支持情况可通过对应的API接口进行判断。

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)
