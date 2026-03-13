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
| [OH_PixelmapNative](../apis-image-kit/capi-image-nativemodule-oh-pixelmapnative.md) | - | Defines an **OH_PixelmapNative** object on the native side using Image Kit.|
| [OH_PixelmapNative*](capi-arkui-nativemodule-oh-pixelmapnative8h.md) | OH_PixelmapNativeHandle | Defines a struct for the pointer to an **OH_PixelmapNative** object.|
| [ArkUI_Node](capi-arkui-nativemodule-arkui-node-descriptor.md) | - | Defines the ArkUI native component instance object.<br>**Since**: 22|
| [ArkUI_Node*](capi-arkui-nativemodule-arkui-node8h.md) | ArkUI_NodeHandle | Defines the pointer type for an ArkUI native component instance object.<br>**Since**: 22|
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md) | ArkUI_DrawableDescriptor_AnimationController | Defines the DrawableDescriptor animation controller object.<br>**Since**: 22|

### Enums

| Name                                                                 | typedef Keyword                     | Description                               |
|---------------------------------------------------------------------|---------------------------------|-----------------------------------|
| [DrawableDescriptor_AnimationStatus](#drawabledescriptor_animationstatus) | DrawableDescriptor_AnimationStatus | Enumerates the playback states of DrawableDescriptor animations.          |
| [DrawableDescriptor_AnimationStopMode](#drawabledescriptor_animationstopmode) | DrawableDescriptor_AnimationStopMode | Enumerates the stop modes of [DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md) animations.<br>**Since**: 24|

### Functions

<!--Table: 30%; 70%-->
| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor* OH_ArkUI_DrawableDescriptor_CreateFromPixelMap(OH_PixelmapNativeHandle pixelMap)](#oh_arkui_drawabledescriptor_createfrompixelmap) | Creates a **DrawableDescriptor** object from a **PixelMap** object.|
| [ArkUI_DrawableDescriptor* OH_ArkUI_DrawableDescriptor_CreateFromAnimatedPixelMap(OH_PixelmapNativeHandle* array, int32_t size)](#oh_arkui_drawabledescriptor_createfromanimatedpixelmap) | Creates a **DrawableDescriptor** object from an array of **PixelMap** objects.|
| [void OH_ArkUI_DrawableDescriptor_Dispose(ArkUI_DrawableDescriptor* drawableDescriptor)](#oh_arkui_drawabledescriptor_dispose) | Disposes of the pointer to a **DrawableDescriptor** object.|
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
| [int32_t OH_ArkUI_DrawableDescriptor_SetAnimationStopMode(ArkUI_DrawableDescriptor* drawableDescriptor, DrawableDescriptor_AnimationStopMode mode)](#oh_arkui_drawabledescriptor_setanimationstopmode) | Sets the stop mode for an animation.|
| [int32_t OH_ArkUI_DrawableDescriptor_GetAnimationStopMode(ArkUI_DrawableDescriptor* drawableDescriptor, DrawableDescriptor_AnimationStopMode* mode)](#oh_arkui_drawabledescriptor_getanimationstopmode) | Obtains the stop mode of an animation.|
| [int32_t OH_ArkUI_DrawableDescriptor_CreateAnimationController(ArkUI_DrawableDescriptor* drawableDescriptor, ArkUI_NodeHandle node, ArkUI_DrawableDescriptor_AnimationController\*\* controller)](#oh_arkui_drawabledescriptor_createanimationcontroller) | Creates an animation controller for the DrawableDescriptor.|
| [void OH_ArkUI_DrawableDescriptor_DisposeAnimationController( ArkUI_DrawableDescriptor_AnimationController* controller)](#oh_arkui_drawabledescriptor_disposeanimationcontroller) | Disposes of the DrawableDescriptor animation controller.|
| [int32_t OH_ArkUI_DrawableDescriptor_StartAnimation(ArkUI_DrawableDescriptor_AnimationController* controller)](#oh_arkui_drawabledescriptor_startanimation) | Starts the DrawableDescriptor animation from the first frame.|
| [int32_t OH_ArkUI_DrawableDescriptor_StopAnimation(ArkUI_DrawableDescriptor_AnimationController* controller)](#oh_arkui_drawabledescriptor_stopanimation) | Stops the DrawableDescriptor animation and returns to the first frame.|
| [int32_t OH_ArkUI_DrawableDescriptor_ResumeAnimation(ArkUI_DrawableDescriptor_AnimationController* controller)](#oh_arkui_drawabledescriptor_resumeanimation) | Resumes the DrawableDescriptor animation from the current frame.|
| [int32_t OH_ArkUI_DrawableDescriptor_PauseAnimation(ArkUI_DrawableDescriptor_AnimationController* controller)](#oh_arkui_drawabledescriptor_pauseanimation) | Pauses the DrawableDescriptor animation at the current frame.|
| [int32_t OH_ArkUI_DrawableDescriptor_GetAnimationStatus(ArkUI_DrawableDescriptor_AnimationController* controller, DrawableDescriptor_AnimationStatus* status)](#oh_arkui_drawabledescriptor_getanimationstatus) | Obtains the playback status of the DrawableDescriptor animation.|

## Enum Description

### DrawableDescriptor_AnimationStatus

```c
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

### DrawableDescriptor_AnimationStopMode

```c
enum DrawableDescriptor_AnimationStopMode
```

**Description**

Enumerates the stop modes of [DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md) animations.

**Since**: 24

| Value| Description|
| -- | -- |
| DRAWABLE_DESCRIPTOR_ANIMATION_FIRST_FRAME = 0 | The animation returns to the first frame when it stops.|
| DRAWABLE_DESCRIPTOR_ANIMATION_LAST_FRAME = 1 | The animation stays at the last frame when it stops.|

## Function Description

### OH_ArkUI_DrawableDescriptor_CreateFromPixelMap()

```c
ArkUI_DrawableDescriptor* OH_ArkUI_DrawableDescriptor_CreateFromPixelMap(OH_PixelmapNativeHandle pixelMap)
```

**Description**


Creates a **DrawableDescriptor** object from a **PixelMap** object.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_PixelmapNativeHandle](capi-arkui-nativemodule-oh-pixelmapnative8h.md) pixelMap | Pointer to the [OH_PixelmapNative](./capi-struct.md) object.|

**Return value**

| Type                           | Description|
|-------------------------------| -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* | Pointer to the **DrawableDescriptor** object.|

### OH_ArkUI_DrawableDescriptor_CreateFromAnimatedPixelMap()

```c
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

```c
void OH_ArkUI_DrawableDescriptor_Dispose(ArkUI_DrawableDescriptor* drawableDescriptor)
```

**Description**


Disposes of the pointer to a **DrawableDescriptor** object.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | Pointer to a **DrawableDescriptor** object.|

### OH_ArkUI_DrawableDescriptor_GetStaticPixelMap()

```c
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
| [OH_PixelmapNativeHandle](capi-arkui-nativemodule-oh-pixelmapnative8h.md) | Pointer to the [OH_PixelmapNative](./capi-struct.md) object.|

### OH_ArkUI_DrawableDescriptor_GetAnimatedPixelMapArray()

```c
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

```c
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

```c
void OH_ArkUI_DrawableDescriptor_SetAnimationDuration(ArkUI_DrawableDescriptor* drawableDescriptor, int32_t duration)
```

**Description**


Sets the total playback duration for an array of **PixelMap** objects.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | Pointer to a **DrawableDescriptor** object.|
| int32_t duration | Total playback duration, in ms. Value range: [0, +∞). If a negative value is passed in, **0** is used.|

### OH_ArkUI_DrawableDescriptor_GetAnimationDuration()

```c
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
| int32_t | Total playback duration, in ms.|

### OH_ArkUI_DrawableDescriptor_SetAnimationIteration()

```c
void OH_ArkUI_DrawableDescriptor_SetAnimationIteration(ArkUI_DrawableDescriptor* drawableDescriptor, int32_t iteration)
```

**Description**


Sets the number of times that an array of **PixelMap** objects is played.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | Pointer to a **DrawableDescriptor** object.|
| int32_t iteration | Number of playback times. Value range: [0, +∞). The value **0** indicates infinite playback. If a negative value is passed in, **0** is used.|

### OH_ArkUI_DrawableDescriptor_GetAnimationIteration()

```c
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

```c
int32_t OH_ArkUI_DrawableDescriptor_SetAnimationFrameDurations(ArkUI_DrawableDescriptor* drawableDescriptor, uint32_t* durations, size_t size)
```

**Description**

Sets the duration for each frame in a DrawableDescriptor animation.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | Pointer to a **DrawableDescriptor** object.|
| uint32_t* durations | Array of the playback durations for each frame in the animation, in ms.<br>If this parameter is not set, the playback follows the total duration. This parameter takes precedence over [OH_ArkUI_DrawableDescriptor_SetAnimationDuration](#oh_arkui_drawabledescriptor_setanimationduration). That is, if both **OH_ArkUI_DrawableDescriptor_SetAnimationDuration** and **OH_ArkUI_DrawableDescriptor_SetAnimationFrameDurations** are set, **OH_ArkUI_DrawableDescriptor_SetAnimationDuration** does not take effect.<br>The array size must match the number of frames in the PixelMap image array.<br>Valid range for each frame's playback duration: [0, +∞). Default value: evenly distributed total duration.|
| size_t size | Array size.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DrawableDescriptor_GetAnimationFrameDurations()

```c
int32_t OH_ArkUI_DrawableDescriptor_GetAnimationFrameDurations(ArkUI_DrawableDescriptor* drawableDescriptor, uint32_t* durations, size_t* size)
```

**Description**

Obtains the duration of each frame in a DrawableDescriptor animation.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | Pointer to a **DrawableDescriptor** object.|
| uint32_t* durations | Array of the playback durations for each frame in the animation, in ms.|
| size_t* size | Array size.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DrawableDescriptor_SetAnimationAutoPlay()

```c
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
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DrawableDescriptor_GetAnimationAutoPlay()

```c
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
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DrawableDescriptor_SetAnimationStopMode()

```c
int32_t OH_ArkUI_DrawableDescriptor_SetAnimationStopMode(ArkUI_DrawableDescriptor* drawableDescriptor, DrawableDescriptor_AnimationStopMode mode)
```

**Description**

Sets the stop mode for an animation.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | Pointer to the [DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md) object.|
| [DrawableDescriptor_AnimationStopMode](#drawabledescriptor_animationstopmode) mode | Stop mode of an animation.<br>The value is an enumerated value of [DrawableDescriptor_AnimationStopMode](#drawabledescriptor_animationstopmode). The default value is [DRAWABLE_DESCRIPTOR_ANIMATION_FIRST_FRAME](#drawabledescriptor_animationstopmode).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DrawableDescriptor_GetAnimationStopMode()

```c
int32_t OH_ArkUI_DrawableDescriptor_GetAnimationStopMode(ArkUI_DrawableDescriptor* drawableDescriptor, DrawableDescriptor_AnimationStopMode* mode)
```

**Description**

Obtains the stop mode of an animation.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawableDescriptor | Pointer to the [DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md) object.|
| [DrawableDescriptor_AnimationStopMode](#drawabledescriptor_animationstopmode)* mode | Stop mode of an animation.<br>For details about the values, see [DrawableDescriptor_AnimationStopMode](#drawabledescriptor_animationstopmode).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DrawableDescriptor_CreateAnimationController()

```c
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
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)** controller | Pointer to a **DrawableDescriptor** animation controller.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DrawableDescriptor_DisposeAnimationController()

```c
void OH_ArkUI_DrawableDescriptor_DisposeAnimationController(ArkUI_DrawableDescriptor_AnimationController* controller)
```

**Description**

Disposes of the DrawableDescriptor animation controller.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)* controller | Pointer to a **DrawableDescriptor** animation controller.|

### OH_ArkUI_DrawableDescriptor_StartAnimation()

```c
int32_t OH_ArkUI_DrawableDescriptor_StartAnimation(ArkUI_DrawableDescriptor_AnimationController* controller);
```

**Description**

Starts playback from the first frame.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)* controller | Pointer to a **DrawableDescriptor** animation controller.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DrawableDescriptor_StopAnimation()

```c
int32_t OH_ArkUI_DrawableDescriptor_StopAnimation(ArkUI_DrawableDescriptor_AnimationController* controller);
```

**Description**

Stops the DrawableDescriptor animation and returns to the first frame.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)* controller | Pointer to a **DrawableDescriptor** animation controller.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DrawableDescriptor_ResumeAnimation()

```c
int32_t OH_ArkUI_DrawableDescriptor_ResumeAnimation(ArkUI_DrawableDescriptor_AnimationController* controller);
```

**Description**

Resumes the DrawableDescriptor animation from the current frame.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)* controller | Pointer to a **DrawableDescriptor** animation controller.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DrawableDescriptor_PauseAnimation()

```c
int32_t OH_ArkUI_DrawableDescriptor_PauseAnimation(ArkUI_DrawableDescriptor_AnimationController* controller);
```

**Description**

Pauses playback on the current frame.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)* controller | Pointer to a **DrawableDescriptor** animation controller.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DrawableDescriptor_GetAnimationStatus()

```c
int32_t OH_ArkUI_DrawableDescriptor_GetAnimationStatus(ArkUI_DrawableDescriptor_AnimationController* controller, DrawableDescriptor_AnimationStatus* status);
```

**Description**

Obtains the playback status of the DrawableDescriptor animation.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor_AnimationController](capi-arkui-nativemodule-arkui-drawabledescriptoranimationcontroller.md)* controller | Pointer to a **DrawableDescriptor** animation controller.|
| [DrawableDescriptor_AnimationStatus](#drawabledescriptor_animationstatus)* status | Playback state of the DrawableDescriptor animation.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|
