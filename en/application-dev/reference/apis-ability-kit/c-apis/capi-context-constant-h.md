# context_constant.h

## Overview

The file declares the context constants of the AbilityRuntime module.

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Related module**: [AbilityRuntime](capi-ability-kit-abilityruntime.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [AbilityRuntime_AreaMode](#abilityruntime_areamode) | AbilityRuntime_AreaMode | Enumerates the data encryption levels. |
| [AbilityRuntime_StartVisibility](#abilityruntime_startvisibility) | AbilityRuntime_StartVisibility | Enumerates the visibility modes of the window and dock bar icons when the ability is started. |
| [AbilityRuntime_WindowMode](#abilityruntime_windowmode) | AbilityRuntime_WindowMode | Enumerates the window modes. |
| [AbilityRuntime_SupportedWindowMode](#abilityruntime_supportedwindowmode) | AbilityRuntime_SupportedWindowMode | Supported window modes |

## Enum type description

### AbilityRuntime_AreaMode

```c
enum AbilityRuntime_AreaMode
```

**Description**

Enumerates the data encryption levels.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

| Enum item | Description |
| -- | -- |
| ABILITY_RUNTIME_AREA_MODE_EL1 = 0 | Device-level encryption. Directories with this encryption level are accessible after the device is powered on.< br>For private files, such as alarms and wallpapers, the application can place them in a directory with the device-level encryption (EL1) to ensure that they can be accessed before the user enters the password.<br>**Since**: 13 |
| ABILITY_RUNTIME_AREA_MODE_EL2 = 1 | User-level encryption. Directories with this encryption level are accessible only after the device is powered on and the password is entered (for the first time).<br>For private files, such as alarms and wallpapers, the application can place them in a directory with the device-level encryption (EL1) to ensure that they can be accessed before the user enters the password.<br>**Since**: 13 |
| ABILITY_RUNTIME_AREA_MODE_EL3 = 2 | User-level encryption. The file permissions vary according to their scenarios.<br>- Open files: You can read and write to files that are already open, whether the screen is locked or unlocked.<br>- Closed files: When the screen is locked, you cannot open, read, or write to closed files. Once the screen is unlocked, you can open, read, and write to closed files.<br>- New files: When the screen is locked, you can create, open, and write to new files, but reading them is not permitted. Once the screen is unlocked, you can create, open, read, and write to new files.<br>For step recording, file download, or music playback that needs to read, write, and create files when the screen is locked, the application can place these files in EL3.<br>**Since**: 13 |
| ABILITY_RUNTIME_AREA_MODE_EL4 = 3 | User-level encryption. The file permissions vary according to their scenarios.<br>- Open files: When the screen is locked, you can read and write to open files in FEB2.0, but not in FEB3.0. When the screen is unlocked, you can read and write to open files.<br>- Closed files: When the screen is locked, you cannot open, read, or write to closed files. Once the screen is unlocked, you can open, read, and write to closed files.<br>- New files: When the screen is locked, you cannot create files. Once the screen is unlocked, you can create, open, read, and write to new files.<br>For files that are related to user security information and do not need to be read, written, or created when the screen is locked, the application can place them in EL4.<br>**Since**: 13 |
| ABILITY_RUNTIME_AREA_MODE_EL5 = 4 | Application-level encryption. The file permissions vary according to their scenarios.<br>- Open files: You can read and write to files that are already open, whether the screen is locked or unlocked.<br> Closed files: When the screen is locked, you can open, read, and write to closed files only if a DataAccessLock (JS API) is obtained. When the screen is unlocked, you can always open, read, and write to closed files.<br>- New files: You can create, open, read, and write to new files, whether the screen is locked or unlocked.<br>By default, sensitive user privacy files cannot be read or written on the lock screen. If such files need to be read or written on the lock screen, you can call Access to apply for reading or writing files before the screen is locked or create new files that can be read and written after the screen is locked. It is more appropriate to place these files in EL5.<br>**Since**: 13 |

### AbilityRuntime_StartVisibility

```c
enum AbilityRuntime_StartVisibility
```

**Description**

Enumerates the visibility modes of the window and dock bar icons when the ability is started.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 17

| Enum item | Description |
| -- | -- |
| ABILITY_RUNTIME_HIDE_UPON_START = 0 | Hides the window and dock bar icons. This mode takes effect only on 2-in-1 devices.<br>**Since**: 17 |
| ABILITY_RUNTIME_SHOW_UPON_START = 1 | Displays the window and dock bar icons. This mode takes effect only on 2-in-1 devices.<br>**Since**: 17 |

### AbilityRuntime_WindowMode

```c
enum AbilityRuntime_WindowMode
```

**Description**

Enumerates the window modes.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 17

| Enum item | Description |
| -- | -- |
| ABILITY_RUNTIME_WINDOW_MODE_UNDEFINED = 0 | Window mode not defined.<br>**Since**: 17 |
| ABILITY_RUNTIME_WINDOW_MODE_FULL_SCREEN = 1 | Full-screen mode. This mode takes effect only on 2-in-1 devices.<br>**Since**: 17 |

### AbilityRuntime_SupportedWindowMode

```c
enum AbilityRuntime_SupportedWindowMode
```

**Description**

Supported window modes

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 17

| Enum item | Description |
| -- | -- |
| ABILITY_RUNTIME_SUPPORTED_WINDOW_MODE_FULL_SCREEN = 0 | A window in full-screen mode is supported.<br>**Since**: 17 |
| ABILITY_RUNTIME_SUPPORTED_WINDOW_MODE_SPLIT = 1 | A window in split-screen mode is supported. Generally, **ABILITY_RUNTIME_SUPPORTED_WINDOW_MODE_FULL_SCREEN** or * *ABILITY_RUNTIME_SUPPORTED_WINDOW_MODE_FLOATING** must be used together. You are not advised to configure only ** ABILITY_RUNTIME_SUPPORTED_WINDOW_MODE_SPLIT**. If only **ABILITY_RUNTIME_SUPPORTED_WINDOW_MODE_SPLIT** is configured, the window on 2-in-1 devices is in floating window mode by default and can transition to the split- screen mode.<br>**Since**: 17 |
| ABILITY_RUNTIME_SUPPORTED_WINDOW_MODE_FLOATING = 2 | A floating window is supported.<br>**Since**: 17 |


