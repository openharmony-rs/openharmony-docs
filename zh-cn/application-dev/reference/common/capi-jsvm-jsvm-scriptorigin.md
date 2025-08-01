# JSVM_ScriptOrigin

## 概述

某段JavaScript代码的原始信息，如sourceMap路径、源文件名、源文件中的起始行/列号等。

**起始版本：** 12

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char* sourceMapUrl | Sourcemap 路径。 |
| const char* resourceName | 源文件名。 |
| size_t resourceLineOffset | 这段代码在源文件中的起始行号。 |
| size_t resourceColumnOffset | 这段代码在源文件中的起始列号。 |


