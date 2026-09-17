# extension_ability.h

## Overview

Declare the common types for the extension ability AbilityRuntime.

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [AbilityRuntime_ExtensionInstance](capi-abilityruntime-abilityruntime-extensioninstance.md) | - | Define the AbilityRuntime_ExtensionInstance structure type. |
| [AbilityRuntime_ExtensionInstance*](capi-abilityruntime-abilityruntime-extensioninstance8h.md) | AbilityRuntime_ExtensionInstanceHandle | Defines the pointer to AbilityRuntime_ExtensionInstance. |

### Function

| Name | Description |
| -- | -- |
| [typedef void AbilityRuntime_Extension_CreateFunc(AbilityRuntime_ExtensionInstanceHandle handle, const char *abilityName)](#abilityruntime_extension_createfunc) | Define the function that must be in the native code to instantiate the native extension ability. |

### Variable

| Name | Description |
| -- | -- |
| [AbilityRuntime_Extension_CreateFunc](capi-extension-ability-h.md#abilityruntime_extension_createfunc) OH_AbilityRuntime_OnNativeExtensionCreate | The name of the function that native extension ability instance looks for when launching its native code.<br>**Since**: 24 |
| void AbilityRuntime_Extension_CreateFunc( AbilityRuntime_ExtensionInstanceHandle handle, const char *abilityName) | Define the function that must be in the native code to instantiate the native extension ability.<br>**Since**: 24 |

## Function description

### AbilityRuntime_Extension_CreateFunc()

```c
typedef void AbilityRuntime_Extension_CreateFunc(AbilityRuntime_ExtensionInstanceHandle handle, const char *abilityName)
```

**Description**

Define the function that must be in the native code to instantiate the native extension ability.

**Since**: 24


