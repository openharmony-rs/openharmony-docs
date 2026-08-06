# HiDebug_JsStackFrame

```c
typedef struct HiDebug_JsStackFrame {...} HiDebug_JsStackFrame
```

## 概述

Defines a struct for the JS stack frame content.

**起始版本：** 20

**相关模块：** [HiDebug](capi-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t relativePc | Relative PC address, which is the offset of the current PC relative to the start address of its mapping area (such as an executable file or shared library). |
| int32_t line | Line number of the code corresponding to the current stack frame in the file. |
| int32_t column | Column number of the code corresponding to the current stack frame in the specified line. |
| const char* mapName | Name of the mapping area to which the current stack frame belongs. |
| const char* functionName | Name of the function corresponding to the current stack frame. |
| const char* url | URL of the code file corresponding to the current stack frame. It can be used to find the corresponding codefile in the local path or on the remote server. |
| const char* packageName | Name of the package to which the code corresponding to the current stack frame belongs. |


