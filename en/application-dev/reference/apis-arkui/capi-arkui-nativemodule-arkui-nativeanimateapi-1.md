# ArkUI_NativeAnimateAPI_1

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e10e7def4863f4f964c4d0cb425b7650081cb83e translatedAt=2026-08-19T08:26:16.296Z pushedAt=2026-08-20T03:15:18.438Z -->

```c
typedef struct {...} ArkUI_NativeAnimateAPI_1
```

## Overview

Declares a set of animation APIs of ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_animate.h](capi-native-animate-h.md)

## Summary

### Member Functions

| Name| Description|
| -- | -- |
| [int32_t (\*animateTo)(ArkUI_ContextHandle context, ArkUI_AnimateOption* option, ArkUI_ContextCallback* update, ArkUI_AnimateCompleteCallback* complete)](#animateto) | Triggers an explicit animation. |
| [int32_t (\*keyframeAnimateTo)(ArkUI_ContextHandle context, ArkUI_KeyframeAnimateOption* option)](#keyframeanimateto) | Triggers a keyframe animation. |
| [ArkUI_AnimatorHandle (\*createAnimator)(ArkUI_ContextHandle context, ArkUI_AnimatorOption* option)](#createanimator) | Creates an animator animation object and returns its pointer (the caller takes ownership of the object). |
| [void (\*disposeAnimator)(ArkUI_AnimatorHandle animatorHandle)](#disposeanimator) | Disposes of the animator animation object pointed to by the passed-in pointer and releases its memory. The pointer cannot be used again after disposal. |

## Member Function Description

### animateTo()

```c
int32_t (*animateTo)(ArkUI_ContextHandle context, ArkUI_AnimateOption* option, ArkUI_ContextCallback* update, ArkUI_AnimateCompleteCallback* complete)
```

**Description**

Performs an explicit animation transition effect.

**Parameters**

| Name                                                                                                | Description|
|-----------------------------------------------------------------------------------------------------| -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | UI context instance, which is used to specify the UI context where the animation resides. It must not be **NULL**. |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to the animation effect option. It must not be **NULL**. |
| [ArkUI_ContextCallback](capi-arkui-nativemodule-arkui-contextcallback.md)* update                   | Pointer to the closure function for the animation effect. The system automatically inserts a transition animation for state changes that occur within the closure function. The parameter must not be **NULL**.<br>**Note:** The component attributes to be set in the closure function must have been set on the component before **animateTo** is called. |
| [ArkUI_AnimateCompleteCallback](capi-arkui-nativemodule-arkui-animatecompletecallback.md)* complete | Pointer to the callback invoked when the animation playback is complete. If **NULL** is passed, no completion callback notification is set. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>            Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>            Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. Check the type and validity of the passed parameters. Possible causes: **context** is invalid or **option** is set to **NULL** or is set improperly. Solution: ensure that **context** is valid and **option** is set correctly and not to **NULL**. |

### keyframeAnimateTo()

```c
int32_t (*keyframeAnimateTo)(ArkUI_ContextHandle context, ArkUI_KeyframeAnimateOption* option)
```

**Description**

Defines a keyframe animation. By specifying keyframes to define the values of attributes at different time points, the system automatically calculates the attribute values of intermediate frames based on the interpolation algorithm to achieve smooth transitions. For details about the keyframe parameter configuration, see [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md). Unlike the explicit transition animation of **animateTo**, **keyframeAnimateTo** is suitable for scenarios where different animation states need to be defined at multiple time points. You can use **animateTo** when only a transition animation from the start state to the end state is required, and use **keyframeAnimateTo** when fine-grained control of the animation process through multiple keyframes is required.

**Parameters**

| Name                                                                      | Description|
|---------------------------------------------------------------------------| -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | UI context instance, which is used to specify the UI context where the keyframe animation resides. It must not be **NULL**. |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Pointer to the keyframe animation option, which is used to specify the parameter of the keyframe animation, including the time point, animation attribute value, and transition effect. It must not be **NULL**. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>            Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>            Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. Check the type and validity of the passed parameters. Possible causes: **context** is invalid or **option** is set to **NULL** or is set improperly. Solution: ensure that **context** is valid and **option** is set correctly and not to **NULL**. |

### createAnimator()

```c
ArkUI_AnimatorHandle (*createAnimator)(ArkUI_ContextHandle context, ArkUI_AnimatorOption* option)
```

**Description**

Creates an animator animation object and returns its pointer. Unlike the trigger-based animation of **animateTo**/**keyframeAnimateTo**, **createAnimator** creates a persistently controllable animation object, which is suitable for scenarios requiring fine-grained control such as repeated starting, stopping, and state listening. You can use **animateTo** or **keyframeAnimateTo** for one-time transition animations, and use **createAnimator** when persistent control of the animation lifecycle is required.

**Parameters**

| Name                                                                      | Description|
|---------------------------------------------------------------------------| -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | UI context instance, which is used to specify the UI context where the animation resides. It must not be **NULL**. |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to the animator animation option, which must not be **NULL**. |

**Returns**

| Type                      | Description|
|--------------------------| -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) | Pointer to the animator animation object, which is used to control the animation object subsequently. **NULL** is returned when the function parameter is invalid. |

### disposeAnimator()

```c
void (*disposeAnimator)(ArkUI_AnimatorHandle animatorHandle)
```

**Description**

Disposes of the animator animation object and releases its memory. After the disposal, the handle must not be used again. When **NULL** or a handle that has been destroyed is passed, the API does not perform the disposal operation.

**Parameters**

| Name| Description|
|-----|----|
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Animator animation object, which must be a valid handle created by **createAnimator**. It must not be an object that has been disposed of. |