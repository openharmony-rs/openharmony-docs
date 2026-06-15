# extension_ability.h

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yangzhongkai-->
<!--Designer: @yangzhongkai-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

## Overview

Provides the type declaration of the ExtensionAbility callback function and the name declaration of the entry function.

**File to include**: <AbilityKit/ability_runtime/extension_ability.h>

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 24

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Struct

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [AbilityRuntime_ExtensionInstance](capi-abilityruntime-extensioninstance.md) | - | Defines the AbilityRuntime_ExtensionInstance structure type.|
| [AbilityRuntime_ExtensionInstance*](capi-abilityruntime-extensioninstance8h.md) | AbilityRuntime_ExtensionInstanceHandle | Defines the pointer to the AbilityRuntime_ExtensionInstance object.|

### Function

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void AbilityRuntime_Extension_CreateFunc(AbilityRuntime_ExtensionInstanceHandle handle, const char *abilityName);](#abilityruntime_extension_createfunc) | AbilityRuntime_Extension_CreateFunc | Type of the callback function for ExtensionAbility creation. Callback function that must be implemented in the ExtensionAbility, which is used to instantiate the ExtensionAbility.|

### Variables

| Name| Type| Description|
|------| --- |------|
| [OH_AbilityRuntime_OnNativeExtensionCreate](#oh_abilityruntime_onnativeextensioncreate) | [AbilityRuntime_Extension_CreateFunc](#abilityruntime_extension_createfunc) | Name declaration of the ExtensionAbility entry function. You need to implement a function of the [AbilityRuntime_Extension_CreateFunc](#abilityruntime_extension_createfunc) type and name it OH_AbilityRuntime_OnNativeExtensionCreate. The system automatically searches for and calls this function to initialize the ExtensionAbility instance.<br>**Since**: 24|

## Function Description

### AbilityRuntime_Extension_CreateFunc()

```c
typedef void AbilityRuntime_Extension_CreateFunc(AbilityRuntime_ExtensionInstanceHandle handle, const char *abilityName)
```

**Description**

Defines the callback function type for ExtensionAbility creation. Callback function that must be implemented in the ExtensionAbility, which is used to instantiate the ExtensionAbility.

**Since**: 24

**Parameters:**

| Name| Description|
|--------|------|
| [AbilityRuntime_ExtensionInstanceHandle](capi-abilityruntime-extensioninstance8h.md) handle | Pointer to the AbilityRuntime_ExtensionInstanceHandle instance passed by the callback function.|
| const char *abilityName | Name of the ExtensionAbility passed by the callback function.|

## Variable Description

### OH_AbilityRuntime_OnNativeExtensionCreate

```c
AbilityRuntime_Extension_CreateFunc OH_AbilityRuntime_OnNativeExtensionCreate
```

**Description**

Declares the entry function name for ExtensionAbility. You need to implement a function of the [AbilityRuntime_Extension_CreateFunc](#abilityruntime_extension_createfunc) type and name it OH_AbilityRuntime_OnNativeExtensionCreate. The system automatically searches for and calls this function to initialize the ExtensionAbility instance.

**Since**: 24

**Sample code:**

```c
#include <AbilityKit/ability_runtime/extension_ability.h>

extern "C" void OH_AbilityRuntime_OnNativeExtensionCreate(AbilityRuntime_ExtensionInstance *instance,
                                                          const char *abilityName) {
    if (!instance) {
        // Record error logs and other service processing.
        return;
    }
    // Initialize the ExtensionAbility.
}
```
