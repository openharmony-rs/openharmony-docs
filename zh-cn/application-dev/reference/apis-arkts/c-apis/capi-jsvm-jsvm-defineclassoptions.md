# JSVM_DefineClassOptions

```c
typedef struct JSVM_DefineClassOptions {...} JSVM_DefineClassOptions
```

## 概述

定义Class的选项。

<!--Device-typedef struct JSVM_DefineClassOptions {...} JSVM_DefineClassOptions--><!--Device-typedef struct JSVM_DefineClassOptions {...} JSVM_DefineClassOptions-End-->

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 18

**相关模块：** [JSVM](capi-arkts-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [JSVM_DefineClassOptionsId](capi-jsvm-types-h.md#jsvm_defineclassoptionsid) id | 定义Class的选项ID。<br><!--Device-JSVM_DefineClassOptionsId id--><!--Device-JSVM_DefineClassOptionsId id-End--> |
| content.ptr | 指向定义Class选项值的指针。<br><!--Device-content.ptr--><!--Device-content.ptr-End--> |
| content.num | 存储整数类型的定义Class选项值。<br><!--Device-content.num--><!--Device-content.num-End--> |
| content.boolean | 存储布尔类型的定义Class选项值。<br><!--Device-content.boolean--><!--Device-content.boolean-End--> |


