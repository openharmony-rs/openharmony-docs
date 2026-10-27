# OH_AbilityRuntime_ModObjDispatcher_MapHandle

```c
typedef struct OH_AbilityRuntime_ModObjDispatcher_MapHandle OH_AbilityRuntime_ModObjDispatcher_MapHandle
```

## Overview

Map handle. The handle points to an ordered collection of key-value pairs. The key and value types are specified at creation. It supports adding or updating key-value pairs, obtaining values by key, deleting key-value pairs, querying whether a specified key exists, obtaining keys or values by index, querying the map size, and clearing operations. Keys support only basic types (BOOL, signed integer, unsigned integer, floating-point number, STRING, ENUM). It can be created through [OH_AbilityRuntime_ModObjDispatcher_MapCreate](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_mapcreate), and must be released through [OH_AbilityRuntime_ModObjDispatcher_MapRelease](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_maprelease) after use.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

**Header file**: [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

