# native_interface.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=37a41c7e4764d3e7f831e1f47fc28c3acf56e6c1 translatedAt=2026-11-09T12:01:28.204Z pushedAt=2026-11-11T01:51:11.922Z nl=1 -->

## Overview

Provides a unified entry for the native module APIs, which are used to initialize the C API environment, obtain the API set of a native module of a specified type, and obtain the latest error information.

**File to include**: <arkui/native_interface.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample**: <!--RP1-->[NativeNodeInterfaceSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/NativeNodeInterfaceSample)<!--RP1End-->

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_NativeAPIVariantKind](#arkui_nativeapivariantkind) | ArkUI_NativeAPIVariantKind | Enumerates the types of native API collections.|
| [OH_ArkUI_NativeModule_RuntimeCheckType](#oh_arkui_nativemodule_runtimechecktype) | OH_ArkUI_NativeModule_RuntimeCheckType | Enumerates the runtime check types of ArkUI C APIs.<br>Each check type corresponds to a scenario of improper use of the ArkUI C APIs, and is used for you to detect misuse of the C APIs at runtime (such as cross-thread calls and access to destroyed objects). You can use [OH_ArkUI_NativeModule_SetRuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_setruntimecheckmode) to independently configure the runtime check mode for each check type. The behavior when a check fails is determined by the configured runtime check mode. For the mode values, see [OH_ArkUI_NativeModule_RuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode). |
| [OH_ArkUI_NativeModule_RuntimeCheckMode](#oh_arkui_nativemodule_runtimecheckmode) | OH_ArkUI_NativeModule_RuntimeCheckMode | Enumerates the runtime check modes of ArkUI C APIs.<br>All runtime check types of the C APIs use the same set of modes defined in this enumeration to set the behavior when a check fails. That is, each check type can be independently set to one of the following three modes. The default mode depends on the build type of the application: an application built in debug mode defaults to [OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode), and an application built in release mode defaults to [OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode). |

### Functions

| Name | Description  |
|--------------|-----------|
| [void* OH_ArkUI_QueryModuleInterfaceByName(ArkUI_NativeAPIVariantKind type, const char* structName)](#oh_arkui_querymoduleinterfacebyname)        | Initializes the C API environment and obtains the native module API collection of the specified type.|
| [const char* OH_ArkUI_NativeModule_GetErrorMessage()](#oh_arkui_nativemodule_geterrormessage) | Obtains the latest error message, including the error codes, API names, and error causes. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_SetRuntimeCheckMode(OH_ArkUI_NativeModule_RuntimeCheckType checkType, OH_ArkUI_NativeModule_RuntimeCheckMode mode)](#oh_arkui_nativemodule_setruntimecheckmode) | Sets the process-level runtime check mode of the ArkUI C API.<br>This API configures the behavior of a specific runtime check type when misuse is detected. The setting is process-level and remains in effect until the next successful call for the same check type.<br>Thread requirement: This API must be called on the UI thread. Calling it from any other thread immediately terminates the application without returning. The thread check is performed before parameter validation.<br>Default behavior: If this API is not called for a check type, the application built in debug mode defaults to [OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode),<br>and the application built in release mode defaults to [OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode). |

### Macros

| Name | Description  |
|--------------|-----------|
| [OH_ArkUI_GetModuleInterface(nativeAPIVariantKind, structType, structPtr)](#oh_arkui_getmoduleinterface)      | Initializes the C API environment and obtains the corresponding struct pointer based on the struct type. |

## Enum Description

### ArkUI_NativeAPIVariantKind

```c
enum ArkUI_NativeAPIVariantKind
```

**Description**


Enumerates the types of native API collections.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_NATIVE_NODE = 0 | API related to UI components. For details, see the [struct](./capi-native-node-h.md#structs) definition in [native_node.h](./capi-native-node-h.md).|
| ARKUI_NATIVE_DIALOG = 1 | API related to dialog boxes. For details, see the [struct](./capi-native-dialog-h.md#structs) definition in [native_dialog.h](./capi-native-dialog-h.md). |
| ARKUI_NATIVE_GESTURE = 2 | API related to gestures. For details, see the [struct](./capi-native-gesture-h.md#structs) definition in [native_gesture.h](./capi-native-gesture-h.md). |
| ARKUI_NATIVE_ANIMATE = 3 | API related to animations. For details, see the [struct](./capi-native-animate-h.md#structs) definition in [native_animate.h](./capi-native-animate-h.md). |
| ARKUI_MULTI_THREAD_NATIVE_NODE = 4 | API related to multi-threaded UI components. For details, see the [struct](./capi-native-node-h.md#structs) definition in [native_node.h](./capi-native-node-h.md).<br>**Since**: 22|

### OH_ArkUI_NativeModule_RuntimeCheckType

```c
enum OH_ArkUI_NativeModule_RuntimeCheckType
```

**Description**

Enumerates the runtime check types of ArkUI C APIs.<br>Each check type corresponds to a scenario of improper use of the ArkUI C APIs, and is used for you to detect misuse of the C APIs at runtime (such as cross-thread calls and access to destroyed objects). You can use [OH_ArkUI_NativeModule_SetRuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_setruntimecheckmode) to independently configure the runtime check mode for each check type. The behavior when a check fails is determined by the configured runtime check mode. For details about the mode values, see [OH_ArkUI_NativeModule_RuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode).

**Since:** 26.1.0

| Value | Description |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_CHECK_TYPE_UI_THREAD = 0 | UI thread check: some ArkUI C APIs must be called on the UI thread. This type is used to detect whether these APIs are called on a non-UI thread. |
| OH_ARKUI_NATIVEMODULE_CHECK_TYPE_NODE_DISPOSED = 1 | Node disposal check: detects whether the [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) passed to a C API has been disposed of. |
| OH_ARKUI_NATIVEMODULE_CHECK_TYPE_ATTRIBUTE_MATCH = 2 | Attribute match check: detects whether [ArkUI_NodeAttributeType](capi-native-node-h.md#arkui_nodeattributetype) passed to [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)/[getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)/[resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute) matches the actual component type of the node. |
| OH_ARKUI_NATIVEMODULE_CHECK_TYPE_MULTI_THREAD = 3 | Multi-thread race check: detects whether another thread is already operating on the same component tree when a multi-thread API is called. |

### OH_ArkUI_NativeModule_RuntimeCheckMode

```c
enum OH_ArkUI_NativeModule_RuntimeCheckMode
```

**Description**

Enumerates the runtime check modes of ArkUI C APIs.<br>All runtime check types of the C APIs use the same set of modes defined in this enumeration to set the behavior when a check fails. That is, each check type can be independently set to one of the following three modes. The default mode depends on the build type of the application: an application built in debug mode defaults to [OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode), and an application built in release mode defaults to [OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode).

**Since:** 26.1.0

| Value | Description |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED = 0 | Disables the specified runtime check. The C API behavior is the same as before the check is introduced. |
| OH_ARKUI_NATIVEMODULE_CHECK_MODE_LOG = 1 | Prints diagnostic logs (including the check type, API name, reason, and native stack) and continues the C API call. |
| OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH = 2 | Prints diagnostic logs and terminates the application immediately. |

## Function Description

### OH_ArkUI_QueryModuleInterfaceByName()

```c
void* OH_ArkUI_QueryModuleInterfaceByName(ArkUI_NativeAPIVariantKind type, const char* structName)
```

**Description**


Initializes the C API environment and obtains the native module API collection of the specified type.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NativeAPIVariantKind](#arkui_nativeapivariantkind) type | Type of the native API collection provided by ArkUI, for example, **ARKUI_NATIVE_NODE** or **ARKUI_NATIVE_GESTURE**. |
| const char* structName | Pointer to the name of a native API struct, which can be obtained by querying the struct definition in the corresponding header file, for example, "ArkUI_NativeNodeAPI_1" in [native_node.h](./capi-native-node-h.md). |

**Return value**

| Type| Description|
| -- | -- |
| void* | Pointer to the native API abstraction, which must be cast to the specific type for use.|

### OH_ArkUI_GetModuleInterface()

```c
#define OH_ArkUI_GetModuleInterface(nativeAPIVariantKind, structType, structPtr)                     \
do {                                                                                                 \
        void* anyNativeAPI = OH_ArkUI_QueryModuleInterfaceByName(nativeAPIVariantKind, #structType); \
        if (anyNativeAPI) {                                                                          \
            structPtr = (structType*)(anyNativeAPI);                                                 \
        }                                                                                            \
    } while (0)                                                                      
```

**Description**


Initializes the C API environment and obtains the corresponding struct pointer based on the struct type.

It applies to the scenario where the native API set type and the API struct type have been determined, and a specific native API struct pointer needs to be obtained to call ArkUI native C APIs. This macro function receives the enumeration parameter **nativeAPIVariantKind** of the [ArkUI_NativeAPIVariantKind](#arkui_nativeapivariantkind) type, the struct type parameter **structType**, and the struct pointer variable **structPtr**. **structPtr** must match **structType**. This macro function calls [OH_ArkUI_QueryModuleInterfaceByName](#oh_arkui_querymoduleinterfacebyname) to initialize the C API environment and obtain the abstract pointer of the native API, converts it to the **structType\*** type, and assigns it to **structPtr**.

**Since**: 12

### OH_ArkUI_NativeModule_GetErrorMessage()

```c
const char* OH_ArkUI_NativeModule_GetErrorMessage()
```

**Description**

Obtains the latest error information, including the error codes, API names, and error causes. For details about the error code, see [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode). When other APIs return an error code, the corresponding error information is saved, and the currently stored error information can be obtained through this API. The returned string is a thread-local global string created by the system, and its content must not be modified. If any editing is required, create a copy of the string content. The information returned by this API may change as versions evolve. It is used only for output to assist in analysis and troubleshooting, and must not be used as a basis for logical judgment. The returned error information does not need to be released manually.

**Since**: 26.0.0

**Return value**

| Type| Description|
| -- | -- |
| const char* | Pointer to the latest error information, including the error codes, API names, and error causes.|

### OH_ArkUI_NativeModule_SetRuntimeCheckMode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_SetRuntimeCheckMode(OH_ArkUI_NativeModule_RuntimeCheckType checkType, OH_ArkUI_NativeModule_RuntimeCheckMode mode)
```

**Description**

Sets the process-level runtime check mode of the ArkUI C API.<br>This API configures the behavior of a specific runtime check type when misuse is detected. The setting is process-level and remains in effect until the next successful call for the same check type.<br>Thread requirement: This API must be called on the UI thread. Calling it from any other thread immediately terminates the application without returning. The thread check is performed before parameter validation.<br>Default behavior: If this API is not called for a check type, the application built in debug mode defaults to [OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode),<br>and the application built in release mode defaults to [OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode).

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_RuntimeCheckType](capi-native-interface-h.md#oh_arkui_nativemodule_runtimechecktype) checkType | [Input parameter] Runtime check type to set. The value is an enumerated value in [OH_ArkUI_NativeModule_RuntimeCheckType](capi-native-interface-h.md#oh_arkui_nativemodule_runtimechecktype). |
| [OH_ArkUI_NativeModule_RuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode) mode | [Input parameter] Runtime check mode. The value is an enumerated value in [OH_ArkUI_NativeModule_RuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode). |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the setting is updated successfully.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **checkType** or **mode** is invalid.<br>The previous settings are retained when an invalid parameter error is returned. |
