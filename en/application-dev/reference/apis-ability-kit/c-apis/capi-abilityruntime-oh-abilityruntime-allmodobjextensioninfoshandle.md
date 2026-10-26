# OH_AbilityRuntime_AllModObjExtensionInfosHandle

```c
typedef struct OH_AbilityRuntime_AllModObjExtensionInfosHandle OH_AbilityRuntime_AllModObjExtensionInfosHandle
```

## Overview

Represents a handle to the collection of all ModularObjectExtensionAbility information in the current app. You can obtain this handle through [OH_AbilityRuntime_AcquireSelfModularObjectExtensionInfos](capi-modular-object-extension-manager-h.md#oh_abilityruntime_acquireselfmodularobjectextensioninfos). This handle points to a collection containing multiple [OH_AbilityRuntime_ModObjExtensionInfoHandle](capi-abilityruntime-oh-abilityruntime-modobjextensioninfohandle.md) objects. You can obtain the number of elements in the collection through [OH_AbilityRuntime_GetCountFromAllModObjExtensionInfos](capi-modular-object-extension-manager-h.md#oh_abilityruntime_getcountfromallmodobjextensioninfos), and obtain the information of a single ModularObjectExtensionAbility by index through [OH_AbilityRuntime_GetModObjExtensionInfoByIndex](capi-modular-object-extension-manager-h.md#oh_abilityruntime_getmodobjextensioninfobyindex). After use, release the collection through [OH_AbilityRuntime_ReleaseAllExtensionInfos](capi-modular-object-extension-manager-h.md#oh_abilityruntime_releaseallextensioninfos).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

**Header file**: [modular_object_extension_manager.h](capi-modular-object-extension-manager-h.md)

