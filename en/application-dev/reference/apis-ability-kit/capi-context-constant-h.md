# context_constant.h

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b3bc27a342923ac4fafa55153b55c4f3b627330f translatedAt=2026-09-03T08:41:57.398Z pushedAt=2026-09-05T10:47:30.095Z -->

## Overview

The file declares the context constants of the AbilityRuntime module.

**File to include**: <AbilityKit/ability_runtime/context_constant.h>

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [AbilityRuntime_AreaMode](#abilityruntime_areamode) | AbilityRuntime_AreaMode | Enumerates the data encryption levels.|
| [AbilityRuntime_StartVisibility](#abilityruntime_startvisibility) | AbilityRuntime_StartVisibility | Enumerates the display modes of the window and dock bar icon when an ability is started. For example, the hidden mode is used when a service needs to be started silently in the background without displaying the UI; the display mode is used when the UI needs to be displayed normally for interaction with users. |
| [AbilityRuntime_WindowMode](#abilityruntime_windowmode) | AbilityRuntime_WindowMode | Enumerates the window modes.|
| [AbilityRuntime_SupportedWindowMode](#abilityruntime_supportedwindowmode) | AbilityRuntime_SupportedWindowMode | Enumerates the window modes supported by a component. When a UIAbility is started in an application, specifies whether the window displays the maximize, windowed, and split-screen buttons. |

## Enum Description

### AbilityRuntime_AreaMode

```c
enum AbilityRuntime_AreaMode
```

**Description**

Enumerates the data encryption levels.

**Since**: 13

| Value| Description|
| -- | -- |
| ABILITY_RUNTIME_AREA_MODE_EL1 = 0 | Device-level encryption. Directories with this encryption level are accessible after the device is powered on.<br>For private files, such as alarms and wallpapers, the application can place them in a directory with the device-level encryption (EL1) to ensure that they can be accessed before the user enters the password.|
| ABILITY_RUNTIME_AREA_MODE_EL2 = 1 | User-level encryption area, a data area that can be accessed only after the device is powered on and the password is entered for the first time.<br>For personal sensitive data that can be used securely only after unlocking, applications can place these files in the user-level encryption area (EL2) to ensure that they can be accessed only after the user enters the password. |
| ABILITY_RUNTIME_AREA_MODE_EL3 = 2 | User-level encryption. The file permissions vary according to their scenarios.<br>- Open files: You can read and write to files that are already open, whether the screen is locked or unlocked.<br>- Closed files: When the screen is locked, you cannot open, read, or write to closed files. Once the screen is unlocked, you can open, read, and write to closed files.<br>- New files: When the screen is locked, you can create, open, and write to new files, but reading them is not permitted. Once the screen is unlocked, you can create, open, read, and write to new files.<br>For step recording, file download, or music playback that needs to read, write, and create files when the screen is locked, the application can place these files in EL3.|
| ABILITY_RUNTIME_AREA_MODE_EL4 = 3 | User-level encryption. The file permissions vary according to their scenarios.<br>- Open files: When the screen is locked, you can read and write to open files in FEB2.0, but not in FEB3.0. When the screen is unlocked, you can read and write to open files.<br>- Closed files: When the screen is locked, you cannot open, read, or write to closed files. Once the screen is unlocked, you can open, read, and write to closed files.<br>- New files: When the screen is locked, you cannot create files. Once the screen is unlocked, you can create, open, read, and write to new files.<br>For files that are related to user security information and do not need to be read, written, or created when the screen is locked, the application can place them in EL4.|
| ABILITY_RUNTIME_AREA_MODE_EL5 = 4 | Application-level encryption. The file permissions vary according to their scenarios.<br>- Open files: You can read and write to files that are already open, whether the screen is locked or unlocked.<br>* Closed files: When the screen is locked, you can open, read, and write to closed files only if a DataAccessLock (JS API) is obtained. When the screen is unlocked, you can always open, read, and write to closed files.<br>- New files: You can create, open, read, and write to new files, whether the screen is locked or unlocked.<br>By default, sensitive user privacy files cannot be read or written on the lock screen. If such files need to be read or written on the lock screen, you can call [Access](js-apis-screenLockFileManager.md#screenlockfilemanageracquireaccess) to apply for reading or writing files before the screen is locked or create new files that can be read and written after the screen is locked. It is more appropriate to place these files in EL5.|

### AbilityRuntime_StartVisibility

```c
enum AbilityRuntime_StartVisibility
```

**Description**

Display mode of the window and dock bar icons when an ability is started. For example, the hidden mode is used when a service needs to be started silently in the background without displaying the UI; the display mode is used when the UI needs to be displayed normally and interacted with by the user.

**Since**: 17

| Value| Description|
| -- | -- |
| ABILITY_RUNTIME_HIDE_UPON_START = 0 | Hides the window and dock bar icon. This takes effect only on PC/2-in-1 devices. |
| ABILITY_RUNTIME_SHOW_UPON_START = 1 | Shows the window and dock bar icon. This takes effect only on PC/2-in-1 devices. |

### AbilityRuntime_WindowMode

```c
enum AbilityRuntime_WindowMode
```

**Description**

Enumerates the window modes.

**Since**: 17

| Value| Description|
| -- | -- |
| ABILITY_RUNTIME_WINDOW_MODE_UNDEFINED = 0 | Window mode not defined.|
| ABILITY_RUNTIME_WINDOW_MODE_FULL_SCREEN = 1 | Full-screen mode. This mode takes effect only on PC/2-in-1 devices. |

### AbilityRuntime_SupportedWindowMode

```c
enum AbilityRuntime_SupportedWindowMode
```

**Description**

Specifies the display modes supported by the window when a UIAbility is started in the application. If this field is not configured, the value of the supportWindowMode field in the [abilities tag](../../quick-start/module-configuration-file.md#abilities) of the corresponding [module.json5 configuration file](../../quick-start/module-configuration-file.md) is used by default.

**Since**: 17

| Value| Description|
| -- | -- |
| ABILITY_RUNTIME_SUPPORTED_WINDOW_MODE_FULL_SCREEN = 0 | A window in full-screen mode is supported.|
| ABILITY_RUNTIME_SUPPORTED_WINDOW_MODE_SPLIT = 1 | The window supports split-screen display. It usually needs to be used in combination with ABILITY_RUNTIME_SUPPORTED_WINDOW_MODE_FULL_SCREEN or ABILITY_RUNTIME_SUPPORTED_WINDOW_MODE_FLOATING (via bitwise OR). It is not recommended to use ABILITY_RUNTIME_SUPPORTED_WINDOW_MODE_SPLIT alone. When only ABILITY_RUNTIME_SUPPORTED_WINDOW_MODE_SPLIT is configured, the window on PC/2-in-1 devices defaults to floating window mode and supports entering split-screen mode. |
| ABILITY_RUNTIME_SUPPORTED_WINDOW_MODE_FLOATING = 2 | A floating window is supported.|
