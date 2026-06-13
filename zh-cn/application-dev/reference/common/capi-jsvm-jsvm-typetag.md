# JSVM_TypeTag
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} JSVM_TypeTag
```

## 概述

类型标记，存储为两个无符号64位整数的128位值。作为一个UUID，通过它，JavaScript对象可以是"tagged"，以确保它们的类型保持不变。

**使用场景：** 在跨语言交互（如C/C++与JavaScript交互）场景中，用于标记和识别JavaScript对象的类型。

**功能特点：** 提供128位唯一标识符，由两个64位整数组成，确保标识的唯一性和准确性。可附加到JavaScript对象上，实现类型标记和验证。

**解决的问题：** 解决JavaScript对象在跨语言交互中的类型识别问题。防止对象类型混淆或被错误识别。

**收益：** 确保JavaScript对象的类型保持一致性，提升跨语言交互的类型安全性。

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 11

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述   |
|----|------|
| uint64_t lower   | 低64位 |
| uint64_t upper   | 高64位 |

