# JSVM_CompileProfile
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef const struct {...} JSVM_CompileProfile
```

## 概述

与JSVM_COMPILE_COMPILE_PROFILE一起传递的编译采样文件。

**使用场景：** 用于应用二次启动时的预编译优化，可提升应用启动速度和运行性能。适用于需要优化启动性能的应用场景。

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 12

**支持设备类型：** Phone | PC/2in1 | Tablet | Wearable。具体支持情况可通过对应的API接口进行判断。

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int *profile | 编译采样文件的指针。 |
| size_t length | 编译采样文件的大小。 |

