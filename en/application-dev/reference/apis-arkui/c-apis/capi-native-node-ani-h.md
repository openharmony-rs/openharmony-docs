# native_node_ani.h

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
| [int32_t OH_ArkUI_NativeModule_GetNodeHandleFromAniValue(ani_env* env, ani_object frameNode, ArkUI_NodeHandle* handle)](#oh_arkui_nativemodule_getnodehandlefromanivalue) | Obtains a <b>FrameNode</b> object on the ArkTS side and maps it to an <b>ArkUI_NodeHandle</b> object on the native side. |
| [int32_t OH_ArkUI_NativeModule_GetContextFromAniValue(ani_env* env, ani_object context, ArkUI_ContextHandle* handle)](#oh_arkui_nativemodule_getcontextfromanivalue) | Obtains a <b>UIContext</b> object on the ArkTS side and maps it to an <b>ArkUI_ContextHandle</b> object on the native side. |
| [int32_t OH_ArkUI_NativeModule_GetNodeContentFromAniValue(ani_env *env, ani_object nodeContent, ArkUI_NodeContentHandle *content)](#oh_arkui_nativemodule_getnodecontentfromanivalue) | Obtains a <b>NodeContent</b> object on the ArkTS side and maps it to an <b>ArkUI_NodeContentHandle</b> object on the native side. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_GetNavDestinationAniParam(ArkUI_NodeHandle node, ani_env* env, ani_value* param)](#oh_arkui_nativemodule_getnavdestinationaniparam) | Obtains the parameters of the NavDestination component where the node is located. |
| [int32_t OH_ArkUI_NativeModule_GetDrawableDescriptorFromAniValue(ani_env *env, ani_object drawable, ArkUI_DrawableDescriptor **drawableDescriptor)](#oh_arkui_nativemodule_getdrawabledescriptorfromanivalue) | Obtains a <b>DrawableDescriptor</b> object on the ArkTS side and maps it to an <b>ArkUI_DrawableDescriptro</b> object on the native side. |
| [int32_t OH_ArkUI_NativeModule_GetDrawableDescriptorFromResourceAniValue(ani_env *env, ani_object resource, ArkUI_DrawableDescriptor **drawableDescriptor)](#oh_arkui_nativemodule_getdrawabledescriptorfromresourceanivalue) | Obtains a <b>Resource</b> object on the ArkTS side and maps it to an <b>ArkUI_DrawableDescriptro</b> object on the native side. |

## Function description

### OH_ArkUI_NativeModule_GetNodeHandleFromAniValue()

```c
int32_t OH_ArkUI_NativeModule_GetNodeHandleFromAniValue(ani_env* env, ani_object frameNode, ArkUI_NodeHandle* handle)
```

**Description**

Obtains a <b>FrameNode</b> object on the ArkTS side and maps it to an <b>ArkUI_NodeHandle</b> object on the native side.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| ani_env* env | Indicates the ANI environment pointer. |
| ani_object frameNode | Indicates the <b>FrameNode</b> object created on the ArkTS side. |
| ArkUI_NodeHandle* handle | Indicates the pointer to the <b>ArkUI_NodeHandle</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NativeModule_GetContextFromAniValue()

```c
int32_t OH_ArkUI_NativeModule_GetContextFromAniValue(ani_env* env, ani_object context, ArkUI_ContextHandle* handle)
```

**Description**

Obtains a <b>UIContext</b> object on the ArkTS side and maps it to an <b>ArkUI_ContextHandle</b> object on the native side.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| ani_env* env | ndicates the ANI environment pointer. |
| ani_object context | Indicates the <b>UIContext</b> object created on the ArkTS side. |
| ArkUI_ContextHandle* handle | Indicates the pointer to the <b>ArkUI_ContextHandle</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NativeModule_GetNodeContentFromAniValue()

```c
int32_t OH_ArkUI_NativeModule_GetNodeContentFromAniValue(ani_env *env, ani_object nodeContent, ArkUI_NodeContentHandle *content)
```

**Description**

Obtains a <b>NodeContent</b> object on the ArkTS side and maps it to an <b>ArkUI_NodeContentHandle</b> object on the native side.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| ani_env *env | Indicates the ANI environment pointer. |
| ani_object nodeContent | Indicates the <b>NodeContent</b> object created on the ArkTS side. |
| ArkUI_NodeContentHandle *content | Indicates the pointer to the <b>ArkUI_NodeContentHandle</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.           Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NativeModule_GetNavDestinationAniParam()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_GetNavDestinationAniParam(ArkUI_NodeHandle node, ani_env* env, ani_value* param)
```

**Description**

Obtains the parameters of the NavDestination component where the node is located.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | The node. |
| ani_env* env | The ANI environment. |
| ani_value* param | The parameter of NavDestination. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the error code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.<br>        Returns {@link ARKUI_ERROR_CODE_GET_INFO_FAILED} if query information failed,          this may be because the node is not in NavDestination. |

### OH_ArkUI_NativeModule_GetDrawableDescriptorFromAniValue()

```c
int32_t OH_ArkUI_NativeModule_GetDrawableDescriptorFromAniValue(ani_env *env, ani_object drawable, ArkUI_DrawableDescriptor **drawableDescriptor)
```

**Description**

Obtains a <b>DrawableDescriptor</b> object on the ArkTS side and maps it to an <b>ArkUI_DrawableDescriptro</b> object on the native side.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| ani_env *env | Indicates the ANI environment pointer. |
| ani_object drawable | Indicates the <b>DrawableDescriptor</b> object created on the ArkTS side. |
| ArkUI_DrawableDescriptor **drawableDescriptor | Indicates the pointer to the <b>ArkUI_DrawableDescriptro</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NativeModule_GetDrawableDescriptorFromResourceAniValue()

```c
int32_t OH_ArkUI_NativeModule_GetDrawableDescriptorFromResourceAniValue(ani_env *env, ani_object resource, ArkUI_DrawableDescriptor **drawableDescriptor)
```

**Description**

Obtains a <b>Resource</b> object on the ArkTS side and maps it to an <b>ArkUI_DrawableDescriptro</b> object on the native side.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| ani_env *env | Indicates the ANI environment pointer. |
| ani_object resource | Indicates the <b>Resource</b> object created on the ArkTS side. |
| ArkUI_DrawableDescriptor **drawableDescriptor | Indicates the pointer to the <b>ArkUI_DrawableDescriptro</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |


