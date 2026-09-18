# native_interface.h

## Overview

Provides a unified entry for the native module APIs.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_NativeAPIVariantKind](#arkui_nativeapivariantkind) | ArkUI_NativeAPIVariantKind | Defines the native API types. |

### Macro

| Name | Description |
| -- | -- |
| OH_ArkUI_GetModuleInterface(nativeAPIVariantKind, structType, structPtr)                      do {                                                                                              void* anyNativeAPI = OH_ArkUI_QueryModuleInterfaceByName(nativeAPIVariantKind, #structType);  if (anyNativeAPI) {                                                                           structPtr = (structType*)(anyNativeAPI);                                                  }                                                                                             } while (0) | Obtains the macro function corresponding to a struct pointer based on the struct type.<br>**Since**: 12 |

### Function

| Name | Description |
| -- | -- |
| [void* OH_ArkUI_QueryModuleInterfaceByName(ArkUI_NativeAPIVariantKind type, const char* structName)](#oh_arkui_querymoduleinterfacebyname) | Obtains the native API set of a specified type. |
| [const char* OH_ArkUI_NativeModule_GetErrorMessage()](#oh_arkui_nativemodule_geterrormessage) | Retrieves the latest error message, which includes the error code, method name, and error cause. When other interfaces return an error code, they save the corresponding error message, and this interface can retrieve the currently stored error message. The information returned by this interface may evolve with versions and is intended solely for output to aid in analysis and troubleshooting. It should not be used for logical decisions.<br> The returned string is a thread-local global string created by the system. The caller must not modify its content. If any editing is required, create a copy of the string content yourself. No memory deallocation is required by the caller. |

## Enum type description

### ArkUI_NativeAPIVariantKind

```c
enum ArkUI_NativeAPIVariantKind
```

**Description**

Defines the native API types.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_NATIVE_NODE | API related to UI components. For details, see the struct definition in <arkui/native_node.h>. |
| ARKUI_NATIVE_DIALOG | API related to dialog boxes. For details, see the struct definition in <arkui/native_dialog.h>. |
| ARKUI_NATIVE_GESTURE | API related to gestures. For details, see the struct definition in <arkui/native_gesture.h>. |
| ARKUI_NATIVE_ANIMATE | API related to animations. For details, see the struct definition in <arkui/native_animate.h>. |
| ARKUI_MULTI_THREAD_NATIVE_NODE |  |


## Function description

### OH_ArkUI_QueryModuleInterfaceByName()

```c
void* OH_ArkUI_QueryModuleInterfaceByName(ArkUI_NativeAPIVariantKind type, const char* structName)
```

**Description**

Obtains the native API set of a specified type.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NativeAPIVariantKind](capi-native-interface-h.md#arkui_nativeapivariantkind) type | Indicates the type of the native API set provided by ArkUI, for example, <b>ARKUI_NATIVE_NODE</b> and <b>ARKUI_NATIVE_GESTURE</b>. |
| const char* structName | Indicates the name of a native struct defined in the corresponding header file, for example, <b>ArkUI_NativeNodeAPI_1</b> in <arkui/native_node.h>. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | Returns the pointer to the abstract native API, which can be used after being converted into a specific type. |

### OH_ArkUI_NativeModule_GetErrorMessage()

```c
const char* OH_ArkUI_NativeModule_GetErrorMessage()
```

**Description**

Retrieves the latest error message, which includes the error code, method name, and error cause. When other interfaces return an error code, they save the corresponding error message, and this interface can retrieve the currently stored error message. The information returned by this interface may evolve with versions and is intended solely for output to aid in analysis and troubleshooting. It should not be used for logical decisions.<br> The returned string is a thread-local global string created by the system. The caller must not modify its content. If any editing is required, create a copy of the string content yourself. No memory deallocation is required by the caller.

**Since**: 26.0.0

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns the most recent error message. |


