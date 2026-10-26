# extension_ability.h

## Overview

Provides the type declaration of the ExtensionAbility callback function and the name declaration of the entry function.

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 24

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [AbilityRuntime_ExtensionInstance](capi-abilityruntime-abilityruntime-extensioninstance.md) | - | Define the AbilityRuntime_ExtensionInstance structure type. |
| [AbilityRuntime_ExtensionInstanceHandle](capi-abilityruntime-abilityruntime-extensioninstancehandle.md) | AbilityRuntime_ExtensionInstanceHandle | Defines the pointer to AbilityRuntime_ExtensionInstance. |

### Function

| Name | Description |
| -- | -- |
| [typedef void AbilityRuntime_Extension_CreateFunc(AbilityRuntime_ExtensionInstanceHandle handle, const char *abilityName)](#abilityruntime_extension_createfunc) | Defines the callback function type for ExtensionAbility creation. Callback function that must be implemented in the ExtensionAbility, which is used to instantiate the ExtensionAbility. |

### Variable

| Name | Description |
| -- | -- |
| [AbilityRuntime_Extension_CreateFunc](capi-extension-ability-h.md#abilityruntime_extension_createfunc) OH_AbilityRuntime_OnNativeExtensionCreate | The name of the function that native extension ability instance looks for when launching its native code.<br>**Since**: 24<br>**System capability**: SystemCapability.Ability.AbilityRuntime.Core |
| void AbilityRuntime_Extension_CreateFunc( AbilityRuntime_ExtensionInstanceHandle handle, const char *abilityName) | Defines the callback function type for ExtensionAbility creation. Callback function that must be implemented in the ExtensionAbility, which is used to instantiate the ExtensionAbility.<br>**Since**: 24<br>**System capability**: SystemCapability.Ability.AbilityRuntime.Core |

## Function description

### AbilityRuntime_Extension_CreateFunc()

```c
typedef void AbilityRuntime_Extension_CreateFunc(AbilityRuntime_ExtensionInstanceHandle handle, const char *abilityName)
```

**Description**

Defines the callback function type for ExtensionAbility creation. Callback function that must be implemented in the ExtensionAbility, which is used to instantiate the ExtensionAbility.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 24


