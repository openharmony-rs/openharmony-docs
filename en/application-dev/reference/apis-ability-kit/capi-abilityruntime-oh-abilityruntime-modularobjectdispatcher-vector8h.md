# OH_AbilityRuntime_ModularObjectDispatcher_Vector*

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=43d5e77d1f5350f21a34e2eda9d75b2c11601c5c translatedAt=2026-09-03T08:35:37.285Z pushedAt=2026-09-05T10:47:30.078Z -->

```c
typedef struct OH_AbilityRuntime_ModularObjectDispatcher_Vector* OH_AbilityRuntime_ModObjDispatcher_VectorHandle
```

## Overview

Vector handle.

The handle points to a dynamic-sized ordered collection of elements of the same type, and supports adding elements, obtaining elements by index, querying the vector size, and clearing operations.

It can be created through [OH_AbilityRuntime_ModObjDispatcher_VectorCreate](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_vectorcreate), and must be released through [OH_AbilityRuntime_ModObjDispatcher_VectorRelease](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_vectorrelease) after use.

**Since:** 26.0.0

**Related module:** [AbilityRuntime](capi-abilityruntime.md)

**File to include:** [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

