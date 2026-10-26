# OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle

```c
struct OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle
```

## Overview

Defines the type descriptor handle of the ModularObject dispatcher. The handle points to the access interface of the type library metadata, and can be used to query information such as interfaces, methods, enums, and structs defined by remote services. It can be obtained through [OH_AbilityRuntime_ModObjDispatcher_GetTypeDescriptor](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_gettypedescriptor). After use, it must be released through [OH_AbilityRuntime_TypeDescriptor_Release](capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_release).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0 /
typedef struct OH_AbilityRuntime_ModularObjectDispatcher_TypeDescriptor

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

**Header file**: [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

