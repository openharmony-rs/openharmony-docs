# OH_AbilityRuntime_ModularObjectDispatcher_TypeDescriptor*

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b64fba1a3bfa56ac6a22a458a141c3f45d9c160b translatedAt=2026-09-03T08:35:13.098Z pushedAt=2026-09-05T10:47:30.076Z -->

```c
typedef struct OH_AbilityRuntime_ModularObjectDispatcher_TypeDescriptor* OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle
```

## Overview

Defines the type descriptor handle of the ModularObject dispatcher.

The handle points to the access interface of the type library metadata, and can be used to query information such as interfaces, methods, enums, and structs defined by remote services.

It can be obtained through [OH_AbilityRuntime_ModObjDispatcher_GetTypeDescriptor](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_gettypedescriptor). After use, it must be released through [OH_AbilityRuntime_TypeDescriptor_Release](capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_release).

**Since:** 26.0.0

**Related module:** [AbilityRuntime](capi-abilityruntime.md)

**File to include:** [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

