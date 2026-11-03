# JSVM_CompileProfile

```c
typedef const struct {...} JSVM_CompileProfile
```

## 概述

与JSVM_COMPILE_COMPILE_PROFILE一起传递的编译采样文件

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 12

**相关模块：** [JSVM](capi-others-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int *profile | 编译采样文件的指针。 |
| size_t length | 编译采样文件的大小。 |


