# OH_AbilityRuntime_ModObjDispatcher_InputParams

```c
typedef struct OH_AbilityRuntime_ModObjDispatcher_InputParams {...} OH_AbilityRuntime_ModObjDispatcher_InputParams
```

## Overview

Defines the parameter structure for method invocation. rgvarg points to the array of parameter variants, and the array length is specified by cArgs. The parameter order must be consistent with the parameter order in the method definition.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

**Header file**: [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_Variant*](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md) rgvarg | Array of argument variants.<br>**Since**: 26.0.0 |
| uint32_t cArgs | Number of arguments.<br>**Since**: 26.0.0 |


