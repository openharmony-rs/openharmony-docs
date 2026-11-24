# HiDebug_JsStackFrame

```c
typedef struct HiDebug_JsStackFrame {...} HiDebug_JsStackFrame
```

## 概述

js栈帧内容的定义。用于在性能分析和调试场景中，记录js调用栈的帧信息，包括代码位置、函数名称、映射区域等关键信息。

<!--Device-struct HiDebug_JsStackFrame {...}--><!--Device-struct HiDebug_JsStackFrame {...}-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**起始版本：** 20

**相关模块：** [HiDebug](capi-performance-analysis-kit-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t relativePc | 相对pc地址。当前pc相对于其所在的映射区域（如可执行文件或共享库）起始地址的偏移量。<br><!--Device-uint64_t relativePc--><!--Device-uint64_t relativePc-End--> |
| int32_t line | 代码所在的行号。当前栈帧对应的代码位于文件的具体行位置。<br><!--Device-int32_t line--><!--Device-int32_t line-End--> |
| int32_t column | 代码所在的列号。当前栈帧对应的代码在指定行的具体列位置。<br><!--Device-int32_t column--><!--Device-int32_t column-End--> |
| const char* mapName | 映射名称。当前栈帧所属的映射区域的名称。<br><!--Device-const char* mapName--><!--Device-const char* mapName-End--> |
| const char* functionName | 函数名称。当前栈帧对应的函数的名称。<br><!--Device-const char* functionName--><!--Device-const char* functionName-End--> |
| const char* url | URL地址。当前栈帧对应代码的文件的URL，无论是本地文件路径还是远程服务器上的文件地址，通过该URL能找到对应的代码文件。<br><!--Device-const char* url--><!--Device-const char* url-End--> |
| const char* packageName | 包名。当前栈帧对应的代码所属包的名称。<br><!--Device-const char* packageName--><!--Device-const char* packageName-End--> |


