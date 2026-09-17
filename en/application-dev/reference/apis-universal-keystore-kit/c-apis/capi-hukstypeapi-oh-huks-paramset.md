# OH_Huks_ParamSet

```c
typedef struct OH_Huks_ParamSet {...} OH_Huks_ParamSet
```

## Overview

Defines the struct of a parameter set.

**Since**: 9

**Related module**: [HuksTypeApi](capi-hukstypeapi.md)

**Header file**: [native_huks_type.h](capi-native-huks-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t paramSetSize | Memory size of the parameter set. |
| uint32_t paramsCnt | Number of parameters in the parameter set. |
| struct [OH_Huks_Param](capi-hukstypeapi-oh-huks-param.md) params[] | Parameter array. |


