# context_constant.h

## Overview

The file declares the context constants of the AbilityRuntime module.

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [AbilityRuntime_AreaMode](#abilityruntime_areamode) | AbilityRuntime_AreaMode | Enumerates the data encryption levels. |
| [AbilityRuntime_StartVisibility](#abilityruntime_startvisibility) | AbilityRuntime_StartVisibility | Enumerates the visibility modes of the window and dock bar icons when the ability is started. |
| [AbilityRuntime_WindowMode](#abilityruntime_windowmode) | AbilityRuntime_WindowMode | Enumerates the window modes. |
| [AbilityRuntime_SupportedWindowMode](#abilityruntime_supportedwindowmode) | AbilityRuntime_SupportedWindowMode |  |

## Enum type description

### AbilityRuntime_AreaMode

```c
enum AbilityRuntime_AreaMode
```

**Description**

Enumerates the data encryption levels.

**Since**: 13

| Enum item | Description |
| -- | -- |
| ABILITY_RUNTIME_AREA_MODE_EL1 = 0 |  |
| ABILITY_RUNTIME_AREA_MODE_EL2 = 1 |  |
| ABILITY_RUNTIME_AREA_MODE_EL3 = 2 |  |
| ABILITY_RUNTIME_AREA_MODE_EL4 = 3 |  |
| ABILITY_RUNTIME_AREA_MODE_EL5 = 4 |  |

### AbilityRuntime_StartVisibility

```c
enum AbilityRuntime_StartVisibility
```

**Description**

Enumerates the visibility modes of the window and dock bar icons when the ability is started.

**Since**: 17

| Enum item | Description |
| -- | -- |
| ABILITY_RUNTIME_HIDE_UPON_START = 0 |  |
| ABILITY_RUNTIME_SHOW_UPON_START = 1 |  |

### AbilityRuntime_WindowMode

```c
enum AbilityRuntime_WindowMode
```

**Description**

Enumerates the window modes.

**Since**: 17

| Enum item | Description |
| -- | -- |
| ABILITY_RUNTIME_WINDOW_MODE_UNDEFINED = 0 |  |
| ABILITY_RUNTIME_WINDOW_MODE_FULL_SCREEN = 1 |  |

### AbilityRuntime_SupportedWindowMode

```c
enum AbilityRuntime_SupportedWindowMode
```

**Description**

| Enum item | Description |
| -- | -- |
| ABILITY_RUNTIME_SUPPORTED_WINDOW_MODE_FULL_SCREEN = 0 |  |
| ABILITY_RUNTIME_SUPPORTED_WINDOW_MODE_SPLIT = 1 |  |
| ABILITY_RUNTIME_SUPPORTED_WINDOW_MODE_FLOATING = 2 |  |


