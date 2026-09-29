# native_interface.h

## Overview

Provides a unified entry for the native module APIs.

**Library**: libace_ndk.z.so

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_NativeAPIVariantKind](#arkui_nativeapivariantkind) | ArkUI_NativeAPIVariantKind | Defines the native API types. |
| [OH_ArkUI_NativeModule_RuntimeCheckType](#oh_arkui_nativemodule_runtimechecktype) | OH_ArkUI_NativeModule_RuntimeCheckType | Defines the runtime check types for ArkUI C APIs.<br> Each check type corresponds to a specific improper usage scenario of ArkUI C APIs, used to detect misuse at runtime (such as cross-thread calls, accessing destroyed objects, etc.). You can use [OH_ArkUI_NativeModule_SetRuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_setruntimecheckmode) to independently configure a runtime check mode for each check type. The behavior upon check failure is determined by the configured runtime check mode. For available modes, see [OH_ArkUI_NativeModule_RuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode). |
| [OH_ArkUI_NativeModule_RuntimeCheckMode](#oh_arkui_nativemodule_runtimecheckmode) | OH_ArkUI_NativeModule_RuntimeCheckMode | Defines the runtime check modes for ArkUI C APIs.<br> All runtime check types use the same set of modes (DISABLED, LOG, CRASH) defined in this enum to determine the behavior upon check failure. That is, each check type can be independently set to one of the following three modes. The default mode depends on the application's build type: For applications compiled in debug mode (Debug build in DevEco Studio, used for development and debugging), the default is [OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode). For applications compiled in release mode (Release build in DevEco Studio, used for production release), the default is [OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode). |

### Macro

| Name | Description |
| -- | -- |
| OH_ArkUI_GetModuleInterface(nativeAPIVariantKind, structType, structPtr)                      do {                                                                                              void* anyNativeAPI = OH_ArkUI_QueryModuleInterfaceByName(nativeAPIVariantKind, #structType);  if (anyNativeAPI) {                                                                           structPtr = (structType*)(anyNativeAPI);                                                  }                                                                                             } while (0) | Obtains the macro function corresponding to a struct pointer based on the struct type.<br>**Since**: 12 |

### Function

| Name | Description |
| -- | -- |
| [void* OH_ArkUI_QueryModuleInterfaceByName(ArkUI_NativeAPIVariantKind type, const char* structName)](#oh_arkui_querymoduleinterfacebyname) | Obtains the native API set of a specified type. |
| [const char* OH_ArkUI_NativeModule_GetErrorMessage()](#oh_arkui_nativemodule_geterrormessage) | Retrieves the latest error message, which includes the error code, method name, and error cause. When other interfaces return an error code, they save the corresponding error message, and this interface can retrieve the currently stored error message. The information returned by this interface may evolve with versions and is intended solely for output to aid in analysis and troubleshooting. It should not be used for logical decisions.<br> The returned string is a thread-local global string created by the system. The caller must not modify its content. If any editing is required, create a copy of the string content yourself. No memory deallocation is required by the caller. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_SetRuntimeCheckMode(OH_ArkUI_NativeModule_RuntimeCheckType checkType, OH_ArkUI_NativeModule_RuntimeCheckMode mode)](#oh_arkui_nativemodule_setruntimecheckmode) | Sets the process-level runtime check mode for ArkUI C APIs.<br> This function configures the behavior of a specific runtime check type when misuse is detected. The setting is process-level and remains in effect until the next successful call for the same check type.<br> <b>Thread requirement:</b> This function must be called on the UI thread. Calling it from any other thread will immediately terminate the application without returning. The thread check is performed before parameter validation.<br> <b>Default behavior:</b> If this function is not called for a specific check type, debug application builds default to [OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode), and release application builds default to [OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode). |

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

### OH_ArkUI_NativeModule_RuntimeCheckType

```c
enum OH_ArkUI_NativeModule_RuntimeCheckType
```

**Description**

Defines the runtime check types for ArkUI C APIs.<br> Each check type corresponds to a specific improper usage scenario of ArkUI C APIs, used to detect misuse at runtime (such as cross-thread calls, accessing destroyed objects, etc.). You can use [OH_ArkUI_NativeModule_SetRuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_setruntimecheckmode) to independently configure a runtime check mode for each check type. The behavior upon check failure is determined by the configured runtime check mode. For available modes, see [OH_ArkUI_NativeModule_RuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode).

**Since**: 26.2.0

| Enum item | Description |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_CHECK_TYPE_UI_THREAD = 0 | UI thread check type: Some ArkUI C APIs must be called on the UI thread. This type detects whether these APIs are called from a non-UI thread.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_CHECK_TYPE_NODE_DISPOSED = 1 | Node disposed check type: Detects whether the ArkUI_NodeHandle passed to a C API has already been disposed.<br>**Since**: 26.2.0 |

### OH_ArkUI_NativeModule_RuntimeCheckMode

```c
enum OH_ArkUI_NativeModule_RuntimeCheckMode
```

**Description**

Defines the runtime check modes for ArkUI C APIs.<br> All runtime check types use the same set of modes (DISABLED, LOG, CRASH) defined in this enum to determine the behavior upon check failure. That is, each check type can be independently set to one of the following three modes. The default mode depends on the application's build type: For applications compiled in debug mode (Debug build in DevEco Studio, used for development and debugging), the default is [OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode). For applications compiled in release mode (Release build in DevEco Studio, used for production release), the default is [OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode).

**Since**: 26.2.0

| Enum item | Description |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED = 0 | Disables the specified runtime check. The C API behavior is the same as before the check was introduced.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_CHECK_MODE_LOG = 1 | Prints diagnostic logs (check type, API name, cause, native stack trace) and continues the C API call.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH = 2 | Prints diagnostic logs and immediately terminates the application.<br>**Since**: 26.2.0 |


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

### OH_ArkUI_NativeModule_SetRuntimeCheckMode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_SetRuntimeCheckMode(OH_ArkUI_NativeModule_RuntimeCheckType checkType, OH_ArkUI_NativeModule_RuntimeCheckMode mode)
```

**Description**

Sets the process-level runtime check mode for ArkUI C APIs.<br> This function configures the behavior of a specific runtime check type when misuse is detected. The setting is process-level and remains in effect until the next successful call for the same check type.<br> <b>Thread requirement:</b> This function must be called on the UI thread. Calling it from any other thread will immediately terminate the application without returning. The thread check is performed before parameter validation.<br> <b>Default behavior:</b> If this function is not called for a specific check type, debug application builds default to [OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode), and release application builds default to [OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode).

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_RuntimeCheckType](capi-native-interface-h.md#oh_arkui_nativemodule_runtimechecktype) checkType | [in] Specifies the runtime check type to configure. The value is an enum value from [OH_ArkUI_NativeModule_RuntimeCheckType](capi-native-interface-h.md#oh_arkui_nativemodule_runtimechecktype). |
| [OH_ArkUI_NativeModule_RuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode) mode | [in] Specifies the runtime check mode. The value is an enum value from [OH_ArkUI_NativeModule_RuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode). |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | Return value: <ul><li>Returns ARKUI_ERROR_CODE_NO_ERROR if the setting is updated successfully. </li><li>Returns ARKUI_ERROR_CODE_PARAM_INVALID if checkType or mode is invalid.</li></ul> When an invalid parameter error is returned, the previous setting is retained. |


