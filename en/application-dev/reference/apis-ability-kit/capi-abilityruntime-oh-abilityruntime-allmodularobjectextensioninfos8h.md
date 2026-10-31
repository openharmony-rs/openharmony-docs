# OH_AbilityRuntime_AllModularObjectExtensionInfos*

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b64fba1a3bfa56ac6a22a458a141c3f45d9c160b translatedAt=2026-09-03T08:29:44.609Z pushedAt=2026-09-05T10:47:30.059Z -->

```c
typedef struct OH_AbilityRuntime_AllModularObjectExtensionInfos* OH_AbilityRuntime_AllModObjExtensionInfosHandle
```

## Overview

Represents a handle to the collection of all ModularObjectExtensionAbility information in the current app. You can obtain this handle through [OH_AbilityRuntime_AcquireSelfModularObjectExtensionInfos](capi-modular-object-extension-manager-h.md#oh_abilityruntime_acquireselfmodularobjectextensioninfos). This handle points to a collection containing multiple [OH_AbilityRuntime_ModObjExtensionInfoHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninfo8h.md) objects. You can obtain the number of elements in the collection through [OH_AbilityRuntime_GetCountFromAllModObjExtensionInfos](capi-modular-object-extension-manager-h.md#oh_abilityruntime_getcountfromallmodobjextensioninfos), and obtain the information of a single ModularObjectExtensionAbility by index through [OH_AbilityRuntime_GetModObjExtensionInfoByIndex](capi-modular-object-extension-manager-h.md#oh_abilityruntime_getmodobjextensioninfobyindex). After use, release the collection through [OH_AbilityRuntime_ReleaseAllExtensionInfos](capi-modular-object-extension-manager-h.md#oh_abilityruntime_releaseallextensioninfos).

**Since:** 26.0.0

**Related module:** [AbilityRuntime](capi-abilityruntime.md)

**File to include:** [modular_object_extension_manager.h](capi-modular-object-extension-manager-h.md)

