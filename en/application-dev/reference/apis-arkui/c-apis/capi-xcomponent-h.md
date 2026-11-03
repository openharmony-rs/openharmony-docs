# xcomponent.h

## Overview

Defines xcomponent attribute enum value.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-arkui-nativemodule.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_XComponentType](#arkui_xcomponenttype) | ArkUI_XComponentType | Enumerates the types of the **XComponent** component. |

### Macro

| Name | Description |
| -- | -- |
| ARKUI_XCOMPONENT_H | Defines xcomponent attribute enum value.<br>**Since**: 12<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |

## Enum type description

### ArkUI_XComponentType

```c
enum ArkUI_XComponentType
```

**Description**

Enumerates the types of the **XComponent** component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_XCOMPONENT_TYPE_SURFACE = 0 | The custom content of EGL/OpenGL ES and media data is displayed individually on the screen.<br>**Since**: 12 |
| ARKUI_XCOMPONENT_TYPE_TEXTURE = 2 | The custom content of EGL/OpenGL ES and media data is grouped and displayed together with content of the component.<br>**Since**: 12 |


