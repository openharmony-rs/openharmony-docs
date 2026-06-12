# JSVM_DefineClassOptions
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} JSVM_DefineClassOptions
```

## 概述

定义Class的选项。

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 18

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

## 汇总

### 成员变量

| 名称                                                                            | 描述            |
|-------------------------------------------------------------------------------|---------------|
| [JSVM_DefineClassOptionsId](capi-jsvm-types-h.md#jsvm_defineclassoptionsid) id | 定义Class的选项ID。 |
| content     | id对应的定义Class选项值联合体。 |
| content.ptr   | 指向定义Class选项值的指针。 |
| content.num      | 存储整数类型的定义Class选项值。 |
| content.boolean   | 存储布尔类型的定义Class选项值。|


