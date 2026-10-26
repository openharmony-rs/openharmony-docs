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
| [ArkUI_NativeAPIVariantKind](#arkui_nativeapivariantkind) | ArkUI_NativeAPIVariantKind | Enumerates the types of native API collections. |
| [OH_ArkUI_NativeModule_RuntimeCheckType](#oh_arkui_nativemodule_runtimechecktype) | OH_ArkUI_NativeModule_RuntimeCheckType | Defines the runtime check types for ArkUI C APIs.<br> Each check type corresponds to a specific improper usage scenario of ArkUI C APIs, used to detect misuse at runtime (such as cross-thread calls, accessing destroyed objects, etc.). You can use [OH_ArkUI_NativeModule_SetRuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_setruntimecheckmode) to independently configure a runtime check mode for each check type. The behavior upon check failure is determined by the configured runtime check mode. For available modes, see [OH_ArkUI_NativeModule_RuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode). |
| [OH_ArkUI_NativeModule_RuntimeCheckMode](#oh_arkui_nativemodule_runtimecheckmode) | OH_ArkUI_NativeModule_RuntimeCheckMode | Defines the runtime check modes for ArkUI C APIs.<br> All runtime check types use the same set of modes (DISABLED, LOG, CRASH) defined in this enum to determine the behavior upon check failure. That is, each check type can be independently set to one of the following three modes. The default mode depends on the application's build type: For applications compiled in debug mode (Debug build in DevEco Studio, used for development and debugging), the default is [OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode). For applications compiled in release mode (Release build in DevEco Studio, used for production release), the default is [OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode). |

### Macro

| Name | Description |
| -- | -- |
| OH_ArkUI_GetModuleInterface(nativeAPIVariantKind, structType, structPtr)                      do {                                                                                              void* anyNativeAPI = OH_ArkUI_QueryModuleInterfaceByName(nativeAPIVariantKind, #structType);  if (anyNativeAPI) {                                                                           structPtr = (structType*)(anyNativeAPI);                                                  }                                                                                             } while (0) | Initializes the C API environment and obtains the corresponding struct pointer based on the struct type.<br> It applies to the scenario where the native API set type and the API struct type have been determined, and a specific native API struct pointer needs to be obtained to call ArkUI native C APIs. This macro function receives the enumeration parameter <b>nativeAPIVariantKind</b> of the [ArkUI_NativeAPIVariantKind](capi-native-interface-h.md#arkui_nativeapivariantkind) type, the struct type parameter <b>structType</b>, and the struct pointer variable <b>structPtr</b>. <b>structPtr</b> must match <b>structType</b>. This macro function calls [OH_ArkUI_QueryModuleInterfaceByName](capi-native-interface-h.md#oh_arkui_querymoduleinterfacebyname) to initialize the C API environment and obtain the abstract pointer of the native API, converts it to the <b>structType*</b> type, and assigns it to <b>structPtr</b>.<br>**Since**: 12 |

### Function

| Name | Description |
| -- | -- |
| [void* OH_ArkUI_QueryModuleInterfaceByName(ArkUI_NativeAPIVariantKind type, const char* structName)](#oh_arkui_querymoduleinterfacebyname) | Initializes the C API environment and obtains the native module API collection of the specified type. |
| [const char* OH_ArkUI_NativeModule_GetErrorMessage()](#oh_arkui_nativemodule_geterrormessage) | Obtains the latest error information, including the error codes, API names, and error causes. For details about the error code, see ArkUI_ErrorCode. When other APIs return an error code, the corresponding error information is saved, and the currently stored error information can be obtained through this API. The returned string is a thread-local global string created by the system, and its content must not be modified. If any editing is required, create a copy of the string content. The information returned by this API may change as versions evolve. It is used only for output to assist in analysis and troubleshooting, and must not be used as a basis for logical judgment. The returned error information does not need to be released manually. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_SetRuntimeCheckMode(OH_ArkUI_NativeModule_RuntimeCheckType checkType, OH_ArkUI_NativeModule_RuntimeCheckMode mode)](#oh_arkui_nativemodule_setruntimecheckmode) | Sets the process-level runtime check mode for ArkUI C APIs.<br> This function configures the behavior of a specific runtime check type when misuse is detected. The setting is process-level and remains in effect until the next successful call for the same check type.<br> <b>Thread requirement:</b> This function must be called on the UI thread. Calling it from any other thread will immediately terminate the application without returning. The thread check is performed before parameter validation.<br> <b>Default behavior:</b> If this function is not called for a specific check type, debug application builds default to [OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode), and release application builds default to [OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode). |

## Enum type description

### ArkUI_NativeAPIVariantKind

```c
enum ArkUI_NativeAPIVariantKind
```

**Description**

Enumerates the types of native API collections.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.1.0

| Enum item | Description |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_CHECK_TYPE_UI_THREAD = 0 | UI thread check type: Some ArkUI C APIs must be called on the UI thread. This type detects whether these APIs are called from a non-UI thread.<br>**Since**: 26.1.0 |
| OH_ARKUI_NATIVEMODULE_CHECK_TYPE_NODE_DISPOSED = 1 | Node disposed check type: Detects whether the ArkUI_NodeHandle passed to a C API has already been disposed.<br>**Since**: 26.1.0 |
| OH_ARKUI_NATIVEMODULE_CHECK_TYPE_ATTRIBUTE_MATCH = 2 | Attribute match check type: Detects whether an ArkUI_NodeAttributeType passed to SetAttribute/GetAttribute/ResetAttribute matches the node's actual component type.<br>**Since**: 26.1.0 |
| OH_ARKUI_NATIVEMODULE_CHECK_TYPE_MULTI_THREAD = 3 | multi thread race condition check type: Detects whether another thread is already operating on the same component tree when a multi thread API is called.<br>**Since**: 26.1.0 |

### OH_ArkUI_NativeModule_RuntimeCheckMode

```c
enum OH_ArkUI_NativeModule_RuntimeCheckMode
```

**Description**

Defines the runtime check modes for ArkUI C APIs.<br> All runtime check types use the same set of modes (DISABLED, LOG, CRASH) defined in this enum to determine the behavior upon check failure. That is, each check type can be independently set to one of the following three modes. The default mode depends on the application's build type: For applications compiled in debug mode (Debug build in DevEco Studio, used for development and debugging), the default is [OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode). For applications compiled in release mode (Release build in DevEco Studio, used for production release), the default is [OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.1.0

| Enum item | Description |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED = 0 | Disables the specified runtime check. The C API behavior is the same as before the check was introduced.<br>**Since**: 26.1.0 |
| OH_ARKUI_NATIVEMODULE_CHECK_MODE_LOG = 1 | Prints diagnostic logs (check type, API name, cause, native stack trace) and continues the C API call.<br>**Since**: 26.1.0 |
| OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH = 2 | Prints diagnostic logs and immediately terminates the application.<br>**Since**: 26.1.0 |


## Function description

### OH_ArkUI_QueryModuleInterfaceByName()

```c
void* OH_ArkUI_QueryModuleInterfaceByName(ArkUI_NativeAPIVariantKind type, const char* structName)
```

**Description**

Initializes the C API environment and obtains the native module API collection of the specified type.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NativeAPIVariantKind](capi-native-interface-h.md#arkui_nativeapivariantkind) type | Type of the native API collection provided by ArkUI, for example, <b>ARKUI_NATIVE_NODE</b> or <b>ARKUI_NATIVE_GESTURE</b>. |
| const char* structName | Pointer to the name of a native API struct, which can be obtained by querying the struct definition in the corresponding header file, for example, <b>ArkUI_NativeNodeAPI_1</b> in <arkui/native_node.h>. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | Pointer to the native API abstraction, which must be cast to the specific type for use. |

### OH_ArkUI_NativeModule_GetErrorMessage()

```c
const char* OH_ArkUI_NativeModule_GetErrorMessage()
```

**Description**

Obtains the latest error information, including the error codes, API names, and error causes. For details about the error code, see ArkUI_ErrorCode. When other APIs return an error code, the corresponding error information is saved, and the currently stored error information can be obtained through this API. The returned string is a thread-local global string created by the system, and its content must not be modified. If any editing is required, create a copy of the string content. The information returned by this API may change as versions evolve. It is used only for output to assist in analysis and troubleshooting, and must not be used as a basis for logical judgment. The returned error information does not need to be released manually.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Pointer to the latest error information, including the error codes, API names, and error causes. |

### OH_ArkUI_NativeModule_SetRuntimeCheckMode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_SetRuntimeCheckMode(OH_ArkUI_NativeModule_RuntimeCheckType checkType, OH_ArkUI_NativeModule_RuntimeCheckMode mode)
```

**Description**

Sets the process-level runtime check mode for ArkUI C APIs.<br> This function configures the behavior of a specific runtime check type when misuse is detected. The setting is process-level and remains in effect until the next successful call for the same check type.<br> <b>Thread requirement:</b> This function must be called on the UI thread. Calling it from any other thread will immediately terminate the application without returning. The thread check is performed before parameter validation.<br> <b>Default behavior:</b> If this function is not called for a specific check type, debug application builds default to [OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode), and release application builds default to [OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_RuntimeCheckType](capi-native-interface-h.md#oh_arkui_nativemodule_runtimechecktype) checkType | [in] Specifies the runtime check type to configure. The value is an enum value from [OH_ArkUI_NativeModule_RuntimeCheckType](capi-native-interface-h.md#oh_arkui_nativemodule_runtimechecktype). |
| [OH_ArkUI_NativeModule_RuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode) mode | [in] Specifies the runtime check mode. The value is an enum value from [OH_ArkUI_NativeModule_RuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode). |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | Return value: <ul><li>Returns ARKUI_ERROR_CODE_NO_ERROR if the setting is updated successfully. </li><li>Returns ARKUI_ERROR_CODE_PARAM_INVALID if checkType or mode is invalid.</li></ul> When an invalid parameter error is returned, the previous setting is retained. |


