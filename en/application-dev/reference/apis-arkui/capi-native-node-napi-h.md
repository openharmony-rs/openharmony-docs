# native_node_napi.h

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @wangyang2022-->
<!--Designer: @piggyguy; @wangyang2022-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=7d33cb479397e5894866e9f123be5fbf84704702 translatedAt=2026-08-25T02:28:00.488Z pushedAt=2026-08-27T02:26:24.381Z -->

## Overview

Provides the APIs used to convert objects such as [FrameNode](js-apis-arkui-frameNode.md), [UIContext](arkts-apis-uicontext-uicontext.md), **NodeContent**, and **DrawableDescriptor** on the ArkTS side to objects on the native side, as well as capabilities such as querying **Navigation** and **Router** page information, registering frame callbacks and idle callbacks, and enabling or disabling event passthrough. These APIs apply to scenarios where ArkUI nodes, context, resources, and page states need to be linked between the ArkTS side and the native side.

**File to include**: `<arkui/native_node_napi.h>`

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample**: <!--RP1-->[native_node_napi](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeNodeNapi/native_node_napi)<!--RP1End-->

## Summary

### Functions

| Name| Description|
| -- | -- |
| [int32_t OH_ArkUI_GetNodeHandleFromNapiValue(napi_env env, napi_value frameNode, ArkUI_NodeHandle* handle)](#oh_arkui_getnodehandlefromnapivalue) | Obtains an **ArkUI_NodeHandle** object on the native side mapped from the **FrameNode** object created on the ArkTS side. This is applicable to scenarios where the native side needs to operate on or manage a FrameNode on the ArkTS side. |
| [int32_t OH_ArkUI_GetContextFromNapiValue(napi_env env, napi_value value, ArkUI_ContextHandle* context)](#oh_arkui_getcontextfromnapivalue) | Obtains an **ArkUI_ContextHandle** object on the native side mapped from the [UIContext](arkts-apis-uicontext-uicontext.md) object created on the ArkTS side. This is applicable to scenarios where the native side needs to invoke ArkUI capabilities based on **UIContext**. |
| [int32_t OH_ArkUI_GetNodeContentFromNapiValue(napi_env env, napi_value value, ArkUI_NodeContentHandle* content)](#oh_arkui_getnodecontentfromnapivalue) | Obtains an **ArkUI_NodeContentHandle** object on the native side mapped from the **NodeContent** object created on the ArkTS side. This is applicable to scenarios where the native side needs to operate on or mount the **NodeContent** content on the ArkTS side. |
| [int32_t OH_ArkUI_GetDrawableDescriptorFromNapiValue(napi_env env, napi_value value, ArkUI_DrawableDescriptor** drawableDescriptor)](#oh_arkui_getdrawabledescriptorfromnapivalue) | Obtains an [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md) object on the native side mapped from the [DrawableDescriptor](arkui-ts/ts-basic-components-image.md#drawabledescriptor10) object created on the ArkTS side. This is applicable to scenarios where the native side needs to use an image resource description object on the ArkTS side. |
| [int32_t OH_ArkUI_GetDrawableDescriptorFromResourceNapiValue(napi_env env, napi_value value, ArkUI_DrawableDescriptor** drawableDescriptor)](#oh_arkui_getdrawabledescriptorfromresourcenapivalue) | Converts a resource object obtained through **$r()** on the ArkTS side into an [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md) object usable on the native side. This is applicable to scenarios where the native side needs to use an ArkTS resource object as an image resource descriptor. |
| [ArkUI_ErrorCode OH_ArkUI_GetNavigationId(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_getnavigationid) | Obtains the ID of the **Navigation** component where the specified node is located.|
| [ArkUI_ErrorCode OH_ArkUI_GetNavDestinationName(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_getnavdestinationname) | Obtains the name of the [NavDestination](arkui-ts/ts-basic-components-navdestination.md) component where the current node is located. |
| [ArkUI_ErrorCode OH_ArkUI_GetNavStackLength(ArkUI_NodeHandle node, int32_t* length)](#oh_arkui_getnavstacklength) | Obtains the length of the **Navigation** stack where the specified node is located.|
| [ArkUI_ErrorCode OH_ArkUI_GetNavDestinationNameByIndex(ArkUI_NodeHandle node, int32_t index, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_getnavdestinationnamebyindex) | Obtains the page name that matches the specified index in the navigation stack where the specified node is located. The index starts from 0, which indicates the bottom of the stack.|
| [ArkUI_ErrorCode OH_ArkUI_GetNavDestinationId(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_getnavdestinationid) | Obtains the ID of the **NavDestination** component where the specified node is located.|
| [ArkUI_ErrorCode OH_ArkUI_GetNavDestinationState(ArkUI_NodeHandle node, ArkUI_NavDestinationState* state)](#oh_arkui_getnavdestinationstate) | Obtains the state of the **NavDestination** component where the specified node is located.|
| [ArkUI_ErrorCode OH_ArkUI_GetNavDestinationIndex(ArkUI_NodeHandle node, int32_t* index)](#oh_arkui_getnavdestinationindex) | Obtains the index of the **NavDestination** component where the current node is located in the page stack. |
| [napi_value OH_ArkUI_GetNavDestinationParam(ArkUI_NodeHandle node)](#oh_arkui_getnavdestinationparam) | Obtains the parameter of the **NavDestination** component where the specified node is located.|
| [ArkUI_ErrorCode OH_ArkUI_GetRouterPageIndex(ArkUI_NodeHandle node, int32_t* index)](#oh_arkui_getrouterpageindex) | Obtains the index of the page where the specified node is located in the page stack for routing.|
| [ArkUI_ErrorCode OH_ArkUI_GetRouterPageName(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_getrouterpagename) | Obtains the name of the page where the specified node is located.|
| [ArkUI_ErrorCode OH_ArkUI_GetRouterPagePath(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_getrouterpagepath) | Obtains the path to the page where the specified node is located.|
| [ArkUI_ErrorCode OH_ArkUI_GetRouterPageState(ArkUI_NodeHandle node, ArkUI_RouterPageState* state)](#oh_arkui_getrouterpagestate) | Obtains the state of the page where the specified node is located.|
| [ArkUI_ErrorCode OH_ArkUI_GetRouterPageId(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_getrouterpageid) | Obtains the ID of the page where the specified node is located.|
| [ArkUI_ErrorCode OH_ArkUI_InitModuleForArkTSEnv(napi_env env)](#oh_arkui_initmoduleforarktsenv) | Initializes ArkUI-related APIs for the specified context environment. This is applicable to scenarios where the context environment needs to be initialized before the native side uses ArkUI-related APIs. This API must not be called on a non-UI thread; otherwise, the program will actively abort. After the specified context environment is initialized using this API, call [OH_ArkUI_NotifyArkTSEnvDestroy()](#oh_arkui_notifyarktsenvdestroy) to notify that the environment has been destroyed when the corresponding environment is destroyed. |
| [void OH_ArkUI_NotifyArkTSEnvDestroy(napi_env env)](#oh_arkui_notifyarktsenvdestroy) | Notifies that the specified context environment has been destroyed. This is applicable to scenarios where the native side synchronously cleans up related states when the ArkTS context environment is destroyed. After the context environment is initialized using [OH_ArkUI_InitModuleForArkTSEnv()](#oh_arkui_initmoduleforarktsenv), this API should be called when the environment is destroyed. This API must not be called on a non-UI thread; otherwise, the program will actively abort. |
| [int32_t OH_ArkUI_PostFrameCallback(ArkUI_ContextHandle uiContext, void* userData, void (\*callback)(uint64_t nanoTimestamp, uint32_t frameCount, void* userData))](#oh_arkui_postframecallback) | Registers a callback to be executed when the next frame is rendered. This is applicable to scenarios where the native side performs UI refresh or rendering-related tasks in the next frame. This API must not be called on a non-UI thread; otherwise, the program will actively abort. |
| [int32_t OH_ArkUI_PostIdleCallback(ArkUI_ContextHandle uiContext, void* userData, void (\*callback)(uint64_t nanoTimeLeft, uint32_t frameCount, void* userData))](#oh_arkui_postidlecallback) | Registers a callback. This is applicable to scenarios where the native side needs to use the idle time between frames to process non-urgent tasks. After the next frame is rendered, if the remaining time before the next VSync signal following that frame is greater than 1 ms, the callback will be executed; if the remaining time is less than 1 ms, the callback will be postponed until the remaining time after a subsequent frame is rendered is greater than 1 ms. If there is no next frame currently, the next frame will be requested automatically. This API must not be called on a non-UI thread; otherwise, the program will actively abort. |
| [ArkUI_ErrorCode OH_ArkUI_EnableEventPassthrough(ArkUI_ContextHandle uiContext, bool enabled, ArkUI_RawInputEventType type)](#oh_arkui_enableeventpassthrough) | Enables or disables event passthrough. Event passthrough indicates that an event is directly delivered to a component without [resampling](../../ui/arkts-interaction-development-guide-touch-screen.md#resampling-and-historical-points) during event distribution. |

## Function Description

### OH_ArkUI_GetNodeHandleFromNapiValue()

```c
int32_t OH_ArkUI_GetNodeHandleFromNapiValue(napi_env env, napi_value frameNode, ArkUI_NodeHandle* handle)
```

**Description**

Obtains an **ArkUI_NodeHandle** object on the native side mapped from the **FrameNode** object created on the ArkTS side. This is applicable to scenarios where the native side needs to operate on or manage a FrameNode on the ArkTS side.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| napi_env env | Pointer to the Node-API environment.|
| napi_value frameNode | **FrameNode** object created on the ArkTS side.|
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)* handle | Pointer to the **ArkUI_NodeHandle**.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. Check whether the passed parameters **env**, **frameNode**, and **handle** are valid. |

### OH_ArkUI_GetContextFromNapiValue()

```c
int32_t OH_ArkUI_GetContextFromNapiValue(napi_env env, napi_value value, ArkUI_ContextHandle* context)
```

**Description**

Obtains an **ArkUI_ContextHandle** object on the native side mapped from the [UIContext](arkts-apis-uicontext-uicontext.md) object created on the ArkTS side. This is applicable to scenarios where the native side needs to invoke ArkUI capabilities based on **UIContext**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| napi_env env | Pointer to the Node-API environment. |
| napi_value value | **UIContext** object created on the ArkTS side. |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md)* context | Pointer to **ArkUI_ContextHandle**.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. Check whether the passed parameters **env**, **value**, and **context** are valid. |

### OH_ArkUI_GetNodeContentFromNapiValue()

```c
int32_t OH_ArkUI_GetNodeContentFromNapiValue(napi_env env, napi_value value, ArkUI_NodeContentHandle* content)
```

**Description**

Obtains an **ArkUI_NodeContentHandle** object on the native side mapped from the **NodeContent** object created on the ArkTS side. This is applicable to scenarios where the native side needs to operate on or mount the **NodeContent** content on the ArkTS side.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| napi_env env | Pointer to the Node-API environment. |
| napi_value value | **NodeContent** object created on the ArkTS side.|
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md)* content | Pointer to the **ArkUI_NodeContentHandle**.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. Check whether the passed parameters **env**, **value**, and **content** are valid. |

### OH_ArkUI_GetDrawableDescriptorFromNapiValue()

```c
int32_t OH_ArkUI_GetDrawableDescriptorFromNapiValue(napi_env env, napi_value value, ArkUI_DrawableDescriptor** drawableDescriptor)
```

**Description**

Obtains an [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md) object on the native side mapped from the [DrawableDescriptor](arkui-ts/ts-basic-components-image.md#drawabledescriptor10) object created on the ArkTS side. This is applicable to scenarios where the native side needs to use an image resource description object on the ArkTS side.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| napi_env env | Pointer to the Node-API environment. |
| napi_value value | [DrawableDescriptor](arkui-ts/ts-basic-components-image.md#drawabledescriptor10) object created on the ArkTS side.|
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)** drawableDescriptor | Double pointer used to receive the **ArkUI_DrawableDescriptor** object.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. Check whether the passed parameters **env**, **value**, and **drawableDescriptor** are valid. |

### OH_ArkUI_GetDrawableDescriptorFromResourceNapiValue()

```c
int32_t OH_ArkUI_GetDrawableDescriptorFromResourceNapiValue(napi_env env, napi_value value, ArkUI_DrawableDescriptor** drawableDescriptor)
```

**Description**

Converts a resource object obtained through **$r()** on the ArkTS side into an [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md) object usable on the native side. This is applicable to scenarios where the native side needs to use an ArkTS resource object as an image resource descriptor.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| napi_env env | Pointer to the Node-API environment. |
| napi_value value | Resource object obtained by **$r()** on the ArkTS side. |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)** drawableDescriptor | Double pointer used to receive the **ArkUI_DrawableDescriptor** object.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. Check whether the passed parameters **env**, **value**, and **drawableDescriptor** are valid. |

### OH_ArkUI_GetNavigationId()

```c
ArkUI_ErrorCode OH_ArkUI_GetNavigationId(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the ID of the [Navigation](arkui-ts/ts-basic-components-navigation.md) component where the specified node is located.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.|
| char* buffer | Pointer to the buffer to which the obtained ID is written.|
| int32_t bufferSize | Buffer size.|
| int32_t* writeLength | Pointer to the length of the string actually written to the buffer if [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.                     Pointer to the minimum size of the buffer required to hold the target when [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>        Returns [ARKUI_ERROR_CODE_GET_INFO_FAILED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the information fails to be obtained, possibly because the current node is not mounted to the page.<br>        Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the data size exceeds the specified buffer size.|

### OH_ArkUI_GetNavDestinationName()

```c
ArkUI_ErrorCode OH_ArkUI_GetNavDestinationName(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the name of the [NavDestination](arkui-ts/ts-basic-components-navdestination.md) component where the specified node is located.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.|
| char* buffer | Pointer to the buffer to which the obtained name is written.|
| int32_t bufferSize | Buffer size.|
| int32_t* writeLength | Pointer to the length of the string actually written to the buffer if [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.                     Pointer to the minimum size of the buffer required to hold the target when [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>        Returns [ARKUI_ERROR_CODE_GET_INFO_FAILED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the information fails to be obtained, possibly because the current node is not mounted to the page.<br>        Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the specified buffer size is smaller than the minimum buffer size required to hold the target.|

### OH_ArkUI_GetNavStackLength()

```c
ArkUI_ErrorCode OH_ArkUI_GetNavStackLength(ArkUI_NodeHandle node, int32_t* length)
```

**Description**

Obtains the length of the **Navigation** stack where the specified node is located.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.|
| int32_t* length | Pointer to the length of the navigation stack. The result, if obtained successfully, is written back to this parameter.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>        Returns [ARKUI_ERROR_CODE_GET_INFO_FAILED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the information fails to be obtained, possibly because the current node is not mounted to the page.|

### OH_ArkUI_GetNavDestinationNameByIndex()

```c
ArkUI_ErrorCode OH_ArkUI_GetNavDestinationNameByIndex(ArkUI_NodeHandle node, int32_t index, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the name of the page in the navigation stack where the specified node is located based on the given index. The index starts from 0, which indicates the bottom of the stack.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.|
| int32_t index | Index of the target page in the navigation stack.|
| char* buffer | Pointer to the buffer to which the obtained name is written.|
| int32_t bufferSize | Buffer size.|
| int32_t* writeLength | Pointer to the length of the string actually written to the buffer if [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.                     Pointer to the minimum size of the buffer required to hold the target when [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_NODE_INDEX_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the index is invalid.<br>        Returns [ARKUI_ERROR_CODE_GET_INFO_FAILED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the information fails to be obtained, possibly because the current node is not mounted to the page.<br>        Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the specified buffer size is smaller than the minimum buffer size required to hold the target.|

### OH_ArkUI_GetNavDestinationId()

```c
ArkUI_ErrorCode OH_ArkUI_GetNavDestinationId(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the ID of the **NavDestination** component where the specified node is located.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.|
| char* buffer | Pointer to the buffer to which the obtained ID is written.|
| int32_t bufferSize | Buffer size.|
| int32_t* writeLength | Pointer to the length of the string actually written to the buffer if [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.                     Pointer to the minimum size of the buffer required to hold the target when [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>        Returns [ARKUI_ERROR_CODE_GET_INFO_FAILED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the information fails to be obtained, possibly because the current node is not mounted to the page.<br>        Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the data size exceeds the specified buffer size.|

### OH_ArkUI_GetNavDestinationState()

```c
ArkUI_ErrorCode OH_ArkUI_GetNavDestinationState(ArkUI_NodeHandle node, ArkUI_NavDestinationState* state)
```

**Description**

Obtains the state of the **NavDestination** component where the specified node is located.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.|
| [ArkUI_NavDestinationState](capi-navigation-router-h.md#arkui_navdestinationstate)* state | Pointer to the state of the **NavDestination** component. The result, if obtained successfully, is written back to this parameter.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>        Returns [ARKUI_ERROR_CODE_GET_INFO_FAILED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the information fails to be obtained, possibly because the current node is not mounted to the page.|

### OH_ArkUI_GetNavDestinationIndex()

```c
ArkUI_ErrorCode OH_ArkUI_GetNavDestinationIndex(ArkUI_NodeHandle node, int32_t* index)
```

**Description**

Obtains the index of the **NavDestination** component where the current node is located in the page stack.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.|
| int32_t* index | Pointer to the zero-based index.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>        Returns [ARKUI_ERROR_CODE_GET_INFO_FAILED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the information fails to be obtained, possibly because the current node is not mounted to the page.|

### OH_ArkUI_GetNavDestinationParam()

```c
napi_value OH_ArkUI_GetNavDestinationParam(ArkUI_NodeHandle node)
```

**Description**

Obtains the parameter of the **NavDestination** component where the specified node is located.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.|

**Return value**

| Type| Description|
| -- | -- |
| napi_value | Parameter object. Returns an empty value if the parameters do not exist or the specified node is null.|

### OH_ArkUI_GetRouterPageIndex()

```c
ArkUI_ErrorCode OH_ArkUI_GetRouterPageIndex(ArkUI_NodeHandle node, int32_t* index)
```

**Description**

Obtains the index of the [Router](arkts-apis-uicontext-router.md) page stack where the specified node is located.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.|
| int32_t* index | Pointer to the one-based index.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the specified node or the passed index is invalid.<br>Returns [ARKUI_ERROR_CODE_GET_INFO_FAILED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the information fails to be obtained, possibly because the current node is not mounted to the page.|

### OH_ArkUI_GetRouterPageName()

```c
ArkUI_ErrorCode OH_ArkUI_GetRouterPageName(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the name of the **Router** page where the specified node is located.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.|
| char* buffer | Pointer to the buffer to which the obtained name is written.|
| int32_t bufferSize | Buffer size.|
| int32_t* writeLength | Pointer to the length of the string actually written to the buffer if [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.                     Pointer to the minimum size of the buffer required to hold the target when [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>        Returns [ARKUI_ERROR_CODE_GET_INFO_FAILED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the information fails to be queried.<br>        Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the specified buffer size is smaller than the minimum buffer size required to hold the target.|

### OH_ArkUI_GetRouterPagePath()

```c
ArkUI_ErrorCode OH_ArkUI_GetRouterPagePath(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the path of the **Router** page where the specified node is located.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.|
| char* buffer | Pointer to the buffer to which the page path is written.|
| int32_t bufferSize | Buffer size.|
| int32_t* writeLength | Pointer to the length of the string actually written to the buffer if [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.                     Pointer to the minimum size of the buffer required to hold the target when [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>        Returns [ARKUI_ERROR_CODE_GET_INFO_FAILED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the information fails to be queried.<br>        Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the specified buffer size is smaller than the minimum buffer size required to hold the target.|

### OH_ArkUI_GetRouterPageState()

```c
ArkUI_ErrorCode OH_ArkUI_GetRouterPageState(ArkUI_NodeHandle node, ArkUI_RouterPageState* state)
```

**Description**

Obtains the status of the **Router** page where the specified node is located.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.|
| [ArkUI_RouterPageState](capi-navigation-router-h.md#arkui_routerpagestate)* state | Pointer to the status of the **Router** page. The result, if obtained successfully, is written back to this parameter.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>        Returns [ARKUI_ERROR_CODE_GET_INFO_FAILED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the information fails to be queried.|

### OH_ArkUI_GetRouterPageId()

```c
ArkUI_ErrorCode OH_ArkUI_GetRouterPageId(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the ID of the **Router** page where the specified node is located.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.|
| char* buffer | Pointer to the buffer to which the page ID is written.|
| int32_t bufferSize | Buffer size.|
| int32_t* writeLength | Pointer to the length of the string actually written to the buffer if [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.                     Pointer to the minimum size of the buffer required to hold the target when [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>        Returns [ARKUI_ERROR_CODE_GET_INFO_FAILED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the information fails to be queried.<br>        Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the data size exceeds the specified buffer size.|

### OH_ArkUI_InitModuleForArkTSEnv()

```c
ArkUI_ErrorCode OH_ArkUI_InitModuleForArkTSEnv(napi_env env)
```

**Description**

Initializes ArkUI-related APIs for the specified context environment. This is applicable to scenarios where the context environment needs to be initialized before the native side uses ArkUI-related APIs. This API must not be called on a non-UI thread; otherwise, the program will actively abort. After the specified context environment is initialized using this API, call [OH_ArkUI_NotifyArkTSEnvDestroy()](#oh_arkui_notifyarktsenvdestroy) to notify that the environment has been destroyed when the corresponding environment is destroyed.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| napi_env env | Pointer to the Node-API environment.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. The possible cause is that **env** is null or the trustlist setting fails. Verify that **env** is valid and try again.<br>         Returns [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a C API initialization error occurs. Verify that the current running environment supports ArkUI native APIs and try again. |

### OH_ArkUI_NotifyArkTSEnvDestroy()

```c
void OH_ArkUI_NotifyArkTSEnvDestroy(napi_env env)
```

**Description**

Notifies that the specified context environment has been destroyed. This is applicable to scenarios where the native side synchronously cleans up related states when the ArkTS context environment is destroyed. After the context environment is initialized using [OH_ArkUI_InitModuleForArkTSEnv()](#oh_arkui_initmoduleforarktsenv), this API should be called when the environment is destroyed. This API must not be called on a non-UI thread; otherwise, the program will actively abort.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| napi_env env | Pointer to the Node-API environment.|

### OH_ArkUI_PostFrameCallback()

```c
int32_t OH_ArkUI_PostFrameCallback(ArkUI_ContextHandle uiContext, void* userData, void (*callback)(uint64_t nanoTimestamp, uint32_t frameCount, void* userData))
```

**Description**

Registers a callback to be executed when the next frame is rendered. This is applicable to scenarios where the native side performs UI refresh or rendering-related tasks in the next frame. This API must not be called on a non-UI thread; otherwise, the program will actively abort.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | Pointer to the [UIContext](arkui-ts/ts-custom-component-api.md#uicontext) object, which is used to bind an instance.|
| void* userData | Pointer to the custom event parameter, which is passed in the callback when the event is triggered.|
| void (\*callback)(uint64_t nanoTimestamp, uint32_t frameCount, void\* userData) | Pointer to the custom callback with the signature void **(\*callback)(uint64_t nanoTimestamp, uint32_t frameCount, void\* userData)**, which is executed when the next frame is rendered. **nanoTimestamp** indicates the timestamp of the frame signal, **frameCount** indicates the frame number, and **userData** indicates the custom data passed in during registration and carried back when the callback is triggered. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a C API initialization error occurs. Ensure that the ArkUI native API running environment has been initialized and try again.<br>         Returns [ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the **UIContext** object is invalid. Check whether **UIContext** is null or invalid.<br>         Returns [ARKUI_ERROR_CODE_CALLBACK_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the callback is invalid. Check whether callback is null. |

### OH_ArkUI_PostIdleCallback()

```c
int32_t OH_ArkUI_PostIdleCallback(ArkUI_ContextHandle uiContext, void* userData, void (*callback)(uint64_t nanoTimeLeft, uint32_t frameCount, void* userData))
```

**Description**

Registers a callback. This is applicable to scenarios where the native side needs to use the idle time between frames to process non-urgent tasks. After the next frame is rendered, if the remaining time before the next VSync signal following that frame is greater than 1 ms, the callback will be executed; if the remaining time is less than 1 ms, the callback will be postponed until the remaining time after a subsequent frame is rendered is greater than 1 ms. If there is no next frame currently, the next frame will be requested automatically. This API must not be called on a non-UI thread; otherwise, the program will actively abort.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | **UIContext** object handle, which is used to bind an instance.|
| void* userData | Pointer to the custom event parameter, which is passed in the callback when the custom callback is triggered.|
| void (\*callback)(uint64_t nanoTimeLeft, uint32_t frameCount, void\* userData) | Pointer to the custom callback with the signature **void (\*callback)(uint64_t nanoTimeLeft, uint32_t frameCount, void\* userData)**, which is executed after the next frame is rendered when the remaining time is greater than 1 ms. **nanoTimeLeft** indicates the remaining time before the deadline of the current frame, **frameCount** indicates the frame number, and **userData** indicates the custom data passed in during registration and carried back when the callback is triggered. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a C API initialization error occurs. Ensure that the ArkUI native API running environment has been initialized and try again.<br>         Returns [ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the **UIContext** object is invalid. Check whether **UIContext** is null or invalid.<br>         Returns [ARKUI_ERROR_CODE_CALLBACK_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the callback is invalid. Check whether callback is null. |

### OH_ArkUI_EnableEventPassthrough()

```c
ArkUI_ErrorCode OH_ArkUI_EnableEventPassthrough(ArkUI_ContextHandle uiContext, bool enabled, ArkUI_RawInputEventType type)
```

**Description**

Enables or disables event passthrough. Event passthrough indicates that an event is directly delivered to a component without [resampling](../../ui/arkts-interaction-development-guide-touch-screen.md#resampling-and-historical-points) during event distribution.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | [UIContext](arkts-apis-uicontext-uicontext.md) object, which is used to bind an instance.|
| bool enabled | Whether to enable event passthrough. **true** to enable; **false** otherwise.|
| [ArkUI_RawInputEventType](capi-common-attributes-h.md#arkui_rawinputeventtype) type | Raw input event type ([ArkUI_RawInputEventType](capi-common-attributes-h.md#arkui_rawinputeventtype)) for enabling or disabling event passthrough.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the UIContext object is invalid.|