# HiDebug_NativeStackFrame

```c
typedef struct HiDebug_NativeStackFrame {...} HiDebug_NativeStackFrame
```

## 概述

Defines the native stack frame content.

**起始版本：** 20

**相关模块：** [HiDebug](capi-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t relativePc | Relative PC address, which is the offset of the current PC relative to the start address of its mapping area (such as an executable file or shared library). |
| uint64_t funcOffset | Offset of the function corresponding to the current stack frame in its mapping area (such as an executable fileor shared library). |
| const char* mapName | Name of the mapping area to which the current stack frame belongs. |
| const char* functionName | Name of the function corresponding to the current stack frame. |
| const char* buildId | Build ID that uniquely identifies the current mapping area (such as an executable file or shared library).During debugging and symbol parsing, **buildId** ensures that the symbol file version matches the actual binaryfile version. |
| const char* reserved | Reserved field for future extension. |


