# JSVM_CompileOptions
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} JSVM_CompileOptions
```

## 概述

配合[OH_JSVM_CompileScriptWithOptions](capi-jsvm-h.md#oh_jsvm_compilescriptwithoptions)接口使用，是其参数中options数组的元素类型。

**起始版本：** 12

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

## 汇总

### 成员变量

| 名称                                                                            | 描述            |
|-------------------------------------------------------------------------------|---------------|
| [JSVM_CompileOptionId](capi-jsvm-types-h.md#jsvm_compileoptionid) id | 编译选项对应的ID。 |
| content     | id对应的编译选项值联合体。 |
| content.ptr   | 指向编译选项值的指针。 |
| content.num      | 存储整数类型的编译选项值。 |
| content.boolean   | 存储布尔类型的编译选项值。|
