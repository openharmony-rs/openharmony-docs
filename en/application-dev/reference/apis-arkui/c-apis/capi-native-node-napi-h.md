# native_node_napi.h

## Overview

Declares APIs for converting <b>FrameNode</b> objects on the ArkTS side to <b>ArkUI_NodeHandle</b> objects on the native side.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [int32_t OH_ArkUI_GetNodeHandleFromNapiValue(napi_env env, napi_value frameNode, ArkUI_NodeHandle* handle)](#oh_arkui_getnodehandlefromnapivalue) | Obtains a <b>FrameNode</b> object on the ArkTS side and maps it to an <b>ArkUI_NodeHandle</b> object on the native side. |
| [int32_t OH_ArkUI_GetContextFromNapiValue(napi_env env, napi_value value, ArkUI_ContextHandle* context)](#oh_arkui_getcontextfromnapivalue) | Obtains a <b>UIContext</b> object on the ArkTS side and maps it to an <b>ArkUI_ContextHandle</b> object on the native side. |
| [int32_t OH_ArkUI_GetNodeContentFromNapiValue(napi_env env, napi_value value, ArkUI_NodeContentHandle* content)](#oh_arkui_getnodecontentfromnapivalue) | Obtains a <b>NodeContent</b> object on the ArkTS side and maps it to an <b>ArkUI_NodeContentHandle</b> object on the native side. |
| [int32_t OH_ArkUI_GetDrawableDescriptorFromNapiValue(napi_env env, napi_value value, ArkUI_DrawableDescriptor** drawableDescriptor)](#oh_arkui_getdrawabledescriptorfromnapivalue) | Obtains a <b>DrawableDescriptor</b> object on the ArkTS side and maps it to an <b>ArkUI_DrawableDescriptor</b> object on the native side. |
| [int32_t OH_ArkUI_GetDrawableDescriptorFromResourceNapiValue(napi_env env, napi_value value, ArkUI_DrawableDescriptor** drawableDescriptor)](#oh_arkui_getdrawabledescriptorfromresourcenapivalue) | Obtains a <b>Resource</b> object on the ArkTS side and maps it to an <b>ArkUI_DrawableDescriptor</b> object on the native side. |
| [ArkUI_ErrorCode OH_ArkUI_GetNavigationId(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_getnavigationid) | Obtain the ID of the Navigation component where the node is located. |
| [ArkUI_ErrorCode OH_ArkUI_GetNavDestinationName(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_getnavdestinationname) | Obtain the name of the NavDestination component where the node is located. |
| [ArkUI_ErrorCode OH_ArkUI_GetNavStackLength(ArkUI_NodeHandle node, int32_t* length)](#oh_arkui_getnavstacklength) | Based on the given index value, obtain the length of the Navigation stack where the node is located. |
| [ArkUI_ErrorCode OH_ArkUI_GetNavDestinationNameByIndex(ArkUI_NodeHandle node, int32_t index, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_getnavdestinationnamebyindex) | Based on the given index value, obtain the page name of the corresponding position in the navigation stack where the node is located. Index values are counted from 0, with 0 being the bottom of the stack. |
| [ArkUI_ErrorCode OH_ArkUI_GetNavDestinationId(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_getnavdestinationid) | Obtain the ID of the NavDestination component where the node is located. |
| [ArkUI_ErrorCode OH_ArkUI_GetNavDestinationState(ArkUI_NodeHandle node, ArkUI_NavDestinationState* state)](#oh_arkui_getnavdestinationstate) | Obtain the state of the NavDestination component where the node is located. |
| [ArkUI_ErrorCode OH_ArkUI_GetNavDestinationIndex(ArkUI_NodeHandle node, int32_t* index)](#oh_arkui_getnavdestinationindex) | Obtain the index of the NavDestination component on the Navigation stack where the node is located. |
| [napi_value OH_ArkUI_GetNavDestinationParam(ArkUI_NodeHandle node)](#oh_arkui_getnavdestinationparam) | Obtain the parameters of the NavDestination component where the node is located. |
| [ArkUI_ErrorCode OH_ArkUI_GetRouterPageIndex(ArkUI_NodeHandle node, int32_t* index)](#oh_arkui_getrouterpageindex) | Obtain the index of the page where the node resides in the Router page stack. |
| [ArkUI_ErrorCode OH_ArkUI_GetRouterPageName(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_getrouterpagename) | Obtain the name of the page where the node is located. |
| [ArkUI_ErrorCode OH_ArkUI_GetRouterPagePath(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_getrouterpagepath) | Obtain the path of the page where the node is located. |
| [ArkUI_ErrorCode OH_ArkUI_GetRouterPageState(ArkUI_NodeHandle node, ArkUI_RouterPageState* state)](#oh_arkui_getrouterpagestate) | Obtain the state of the page where the node is located. |
| [ArkUI_ErrorCode OH_ArkUI_GetRouterPageId(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_getrouterpageid) | Obtain the ID of the page where the node is located. |
| [int32_t OH_ArkUI_PostFrameCallback(ArkUI_ContextHandle uiContext, void* userData, void (\*callback)(uint64_t nanoTimestamp, uint32_t frameCount, void* userData))](#oh_arkui_postframecallback) | Register a callback to be executed when rendering in the next frame. Cannot be called on the non-UI thread. Checking for non-UI thread calls will abort. |
| [ArkUI_ErrorCode OH_ArkUI_InitModuleForArkTSEnv(napi_env env)](#oh_arkui_initmoduleforarktsenv) | Initialize the ArkTS method for the specified env environment. Cannot be called on the non-UI thread. Checking for non-UI thread calls will abort. |
| [void OH_ArkUI_NotifyArkTSEnvDestroy(napi_env env)](#oh_arkui_notifyarktsenvdestroy) | Notifies that the specified context environment has been destroyed. This function must not be called from a non-UI thread; otherwise, the program will actively abort. |
| [int32_t OH_ArkUI_PostIdleCallback(ArkUI_ContextHandle uiContext, void* userData, void (\*callback)(uint64_t nanoTimeLeft, uint32_t frameCount, void* userData))](#oh_arkui_postidlecallback) | Register a callback to be executed at the end of the next idle frame. If there is no next frame, will request one automatically. |
| [ArkUI_ErrorCode OH_ArkUI_EnableEventPassthrough(ArkUI_ContextHandle uiContext, bool enabled, ArkUI_RawInputEventType type)](#oh_arkui_enableeventpassthrough) | Enables or disables event passthrough. Event passthrough indicates that an event is directly delivered to a component without resampling during event distribution. |

## Function description

### OH_ArkUI_GetNodeHandleFromNapiValue()

```c
int32_t OH_ArkUI_GetNodeHandleFromNapiValue(napi_env env, napi_value frameNode, ArkUI_NodeHandle* handle)
```

**Description**

Obtains a <b>FrameNode</b> object on the ArkTS side and maps it to an <b>ArkUI_NodeHandle</b> object on the native side.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates the NAPI environment pointer. |
| napi_value frameNode | Indicates the <b>FrameNode</b> object created on the ArkTS side. |
| ArkUI_NodeHandle* handle | Indicates the pointer to the <b>ArkUI_NodeHandle</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_GetContextFromNapiValue()

```c
int32_t OH_ArkUI_GetContextFromNapiValue(napi_env env, napi_value value, ArkUI_ContextHandle* context)
```

**Description**

Obtains a <b>UIContext</b> object on the ArkTS side and maps it to an <b>ArkUI_ContextHandle</b> object on the native side.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates the NAPI environment pointer. |
| napi_value value | Indicates the <b>UIContext</b> object created on the ArkTS side. |
| ArkUI_ContextHandle* context | Indicates the pointer to the <b>ArkUI_ContextHandle</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_GetNodeContentFromNapiValue()

```c
int32_t OH_ArkUI_GetNodeContentFromNapiValue(napi_env env, napi_value value, ArkUI_NodeContentHandle* content)
```

**Description**

Obtains a <b>NodeContent</b> object on the ArkTS side and maps it to an <b>ArkUI_NodeContentHandle</b> object on the native side.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates the NAPI environment pointer. |
| napi_value value | Indicates the <b>NodeContent</b> object created on the ArkTS side. |
| ArkUI_NodeContentHandle* content | Indicates the pointer to the <b>ArkUI_NodeContentHandle</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.           Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.           Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_GetDrawableDescriptorFromNapiValue()

```c
int32_t OH_ArkUI_GetDrawableDescriptorFromNapiValue(napi_env env, napi_value value, ArkUI_DrawableDescriptor** drawableDescriptor)
```

**Description**

Obtains a <b>DrawableDescriptor</b> object on the ArkTS side and maps it to an <b>ArkUI_DrawableDescriptor</b> object on the native side.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates the NAPI environment pointer. |
| napi_value value | Indicates the <b>DrawableDescriptor</b> object created on the ArkTS side. |
| ArkUI_DrawableDescriptor** drawableDescriptor | Indicates the pointer to the <b>ArkUI_DrawableDescriptor</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_GetDrawableDescriptorFromResourceNapiValue()

```c
int32_t OH_ArkUI_GetDrawableDescriptorFromResourceNapiValue(napi_env env, napi_value value, ArkUI_DrawableDescriptor** drawableDescriptor)
```

**Description**

Obtains a <b>Resource</b> object on the ArkTS side and maps it to an <b>ArkUI_DrawableDescriptor</b> object on the native side.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates the NAPI environment pointer. |
| napi_value value | Indicates the <b>Resource</b> object created on the ArkTS side. |
| ArkUI_DrawableDescriptor** drawableDescriptor | Indicates the pointer to the <b>ArkUI_DrawableDescriptor</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_GetNavigationId()

```c
ArkUI_ErrorCode OH_ArkUI_GetNavigationId(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtain the ID of the Navigation component where the node is located.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | The node. |
| char* buffer | The buffer to which NavigationID writes to the memory, memory space needs to be allocated by the developer. |
| int32_t bufferSize | The buffer size |
| int32_t* writeLength | Indicates the string length actually written to the buffer when returning [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode). Indicates the minimum buffer size that can accommodate the target when [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | The error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the node, buffer or writeLength is null.          [ARKUI_ERROR_CODE_GET_INFO_FAILED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if query information failed,          this may be because the node is not in Navigation.          [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) If the buffer size is less than the minimum buffer size. |

### OH_ArkUI_GetNavDestinationName()

```c
ArkUI_ErrorCode OH_ArkUI_GetNavDestinationName(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtain the name of the NavDestination component where the node is located.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | The node. |
| char* buffer | The buffer to which NavDestination name writes to the memory, memory space needs to be allocated by the developer. |
| int32_t bufferSize | The buffer size |
| int32_t* writeLength | Indicates the string length actually written to the buffer when returning [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode). Indicates the minimum buffer size that can accommodate the target when [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | The error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the node, buffer or writeLength is null.          [ARKUI_ERROR_CODE_GET_INFO_FAILED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if query information failed,          this may be because the node is not in Navigation.          [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) If the buffer size is less than the minimum buffer size. |

### OH_ArkUI_GetNavStackLength()

```c
ArkUI_ErrorCode OH_ArkUI_GetNavStackLength(ArkUI_NodeHandle node, int32_t* length)
```

**Description**

Based on the given index value, obtain the length of the Navigation stack where the node is located.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | The node. |
| int32_t* length | The length of the stack. After the operation succeeds, the result is written back to this parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | The error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the node or length is null.          [ARKUI_ERROR_CODE_GET_INFO_FAILED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if query information failed,          this may be because the node is not in Navigation. |

### OH_ArkUI_GetNavDestinationNameByIndex()

```c
ArkUI_ErrorCode OH_ArkUI_GetNavDestinationNameByIndex(ArkUI_NodeHandle node, int32_t index, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Based on the given index value, obtain the page name of the corresponding position in the navigation stack where the node is located. Index values are counted from 0, with 0 being the bottom of the stack.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | The node. |
| int32_t index | The index of the NavDestination in the stack is queried. |
| char* buffer | The buffer to which NavDestination index writes to the memory, memory space needs to be allocated by the developer. |
| int32_t bufferSize | The buffer size |
| int32_t* writeLength | Indicates the string length actually written to the buffer when returning [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode). Indicates the minimum buffer size that can accommodate the target when [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | The error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the node, buffer or writeLength is null.          [ARKUI_ERROR_CODE_NODE_INDEX_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if index is an invalid value.          [ARKUI_ERROR_CODE_GET_INFO_FAILED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if query information failed,          this may be because the node is not in Navigation.          [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) If the buffer size is less than the minimum buffer size. |

### OH_ArkUI_GetNavDestinationId()

```c
ArkUI_ErrorCode OH_ArkUI_GetNavDestinationId(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtain the ID of the NavDestination component where the node is located.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | The node. |
| char* buffer | The buffer to which NavDestination ID writes to the memory, memory space needs to be allocated by the developer. |
| int32_t bufferSize | The buffer size |
| int32_t* writeLength | Indicates the string length actually written to the buffer when returning [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode). Indicates the minimum buffer size that can accommodate the target when [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | The error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the node, buffer or writeLength is null.          [ARKUI_ERROR_CODE_GET_INFO_FAILED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if query information failed,          this may be because the node is not in Navigation.          [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) If the buffer size is less than the minimum buffer size. |

### OH_ArkUI_GetNavDestinationState()

```c
ArkUI_ErrorCode OH_ArkUI_GetNavDestinationState(ArkUI_NodeHandle node, ArkUI_NavDestinationState* state)
```

**Description**

Obtain the state of the NavDestination component where the node is located.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | The node. |
| ArkUI_NavDestinationState* state | The state value of NavDestination is written back into this parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | The error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the node or state is null.          [ARKUI_ERROR_CODE_GET_INFO_FAILED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if query information failed,          this may be because the node is not in Navigation. |

### OH_ArkUI_GetNavDestinationIndex()

```c
ArkUI_ErrorCode OH_ArkUI_GetNavDestinationIndex(ArkUI_NodeHandle node, int32_t* index)
```

**Description**

Obtain the index of the NavDestination component on the Navigation stack where the node is located.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | The node. |
| int32_t* index | Index value, counted from 0. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | The error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the node or index is null.          [ARKUI_ERROR_CODE_GET_INFO_FAILED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if query information failed,          this may be because the node is not in Navigation. |

### OH_ArkUI_GetNavDestinationParam()

```c
napi_value OH_ArkUI_GetNavDestinationParam(ArkUI_NodeHandle node)
```

**Description**

Obtain the parameters of the NavDestination component where the node is located.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | The node. |

**Returns**:

| Type | Description |
| -- | -- |
| napi_value | The parameters.          If a null pointer is returned, it may be because the node is empty or the parameters does not exist. |

### OH_ArkUI_GetRouterPageIndex()

```c
ArkUI_ErrorCode OH_ArkUI_GetRouterPageIndex(ArkUI_NodeHandle node, int32_t* index)
```

**Description**

Obtain the index of the page where the node resides in the Router page stack.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | The node. |
| int32_t* index | Index value, counted from 1. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | The error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the node or index is null.          [ARKUI_ERROR_CODE_GET_INFO_FAILED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if query information failed,          this may be because the node is not in RouterPage. |

### OH_ArkUI_GetRouterPageName()

```c
ArkUI_ErrorCode OH_ArkUI_GetRouterPageName(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtain the name of the page where the node is located.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | The node. |
| char* buffer | The buffer to which page name writes to the memory, memory space needs to be allocated by the developer. |
| int32_t bufferSize | The buffer size |
| int32_t* writeLength | Indicates the string length actually written to the buffer when returning [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode). Indicates the minimum buffer size that can accommodate the target when [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | The error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the node, buffer or writeLength is null.          [ARKUI_ERROR_CODE_GET_INFO_FAILED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if query information failed,          this may be because the node is not in RouterPage.          [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) If the buffer size is less than the minimum buffer size. |

### OH_ArkUI_GetRouterPagePath()

```c
ArkUI_ErrorCode OH_ArkUI_GetRouterPagePath(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtain the path of the page where the node is located.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | The node. |
| char* buffer | The buffer to which page path writes to the memory, memory space needs to be allocated by the developer. |
| int32_t bufferSize | The buffer size |
| int32_t* writeLength | Indicates the string length actually written to the buffer when returning [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode). Indicates the minimum buffer size that can accommodate the target when [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | The error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the node, buffer or writeLength is null.          [ARKUI_ERROR_CODE_GET_INFO_FAILED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if query information failed,          this may be because the node is not in RouterPage.          [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) If the buffer size is less than the minimum buffer size. |

### OH_ArkUI_GetRouterPageState()

```c
ArkUI_ErrorCode OH_ArkUI_GetRouterPageState(ArkUI_NodeHandle node, ArkUI_RouterPageState* state)
```

**Description**

Obtain the state of the page where the node is located.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | The node. |
| ArkUI_RouterPageState* state | The state value of the page is written back to this parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | The error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the node or state is null.          [ARKUI_ERROR_CODE_GET_INFO_FAILED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if query information failed,          this may be because the node is not in RouterPage. |

### OH_ArkUI_GetRouterPageId()

```c
ArkUI_ErrorCode OH_ArkUI_GetRouterPageId(ArkUI_NodeHandle node, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtain the ID of the page where the node is located.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | The node. |
| char* buffer | The buffer to which page ID writes to the memory, memory space needs to be allocated by the developer. |
| int32_t bufferSize | The buffer size |
| int32_t* writeLength | Indicates the string length actually written to the buffer when returning [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode). Indicates the minimum buffer size that can accommodate the target when [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | The error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the node, buffer or writeLength is null.          [ARKUI_ERROR_CODE_GET_INFO_FAILED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if query information failed,          this may be because the node is not in RouterPage.          [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) If the buffer size is less than the minimum buffer size. |

### OH_ArkUI_PostFrameCallback()

```c
int32_t OH_ArkUI_PostFrameCallback(ArkUI_ContextHandle uiContext, void* userData, void (*callback)(uint64_t nanoTimestamp, uint32_t frameCount, void* userData))
```

**Description**

Register a callback to be executed when rendering in the next frame. Cannot be called on the non-UI thread. Checking for non-UI thread calls will abort.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ContextHandle uiContext | ArkUI_ContextHandle. |
| void\* userData | Indicates the custom data to be saved. |
| void (\*callback)(uint64_t nanoTimestamp | Custom callback function. |
| void (\*callback)(uint64_t nanoTimestamp | Timestamp of frame signal. |
| uint32_t frameCount | Frame count. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the CAPI init error.          Returns [ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the uiContext is invalid.          Returns [ARKUI_ERROR_CODE_CALLBACK_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the callback function is invalid. |

### OH_ArkUI_InitModuleForArkTSEnv()

```c
ArkUI_ErrorCode OH_ArkUI_InitModuleForArkTSEnv(napi_env env)
```

**Description**

Initialize the ArkTS method for the specified env environment. Cannot be called on the non-UI thread. Checking for non-UI thread calls will abort.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | napi environment pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | The error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if env is null or failed to set the whitelist.          [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the CAPI init error. |

### OH_ArkUI_NotifyArkTSEnvDestroy()

```c
void OH_ArkUI_NotifyArkTSEnvDestroy(napi_env env)
```

**Description**

Notifies that the specified context environment has been destroyed. This function must not be called from a non-UI thread; otherwise, the program will actively abort.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Pointer to the Node-API environment. |

### OH_ArkUI_PostIdleCallback()

```c
int32_t OH_ArkUI_PostIdleCallback(ArkUI_ContextHandle uiContext, void* userData, void (*callback)(uint64_t nanoTimeLeft, uint32_t frameCount, void* userData))
```

**Description**

Register a callback to be executed at the end of the next idle frame. If there is no next frame, will request one automatically.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ContextHandle uiContext | ArkUI_ContextHandle. |
| void\* userData | Indicates the custom data to be saved. |
| void (\*callback)(uint64_t nanoTimeLeft | Custom callback function. |
| void (\*callback)(uint64_t nanoTimeLeft | Time remaining until the end of the current frame. |
| uint32_t frameCount | Frame count. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the CAPI init error.          Returns [ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the uiContext is invalid.          Returns [ARKUI_ERROR_CODE_CALLBACK_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the callback function is invalid. |

### OH_ArkUI_EnableEventPassthrough()

```c
ArkUI_ErrorCode OH_ArkUI_EnableEventPassthrough(ArkUI_ContextHandle uiContext, bool enabled, ArkUI_RawInputEventType type)
```

**Description**

Enables or disables event passthrough. Event passthrough indicates that an event is directly delivered to a component without resampling during event distribution.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle uiContext | UIContext object used to bind the instance. |
| bool enabled | Whether to enable event passthrough. <b>true</b>: enable; <b>false</b>: disable (default value). |
| ArkUI_RawInputEventType type | Raw input event type [ArkUI_RawInputEventType](capi-common-attributes-h.md#arkui_rawinputeventtype) for enabling or disabling event passthrough. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the UIContext object is invalid. |


