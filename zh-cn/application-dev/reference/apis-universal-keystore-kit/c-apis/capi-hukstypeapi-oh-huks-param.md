# OH_Huks_Param

```c
typedef struct OH_Huks_Param {...} OH_Huks_Param
```

## 概述

定义参数集中的参数结构体类型。

**起始版本：** 9

**相关模块：** [HuksTypeApi](capi-hukstypeapi.md)

**所在头文件：** [native_huks_type.h](capi-native-huks-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t tag; union | 标签值。 |
| bool boolParam | bool型参数。 |
| int32_t int32Param | int32_t型参数。 |
| uint32_t uint32Param | uint32_t型参数。 |
| uint64_t uint64Param | uint64_t型参数。 |
| struct [OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) blob; } | OH_Huks_Blob型参数。 |


