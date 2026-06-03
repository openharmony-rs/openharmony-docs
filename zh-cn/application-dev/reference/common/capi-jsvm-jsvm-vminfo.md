# JSVM_VMInfo
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} JSVM_VMInfo
```

## 概述

JavaScript虚拟机信息。

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 11

**支持设备类型：** Phone | PC/2in1 | Tablet | Wearable。具体支持情况可通过对应的API接口进行判断。

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t apiVersion | 此虚拟机支持的最高API版本。 |
| const char* engine | 实现虚拟机的引擎名称。 |
| const char* version | 虚拟机的版本。 |
| uint32_t cachedDataVersionTag | 缓存数据版本标签。 |


