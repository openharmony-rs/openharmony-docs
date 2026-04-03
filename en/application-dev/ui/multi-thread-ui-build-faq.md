# FAQs About UI Parallelization
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

## How to Obtain and Use Multi-thread NDK APIs

From API version 22, **ARKUI_MULTI_THREAD_NATIVE_NODE** is added to [ArkUI_NativeAPIVariantKind](../reference/apis-arkui/capi-native-interface-h.md#arkui_nativeapivariantkind).

Call the [OH_ArkUI_GetModuleInterface](../reference/apis-arkui/capi-native-interface-h.md#oh_arkui_getmoduleinterface) API and pass **ARKUI_MULTI_THREAD_NATIVE_NODE** as the input parameter to obtain the multi-threaded NDK API set. Refer to [Using Multi-threaded NDK APIs](../ui/ndk-build-on-multi-thread.md#using-multi-threaded-ndk-apis) for the complete example.

## Calling a multi-threaded NDK API returns the **ARKUI_ERROR_CODE_NODE_ON_INVALID_THREAD** error code.

**Symptom**

Calling a multi-threaded NDK API returns the **ARKUI_ERROR_CODE_NODE_ON_INVALID_THREAD** error code.

**Solution**

Refer to [Multi-threaded NDK API Set Specifications](../ui/ndk-build-on-multi-thread.md#multi-threaded-ndk-api-set-specifications) to check whether the called API supports multi-thread calling, and then perform the following steps:

1. If the API can be called only on the UI thread, adjust the function call timing and call the API on the UI thread.
2. If the API supports multi-thread calling, the error occurs because the node operated by the API is in the Attached state.
   - Check whether the node is created by the multi-threaded [createNode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#createnode) API.
   - Remove all non-convertible attached components from the component tree where the component is located by referring to [Multi-threaded NDK API Set Specifications](../ui/ndk-build-on-multi-thread.md#multi-threaded-ndk-api-set-specifications).

## How to Ensure Thread Safety When Operating ArkUI Components in Multiple Threads

When multi-threaded NDK APIs are used, multiple threads operate the same component or component tree at the same time. In this case, thread safety cannot be ensured. You need to avoid this situation through proper architectural design.

You can follow the restrictions in [Multi-threaded NDK API Set Specifications](../ui/ndk-build-on-multi-thread.md#multi-threaded-ndk-api-set-specifications) to ensure thread safety.
