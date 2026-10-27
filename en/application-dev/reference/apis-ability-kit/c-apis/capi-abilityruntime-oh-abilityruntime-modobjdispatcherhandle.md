# OH_AbilityRuntime_ModObjDispatcherHandle

```c
typedef struct OH_AbilityRuntime_ModObjDispatcherHandle OH_AbilityRuntime_ModObjDispatcherHandle
```

## Overview

Handle to a ModularObject dispatcher. This handle points to a ModularObject dispatcher instance. It can be created by [OH_AbilityRuntime_ModObjDispatcher_CreateMainServiceInstance](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_createmainserviceinstance) or [OH_AbilityRuntime_ModObjDispatcher_CreateSubInstance](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_createsubinstance), and must be released by [OH_AbilityRuntime_ModObjDispatcher_Release](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_release) after use.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

**Header file**: [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

