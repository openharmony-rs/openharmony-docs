# native_node_ani.h

## 概述

提供ArkTS1.2的FrameNode转换NodeHandle的方式。

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 23

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [int32_t OH_ArkUI_NativeModule_GetNodeHandleFromAniValue(ani_env* env, ani_object frameNode, ArkUI_NodeHandle* handle)](#oh_arkui_nativemodule_getnodehandlefromanivalue) | 获取ArkTS侧创建的FrameNode节点对象映射到Native侧的ArkUI_NodeHandle。 |
| [int32_t OH_ArkUI_NativeModule_GetContextFromAniValue(ani_env* env, ani_object context, ArkUI_ContextHandle* handle)](#oh_arkui_nativemodule_getcontextfromanivalue) | 获取ArkTS侧创建的UIContext对象映射到Native侧的ArkUI_ContextHandle。 |
| [int32_t OH_ArkUI_NativeModule_GetNodeContentFromAniValue(ani_env *env, ani_object nodeContent, ArkUI_NodeContentHandle *content)](#oh_arkui_nativemodule_getnodecontentfromanivalue) | 获取ArkTS侧创建的NodeContent对象映射到Native侧的ArkUI_NodeContentHandle。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_GetNavDestinationAniParam(ArkUI_NodeHandle node, ani_env* env, ani_value* param)](#oh_arkui_nativemodule_getnavdestinationaniparam) | 获取指定节点所在的NavDestination页面的参数。 |
| [int32_t OH_ArkUI_NativeModule_GetDrawableDescriptorFromAniValue(ani_env *env, ani_object drawable, ArkUI_DrawableDescriptor **drawableDescriptor)](#oh_arkui_nativemodule_getdrawabledescriptorfromanivalue) | 获取ArkTS侧的<b>DrawableDescriptor</b>对象，并将其映射到Native侧的<b>ArkUI_DrawableDescriptor</b>对象。 |
| [int32_t OH_ArkUI_NativeModule_GetDrawableDescriptorFromResourceAniValue(ani_env *env, ani_object resource, ArkUI_DrawableDescriptor **drawableDescriptor)](#oh_arkui_nativemodule_getdrawabledescriptorfromresourceanivalue) | 获取ArkTS侧的<b>Resource</b>对象，并将其映射到Native侧的<b>ArkUI_DrawableDescriptor</b>对象。 |

## 函数说明

### OH_ArkUI_NativeModule_GetNodeHandleFromAniValue()

```c
int32_t OH_ArkUI_NativeModule_GetNodeHandleFromAniValue(ani_env* env, ani_object frameNode, ArkUI_NodeHandle* handle)
```

**描述**

获取ArkTS侧创建的FrameNode节点对象映射到Native侧的ArkUI_NodeHandle。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ani_env* env | ANI的环境指针。 |
| ani_object frameNode | ArkTS侧创建的FrameNode对象。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)* handle | ArkUI_NodeHandle指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>     <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>     <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_GetContextFromAniValue()

```c
int32_t OH_ArkUI_NativeModule_GetContextFromAniValue(ani_env* env, ani_object context, ArkUI_ContextHandle* handle)
```

**描述**

获取ArkTS侧创建的UIContext对象映射到Native侧的ArkUI_ContextHandle。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ani_env* env | ANI的环境指针。 |
| ani_object context | ArkTS侧创建的UIContext对象。 |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md)* handle | ArkUI_ContextHandle指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>     <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>     <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_GetNodeContentFromAniValue()

```c
int32_t OH_ArkUI_NativeModule_GetNodeContentFromAniValue(ani_env *env, ani_object nodeContent, ArkUI_NodeContentHandle *content)
```

**描述**

获取ArkTS侧创建的NodeContent对象映射到Native侧的ArkUI_NodeContentHandle。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ani_env *env | ANI的环境指针。 |
| ani_object nodeContent | ArkTS侧创建的NodeContent对象。 |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) *content | ArkUI_NodeContentHandle指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>     <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>     <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_GetNavDestinationAniParam()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_GetNavDestinationAniParam(ArkUI_NodeHandle node, ani_env* env, ani_value* param)
```

**描述**

获取指定节点所在的NavDestination页面的参数。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 指定的节点。 |
| ani_env* env | ANI的环境指针。 |
| ani_value* param | 返回的页面参数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 错误码。<br>     <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>     <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>     <br>[ARKUI_ERROR_CODE_GET_INFO_FAILED](capi-native-type-h.md#arkui_errorcode) 查询页面参数信息失败。 |

### OH_ArkUI_NativeModule_GetDrawableDescriptorFromAniValue()

```c
int32_t OH_ArkUI_NativeModule_GetDrawableDescriptorFromAniValue(ani_env *env, ani_object drawable, ArkUI_DrawableDescriptor **drawableDescriptor)
```

**描述**

获取ArkTS侧的<b>DrawableDescriptor</b>对象，并将其映射到Native侧的<b>ArkUI_DrawableDescriptor</b>对象。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ani_env *env | 表示ANI环境指针。 |
| ani_object drawable | 表示在ArkTS侧创建的<b>DrawableDescriptor</b>对象。 |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md) **drawableDescriptor | 表示指向<b>ArkUI_DrawableDescriptor</b>对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回错误代码。<br>     如果操作成功，则返回 [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     如果发生参数错误，则返回 [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_NativeModule_GetDrawableDescriptorFromResourceAniValue()

```c
int32_t OH_ArkUI_NativeModule_GetDrawableDescriptorFromResourceAniValue(ani_env *env, ani_object resource, ArkUI_DrawableDescriptor **drawableDescriptor)
```

**描述**

获取ArkTS侧的<b>Resource</b>对象，并将其映射到Native侧的<b>ArkUI_DrawableDescriptor</b>对象。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ani_env *env | 表示ANI环境指针。 |
| ani_object resource | 表示在ArkTS端创建的<b>Resource</b>对象。 |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md) **drawableDescriptor | 表示指向<b>ArkUI_DrawableDescriptor</b>对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回错误代码。<br>     如果操作成功，则返回 [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     如果发生参数错误，则返回 [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |


