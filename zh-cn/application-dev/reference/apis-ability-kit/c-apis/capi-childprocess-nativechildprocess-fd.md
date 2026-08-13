# NativeChildProcess_Fd

```c
typedef struct NativeChildProcess_Fd {...} NativeChildProcess_Fd
```

## 概述

The struct describes the information about the file descriptor passed to the child process.

**起始版本：** 13

**相关模块：** [ChildProcess](capi-childprocess.md)

**所在头文件：** [native_child_process.h](capi-native-child-process-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char* fdName |  |
| int32_t fd |  |
| struct [NativeChildProcess_Fd*](capi-childprocess-nativechildprocess-fd.md) next |  |


