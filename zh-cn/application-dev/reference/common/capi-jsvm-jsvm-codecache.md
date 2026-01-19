# JSVM_CodeCache
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} JSVM_CodeCache
```

## 概述

表示当id为JSVM_COMPILE_CODE_CACHE时，content的类型。

**起始版本：** 12

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

## 汇总

### 成员变量

| 名称              | 描述          |
|------------------|---------------|
| uint8_t* cache   | 缓存地址。     |
| size_t length    | 缓存大小。     |