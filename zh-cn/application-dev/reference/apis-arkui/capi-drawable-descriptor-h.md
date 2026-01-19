# drawable_descriptor.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

提供NativeDrawableDescriptor接口的类型定义。

**引用文件：** <arkui/drawable_descriptor.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**相关示例：** <!--RP1-->[DrawableDescriptorSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/DrawableDescriptorSample)<!--RP1End-->

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md) | ArkUI_DrawableDescriptor | 定义DrawableDescriptor对象。 |
| [OH_PixelmapNative](../apis-image-kit/capi-image-nativemodule-oh-pixelmapnative.md) | - | 使用Image Kit定义的Native侧的OH_PixelmapNative对象。 |
| [OH_PixelmapNative*](capi-arkui-nativemodule-oh-pixelmapnative8h.md) | OH_PixelmapNativeHandle | 定义OH_PixelmapNative对象指针类型。 |
| [ArkUI_Node](capi-arkui-nativemodule-arkui-node-descriptor.md) | - | 定义ArkUI native组件实例对象。 |
| [ArkUI_Node*](capi-arkui-nativemodule-arkui-node8h.md) | ArkUI_NodeHandle | 定义ArkUI native组件实例对象指针定义。 |
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md) | ArkUI_DrawableDescriptor_AnimationController | 定义DrawableDescriptor动图控制器对象。 |

### 枚举

| 名称                                                                  | typedef关键字                      | 描述                                |
|---------------------------------------------------------------------|---------------------------------|-----------------------------------|
| [DrawableDescriptor_AnimationStatus](#drawabledescriptor_animationstatus) | DrawableDescriptor_AnimationStatus | 定义DrawableDescriptor动图的播放状态。           |

### 函数

| 名称 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor* OH_ArkUI_DrawableDescriptor_CreateFromPixelMap(OH_PixelmapNativeHandle pixelMap)](#oh_arkui_drawabledescriptor_createfrompixelmap) | 使用PixelMap创建DrawableDescriptor对象。 |
| [ArkUI_DrawableDescriptor* OH_ArkUI_DrawableDescriptor_CreateFromAnimatedPixelMap(OH_PixelmapNativeHandle* array, int32_t size)](#oh_arkui_drawabledescriptor_createfromanimatedpixelmap) | 使用PixelMap图片数组创建DrawableDescriptor对象。 |
| [void OH_ArkUI_DrawableDescriptor_Dispose(ArkUI_DrawableDescriptor* drawableDescriptor)](#oh_arkui_drawabledescriptor_dispose) | 销毁DrawableDescriptor对象指针。 |
| [OH_PixelmapNativeHandle OH_ArkUI_DrawableDescriptor_GetStaticPixelMap(ArkUI_DrawableDescriptor* drawableDescriptor)](#oh_arkui_drawabledescriptor_getstaticpixelmap) | 获取PixelMap图片对象指针。 |
| [OH_PixelmapNativeHandle* OH_ArkUI_DrawableDescriptor_GetAnimatedPixelMapArray(ArkUI_DrawableDescriptor* drawableDescriptor)](#oh_arkui_drawabledescriptor_getanimatedpixelmaparray) | 获取用于播放动画的PixelMap图片数组数据。 |
| [int32_t OH_ArkUI_DrawableDescriptor_GetAnimatedPixelMapArraySize(ArkUI_DrawableDescriptor* drawableDescriptor)](#oh_arkui_drawabledescriptor_getanimatedpixelmaparraysize) | 获取用于播放动画的PixelMap图片数组数据。 |
| [void OH_ArkUI_DrawableDescriptor_SetAnimationDuration(ArkUI_DrawableDescriptor* drawableDescriptor, int32_t duration)](#oh_arkui_drawabledescriptor_setanimationduration) | 设置PixelMap图片数组播放总时长。 |
| [int32_t OH_ArkUI_DrawableDescriptor_GetAnimationDuration(ArkUI_DrawableDescriptor* drawableDescriptor)](#oh_arkui_drawabledescriptor_getanimationduration) | 获取PixelMap图片数组播放总时长。 |
| [void OH_ArkUI_DrawableDescriptor_SetAnimationIteration(ArkUI_DrawableDescriptor* drawableDescriptor, int32_t iteration)](#oh_arkui_drawabledescriptor_setanimationiteration) | 设置PixelMap图片数组播放次数。 |
| [int32_t OH_ArkUI_DrawableDescriptor_GetAnimationIteration(ArkUI_DrawableDescriptor* drawableDescriptor)](#oh_arkui_drawabledescriptor_getanimationiteration) | 获取PixelMap图片数组播放次数。 |
| [int32_t OH_ArkUI_DrawableDescriptor_SetAnimationFrameDurations(ArkUI_DrawableDescriptor* drawableDescriptor, uint32_t* durations, size_t size)](#oh_arkui_drawabledescriptor_setanimationframedurations) | 设置动图中的单帧播放时间。 |
| [int32_t OH_ArkUI_DrawableDescriptor_GetAnimationFrameDurations(ArkUI_DrawableDescriptor* drawableDescriptor, uint32_t* durations, size_t* size)](#oh_arkui_drawabledescriptor_getanimationframedurations) | 获取动图中的单帧播放时间。 |
| [int32_t OH_ArkUI_DrawableDescriptor_SetAnimationAutoPlay(ArkUI_DrawableDescriptor* drawableDescriptor, uint32_t autoPlay)](#oh_arkui_drawabledescriptor_setanimationautoplay) | 设置动图是否自动播放。 |
| [int32_t OH_ArkUI_DrawableDescriptor_GetAnimationAutoPlay(ArkUI_DrawableDescriptor* drawableDescriptor, uint32_t* autoPlay)](#oh_arkui_drawabledescriptor_getanimationautoplay) | 获取动图是否自动播放。 |
| [int32_t OH_ArkUI_DrawableDescriptor_CreateAnimationController(ArkUI_DrawableDescriptor* drawableDescriptor, ArkUI_NodeHandle node, ArkUI_DrawableDescriptor_AnimationController\*\* controller)](#oh_arkui_drawabledescriptor_createanimationcontroller) | 创建动图控制器。 |
| [void OH_ArkUI_DrawableDescriptor_DisposeAnimationController( ArkUI_DrawableDescriptor_AnimationController* controller)](#oh_arkui_drawabledescriptor_disposeanimationcontroller) | 销毁动图控制器。 |
| [int32_t OH_ArkUI_DrawableDescriptor_StartAnimation(ArkUI_DrawableDescriptor_AnimationController* controller)](#oh_arkui_drawabledescriptor_startanimation) | 从首帧开始播放。 |
| [int32_t OH_ArkUI_DrawableDescriptor_StopAnimation(ArkUI_DrawableDescriptor_AnimationController* controller)](#oh_arkui_drawabledescriptor_stopanimation) | 停止动图播放并回到首帧。 |
| [int32_t OH_ArkUI_DrawableDescriptor_ResumeAnimation(ArkUI_DrawableDescriptor_AnimationController* controller)](#oh_arkui_drawabledescriptor_resumeanimation) | 从当前帧恢复动图播放。 |
| [int32_t OH_ArkUI_DrawableDescriptor_PauseAnimation(ArkUI_DrawableDescriptor_AnimationController* controller)](#oh_arkui_drawabledescriptor_pauseanimation) | 暂停动图的播放，保持在当前帧。 |
| [int32_t OH_ArkUI_DrawableDescriptor_GetAnimationStatus(ArkUI_DrawableDescriptor_AnimationController* controller, DrawableDescriptor_AnimationStatus* status)](#oh_arkui_drawabledescriptor_getanimationstatus) | 获取动图的播放状态。 |

## 枚举类型说明

### DrawableDescriptor_AnimationStatus

```c
enum DrawableDescriptor_AnimationStatus
```

**描述：**


定义DrawableDescriptor动图的播放状态。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| DRAWABLE_DESCRIPTOR_ANIMATION_STATUS_INITIAL = 0 | 动画初始状态。 |
| DRAWABLE_DESCRIPTOR_ANIMATION_STATUS_RUNNING = 1 | 动画处于播放状态。 |
| DRAWABLE_DESCRIPTOR_ANIMATION_STATUS_PAUSED = 2 | 动画处于暂停状态。 |
| DRAWABLE_DESCRIPTOR_ANIMATION_STATUS_STOPPED = 3 | 动画处于停止状态。 |

## 函数说明

### OH_ArkUI_DrawableDescriptor_CreateFromPixelMap()

```c
ArkUI_DrawableDescriptor* OH_ArkUI_DrawableDescriptor_CreateFromPixelMap(OH_PixelmapNativeHandle pixelMap)
```

**描述：**


使用PixelMap创建DrawableDescriptor对象。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PixelmapNativeHandle](capi-arkui-nativemodule-oh-pixelmapnative8h.md) pixelMap | PixelMap对象指针。 |

**返回：**

| 类型                            | 说明 |
|-------------------------------| -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* | 返回DrawableDescriptor对象指针。 |

### OH_ArkUI_DrawableDescriptor_CreateFromAnimatedPixelMap()

```c
ArkUI_DrawableDescriptor* OH_ArkUI_DrawableDescriptor_CreateFromAnimatedPixelMap(OH_PixelmapNativeHandle* array, int32_t size)
```

**描述：**


使用PixelMap图片数组创建DrawableDescriptor对象。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PixelmapNativeHandle](capi-arkui-nativemodule-oh-pixelmapnative8h.md)* array | PixelMap图片数组对象指针。 |
| int32_t size | PixelMap图片数组大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* | 返回DrawableDescriptor对象指针。 |

### OH_ArkUI_DrawableDescriptor_Dispose()

```c
void OH_ArkUI_DrawableDescriptor_Dispose(ArkUI_DrawableDescriptor* drawableDescriptor)
```

**描述：**


销毁DrawableDescriptor对象指针。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | DrawableDescriptor对象指针。 |

### OH_ArkUI_DrawableDescriptor_GetStaticPixelMap()

```c
OH_PixelmapNativeHandle OH_ArkUI_DrawableDescriptor_GetStaticPixelMap(ArkUI_DrawableDescriptor* drawableDescriptor)
```

**描述：**


获取PixelMap图片对象指针。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | DrawableDescriptor对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_PixelmapNativeHandle](capi-arkui-nativemodule-oh-pixelmapnative8h.md) | PixelMap对象指针。 |

### OH_ArkUI_DrawableDescriptor_GetAnimatedPixelMapArray()

```c
OH_PixelmapNativeHandle* OH_ArkUI_DrawableDescriptor_GetAnimatedPixelMapArray(ArkUI_DrawableDescriptor* drawableDescriptor)
```

**描述：**


获取用于播放动画的PixelMap图片数组数据。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | DrawableDescriptor对象指针。 |

**返回：**

| 类型                           | 说明 |
|------------------------------| -- |
| [OH_PixelmapNativeHandle](capi-arkui-nativemodule-oh-pixelmapnative8h.md)* | PixelMap图片数组指针。 |

### OH_ArkUI_DrawableDescriptor_GetAnimatedPixelMapArraySize()

```c
int32_t OH_ArkUI_DrawableDescriptor_GetAnimatedPixelMapArraySize(ArkUI_DrawableDescriptor* drawableDescriptor)
```

**描述：**


获取用于播放动画的PixelMap图片数组数据。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | DrawableDescriptor对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | PixelMap图片数组大小。 |

### OH_ArkUI_DrawableDescriptor_SetAnimationDuration()

```c
void OH_ArkUI_DrawableDescriptor_SetAnimationDuration(ArkUI_DrawableDescriptor* drawableDescriptor, int32_t duration)
```

**描述：**


设置PixelMap图片数组播放总时长。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | DrawableDescriptor对象指针。 |
| int32_t duration | 播放总时长，单位毫秒。 |

### OH_ArkUI_DrawableDescriptor_GetAnimationDuration()

```c
int32_t OH_ArkUI_DrawableDescriptor_GetAnimationDuration(ArkUI_DrawableDescriptor* drawableDescriptor)
```

**描述：**


获取PixelMap图片数组播放总时长。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | DrawableDescriptor对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 播放总时长，单位毫秒。 |

### OH_ArkUI_DrawableDescriptor_SetAnimationIteration()

```c
void OH_ArkUI_DrawableDescriptor_SetAnimationIteration(ArkUI_DrawableDescriptor* drawableDescriptor, int32_t iteration)
```

**描述：**


设置PixelMap图片数组播放次数。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | DrawableDescriptor对象指针。 |
| int32_t iteration | 播放次数。 |

### OH_ArkUI_DrawableDescriptor_GetAnimationIteration()

```c
int32_t OH_ArkUI_DrawableDescriptor_GetAnimationIteration(ArkUI_DrawableDescriptor* drawableDescriptor)
```

**描述：**


获取PixelMap图片数组播放次数。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | DrawableDescriptor对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 播放次数。 |

### OH_ArkUI_DrawableDescriptor_SetAnimationFrameDurations()

```c
int32_t OH_ArkUI_DrawableDescriptor_SetAnimationFrameDurations(ArkUI_DrawableDescriptor* drawableDescriptor, uint32_t* durations, size_t size)
```

**描述：**

设置动图中的单帧播放时间。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | DrawableDescriptor对象指针。 |
| uint32_t* durations | 动图中的单帧播放时间数组，单位毫秒。<br/>不设置则按照总时间播放。设置的优先级高于duration，即同时设置了duration和frameDurations时，duration不生效。<br/>数组大小必须与PixelMap图片数组大小相同。<br/>每帧播放时间取值范围：[0, +∞)。 |
| size_t size | 数组大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_INVALID_PARAM](capi-native-type-h.md#arkui_errorcode) 输入参数错误。 |

### OH_ArkUI_DrawableDescriptor_GetAnimationFrameDurations()

```c
int32_t OH_ArkUI_DrawableDescriptor_GetAnimationFrameDurations(ArkUI_DrawableDescriptor* drawableDescriptor, uint32_t* durations, size_t* size)
```

**描述：**

获取动图中的单帧播放时间。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | DrawableDescriptor对象指针。 |
| uint32_t* durations | 动图中的单帧播放时间数组。 |
| size_t* size | 数组大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_INVALID_PARAM](capi-native-type-h.md#arkui_errorcode) 输入参数错误。 |

### OH_ArkUI_DrawableDescriptor_SetAnimationAutoPlay()

```c
int32_t OH_ArkUI_DrawableDescriptor_SetAnimationAutoPlay(ArkUI_DrawableDescriptor* drawableDescriptor, uint32_t autoPlay)
```

**描述：**

设置动图是否自动播放。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | DrawableDescriptor对象指针。 |
| uint32_t autoPlay | 是否自动播放。<br/>1表示自动播放，0表示不自动播放。<br/>默认值为1。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_INVALID_PARAM](capi-native-type-h.md#arkui_errorcode) 输入参数错误。 |

### OH_ArkUI_DrawableDescriptor_GetAnimationAutoPlay()

```c
int32_t OH_ArkUI_DrawableDescriptor_GetAnimationAutoPlay(ArkUI_DrawableDescriptor* drawableDescriptor, uint32_t* autoPlay)
```

**描述：**

获取动图是否自动播放。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | DrawableDescriptor对象指针。 |
| uint32_t* autoPlay | 是否自动播放。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_INVALID_PARAM](capi-native-type-h.md#arkui_errorcode) 输入参数错误。 |

### OH_ArkUI_DrawableDescriptor_CreateAnimationController()

```c
int32_t OH_ArkUI_DrawableDescriptor_CreateAnimationController(ArkUI_DrawableDescriptor* drawableDescriptor, ArkUI_NodeHandle node, ArkUI_DrawableDescriptor_AnimationController** controller)
```

**描述：**

创建动图控制器。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | DrawableDescriptor对象指针。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 组件节点指针。 |
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)** controller | DrawableDescriptor动图控制器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_INVALID_PARAM](capi-native-type-h.md#arkui_errorcode) 输入参数错误。 |

### OH_ArkUI_DrawableDescriptor_DisposeAnimationController()

```c
void OH_ArkUI_DrawableDescriptor_DisposeAnimationController(ArkUI_DrawableDescriptor_AnimationController* controller)
```

**描述：**

销毁动图控制器。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)* controller | DrawableDescriptor动图控制器对象指针。 |

### OH_ArkUI_DrawableDescriptor_StartAnimation()

```c
int32_t OH_ArkUI_DrawableDescriptor_StartAnimation(ArkUI_DrawableDescriptor_AnimationController* controller);
```

**描述：**

从首帧开始播放。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)* controller | DrawableDescriptor动图控制器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_INVALID_PARAM](capi-native-type-h.md#arkui_errorcode) 输入参数错误。 |

### OH_ArkUI_DrawableDescriptor_StopAnimation()

```c
int32_t OH_ArkUI_DrawableDescriptor_StopAnimation(ArkUI_DrawableDescriptor_AnimationController* controller);
```

**描述：**

停止动图播放并回到首帧。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)* controller | DrawableDescriptor动图控制器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_INVALID_PARAM](capi-native-type-h.md#arkui_errorcode) 输入参数错误。 |

### OH_ArkUI_DrawableDescriptor_ResumeAnimation()

```c
int32_t OH_ArkUI_DrawableDescriptor_ResumeAnimation(ArkUI_DrawableDescriptor_AnimationController* controller);
```

**描述：**

从当前帧恢复动图播放。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)* controller | DrawableDescriptor动图控制器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_INVALID_PARAM](capi-native-type-h.md#arkui_errorcode) 输入参数错误。 |

### OH_ArkUI_DrawableDescriptor_PauseAnimation()

```c
int32_t OH_ArkUI_DrawableDescriptor_PauseAnimation(ArkUI_DrawableDescriptor_AnimationController* controller);
```

**描述：**

暂停动图的播放，保持在当前帧。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)* controller | DrawableDescriptor动图控制器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_INVALID_PARAM](capi-native-type-h.md#arkui_errorcode) 输入参数错误。 |

### OH_ArkUI_DrawableDescriptor_GetAnimationStatus()

```c
int32_t OH_ArkUI_DrawableDescriptor_GetAnimationStatus(ArkUI_DrawableDescriptor_AnimationController* controller, DrawableDescriptor_AnimationStatus* status);
```

**描述：**

获取动图的播放状态。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)* controller | DrawableDescriptor动图控制器对象指针。 |
| [DrawableDescriptor_AnimationStatus](#drawabledescriptor_animationstatus)* status | DrawableDescriptor动图的播放状态。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_INVALID_PARAM](capi-native-type-h.md#arkui_errorcode) 输入参数错误。 |
