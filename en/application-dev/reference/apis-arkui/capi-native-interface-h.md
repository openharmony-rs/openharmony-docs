# native_interface.h

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=ba15987bdaff6b5722a2515323f97341807b6ce9 translatedAt=2026-08-21T12:07:40.330Z pushedAt=2026-08-24T08:05:59.999Z -->

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

### Functions

| Name | Description  |
|--------------|-----------|
| [void* OH_ArkUI_QueryModuleInterfaceByName(ArkUI_NativeAPIVariantKind type, const char* structName)](#oh_arkui_querymoduleinterfacebyname)        | Initializes the C API environment and obtains the native module API collection of the specified type.|
| [const char* OH_ArkUI_NativeModule_GetErrorMessage()](#oh_arkui_nativemodule_geterrormessage) | Obtains the latest error message, including the error codes, API names, and error causes. |

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