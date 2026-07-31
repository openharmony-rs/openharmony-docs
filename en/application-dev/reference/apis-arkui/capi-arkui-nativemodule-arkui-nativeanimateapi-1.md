# ArkUI_NativeAnimateAPI_1

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=f8ecdb82f3ec053eb7dde21e27a6f047d194898a translatedAt=2026-07-17T09:26:25.832Z pushedAt=2026-07-17T11:39:52.844Z -->

```c
typedef struct {...} ArkUI_NativeAnimateAPI_1
```

## Overview

Declares the native animation APIs provided by ArkUI.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_animate.h](capi-native-animate-h.md)

## Summary

### Member Functions

| Name| Description|
| -- | -- |
| [int32_t (\*animateTo)(ArkUI_ContextHandle context, ArkUI_AnimateOption* option, ArkUI_ContextCallback* update,ArkUI_AnimateCompleteCallback* complete)](#animateto) | Triggers an explicit animation. |
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
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context                           | UI context instance, which is used to specify the UI context where the animation resides. |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option                       | Animation effect option. |
| [ArkUI_ContextCallback](capi-arkui-nativemodule-arkui-contextcallback.md)* update                   | Closure function for the animation effect. The system automatically inserts a transition animation for state changes that occur within the closure function.<br>**Note:** The component attributes to be set in the closure function must have been set on the component before **animateTo** is called. |
| [ArkUI_AnimateCompleteCallback](capi-arkui-nativemodule-arkui-animatecompletecallback.md)* complete | Callback invoked when the animation playback is complete. If **NULL** is passed, no completion callback notification is set. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>            Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>            Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### keyframeAnimateTo()

```c
int32_t (*keyframeAnimateTo)(ArkUI_ContextHandle context, ArkUI_KeyframeAnimateOption* option)
```

**Description**

Defines a keyframe animation.

**Parameters**

| Name                                                                      | Description|
|---------------------------------------------------------------------------| -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | UI context instance, which is used to specify the UI context where the keyframe animation resides. |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option                                   | Keyframe animation parameter.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>            Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>            Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### createAnimator()

```c
ArkUI_AnimatorHandle (*createAnimator)(ArkUI_ContextHandle context, ArkUI_AnimatorOption* option)
```

**Description**

Creates an animator object.

**Parameters**

| Name                                                                      | Description|
|---------------------------------------------------------------------------| -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | UI context instance, which is used to specify the UI context where the animation resides. |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option                                          | Animator animation parameter.|

**Returns**

| Type                      | Description|
|--------------------------| -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) | Pointer to the animator animation object, which is used to control the animation object subsequently. **NULL** is returned when the function parameter is invalid. |

### disposeAnimator()

```c
void (*disposeAnimator)(ArkUI_AnimatorHandle animatorHandle)
```

**Description**

Disposes of an animator animation object.

**Parameters**

| Name| Description|
|-----|----|
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Animator animation object.|