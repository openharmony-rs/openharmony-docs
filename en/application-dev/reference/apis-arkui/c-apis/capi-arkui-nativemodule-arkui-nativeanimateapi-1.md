# ArkUI_NativeAnimateAPI_1

```c
typedef struct ArkUI_NativeAnimateAPI_1 {...} ArkUI_NativeAnimateAPI_1
```

## Overview

Declares the native animation APIs provided by ArkUI.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_animate.h](capi-native-animate-h.md)

## Summary

### Member functions

| Name | Description |
| -- | -- |
| [int32_t (\*animateTo)(ArkUI_ContextHandle context, ArkUI_AnimateOption* option, ArkUI_ContextCallback* update,ArkUI_AnimateCompleteCallback* complete)](#animateto) | Defines an explicit animation. |
| [int32_t (\*keyframeAnimateTo)(ArkUI_ContextHandle context, ArkUI_KeyframeAnimateOption* option)](#keyframeanimateto) | Defines a keyframe animation. |
| [ArkUI_AnimatorHandle (\*createAnimator)(ArkUI_ContextHandle context, ArkUI_AnimatorOption* option)](#createanimator) | Creates an animator object. |
| [void (\*disposeAnimator)(ArkUI_AnimatorHandle animatorHandle)](#disposeanimator) | Disposes of an animator object. |

## Member function description

### animateTo()

```c
int32_t (*animateTo)(ArkUI_ContextHandle context, ArkUI_AnimateOption* option, ArkUI_ContextCallback* update,ArkUI_AnimateCompleteCallback* complete)
```

**Description**

Defines an explicit animation.

> **Note**:
>
> Make sure the component attributes to be set in the event closure have been set before.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle context | **UIContext** instance. |
|  [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Defines the animation configuration. |
|  ArkUI_ContextCallback* update | Closure function for the animation. The system automatically inserts the transition animation if the state changes in the closure function. <br>Note: Make sure the component attributes to be set in the closure function have been set before. |
| [ArkUI_AnimateCompleteCallback](capi-arkui-nativemodule-arkui-animatecompletecallback.md)* complete | Callback invoked when the animation playback is complete. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>               <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>              </ul> |

### keyframeAnimateTo()

```c
int32_t (*keyframeAnimateTo)(ArkUI_ContextHandle context, ArkUI_KeyframeAnimateOption* option)
```

**Description**

Defines a keyframe animation.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle context | **UIContext** instance. |
|  [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Keyframe animation parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>               <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>              </ul> |

### createAnimator()

```c
ArkUI_AnimatorHandle (*createAnimator)(ArkUI_ContextHandle context, ArkUI_AnimatorOption* option)
```

**Description**

Creates an animator object.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle context | **UIContext** instance. |
|  [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) | Returns the pointer to the animator object; returns NULL if a parameter error occurs. |

### disposeAnimator()

```c
void (*disposeAnimator)(ArkUI_AnimatorHandle animatorHandle)
```

**Description**

Disposes of an animator object.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Animator object. |


