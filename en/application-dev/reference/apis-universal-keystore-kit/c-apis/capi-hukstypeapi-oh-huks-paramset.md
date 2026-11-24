# OH_Huks_ParamSet

```c
typedef struct OH_Huks_ParamSet {...} OH_Huks_ParamSet
```

## Overview

Defines the struct of a parameter set.

<!--Device-struct OH_Huks_ParamSet {...}--><!--Device-struct OH_Huks_ParamSet {...}-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

**Related module**: [HuksTypeApi](capi-universal-keystore-kit-hukstypeapi.md)

**Header file**: [native_huks_type.h](capi-native-huks-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t paramSetSize | Memory size of the parameter set.<br><!--Device-uint32_t paramSetSize--><!--Device-uint32_t paramSetSize-End--> |
| uint32_t paramsCnt | Number of parameters in the parameter set.<br><!--Device-uint32_t paramsCnt--><!--Device-uint32_t paramsCnt-End--> |
| [struct OH_Huks_Param](capi-hukstypeapi-oh-huks-param.md) params[] | Parameter array.<br><!--Device-struct OH_Huks_Param params[]--><!--Device-struct OH_Huks_Param params[]-End--> |


