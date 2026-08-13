# JSVM_TypeTag

```c
typedef struct JSVM_TypeTag {...} JSVM_TypeTag
```

## 概述

类型标记，存储为两个无符号64位整数的128位值。作为一个UUID，通过它，JavaScript对象可以是"tagged"，以确保它们的类型保持不变。

**起始版本：** 11

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

