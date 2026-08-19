# JSVM_CompileOptions

```c
typedef struct JSVM_CompileOptions {...} JSVM_CompileOptions
```

## 概述

对应JSVM的编译选项，包含内容和ID。

**起始版本：** 12

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [JSVM_CompileOptionId](capi-jsvm-types-h.md#jsvm_compileoptionid) id | JSVM编译选项ID。 |
| union | id对应的编译选项值联合体。 |
| void *ptr | 指向编译选项值的指针。 |
| int num | 存储整数类型的编译选项值。 |
| bool boolean; } content | 存储布尔类型的编译选项值。 |


