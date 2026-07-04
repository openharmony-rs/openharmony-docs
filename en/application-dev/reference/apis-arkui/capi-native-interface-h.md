# native_interface.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Provides a unified entry for the native module APIs.

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

### Macros

| Name | Description  |
|--------------|-----------|
| [OH_ArkUI_GetModuleInterface(nativeAPIVariantKind, structType, structPtr)](#oh_arkui_getmoduleinterface)      | Obtains the corresponding struct pointer based on the struct type.|

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
| ARKUI_NATIVE_DIALOG = 1 | API related to dialog boxes. For details, see the [struct](capi-native-dialog-h.md#structs) definition in [native_dialog.h](./capi-native-dialog-h.md).|
| ARKUI_NATIVE_GESTURE = 2 | API related to gestures. For details, see the [struct](capi-native-gesture-h.md#structs) definition in [native_gesture.h](./capi-native-gesture-h.md).|
| ARKUI_NATIVE_ANIMATE = 3 | API related to animations. For details, see the [struct](capi-native-animate-h.md#structs) definition in [native_animate.h](./capi-native-animate-h.md).|
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
| [ArkUI_NativeAPIVariantKind](capi-native-interface-h.md#arkui_nativeapivariantkind) type | Type of the native API collection provided by ArkUI, for example, **ARKUI_NATIVE_NODE** or **ARKUI_NATIVE_GESTURE**.|
| const char* structName | Pointer to the name of a native struct, obtained by querying the struct definitions in the corresponding header file, for example, **ArkUI_NativeNodeAPI_1** in [native_node.h](./capi-native-node-h.md).|

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


Obtains the corresponding struct pointer based on the struct type. This API takes parameters of **nativeAPIVariantKind** (an enumeration of type [ArkUI_NativeAPIVariantKind](capi-native-interface-h.md#arkui_nativeapivariantkind)), **structType** (of type const char\*), **structPtr** (of type structType\*). It calls [OH_ArkUI_QueryModuleInterfaceByName](#oh_arkui_querymoduleinterfacebyname) to obtain a native API pointer, casts it to structType\*, and assigns the result to **structPtr**.

**Since**: 12

### OH_ArkUI_NativeModule_GetErrorMessage()

```c
const char* OH_ArkUI_NativeModule_GetErrorMessage()
```

**Description**

Obtains the latest error information, including the error codes, method names, and error causes. For details about the error codes, see [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode). When an error code is returned by another API, the corresponding error information is saved. You can use this API to obtain the saved error information. The returned string is a thread-local global string created by the system, and cannot be modified. If you need to edit the string, create a copy of the string content. The information returned by this API may vary with version evolution. Therefore, the information is used only for output to assist in analysis and troubleshooting, and should not be used as a basis for logic judgment. The returned error information does not need to be manually released.

**Since**: 26.0.0

**Return value**

| Type| Description|
| -- | -- |
| const char* | Pointer to the latest error information, including the error codes, method names, and error causes.|
