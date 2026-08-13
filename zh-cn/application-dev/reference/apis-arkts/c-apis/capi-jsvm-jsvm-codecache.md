# JSVM_CodeCache

```c
typedef struct JSVM_CodeCache {...} JSVM_CodeCache
```

## 概述

对应JSVM代码缓存的地址与大小。

**起始版本：** 12

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t *cache | 缓存地址。 |
| size_t length | 缓存大小。 |


