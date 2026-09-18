# JSVM_EnvScope__*

```c
typedef struct JSVM_EnvScope__* JSVM_EnvScope
```

## 概述

表示用于控制附加到当前虚拟机实例的环境。只有当线程通过 OH_JSVM_OpenEnvScope进入该环境的JSVM_EnvScope后，该环境才 对线程的虚拟机实例可用。

**起始版本：** 11

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

