# NativeChildProcess_Fd

```c
typedef struct NativeChildProcess_Fd {...} NativeChildProcess_Fd
```

## 概述

传递给子进程的文件描述符信息。

<!--Device-struct NativeChildProcess_Fd {...}--><!--Device-struct NativeChildProcess_Fd {...}-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 13

**相关模块：** [ChildProcess](capi-ability-kit-childprocess.md)

**所在头文件：** [native_child_process.h](capi-native-child-process-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char* fdName | 文件描述符的键，最大长度为20字符。<br><!--Device-char* fdName--><!--Device-char* fdName-End--> |
| int32_t fd | 文件描述符的值。<br><!--Device-int32_t fd--><!--Device-int32_t fd-End--> |
| [struct NativeChildProcess_Fd*](capi-childprocess-nativechildprocess-fd.md) next | 下一个文件描述记录指针。<br><!--Device-struct NativeChildProcess_Fd* next--><!--Device-struct NativeChildProcess_Fd* next-End--> |


