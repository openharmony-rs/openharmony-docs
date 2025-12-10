# drawable_descriptor.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Declares the APIs of **NativeDrawableDescriptor**.

**File to include**: <arkui/drawable_descriptor.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample**: <!--RP1-->[DrawableDescriptorSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/DrawableDescriptorSample)<!--RP1End-->

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md) | ArkUI_DrawableDescriptor | Defines a struct for the **DrawableDescriptor** object.|
| [OH_PixelmapNative*](capi-arkui-nativemodule-oh-pixelmapnative8h.md) | OH_PixelmapNativeHandle | Defines a struct for the pointer to an **OH_PixelmapNative** object.|
| [ArkUI_Node*](capi-arkui-nativemodule-arkui-node8h.md) | ArkUI_NodeHandle | Defines the pointer type for an ArkUI native component instance object.|
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md) | ArkUI_DrawableDescriptor_AnimationController | Defines the DrawableDescriptor animation controller object.|

### Enums

| Name                                                                 | typedef Keyword                     | Description                               |
|---------------------------------------------------------------------|---------------------------------|-----------------------------------|
| [DrawableDescriptor_AnimationStatus](#drawabledescriptor_animationstatus) | DrawableDescriptor_AnimationStatus | Enumerates the playback states of DrawableDescriptor animations.          |

### Functions

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor* OH_ArkUI_DrawableDescriptor_CreateFromPixelMap(OH_PixelmapNativeHandle pixelMap)](#oh_arkui_drawabledescriptor_createfrompixelmap) | Creates a **DrawableDescriptor** object from a **PixelMap** object.|
| [ArkUI_DrawableDescriptor* OH_ArkUI_DrawableDescriptor_CreateFromAnimatedPixelMap(OH_PixelmapNativeHandle* array, int32_t size)](#oh_arkui_drawabledescriptor_createfromanimatedpixelmap) | Creates a **DrawableDescriptor** object from an array of **PixelMap** objects.|
| [void OH_ArkUI_DrawableDescriptor_Dispose(ArkUI_DrawableDescriptor* drawableDescriptor)](#oh_arkui_drawabledescriptor_dispose) | Disposes the pointer to a **DrawableDescriptor** object.|
| [OH_PixelmapNativeHandle OH_ArkUI_DrawableDescriptor_GetStaticPixelMap(ArkUI_DrawableDescriptor* drawableDescriptor)](#oh_arkui_drawabledescriptor_getstaticpixelmap) | Obtains the pointer to a **PixelMap** object.|
| [OH_PixelmapNativeHandle* OH_ArkUI_DrawableDescriptor_GetAnimatedPixelMapArray(ArkUI_DrawableDescriptor* drawableDescriptor)](#oh_arkui_drawabledescriptor_getanimatedpixelmaparray) | Obtains an array of **PixelMap** objects for playing an animation.|
| [int32_t OH_ArkUI_DrawableDescriptor_GetAnimatedPixelMapArraySize(ArkUI_DrawableDescriptor* drawableDescriptor)](#oh_arkui_drawabledescriptor_getanimatedpixelmaparraysize) | Obtains an array of **PixelMap** objects for playing an animation.|
| [void OH_ArkUI_DrawableDescriptor_SetAnimationDuration(ArkUI_DrawableDescriptor* drawableDescriptor, int32_t duration)](#oh_arkui_drawabledescriptor_setanimationduration) | Sets the total playback duration for an array of **PixelMap** objects.|
| [int32_t OH_ArkUI_DrawableDescriptor_GetAnimationDuration(ArkUI_DrawableDescriptor* drawableDescriptor)](#oh_arkui_drawabledescriptor_getanimationduration) | Obtains the total playback duration for an array of **PixelMap** objects.|
| [void OH_ArkUI_DrawableDescriptor_SetAnimationIteration(ArkUI_DrawableDescriptor* drawableDescriptor, int32_t iteration)](#oh_arkui_drawabledescriptor_setanimationiteration) | Sets the number of times that an array of **PixelMap** objects is played.|
| [int32_t OH_ArkUI_DrawableDescriptor_GetAnimationIteration(ArkUI_DrawableDescriptor* drawableDescriptor)](#oh_arkui_drawabledescriptor_getanimationiteration) | Obtains the number of times that an array of **PixelMap** objects is played.|
| [int32_t OH_ArkUI_DrawableDescriptor_SetAnimationFrameDurations(ArkUI_DrawableDescriptor* drawableDescriptor, uint32_t* durations, size_t size)](#oh_arkui_drawabledescriptor_setanimationframedurations) | Sets the duration for each frame in a DrawableDescriptor animation.|
| [int32_t OH_ArkUI_DrawableDescriptor_GetAnimationFrameDurations(ArkUI_DrawableDescriptor* drawableDescriptor, uint32_t* durations, size_t* size)](#oh_arkui_drawabledescriptor_getanimationframedurations) | Obtains the duration of each frame in a DrawableDescriptor animation.|
| [int32_t OH_ArkUI_DrawableDescriptor_SetAnimationAutoPlay(ArkUI_DrawableDescriptor* drawableDescriptor, uint32_t autoPlay)](#oh_arkui_drawabledescriptor_setanimationautoplay) | Specifies whether to enable autoplay for a DrawableDescriptor animation.|
| [int32_t OH_ArkUI_DrawableDescriptor_GetAnimationAutoPlay(ArkUI_DrawableDescriptor* drawableDescriptor, uint32_t* autoPlay)](#oh_arkui_drawabledescriptor_getanimationautoplay) | Checks whether autoplay is enabled for a DrawableDescriptor animation.|
| [int32_t OH_ArkUI_DrawableDescriptor_CreateAnimationController(ArkUI_DrawableDescriptor* drawableDescriptor, ArkUI_NodeHandle node, ArkUI_DrawableDescriptor_AnimationController\*\* controller)](#oh_arkui_drawabledescriptor_createanimationcontroller) | Creates an animation controller for the DrawableDescriptor.|
| [void OH_ArkUI_DrawableDescriptor_DisposeAnimationController( ArkUI_DrawableDescriptor_AnimationController* controller)](#oh_arkui_drawabledescriptor_disposeanimationcontroller) | Disposes the DrawableDescriptor animation controller.|
| [int32_t OH_ArkUI_DrawableDescriptor_StartAnimation(ArkUI_DrawableDescriptor_AnimationController* controller)](#oh_arkui_drawabledescriptor_startanimation) | Starts the DrawableDescriptor animation from the first frame.|
| [int32_t OH_ArkUI_DrawableDescriptor_StopAnimation(ArkUI_DrawableDescriptor_AnimationController* controller)](#oh_arkui_drawabledescriptor_stopanimation) | Stops the DrawableDescriptor animation and returns to the first frame.|
| [int32_t OH_ArkUI_DrawableDescriptor_ResumeAnimation(ArkUI_DrawableDescriptor_AnimationController* controller)](#oh_arkui_drawabledescriptor_resumeanimation) | Resumes the DrawableDescriptor animation from the current frame.|
| [int32_t OH_ArkUI_DrawableDescriptor_PauseAnimation(ArkUI_DrawableDescriptor_AnimationController* controller)](#oh_arkui_drawabledescriptor_pauseanimation) | Pauses the DrawableDescriptor animation at the current frame.|
| [int32_t OH_ArkUI_DrawableDescriptor_GetAnimationStatus(ArkUI_DrawableDescriptor_AnimationController* controller, DrawableDescriptor_AnimationStatus* status)](#oh_arkui_drawabledescriptor_getanimationstatus) | Obtains the playback status of the DrawableDescriptor animation.|

## Enum Description

### DrawableDescriptor_AnimationStatus

```
enum DrawableDescriptor_AnimationStatus
```

**Description**


Enumerates the playback states of DrawableDescriptor animations.

**Since**: 22

| Value| Description|
| -- | -- |
| DRAWABLE_DESCRIPTOR_ANIMATION_STATUS_INITIAL = 0 | The animation is in the initial state.|
| DRAWABLE_DESCRIPTOR_ANIMATION_STATUS_RUNNING = 1 | The animation is being played.|
| DRAWABLE_DESCRIPTOR_ANIMATION_STATUS_PAUSED = 2 | The animation is paused.|
| DRAWABLE_DESCRIPTOR_ANIMATION_STATUS_STOPPED = 3 | The animation is stopped.|

## Function Description

### OH_ArkUI_DrawableDescriptor_CreateFromPixelMap()

```
ArkUI_DrawableDescriptor* OH_ArkUI_DrawableDescriptor_CreateFromPixelMap(OH_PixelmapNativeHandle pixelMap)
```

**Description**


Creates a **DrawableDescriptor** object from a **PixelMap** object.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_PixelmapNativeHandle](capi-arkui-nativemodule-oh-pixelmapnative8h.md) pixelMap | Pointer to a **PixelMap** object.|

**Return value**

| Type                           | Description|
|-------------------------------| -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* | Pointer to the **DrawableDescriptor** object.|

### OH_ArkUI_DrawableDescriptor_CreateFromAnimatedPixelMap()

```
ArkUI_DrawableDescriptor* OH_ArkUI_DrawableDescriptor_CreateFromAnimatedPixelMap(OH_PixelmapNativeHandle* array, int32_t size)
```

**Description**


Creates a **DrawableDescriptor** object from an array of **PixelMap** objects.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_PixelmapNativeHandle](capi-arkui-nativemodule-oh-pixelmapnative8h.md)* array | Pointer to the array of **PixelMap** objects.|
| int32_t size | Size of the **PixelMap** object array.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* | Pointer to the **DrawableDescriptor** object.|

### OH_ArkUI_DrawableDescriptor_Dispose()

```
void OH_ArkUI_DrawableDescriptor_Dispose(ArkUI_DrawableDescriptor* drawableDescriptor)
```

**Description**


Disposes the pointer to a **DrawableDescriptor** object.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | Pointer to a **DrawableDescriptor** object.|

### OH_ArkUI_DrawableDescriptor_GetStaticPixelMap()

```
OH_PixelmapNativeHandle OH_ArkUI_DrawableDescriptor_GetStaticPixelMap(ArkUI_DrawableDescriptor* drawableDescriptor)
```

**Description**


Obtains the pointer to a **PixelMap** object.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | Pointer to a **DrawableDescriptor** object.|

**Return value**

| Type| Description|
| -- | -- |
| [OH_PixelmapNativeHandle](capi-arkui-nativemodule-oh-pixelmapnative8h.md) | Pointer to a **PixelMap** object.|

### OH_ArkUI_DrawableDescriptor_GetAnimatedPixelMapArray()

```
OH_PixelmapNativeHandle* OH_ArkUI_DrawableDescriptor_GetAnimatedPixelMapArray(ArkUI_DrawableDescriptor* drawableDescriptor)
```

**Description**


Obtains an array of **PixelMap** objects for playing an animation.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | Pointer to a **DrawableDescriptor** object.|

**Return value**

| Type                          | Description|
|------------------------------| -- |
| [OH_PixelmapNativeHandle](capi-arkui-nativemodule-oh-pixelmapnative8h.md)* | Pointer to the array of **PixelMap** objects.|

### OH_ArkUI_DrawableDescriptor_GetAnimatedPixelMapArraySize()

```
int32_t OH_ArkUI_DrawableDescriptor_GetAnimatedPixelMapArraySize(ArkUI_DrawableDescriptor* drawableDescriptor)
```

**Description**


Obtains an array of **PixelMap** objects for playing an animation.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | Pointer to a **DrawableDescriptor** object.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Size of the **PixelMap** object array.|

### OH_ArkUI_DrawableDescriptor_SetAnimationDuration()

```
void OH_ArkUI_DrawableDescriptor_SetAnimationDuration(ArkUI_DrawableDescriptor* drawableDescriptor, int32_t duration)
```

**Description**


Sets the total playback duration for an array of **PixelMap** objects.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | Pointer to a **DrawableDescriptor** object.|
| int32_t duration | Total playback duration, in milliseconds.|

### OH_ArkUI_DrawableDescriptor_GetAnimationDuration()

```
int32_t OH_ArkUI_DrawableDescriptor_GetAnimationDuration(ArkUI_DrawableDescriptor* drawableDescriptor)
```

**Description**


Obtains the total playback duration for an array of **PixelMap** objects.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | Pointer to a **DrawableDescriptor** object.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Total playback duration, in milliseconds.|

### OH_ArkUI_DrawableDescriptor_SetAnimationIteration()

```
void OH_ArkUI_DrawableDescriptor_SetAnimationIteration(ArkUI_DrawableDescriptor* drawableDescriptor, int32_t iteration)
```

**Description**


Sets the number of times that an array of **PixelMap** objects is played.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | Pointer to a **DrawableDescriptor** object.|
| int32_t iteration | Number of playback times.|

### OH_ArkUI_DrawableDescriptor_GetAnimationIteration()

```
int32_t OH_ArkUI_DrawableDescriptor_GetAnimationIteration(ArkUI_DrawableDescriptor* drawableDescriptor)
```

**Description**


Obtains the number of times that an array of **PixelMap** objects is played.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | Pointer to a **DrawableDescriptor** object.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Number of playback times.|

### OH_ArkUI_DrawableDescriptor_SetAnimationFrameDurations()

```
int32_t OH_ArkUI_DrawableDescriptor_SetAnimationFrameDurations(ArkUI_DrawableDescriptor* drawableDescriptor, uint32_t* durations, size_t size)
```

**Description**

Sets the duration for each frame in a DrawableDescriptor animation.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | Pointer to a **DrawableDescriptor** object.|
| uint32_t* durations | Duration for each frame in the DrawableDescriptor animation, in milliseconds.<br>If this parameter is not set, the playback follows the total duration. This setting has higher priority than the **duration** parameter; when both **duration** and **frameDurations** are set, **duration** is ignored.<br>The array size must match the number of frames in the PixelMap image array.<br>Valid range for each frame's playback duration: [0, +∞).|
| size_t size | Array size.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_INVALID_PARAM](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DrawableDescriptor_GetAnimationFrameDurations()

```
int32_t OH_ArkUI_DrawableDescriptor_GetAnimationFrameDurations(ArkUI_DrawableDescriptor* drawableDescriptor, uint32_t* durations, size_t* size)
```

**Description**

Obtains the duration of each frame in a DrawableDescriptor animation.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | Pointer to a **DrawableDescriptor** object.|
| uint32_t* durations | Array of the playback durations for each frame in the animation, in milliseconds.|
| size_t* size | Array size.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_INVALID_PARAM](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DrawableDescriptor_SetAnimationAutoPlay()

```
int32_t OH_ArkUI_DrawableDescriptor_SetAnimationAutoPlay(ArkUI_DrawableDescriptor* drawableDescriptor, uint32_t autoPlay)
```

**Description**

Specifies whether to enable autoplay for a DrawableDescriptor animation.

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | Pointer to a **DrawableDescriptor** object.|
| uint32_t autoPlay | Whether to enable autoplay.<br>**1** to enable, **0** otherwise.<br>The default value is **1**.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_INVALID_PARAM](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DrawableDescriptor_GetAnimationAutoPlay()

```
int32_t OH_ArkUI_DrawableDescriptor_GetAnimationAutoPlay(ArkUI_DrawableDescriptor* drawableDescriptor, uint32_t* autoPlay)
```

**Description**

Checks whether autoplay is enabled for a DrawableDescriptor animation.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | Pointer to a **DrawableDescriptor** object.|
| uint32_t* autoPlay | Whether autoplay is enabled.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_INVALID_PARAM](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DrawableDescriptor_CreateAnimationController()

```
int32_t OH_ArkUI_DrawableDescriptor_CreateAnimationController(ArkUI_DrawableDescriptor* drawableDescriptor, ArkUI_NodeHandle node, ArkUI_DrawableDescriptor_AnimationController** controller)
```

**Description**

Creates an animation controller for the DrawableDescriptor.

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | Pointer to a **DrawableDescriptor** object.|
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the component node.|
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)** controller | Pointer to the created DrawableDescriptor animation controller.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_INVALID_PARAM](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DrawableDescriptor_DisposeAnimationController()

```
void OH_ArkUI_DrawableDescriptor_DisposeAnimationController(ArkUI_DrawableDescriptor_AnimationController* controller)
```

**Description**

Disposes the DrawableDescriptor animation controller.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)* controller | Pointer to the target DrawableDescriptor animation controller.|

### OH_ArkUI_DrawableDescriptor_StartAnimation()

```
int32_t OH_ArkUI_DrawableDescriptor_StartAnimation(ArkUI_DrawableDescriptor_AnimationController* controller);
```

**Description**

Starts playback from the first frame.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)* controller | Pointer to the target DrawableDescriptor animation controller.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_INVALID_PARAM](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DrawableDescriptor_StopAnimation()

```
int32_t OH_ArkUI_DrawableDescriptor_StopAnimation(ArkUI_DrawableDescriptor_AnimationController* controller);
```

**Description**

Stops the DrawableDescriptor animation and returns to the first frame.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)* controller | Pointer to the target DrawableDescriptor animation controller.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_INVALID_PARAM](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DrawableDescriptor_ResumeAnimation()

```
int32_t OH_ArkUI_DrawableDescriptor_ResumeAnimation(ArkUI_DrawableDescriptor_AnimationController* controller);
```

**Description**

Resumes the DrawableDescriptor animation from the current frame.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)* controller | Pointer to the target DrawableDescriptor animation controller.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_INVALID_PARAM](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DrawableDescriptor_PauseAnimation()

```
int32_t OH_ArkUI_DrawableDescriptor_PauseAnimation(ArkUI_DrawableDescriptor_AnimationController* controller);
```

**Description**

Pauses playback on the current frame.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)* controller | Pointer to the target DrawableDescriptor animation controller.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_INVALID_PARAM](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DrawableDescriptor_GetAnimationStatus()

```
int32_t OH_ArkUI_DrawableDescriptor_GetAnimationStatus(ArkUI_DrawableDescriptor_AnimationController* controller, DrawableDescriptor_AnimationStatus* status);
```

**Description**

Obtains the playback status of the DrawableDescriptor animation.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)* controller | Pointer to the target DrawableDescriptor animation controller.|
| [DrawableDescriptor_AnimationStatus](#drawabledescriptor_animationstatus)* status | Playback state of the DrawableDescriptor animation.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_INVALID_PARAM](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|
