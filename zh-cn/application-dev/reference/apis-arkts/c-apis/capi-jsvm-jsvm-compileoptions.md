# JSVM_CompileOptions

```c
typedef struct JSVM_CompileOptions {...} JSVM_CompileOptions
```

## 概述

对应JSVM的编译选项，包含内容和ID。

<!--Device-typedef struct JSVM_CompileOptions {...} JSVM_CompileOptions--><!--Device-typedef struct JSVM_CompileOptions {...} JSVM_CompileOptions-End-->

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 12

**相关模块：** [JSVM](capi-arkts-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [JSVM_CompileOptionId](capi-jsvm-types-h.md#jsvm_compileoptionid) id | JSVM编译选项ID。<br><!--Device-JSVM_CompileOptionId id--><!--Device-JSVM_CompileOptionId id-End--> |
| content.ptr | 指向编译选项值的指针。<br><!--Device-content.ptr--><!--Device-content.ptr-End--> |
| content.num | 存储整数类型的编译选项值。<br><!--Device-content.num--><!--Device-content.num-End--> |
| content.boolean | 存储布尔类型的编译选项值。<br><!--Device-content.boolean--><!--Device-content.boolean-End--> |


