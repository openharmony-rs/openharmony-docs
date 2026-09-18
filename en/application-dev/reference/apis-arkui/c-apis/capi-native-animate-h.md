# native_animate.h

## Overview

Defines a set of animation APIs of ArkUI on the native side. The APIs in **native_animate.h** must be called in the main thread.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md) | ArkUI_ExpectedFrameRateRange | Defines the expected frame rate range of the animation. |
| [ArkUI_AnimateCompleteCallback](capi-arkui-nativemodule-arkui-animatecompletecallback.md) | ArkUI_AnimateCompleteCallback | Defines the callback type for when the animation playback is complete. |
| [ArkUI_NativeAnimateAPI_1](capi-arkui-nativemodule-arkui-nativeanimateapi-1.md) | ArkUI_NativeAnimateAPI_1 | Declares the native animation APIs provided by ArkUI. |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md) | ArkUI_AnimateOption | Defines the animation configuration. |
| [ArkUI_Curve](capi-arkui-nativemodule-arkui-curve.md) | ArkUI_Curve | Defines an interpolation curve. |
| [ArkUI_Curve*](capi-arkui-nativemodule-arkui-curve8h.md) | ArkUI_CurveHandle | Defines the pointer to an interpolation curve. |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md) | ArkUI_KeyframeAnimateOption | Defines the keyframe animation parameter object. |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md) | ArkUI_AnimatorOption | Defines the animator parameter object. |
| [ArkUI_Animator*](capi-arkui-nativemodule-arkui-animator8h.md) | ArkUI_AnimatorHandle | Defines the pointer to an animator object. |
| [ArkUI_AnimatorEvent](capi-arkui-nativemodule-arkui-animatorevent.md) | ArkUI_AnimatorEvent | Defines the animator callback event object. |
| [ArkUI_AnimatorOnFrameEvent](capi-arkui-nativemodule-arkui-animatoronframeevent.md) | ArkUI_AnimatorOnFrameEvent | Defines the callback object when the animator receives a frame. |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md) | ArkUI_TransitionEffect | Defines the transition parameter object for transition property configuration. |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_AnimateOption* OH_ArkUI_AnimateOption_Create()](#oh_arkui_animateoption_create) | Creates an animation configuration. |
| [void OH_ArkUI_AnimateOption_Dispose(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_dispose) | Disposes of an animation configuration. |
| [uint32_t OH_ArkUI_AnimateOption_GetDuration(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_getduration) | Obtains the animation duration, in milliseconds. |
| [float OH_ArkUI_AnimateOption_GetTempo(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_gettempo) | Obtains the playback speed of an animation. |
| [ArkUI_AnimationCurve OH_ArkUI_AnimateOption_GetCurve(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_getcurve) | Obtains an animation curve. |
| [int32_t OH_ArkUI_AnimateOption_GetDelay(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_getdelay) | Obtains the animation delay, in milliseconds. |
| [int32_t OH_ArkUI_AnimateOption_GetIterations(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_getiterations) | Obtains the number of times that an animation is played. |
| [ArkUI_AnimationPlayMode OH_ArkUI_AnimateOption_GetPlayMode(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_getplaymode) | Obtains the playback mode of an animation. |
| [ArkUI_ExpectedFrameRateRange* OH_ArkUI_AnimateOption_GetExpectedFrameRateRange(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_getexpectedframeraterange) | Obtains the expected frame rate range of an animation. |
| [void OH_ArkUI_AnimateOption_SetDuration(ArkUI_AnimateOption* option, int32_t value)](#oh_arkui_animateoption_setduration) | Sets the animation duration, in milliseconds. |
| [void OH_ArkUI_AnimateOption_SetTempo(ArkUI_AnimateOption* option, float value)](#oh_arkui_animateoption_settempo) | Sets the playback speed of an animation. |
| [void OH_ArkUI_AnimateOption_SetCurve(ArkUI_AnimateOption* option, ArkUI_AnimationCurve value)](#oh_arkui_animateoption_setcurve) | Animation curve. |
| [void OH_ArkUI_AnimateOption_SetDelay(ArkUI_AnimateOption* option, int32_t value)](#oh_arkui_animateoption_setdelay) | Sets the animation delay, in milliseconds. |
| [void OH_ArkUI_AnimateOption_SetIterations(ArkUI_AnimateOption* option, int32_t value)](#oh_arkui_animateoption_setiterations) | Sets the number of times that an animation is played. |
| [void OH_ArkUI_AnimateOption_SetPlayMode(ArkUI_AnimateOption* option, ArkUI_AnimationPlayMode value)](#oh_arkui_animateoption_setplaymode) | Sets the playback mode for an animation. |
| [void OH_ArkUI_AnimateOption_SetExpectedFrameRateRange(ArkUI_AnimateOption* option, ArkUI_ExpectedFrameRateRange* value)](#oh_arkui_animateoption_setexpectedframeraterange) | Defines a struct for the expected frame rate range of the animation. |
| [void OH_ArkUI_AnimateOption_SetICurve(ArkUI_AnimateOption* option, ArkUI_CurveHandle value)](#oh_arkui_animateoption_seticurve) | Sets the animation curve for an animation. |
| [ArkUI_CurveHandle OH_ArkUI_AnimateOption_GetICurve(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_geticurve) | Obtains the animation curve of an animation. |
| [ArkUI_KeyframeAnimateOption* OH_ArkUI_KeyframeAnimateOption_Create(int32_t size)](#oh_arkui_keyframeanimateoption_create) | Creates a keyframe animation parameter object. |
| [void OH_ArkUI_KeyframeAnimateOption_Dispose(ArkUI_KeyframeAnimateOption* option)](#oh_arkui_keyframeanimateoption_dispose) | Disposes of a keyframe animation parameter object. |
| [int32_t OH_ArkUI_KeyframeAnimateOption_SetDelay(ArkUI_KeyframeAnimateOption* option, int32_t value)](#oh_arkui_keyframeanimateoption_setdelay) | Sets the overall delay of a keyframe animation, in milliseconds. By default, the keyframe animation starts without any delay. |
| [int32_t OH_ArkUI_KeyframeAnimateOption_SetIterations(ArkUI_KeyframeAnimateOption* option, int32_t value)](#oh_arkui_keyframeanimateoption_setiterations) | Sets the number of times that the keyframe animation is played. By default, the animation is played once. The value **-1** indicates that the animation is played for an unlimited number of times. The value **0** indicates that no animation is played. |
| [int32_t OH_ArkUI_KeyframeAnimateOption_RegisterOnFinishCallback(ArkUI_KeyframeAnimateOption* option, void* userData, void (\*onFinish)(void* userData))](#oh_arkui_keyframeanimateoption_registeronfinishcallback) | Sets the callback invoked when the keyframe animation playback is complete. This function is called after the {@link keyframe animation} has played for the specified number of times. |
| [int32_t OH_ArkUI_KeyframeAnimateOption_SetExpectedFrameRate(ArkUI_KeyframeAnimateOption* option, ArkUI_ExpectedFrameRateRange* frameRate)](#oh_arkui_keyframeanimateoption_setexpectedframerate) | Sets the expected frame rate for a keyframe animation. |
| [int32_t OH_ArkUI_KeyframeAnimateOption_SetDuration(ArkUI_KeyframeAnimateOption* option, int32_t value, int32_t index)](#oh_arkui_keyframeanimateoption_setduration) | Sets the duration of a keyframe animation, in milliseconds. |
| [int32_t OH_ArkUI_KeyframeAnimateOption_SetCurve(ArkUI_KeyframeAnimateOption* option, ArkUI_CurveHandle value, int32_t index)](#oh_arkui_keyframeanimateoption_setcurve) | Sets the animation curve for a specific keyframe animation segment. |
| [int32_t OH_ArkUI_KeyframeAnimateOption_RegisterOnEventCallback(ArkUI_KeyframeAnimateOption* option, void* userData, void (\*event)(void* userData), int32_t index)](#oh_arkui_keyframeanimateoption_registeroneventcallback) | Sets the closure function of the state at the time of the keyframe, that is, the state to be reached at the time of the keyframe. |
| [int32_t OH_ArkUI_KeyframeAnimateOption_GetDelay(ArkUI_KeyframeAnimateOption* option)](#oh_arkui_keyframeanimateoption_getdelay) | Obtains the overall delay of a keyframe animation, in milliseconds. |
| [int32_t OH_ArkUI_KeyframeAnimateOption_GetIterations(ArkUI_KeyframeAnimateOption* option)](#oh_arkui_keyframeanimateoption_getiterations) | Obtains the number of times that a keyframe animation is played. |
| [ArkUI_ExpectedFrameRateRange* OH_ArkUI_KeyframeAnimateOption_GetExpectedFrameRate(ArkUI_KeyframeAnimateOption* option)](#oh_arkui_keyframeanimateoption_getexpectedframerate) | Obtains the expected frame rate from keyframe animation parameters. |
| [int32_t OH_ArkUI_KeyframeAnimateOption_GetDuration(ArkUI_KeyframeAnimateOption* option, int32_t index)](#oh_arkui_keyframeanimateoption_getduration) | Obtains the duration of a specific state in a keyframe animation, in milliseconds. |
| [ArkUI_CurveHandle OH_ArkUI_KeyframeAnimateOption_GetCurve(ArkUI_KeyframeAnimateOption* option, int32_t index)](#oh_arkui_keyframeanimateoption_getcurve) | Obtains the animation curve of a specific state in a keyframe animation. |
| [ArkUI_AnimatorOption* OH_ArkUI_AnimatorOption_Create(int32_t keyframeSize)](#oh_arkui_animatoroption_create) | Creates an **AnimatorOption** object. |
| [void OH_ArkUI_AnimatorOption_Dispose(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_dispose) | Disposes of an **AnimatorOption** object. |
| [int32_t OH_ArkUI_AnimatorOption_SetDuration(ArkUI_AnimatorOption* option, int32_t value)](#oh_arkui_animatoroption_setduration) | Sets the duration of an animator animation, in milliseconds. |
| [int32_t OH_ArkUI_AnimatorOption_SetDelay(ArkUI_AnimatorOption* option, int32_t value)](#oh_arkui_animatoroption_setdelay) | Sets the delay time of the animator playback, in milliseconds. |
| [int32_t OH_ArkUI_AnimatorOption_SetIterations(ArkUI_AnimatorOption* option, int32_t value)](#oh_arkui_animatoroption_setiterations) | Sets the number of times that an animator animation is played. By default, the animation is played once. The value **-1** indicates that the animation is played for an unlimited number of times. The value **0** indicates that no animation is played. |
| [int32_t OH_ArkUI_AnimatorOption_SetFill(ArkUI_AnimatorOption* option, ArkUI_AnimationFillMode value)](#oh_arkui_animatoroption_setfill) | Sets the status of the component before and after the animator animation execution. |
| [int32_t OH_ArkUI_AnimatorOption_SetDirection(ArkUI_AnimatorOption* option, ArkUI_AnimationDirection value)](#oh_arkui_animatoroption_setdirection) | Set the playback direction. |
| [int32_t OH_ArkUI_AnimatorOption_SetCurve(ArkUI_AnimatorOption* option, ArkUI_CurveHandle value)](#oh_arkui_animatoroption_setcurve) | Sets the interpolation curve for the animation of an animator. |
| [int32_t OH_ArkUI_AnimatorOption_SetBegin(ArkUI_AnimatorOption* option, float value)](#oh_arkui_animatoroption_setbegin) | Sets the interpolation start point of an animation. |
| [int32_t OH_ArkUI_AnimatorOption_SetEnd(ArkUI_AnimatorOption* option, float value)](#oh_arkui_animatoroption_setend) | Sets the interpolation end point for the animation of an animator. |
| [int32_t OH_ArkUI_AnimatorOption_SetExpectedFrameRateRange(ArkUI_AnimatorOption* option, ArkUI_ExpectedFrameRateRange* value)](#oh_arkui_animatoroption_setexpectedframeraterange) | Sets the expected frame rate range of an animation. |
| [int32_t OH_ArkUI_AnimatorOption_SetKeyframe(ArkUI_AnimatorOption* option, float time, float value, int32_t index)](#oh_arkui_animatoroption_setkeyframe) | Sets the keyframe parameters of an animator animation. |
| [int32_t OH_ArkUI_AnimatorOption_SetKeyframeCurve(ArkUI_AnimatorOption* option, ArkUI_CurveHandle value, int32_t index)](#oh_arkui_animatoroption_setkeyframecurve) | Sets the keyframe curve type for the animation of an animator. |
| [int32_t OH_ArkUI_AnimatorOption_GetDuration(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getduration) | Obtains the duration for playing an animation. |
| [int32_t OH_ArkUI_AnimatorOption_GetDelay(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getdelay) | Obtains the delay for playing an animation. |
| [int32_t OH_ArkUI_AnimatorOption_GetIterations(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getiterations) | Obtains the number of times that an animator animation is played. |
| [ArkUI_AnimationFillMode OH_ArkUI_AnimatorOption_GetFill(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getfill) | Obtains the status of the component before and after the animator animation execution. |
| [ArkUI_AnimationDirection OH_ArkUI_AnimatorOption_GetDirection(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getdirection) | Obtains the playback direction of an animator animation. |
| [ArkUI_CurveHandle OH_ArkUI_AnimatorOption_GetCurve(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getcurve) | Obtains the interpolation curve of the animation of an animator. |
| [float OH_ArkUI_AnimatorOption_GetBegin(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getbegin) | Obtains the interpolation start point of an animation. |
| [float OH_ArkUI_AnimatorOption_GetEnd(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getend) | Obtains the interpolation end point of an animation. |
| [ArkUI_ExpectedFrameRateRange* OH_ArkUI_AnimatorOption_GetExpectedFrameRateRange(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getexpectedframeraterange) | Obtains the expected frame rate range of an animator animation. |
| [float OH_ArkUI_AnimatorOption_GetKeyframeTime(ArkUI_AnimatorOption* option, int32_t index)](#oh_arkui_animatoroption_getkeyframetime) | Obtains the keyframe time of the animator playback, in milliseconds. |
| [float OH_ArkUI_AnimatorOption_GetKeyframeValue(ArkUI_AnimatorOption* option, int32_t index)](#oh_arkui_animatoroption_getkeyframevalue) | Obtains the keyframe value of an animation. |
| [ArkUI_CurveHandle OH_ArkUI_AnimatorOption_GetKeyframeCurve(ArkUI_AnimatorOption* option, int32_t index)](#oh_arkui_animatoroption_getkeyframecurve) | Obtains the interpolation curve for a keyframe in the animation of an animator. |
| [void* OH_ArkUI_AnimatorEvent_GetUserData(ArkUI_AnimatorEvent* event)](#oh_arkui_animatorevent_getuserdata) | Obtains the user-defined object in an animation event object. |
| [void* OH_ArkUI_AnimatorOnFrameEvent_GetUserData(ArkUI_AnimatorOnFrameEvent* event)](#oh_arkui_animatoronframeevent_getuserdata) | Obtains the user-defined object in the frame event of an animation. |
| [float OH_ArkUI_AnimatorOnFrameEvent_GetValue(ArkUI_AnimatorOnFrameEvent* event)](#oh_arkui_animatoronframeevent_getvalue) | Obtains the interpolation result in the animation frame callback event object. |
| [int32_t OH_ArkUI_AnimatorOption_RegisterOnFrameCallback(ArkUI_AnimatorOption* option, void* userData, void (\*callback)(ArkUI_AnimatorOnFrameEvent* event))](#oh_arkui_animatoroption_registeronframecallback) | Sets the callback invoked when the animator receives a frame. |
| [int32_t OH_ArkUI_AnimatorOption_RegisterOnFinishCallback(ArkUI_AnimatorOption* option, void* userData, void (\*callback)(ArkUI_AnimatorEvent* event))](#oh_arkui_animatoroption_registeronfinishcallback) | Sets the callback invoked when the animation playback is complete. |
| [int32_t OH_ArkUI_AnimatorOption_RegisterOnCancelCallback(ArkUI_AnimatorOption* option, void* userData, void (\*callback)(ArkUI_AnimatorEvent* event))](#oh_arkui_animatoroption_registeroncancelcallback) | Sets the callback invoked when the animation playback is canceled. |
| [int32_t OH_ArkUI_AnimatorOption_RegisterOnRepeatCallback(ArkUI_AnimatorOption* option, void* userData, void (\*callback)(ArkUI_AnimatorEvent* event))](#oh_arkui_animatoroption_registeronrepeatcallback) | Sets the callback invoked when the animation playback is repeated. |
| [int32_t OH_ArkUI_Animator_ResetAnimatorOption(ArkUI_AnimatorHandle animatorHandle, ArkUI_AnimatorOption* option)](#oh_arkui_animator_resetanimatoroption) | Resets the animation of an animator. |
| [int32_t OH_ArkUI_Animator_Play(ArkUI_AnimatorHandle animatorHandle)](#oh_arkui_animator_play) | Starts the animation of an animator. |
| [int32_t OH_ArkUI_Animator_Finish(ArkUI_AnimatorHandle animatorHandle)](#oh_arkui_animator_finish) | Ends the animation of an animator. |
| [int32_t OH_ArkUI_Animator_Pause(ArkUI_AnimatorHandle animatorHandle)](#oh_arkui_animator_pause) | Pauses the animation of an animator. |
| [int32_t OH_ArkUI_Animator_Cancel(ArkUI_AnimatorHandle animatorHandle)](#oh_arkui_animator_cancel) | Cancels the animation of an animator. |
| [int32_t OH_ArkUI_Animator_Reverse(ArkUI_AnimatorHandle animatorHandle)](#oh_arkui_animator_reverse) | Plays this animation in reverse order. |
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateCurveByType(ArkUI_AnimationCurve curve)](#oh_arkui_curve_createcurvebytype) | Implements initialization for the interpolation curve, which is used to create an interpolation curve based on the input parameter. |
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateStepsCurve(int32_t count, bool end)](#oh_arkui_curve_createstepscurve) | Creates a step curve. |
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateCubicBezierCurve(float x1, float y1, float x2, float y2)](#oh_arkui_curve_createcubicbeziercurve) | Creates a cubic Bezier curve. |
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateSpringCurve(float velocity, float mass, float stiffness, float damping)](#oh_arkui_curve_createspringcurve) | Creates a spring curve. The curve shape is determined by the spring parameters, and the animation duration is controlled by the **duration** parameter in {@link animation} and [animateTo](capi-arkui-nativemodule-arkui-nativeanimateapi-1.md#animateto). |
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateSpringMotion(float response, float dampingFraction, float overlapDuration)](#oh_arkui_curve_createspringmotion) | Creates a spring animation curve. If multiple spring animations are applied to the same attribute of an object, each animation replaces their predecessor and inherits the velocity. |
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateResponsiveSpringMotion(float response, float dampingFraction, float overlapDuration)](#oh_arkui_curve_createresponsivespringmotion) | Creates a responsive spring animation curve. It is a special case of **springMotion**, with the only difference in the default values. It can be used together with **springMotion**. |
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateInterpolatingSpring(float velocity, float mass, float stiffness, float damping)](#oh_arkui_curve_createinterpolatingspring) | Creates an interpolating spring curve animated from 0 to 1. The actual animation value is calculated based on the curve. |
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateCustomCurve(void* userData, float (\*interpolate)(float fraction, void* userdata))](#oh_arkui_curve_createcustomcurve) | Creates a custom curve. |
| [void OH_ArkUI_Curve_DisposeCurve(ArkUI_CurveHandle curveHandle)](#oh_arkui_curve_disposecurve) | Disposes of a custom curve. |
| [ArkUI_TransitionEffect* OH_ArkUI_CreateOpacityTransitionEffect(float opacity)](#oh_arkui_createopacitytransitioneffect) | Creates an opacity effect object for component transitions. |
| [ArkUI_TransitionEffect* OH_ArkUI_CreateTranslationTransitionEffect(ArkUI_TranslationOptions* translate)](#oh_arkui_createtranslationtransitioneffect) | Creates a translation effect object for component transitions. |
| [ArkUI_TransitionEffect* OH_ArkUI_CreateScaleTransitionEffect(ArkUI_ScaleOptions* scale)](#oh_arkui_createscaletransitioneffect) | Creates a scaling effect object for component transitions. |
| [ArkUI_TransitionEffect* OH_ArkUI_CreateRotationTransitionEffect(ArkUI_RotationOptions* rotate)](#oh_arkui_createrotationtransitioneffect) | Creates a rotation effect object for component transition. |
| [ArkUI_TransitionEffect* OH_ArkUI_CreateMovementTransitionEffect(ArkUI_TransitionEdge edge)](#oh_arkui_createmovementtransitioneffect) | Creates a movement transition effect object for the component. |
| [ArkUI_TransitionEffect* OH_ArkUI_CreateAsymmetricTransitionEffect(ArkUI_TransitionEffect* appear, ArkUI_TransitionEffect* disappear)](#oh_arkui_createasymmetrictransitioneffect) | Creates an asymmetric transition effect. |
| [ArkUI_TransitionEffect* OH_ArkUI_CreateIdentityTransitionEffect(void)](#oh_arkui_createidentitytransitioneffect) | Create an identity transition effect. Identity transition effect performs no visual transition animation. It can alse be used as the appear or disappear parameter of OH_ArkUI_CreateAsymmetricTransitionEffect to indicate no animation on one side. |
| [void OH_ArkUI_TransitionEffect_Dispose(ArkUI_TransitionEffect* effect)](#oh_arkui_transitioneffect_dispose) | Disposes of a transition effect. |
| [int32_t OH_ArkUI_TransitionEffect_Combine(ArkUI_TransitionEffect* firstEffect, ArkUI_TransitionEffect* secondEffect)](#oh_arkui_transitioneffect_combine) | Sets a combination of transition effects. |
| [int32_t OH_ArkUI_TransitionEffect_SetAnimation(ArkUI_TransitionEffect* effect, ArkUI_AnimateOption* animation)](#oh_arkui_transitioneffect_setanimation) | Sets transition effect animation settings. |

## Function description

### OH_ArkUI_AnimateOption_Create()

```c
ArkUI_AnimateOption* OH_ArkUI_AnimateOption_Create()
```

**Description**

Creates an animation configuration.

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_AnimateOption*](capi-arkui-nativemodule-arkui-animateoption.md) | Pointer to the created animation configuration. |

### OH_ArkUI_AnimateOption_Dispose()

```c
void OH_ArkUI_AnimateOption_Dispose(ArkUI_AnimateOption* option)
```

**Description**

Disposes of an animation configuration.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration. <br>If **option** is set to **NULL**, the operation is invalid. |

### OH_ArkUI_AnimateOption_GetDuration()

```c
uint32_t OH_ArkUI_AnimateOption_GetDuration(ArkUI_AnimateOption* option)
```

**Description**

Obtains the animation duration, in milliseconds.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration. <br>If **option** is set to **NULL**, **0** is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Animation duration, in milliseconds. If option is invalid, 0 is returned. |

### OH_ArkUI_AnimateOption_GetTempo()

```c
float OH_ArkUI_AnimateOption_GetTempo(ArkUI_AnimateOption* option)
```

**Description**

Obtains the playback speed of an animation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration. <br>If **option** is set to **NULL**, **0.0** is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Animation playback speed. Value range: [0, +∞). If option is invalid, 0.0 is returned. |

### OH_ArkUI_AnimateOption_GetCurve()

```c
ArkUI_AnimationCurve OH_ArkUI_AnimateOption_GetCurve(ArkUI_AnimateOption* option)
```

**Description**

Obtains an animation curve.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration. <br>If **option** is set to **NULL**, **-1** is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_AnimationCurve | Animation curve. If option is invalid,-1 is returned. |

### OH_ArkUI_AnimateOption_GetDelay()

```c
int32_t OH_ArkUI_AnimateOption_GetDelay(ArkUI_AnimateOption* option)
```

**Description**

Obtains the animation delay, in milliseconds.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration. <br>If **option** is set to **NULL**, **0** is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Delay of animation playback. If option is invalid, 0 is returned. |

### OH_ArkUI_AnimateOption_GetIterations()

```c
int32_t OH_ArkUI_AnimateOption_GetIterations(ArkUI_AnimateOption* option)
```

**Description**

Obtains the number of times that an animation is played.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration. <br>If **option** is set to **NULL**, **0** is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Number of times that the animation is played. If option is invalid, 0 is returned. |

### OH_ArkUI_AnimateOption_GetPlayMode()

```c
ArkUI_AnimationPlayMode OH_ArkUI_AnimateOption_GetPlayMode(ArkUI_AnimateOption* option)
```

**Description**

Obtains the playback mode of an animation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration. <br>If **option** is set to **NULL**, **-1** is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_AnimationPlayMode | Animation playback mode. If option is invalid,-1 is returned. |

### OH_ArkUI_AnimateOption_GetExpectedFrameRateRange()

```c
ArkUI_ExpectedFrameRateRange* OH_ArkUI_AnimateOption_GetExpectedFrameRateRange(ArkUI_AnimateOption* option)
```

**Description**

Obtains the expected frame rate range of an animation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration. <br>If **option** is set to **NULL**, **NULL** is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ExpectedFrameRateRange*](capi-arkui-nativemodule-arkui-expectedframeraterange.md) | Expected frame rate range of the animation, in fps. If option is invalid, NULL is returned. |

### OH_ArkUI_AnimateOption_SetDuration()

```c
void OH_ArkUI_AnimateOption_SetDuration(ArkUI_AnimateOption* option, int32_t value)
```

**Description**

Sets the animation duration, in milliseconds.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration. <br>If **option** is set to **NULL**, the operation is invalid. |
| int32_t value | Animation duration, in milliseconds. Value range: [0, +∞). <br>If the value is less than 0, **0** is used. |

### OH_ArkUI_AnimateOption_SetTempo()

```c
void OH_ArkUI_AnimateOption_SetTempo(ArkUI_AnimateOption* option, float value)
```

**Description**

Sets the playback speed of an animation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration. <br>If **option** is set to **NULL**, the operation is invalid. |
| float value | Animation playback speed. Value range: [0, +∞). <br>**NOTE**<br><br>If the value is less than 0, the default value **1** is used. |

### OH_ArkUI_AnimateOption_SetCurve()

```c
void OH_ArkUI_AnimateOption_SetCurve(ArkUI_AnimateOption* option, ArkUI_AnimationCurve value)
```

**Description**

Animation curve.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration. <br>If **option** is set to **NULL**, the operation is invalid. |
| ArkUI_AnimationCurve value | Animation curve. Default value: {@link ARKUI_CURVE_LINEAR}. You are advised to use<br>    {@link ARKUI_CURVE_EASE_IN_OUT} to obtain a smoother animation effect. <br>If the value is abnormal, the setting is invalid. |

### OH_ArkUI_AnimateOption_SetDelay()

```c
void OH_ArkUI_AnimateOption_SetDelay(ArkUI_AnimateOption* option, int32_t value)
```

**Description**

Sets the animation delay, in milliseconds.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration. <br>If **option** is set to **NULL**, the operation is invalid. |
| int32_t value | Animation delay, in milliseconds. Value range: (-∞, +∞). Default value: **0**, indicating no animation delay. A value greater than 0 means to begin the animation after the specified amount of time has elapsed. A value less than 0 means to begin the animation in advance. If **value** is less than **0** and the absolute value of **value** is less than the actual animation duration, the animation starts its first frame from the state at the absolute value. If the absolute value of **value** is greater than or equal to the actual animation duration, the animation starts its first frame from the end state. The actual animation duration is equal to the duration of a single animation multiplied by the number of animation playback times. |

### OH_ArkUI_AnimateOption_SetIterations()

```c
void OH_ArkUI_AnimateOption_SetIterations(ArkUI_AnimateOption* option, int32_t value)
```

**Description**

Sets the number of times that an animation is played.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration. <br>If **option** is set to **NULL**, the operation is invalid. |
| int32_t value | Number of times that the animation is played. Value range: [-1, +∞). If this parameter is set to **0**, the animation is not played. If this parameter is set to **-1**, the animation is played for an infinite number of times. Default value: **1** (played once). <br>If the value is less than -1, the operation is invalid. |

### OH_ArkUI_AnimateOption_SetPlayMode()

```c
void OH_ArkUI_AnimateOption_SetPlayMode(ArkUI_AnimateOption* option, ArkUI_AnimationPlayMode value)
```

**Description**

Sets the playback mode for an animation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration. <br>If **option** is set to **NULL**, the operation is invalid. |
| ArkUI_AnimationPlayMode value | Animation playback mode. Default value: {@link ARKUI_ANIMATION_PLAY_MODE_NORMAL}. <br>If the value is abnormal, the operation is invalid. |

### OH_ArkUI_AnimateOption_SetExpectedFrameRateRange()

```c
void OH_ArkUI_AnimateOption_SetExpectedFrameRateRange(ArkUI_AnimateOption* option, ArkUI_ExpectedFrameRateRange* value)
```

**Description**

Defines a struct for the expected frame rate range of the animation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration. <br>If **option** is set to **NULL**, the operation is invalid. |
| [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md)* value | Expected frame rate range of the animation, in fps. <br>If **value** is set to **NULL**, the operation is invalid. |

### OH_ArkUI_AnimateOption_SetICurve()

```c
void OH_ArkUI_AnimateOption_SetICurve(ArkUI_AnimateOption* option, ArkUI_CurveHandle value)
```

**Description**

Sets the animation curve for an animation.

> **Note**:
>
> This method is better than the value set by OH_ArkUI_AnimateOption_SetCurve.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Animator animation parameters. <br>If **option** is set to **NULL**, the operation is invalid. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) value | Animation curve parameters. <br>If **value** is set to **NULL**, the operation is invalid. |

### OH_ArkUI_AnimateOption_GetICurve()

```c
ArkUI_CurveHandle OH_ArkUI_AnimateOption_GetICurve(ArkUI_AnimateOption* option)
```

**Description**

Obtains the animation curve of an animation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Animator animation parameters. <br>If **option** is set to **NULL**, **NULL** is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Animation curve parameters. Returns NULL if the option parameter is invalid. |

### OH_ArkUI_KeyframeAnimateOption_Create()

```c
ArkUI_KeyframeAnimateOption* OH_ArkUI_KeyframeAnimateOption_Create(int32_t size)
```

**Description**

Creates a keyframe animation parameter object.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t size | Number of keyframe animation states. <br>Returns **NULL** if the value of **size** is less than 0. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_KeyframeAnimateOption*](capi-arkui-nativemodule-arkui-keyframeanimateoption.md) | Keyframe animation parameter object. If the value of size is less than 0 or if option is abnormal,       NULL is returned. |

### OH_ArkUI_KeyframeAnimateOption_Dispose()

```c
void OH_ArkUI_KeyframeAnimateOption_Dispose(ArkUI_KeyframeAnimateOption* option)
```

**Description**

Disposes of a keyframe animation parameter object.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Keyframe animation parameter object. <br>If **option** is set to **NULL**, the operation is invalid. |

### OH_ArkUI_KeyframeAnimateOption_SetDelay()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_SetDelay(ArkUI_KeyframeAnimateOption* option, int32_t value)
```

**Description**

Sets the overall delay of a keyframe animation, in milliseconds. By default, the keyframe animation starts without any delay.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Keyframe animation parameters. <br>If **option** is set to **NULL**, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |
| int32_t value | Animation delay, in milliseconds. Value range: (-∞, +∞). Default value: **0**, indicating no animation delay. A value greater than 0 means to begin the animation after the specified amount of time has elapsed. A value less than 0 means to begin the animation in advance. If **value** is less than **0** and the absolute value of **value** is less than the actual animation duration, the animation starts its first frame from the state at the absolute value. If the absolute value of **value** is greater than or equal to the actual animation duration, the animation starts its first frame from the end state. The actual animation duration is equal to the duration of a single animation multiplied by the number of animation playback times. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_KeyframeAnimateOption_SetIterations()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_SetIterations(ArkUI_KeyframeAnimateOption* option, int32_t value)
```

**Description**

Sets the number of times that the keyframe animation is played. By default, the animation is played once. The value **-1** indicates that the animation is played for an unlimited number of times. The value **0** indicates that no animation is played.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Keyframe animation parameters. <br>If **option** is set to **NULL**, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |
| int32_t value | Number of times that the animation is played. Value range: [-1, +∞). If this parameter is set to **0**, the animation is not played. If this parameter is set to **-1**, the animation is played for an infinite number of times. Default value: **1**, indicating that the animation is played once. <br>If the value is less than **-1**, the operation is invalid, and the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_KeyframeAnimateOption_RegisterOnFinishCallback()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_RegisterOnFinishCallback(ArkUI_KeyframeAnimateOption* option, void* userData, void (*onFinish)(void* userData))
```

**Description**

Sets the callback invoked when the keyframe animation playback is complete. This function is called after the {@link keyframe animation} has played for the specified number of times.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_KeyframeAnimateOption\* option | Keyframe animation parameters. <br>If **option** is set to **NULL**, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |
| void\* userData | Pointer to a custom object. <br>Abnormal value processing is not involved. |
| void (\*onFinish)(void\* userData) | Indicates the callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_KeyframeAnimateOption_SetExpectedFrameRate()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_SetExpectedFrameRate(ArkUI_KeyframeAnimateOption* option, ArkUI_ExpectedFrameRateRange* frameRate)
```

**Description**

Sets the expected frame rate for a keyframe animation.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Keyframe animation parameters. <br>If **option** is set to **NULL**, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |
| [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md)* frameRate | Expected frame rate for the keyframe animation. <br>If **frameRate** is set to **NULL**, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_KeyframeAnimateOption_SetDuration()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_SetDuration(ArkUI_KeyframeAnimateOption* option, int32_t value, int32_t index)
```

**Description**

Sets the duration of a keyframe animation, in milliseconds.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Keyframe animation parameters. <br>If **option** is set to **NULL**, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |
| int32_t value | Keyframe animation duration, in ms. The default value is 1000 ms. Value range: [0, +∞). <br>If the value is less than 0, **0** is used. |
| int32_t index | Index of the keyframe state segment. <br>If the value of **index** is less than 0, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_KeyframeAnimateOption_SetCurve()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_SetCurve(ArkUI_KeyframeAnimateOption* option, ArkUI_CurveHandle value, int32_t index)
```

**Description**

Sets the animation curve for a specific keyframe animation segment.

> **Note**:
>
> Because the <b>springMotion</b>, <b>responsiveSpringMotion</b>, and <b>interpolatingSpring</b> curves do not have effective duration settings, they are not supported.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Keyframe animation parameters. <br>If **option** is set to **NULL**, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) value | Animation curve to set. Default value: {@link ARKUI_CURVE_EASE_IN_OUT}. |
| int32_t index | Index of the keyframe state segment. Value range: [0, size – 1], where **size** indicates the number of keyframe animation states. <br>If the value of **index** is less than 0 or out of range, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_KeyframeAnimateOption_RegisterOnEventCallback()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_RegisterOnEventCallback(ArkUI_KeyframeAnimateOption* option, void* userData, void (*event)(void* userData), int32_t index)
```

**Description**

Sets the closure function of the state at the time of the keyframe, that is, the state to be reached at the time of the keyframe.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_KeyframeAnimateOption\* option | Keyframe animation parameters. <br>If **option** is set to **NULL**, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |
| void (\*event)(void\* userData) | Indicates a closure function. |
| void\* userData | Pointer to a user-defined object. <br>Abnormal value processing is not involved. |
| int32_t index | Index of the keyframe state segment. Value range: [0, size – 1], where **size** indicates the number of keyframe animation states. <br>If the value of **index** is less than 0 or out of range, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_KeyframeAnimateOption_GetDelay()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_GetDelay(ArkUI_KeyframeAnimateOption* option)
```

**Description**

Obtains the overall delay of a keyframe animation, in milliseconds.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Keyframe animation parameters. <br>If **option** is set to **NULL**, **0** is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Overall delay, in milliseconds. If option is invalid, 0 is returned. |

### OH_ArkUI_KeyframeAnimateOption_GetIterations()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_GetIterations(ArkUI_KeyframeAnimateOption* option)
```

**Description**

Obtains the number of times that a keyframe animation is played.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Keyframe animation parameters. <br>If **option** is set to **NULL**, **0** is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Number of times that the animation is played. If option is invalid, 0 is returned. |

### OH_ArkUI_KeyframeAnimateOption_GetExpectedFrameRate()

```c
ArkUI_ExpectedFrameRateRange* OH_ArkUI_KeyframeAnimateOption_GetExpectedFrameRate(ArkUI_KeyframeAnimateOption* option)
```

**Description**

Obtains the expected frame rate from keyframe animation parameters.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Keyframe animation parameters. <br>If **option** is set to **NULL**, **NULL** is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ExpectedFrameRateRange*](capi-arkui-nativemodule-arkui-expectedframeraterange.md) | Returns the expected frame rate obtained. If option is invalid, NULL is returned. |

### OH_ArkUI_KeyframeAnimateOption_GetDuration()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_GetDuration(ArkUI_KeyframeAnimateOption* option, int32_t index)
```

**Description**

Obtains the duration of a specific state in a keyframe animation, in milliseconds.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Keyframe animation parameters. <br>If **option** is set to **NULL**, **0** is returned. |
| int32_t index | Index of the keyframe state segment. <br>If the value of **index** is less than 0, **0** is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Duration, in milliseconds. If option is invalid, 0 is returned. |

### OH_ArkUI_KeyframeAnimateOption_GetCurve()

```c
ArkUI_CurveHandle OH_ArkUI_KeyframeAnimateOption_GetCurve(ArkUI_KeyframeAnimateOption* option, int32_t index)
```

**Description**

Obtains the animation curve of a specific state in a keyframe animation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Keyframe animation parameters. <br>If **option** is set to **NULL**, **NULL** is returned. |
| int32_t index | Index of the keyframe state segment. <br>If the value of **index** is less than 0, **NULL** is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Animation curve. If the parameter is abnormal, NULL is returned. |

### OH_ArkUI_AnimatorOption_Create()

```c
ArkUI_AnimatorOption* OH_ArkUI_AnimatorOption_Create(int32_t keyframeSize)
```

**Description**

Creates an **AnimatorOption** object.

> **Note**:
>
> When <b>keyframeSize</b> is greater than 0, the animation interpolation start point is 0, and the animation interpolation end point is 1; no setting is allowed.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t keyframeSize | Number of keyframes. <br>If the value of **keyframeSize** is less than 0, **NULL** is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_AnimatorOption*](capi-arkui-nativemodule-arkui-animatoroption.md) | Pointer to the animator parameter object. If the value of size is less than 0 or if option is      abnormal, NULL is returned. |

### OH_ArkUI_AnimatorOption_Dispose()

```c
void OH_ArkUI_AnimatorOption_Dispose(ArkUI_AnimatorOption* option)
```

**Description**

Disposes of an **AnimatorOption** object.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the operation is invalid. |

### OH_ArkUI_AnimatorOption_SetDuration()

```c
int32_t OH_ArkUI_AnimatorOption_SetDuration(ArkUI_AnimatorOption* option, int32_t value)
```

**Description**

Sets the duration of an animator animation, in milliseconds.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |
| int32_t value | Playback duration, in ms. The default value is 0 ms. Value range: [0, +∞). <br>If the value is less than 0, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_SetDelay()

```c
int32_t OH_ArkUI_AnimatorOption_SetDelay(ArkUI_AnimatorOption* option, int32_t value)
```

**Description**

Sets the delay time of the animator playback, in milliseconds.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |
| int32_t value | Animation delay, in milliseconds. Value range: (-∞, +∞). Default value: **0**, indicating no animation delay. A value greater than 0 means to begin the animation after the specified amount of time has elapsed. A value less than 0 means to begin the animation in advance. If **value** is less than **0** and the absolute value of **value** is less than the actual animation duration, the animation starts its first frame from the state at the absolute value. If the absolute value of **value** is greater than or equal to the actual animation duration, the animation starts its first frame from the end state. The actual animation duration is equal to the duration of a single animation multiplied by the number of animation playback times. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_SetIterations()

```c
int32_t OH_ArkUI_AnimatorOption_SetIterations(ArkUI_AnimatorOption* option, int32_t value)
```

**Description**

Sets the number of times that an animator animation is played. By default, the animation is played once. The value **-1** indicates that the animation is played for an unlimited number of times. The value **0** indicates that no animation is played.

> **Note**:
>
> If this parameter is set to a negative value other than <b>-1</b>, the value is invalid. In this case, the animation is played once.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |
| int32_t value | Value range: [-1, +∞). If this parameter is set to **0**, the animation is not played. If this parameter is set to **-1**, the animation is played for an infinite number of times. Default value: **1** ( played once). <br>If the value is less than -1, the operation is invalid. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_SetFill()

```c
int32_t OH_ArkUI_AnimatorOption_SetFill(ArkUI_AnimatorOption* option, ArkUI_AnimationFillMode value)
```

**Description**

Sets the status of the component before and after the animator animation execution.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |
| ArkUI_AnimationFillMode value | Status of the component before and after the animator animation execution. Default value: {@link ARKUI_ANIMATION_FILL_MODE_FORWARDS}.<br>    <br>If the value is less than 0, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_SetDirection()

```c
int32_t OH_ArkUI_AnimatorOption_SetDirection(ArkUI_AnimatorOption* option, ArkUI_AnimationDirection value)
```

**Description**

Set the playback direction.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |
| ArkUI_AnimationDirection value | Animation playback direction. <br>If the value is less than 0, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_SetCurve()

```c
int32_t OH_ArkUI_AnimatorOption_SetCurve(ArkUI_AnimatorOption* option, ArkUI_CurveHandle value)
```

**Description**

Sets the interpolation curve for the animation of an animator.

> **Note**:
>
> <b>springCurve</b>, <b>springMotion</b>, <b>responsiveSpringMotion</b>, <b>interpolatingSpring</b>, and <b>customCurve</b> curves are not supported.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) value | Interpolation curve. Default value: {@link ARKUI_CURVE_LINEAR}. You are advised to use<br>    {@link ARKUI_CURVE_EASE_IN_OUT} to obtain a smoother animation effect.<br>    <br>If **value** is set to **NULL**, the default curve {@link ARKUI_CURVE_LINEAR} is used. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_SetBegin()

```c
int32_t OH_ArkUI_AnimatorOption_SetBegin(ArkUI_AnimatorOption* option, float value)
```

**Description**

Sets the interpolation start point of an animation.

> **Note**:
>
> This API does not take effect when the animation is a keyframe animation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |
| float value | Interpolation start point of the animation. Value range: (-∞, +∞). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_SetEnd()

```c
int32_t OH_ArkUI_AnimatorOption_SetEnd(ArkUI_AnimatorOption* option, float value)
```

**Description**

Sets the interpolation end point for the animation of an animator.

> **Note**:
>
> This API does not take effect when the animation is a keyframe animation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |
| float value | Interpolation end point of the animation. Value range: (-∞, +∞). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_SetExpectedFrameRateRange()

```c
int32_t OH_ArkUI_AnimatorOption_SetExpectedFrameRateRange(ArkUI_AnimatorOption* option, ArkUI_ExpectedFrameRateRange* value)
```

**Description**

Sets the expected frame rate range of an animation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |
| [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md)* value | Expected frame rate range. <br>If **value** is set to **NULL**, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_SetKeyframe()

```c
int32_t OH_ArkUI_AnimatorOption_SetKeyframe(ArkUI_AnimatorOption* option, float time, float value, int32_t index)
```

**Description**

Sets the keyframe parameters of an animator animation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |
| float time | Keyframe time. Value range: [0, 1]. The value must be in ascending order. Default value: evenly distributed by index (for example, **0.0** for the first frame, **0.5** for the second frame, and **1.0** for the third frame). <br>If the value of **time** is less than 0 or greater than 1, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |
| float value | Keyframe value. Value range: (-∞, +∞). |
| int32_t index | Keyframe index. <br>If the value of **index** is less than 0, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_SetKeyframeCurve()

```c
int32_t OH_ArkUI_AnimatorOption_SetKeyframeCurve(ArkUI_AnimatorOption* option, ArkUI_CurveHandle value, int32_t index)
```

**Description**

Sets the keyframe curve type for the animation of an animator.

> **Note**:
>
> <b>springCurve</b>, <b>springMotion</b>, <b>responsiveSpringMotion</b>, <b>interpolatingSpring</b>, and <b>customCurve</b> curves are not supported.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) value | Interpolation curve. Default value: **NULL**, indicating linear interpolation. |
| int32_t index | Keyframe index. <br>If the value of **index** is less than 0, the error code {@link ARKUI_ERROR_CODE_PARAM_INVALID} is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_GetDuration()

```c
int32_t OH_ArkUI_AnimatorOption_GetDuration(ArkUI_AnimatorOption* option)
```

**Description**

Obtains the duration for playing an animation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator animation parameters. <br>If **option** is set to **NULL**, **0** is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Duration for playing the animation, in milliseconds. If option is invalid, 0 is returned. |

### OH_ArkUI_AnimatorOption_GetDelay()

```c
int32_t OH_ArkUI_AnimatorOption_GetDelay(ArkUI_AnimatorOption* option)
```

**Description**

Obtains the delay for playing an animation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator animation parameters. If **option** is set to **NULL**, **0** is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Delay for playing the animation, in milliseconds. If option is invalid, 0 is returned. |

### OH_ArkUI_AnimatorOption_GetIterations()

```c
int32_t OH_ArkUI_AnimatorOption_GetIterations(ArkUI_AnimatorOption* option)
```

**Description**

Obtains the number of times that an animator animation is played.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. If **option** is set to **NULL**, **0** is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Number of times that the animation is played. If option is invalid, 0 is returned. |

### OH_ArkUI_AnimatorOption_GetFill()

```c
ArkUI_AnimationFillMode OH_ArkUI_AnimatorOption_GetFill(ArkUI_AnimatorOption* option)
```

**Description**

Obtains the status of the component before and after the animator animation execution.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator animation parameters. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_AnimationFillMode | Status of the component before and after the animator animation execution. If option is invalid,-1      is returned. |

### OH_ArkUI_AnimatorOption_GetDirection()

```c
ArkUI_AnimationDirection OH_ArkUI_AnimatorOption_GetDirection(ArkUI_AnimatorOption* option)
```

**Description**

Obtains the playback direction of an animator animation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator animation parameters. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_AnimationDirection | Animation playback direction. If option is invalid,-1 is returned. |

### OH_ArkUI_AnimatorOption_GetCurve()

```c
ArkUI_CurveHandle OH_ArkUI_AnimatorOption_GetCurve(ArkUI_AnimatorOption* option)
```

**Description**

Obtains the interpolation curve of the animation of an animator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator animation parameters. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Interpolation curve. If option is invalid, NULL is returned. |

### OH_ArkUI_AnimatorOption_GetBegin()

```c
float OH_ArkUI_AnimatorOption_GetBegin(ArkUI_AnimatorOption* option)
```

**Description**

Obtains the interpolation start point of an animation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator animation parameters. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Interpolation start point of the animation. If option is invalid, 0.0 is returned. |

### OH_ArkUI_AnimatorOption_GetEnd()

```c
float OH_ArkUI_AnimatorOption_GetEnd(ArkUI_AnimatorOption* option)
```

**Description**

Obtains the interpolation end point of an animation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator animation parameters. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Interpolation end point of the animation. If option is invalid, 0.0 is returned. |

### OH_ArkUI_AnimatorOption_GetExpectedFrameRateRange()

```c
ArkUI_ExpectedFrameRateRange* OH_ArkUI_AnimatorOption_GetExpectedFrameRateRange(ArkUI_AnimatorOption* option)
```

**Description**

Obtains the expected frame rate range of an animator animation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator animation parameters. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ExpectedFrameRateRange*](capi-arkui-nativemodule-arkui-expectedframeraterange.md) | Pointer to the expected frame rate range object. Returns NULL if a parameter error occurs. |

### OH_ArkUI_AnimatorOption_GetKeyframeTime()

```c
float OH_ArkUI_AnimatorOption_GetKeyframeTime(ArkUI_AnimatorOption* option, int32_t index)
```

**Description**

Obtains the keyframe time of the animator playback, in milliseconds.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. |
| int32_t index | Keyframe index. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Keyframe time, in milliseconds. |

### OH_ArkUI_AnimatorOption_GetKeyframeValue()

```c
float OH_ArkUI_AnimatorOption_GetKeyframeValue(ArkUI_AnimatorOption* option, int32_t index)
```

**Description**

Obtains the keyframe value of an animation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. |
| int32_t index | Keyframe index. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Keyframe value. |

### OH_ArkUI_AnimatorOption_GetKeyframeCurve()

```c
ArkUI_CurveHandle OH_ArkUI_AnimatorOption_GetKeyframeCurve(ArkUI_AnimatorOption* option, int32_t index)
```

**Description**

Obtains the interpolation curve for a keyframe in the animation of an animator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. |
| int32_t index | Keyframe index. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Interpolation curve. Returns NULL if a parameter error occurs. |

### OH_ArkUI_AnimatorEvent_GetUserData()

```c
void* OH_ArkUI_AnimatorEvent_GetUserData(ArkUI_AnimatorEvent* event)
```

**Description**

Obtains the user-defined object in an animation event object.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorEvent](capi-arkui-nativemodule-arkui-animatorevent.md)* event | Animation event object. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | User-defined object. |

### OH_ArkUI_AnimatorOnFrameEvent_GetUserData()

```c
void* OH_ArkUI_AnimatorOnFrameEvent_GetUserData(ArkUI_AnimatorOnFrameEvent* event)
```

**Description**

Obtains the user-defined object in the frame event of an animation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOnFrameEvent](capi-arkui-nativemodule-arkui-animatoronframeevent.md)* event | Animation event object. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | User-defined object. |

### OH_ArkUI_AnimatorOnFrameEvent_GetValue()

```c
float OH_ArkUI_AnimatorOnFrameEvent_GetValue(ArkUI_AnimatorOnFrameEvent* event)
```

**Description**

Obtains the interpolation result in the animation frame callback event object.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOnFrameEvent](capi-arkui-nativemodule-arkui-animatoronframeevent.md)* event | Animation event object. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Animation interpolation result.      <br>NOTE      <br>During the animation, the interpolation result changes between the interpolation start point      [OH_ArkUI_AnimatorOption_SetBegin](capi-native-animate-h.md#oh_arkui_animatoroption_setbegin) and the interpolation end point [OH_ArkUI_AnimatorOption_SetEnd](capi-native-animate-h.md#oh_arkui_animatoroption_setend)      based on the animation parameters. |

### OH_ArkUI_AnimatorOption_RegisterOnFrameCallback()

```c
int32_t OH_ArkUI_AnimatorOption_RegisterOnFrameCallback(ArkUI_AnimatorOption* option, void* userData, void (*callback)(ArkUI_AnimatorOnFrameEvent* event))
```

**Description**

Sets the callback invoked when the animator receives a frame.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_AnimatorOption\* option | Animator animation parameters. |
| void\* userData | User-defined parameter. |
| void (\*callback)(ArkUI_AnimatorOnFrameEvent\* event) | Indicates the callback to set. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_RegisterOnFinishCallback()

```c
int32_t OH_ArkUI_AnimatorOption_RegisterOnFinishCallback(ArkUI_AnimatorOption* option, void* userData, void (*callback)(ArkUI_AnimatorEvent* event))
```

**Description**

Sets the callback invoked when the animation playback is complete.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_AnimatorOption\* option | Animator animation parameters. |
| void\* userData | User-defined parameter. |
| void (\*callback)(ArkUI_AnimatorEvent\* event) | Indicates the callback to set. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_RegisterOnCancelCallback()

```c
int32_t OH_ArkUI_AnimatorOption_RegisterOnCancelCallback(ArkUI_AnimatorOption* option, void* userData, void (*callback)(ArkUI_AnimatorEvent* event))
```

**Description**

Sets the callback invoked when the animation playback is canceled.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_AnimatorOption\* option | Animator animation parameters. |
| void\* userData | User-defined parameter. |
| void (\*callback)(ArkUI_AnimatorEvent\* event) | Indicates the callback to set. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_RegisterOnRepeatCallback()

```c
int32_t OH_ArkUI_AnimatorOption_RegisterOnRepeatCallback(ArkUI_AnimatorOption* option, void* userData, void (*callback)(ArkUI_AnimatorEvent* event))
```

**Description**

Sets the callback invoked when the animation playback is repeated.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_AnimatorOption\* option | Animator animation parameters. |
| void\* userData | User-defined parameter. |
| void (\*callback)(ArkUI_AnimatorEvent\* event) | Indicates the callback to set. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Animator_ResetAnimatorOption()

```c
int32_t OH_ArkUI_Animator_ResetAnimatorOption(ArkUI_AnimatorHandle animatorHandle, ArkUI_AnimatorOption* option)
```

**Description**

Resets the animation of an animator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Animator object. |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator animation parameters. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Animator_Play()

```c
int32_t OH_ArkUI_Animator_Play(ArkUI_AnimatorHandle animatorHandle)
```

**Description**

Starts the animation of an animator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Animator object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Animator_Finish()

```c
int32_t OH_ArkUI_Animator_Finish(ArkUI_AnimatorHandle animatorHandle)
```

**Description**

Ends the animation of an animator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Animator object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Animator_Pause()

```c
int32_t OH_ArkUI_Animator_Pause(ArkUI_AnimatorHandle animatorHandle)
```

**Description**

Pauses the animation of an animator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Animator object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Animator_Cancel()

```c
int32_t OH_ArkUI_Animator_Cancel(ArkUI_AnimatorHandle animatorHandle)
```

**Description**

Cancels the animation of an animator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Animator object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Animator_Reverse()

```c
int32_t OH_ArkUI_Animator_Reverse(ArkUI_AnimatorHandle animatorHandle)
```

**Description**

Plays this animation in reverse order.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Animator object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Curve_CreateCurveByType()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateCurveByType(ArkUI_AnimationCurve curve)
```

**Description**

Implements initialization for the interpolation curve, which is used to create an interpolation curve based on the input parameter.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AnimationCurve curve | Curve type. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Pointer to the interpolation object of the curve. Returns NULL if a parameter error occurs. |

### OH_ArkUI_Curve_CreateStepsCurve()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateStepsCurve(int32_t count, bool end)
```

**Description**

Creates a step curve.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t count | Number of steps. The value must be a positive integer. Value range: [1, +∞). <br>If the value of **count** is abnormal, the operation is invalid. |
| bool end | Whether the step change occurs at the start or end of each interval. **true**: The step change occurs at the end of each interval. **false**: The step change occurs at the start of each interval. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Pointer to the interpolation object of the curve. Returns NULL if a parameter error occurs. |

### OH_ArkUI_Curve_CreateCubicBezierCurve()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateCubicBezierCurve(float x1, float y1, float x2, float y2)
```

**Description**

Creates a cubic Bezier curve.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| float x1 | X-coordinate of the first point on the Bezier curve. Value range: [0, 1]. A value less than 0 is treated as **0**. A value greater than 1 is treated as **1**. |
| float y1 | Y-coordinate of the first point on the Bezier curve. |
| float x2 | X-coordinate of the second point on the Bezier curve. Value range: [0, 1]. A value less than 0 is treated as **0**. A value greater than 1 is treated as **1**. |
| float y2 | Y-coordinate of the second point on the Bezier curve. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Pointer to the interpolation object of the curve. Returns NULL if a parameter error occurs. |

### OH_ArkUI_Curve_CreateSpringCurve()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateSpringCurve(float velocity, float mass, float stiffness, float damping)
```

**Description**

Creates a spring curve. The curve shape is determined by the spring parameters, and the animation duration is controlled by the **duration** parameter in {@link animation} and [animateTo](capi-arkui-nativemodule-arkui-nativeanimateapi-1.md#animateto).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| float velocity | Initial velocity. It is applied by external factors to the spring animation, designed to help ensure the smooth transition from the previous motion state. The velocity is the normalized velocity, and its value is equal to the actual velocity at the beginning of the animation divided by the animation attribute change value. |
| float mass | Mass. It describes the inertia of the object in the elastic system, affecting the amplitude of oscillation and the speed of return to equilibrium. The greater the mass, the greater the amplitude of the oscillation, and the slower the speed of restoring to the equilibrium position. Value range: [0, +∞). <br>If the value is less than or equal to 0, **1** is used. |
| float stiffness | Stiffness. It is the degree to which an object deforms by resisting the force applied. In an elastic system, the greater the stiffness, the stronger the ability to resist deformation, and the faster the speed of restoring to the equilibrium position. Value range: [0, +∞). <br>If the value is less than or equal to 0, **1** is used. |
| float damping | Damping. It is used to describe the oscillation and attenuation of the system after being disturbed. The larger the damping, the smaller the number of oscillations of elastic motion, and the smaller the oscillation amplitude. Value range: [0, +∞). <br>If the value is less than or equal to 0, **1** is used. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Pointer to the interpolation object of the curve. Returns NULL if a parameter error occurs. |

### OH_ArkUI_Curve_CreateSpringMotion()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateSpringMotion(float response, float dampingFraction, float overlapDuration)
```

**Description**

Creates a spring animation curve. If multiple spring animations are applied to the same attribute of an object, each animation replaces their predecessor and inherits the velocity.

> **Note**:
>
> The animation duration is subject to the curve parameters, rather than the <b>duration</b> parameter in <b>animation</b> or <b>animateTo</b>.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| float response | Duration of one complete oscillation. Value range: (0, +∞). <br>If the value is less than or equal to 0, **0.55** is used. |
| float dampingFraction | Damping coefficient. > 0 and < 1: underdamped. In this case, the spring overshoots the equilibrium position. **1**: critically damped. > 1: overdamped. In this case, the spring approaches equilibrium gradually. Value range: (0, +∞). <br>If the value is less than or equal to 0, **0.825** is used. |
| float overlapDuration | Duration for animations to overlap, in seconds. When animations overlap, the **response**<br>values of these animations will transit smoothly over this duration if they are different. Value range: [0, +∞). <br>If the value is less than 0, **0** is used. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Pointer to the interpolation object of the curve. Returns NULL if a parameter error occurs. |

### OH_ArkUI_Curve_CreateResponsiveSpringMotion()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateResponsiveSpringMotion(float response, float dampingFraction, float overlapDuration)
```

**Description**

Creates a responsive spring animation curve. It is a special case of **springMotion**, with the only difference in the default values. It can be used together with **springMotion**.

> **Note**:
>
> The animation duration is subject to the curve parameters, rather than the <b>duration</b> parameter in <b>animation</b> or <b>animateTo</b>.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| float response | Duration of one complete oscillation. Value range: (0, +∞). <br>If the value is less than or equal to 0, **0.15** is used. |
| float dampingFraction | Damping coefficient. > 0 and < 1: underdamped. In this case, the spring overshoots the equilibrium position. **1**: critically damped. > 1: overdamped. In this case, the spring approaches equilibrium gradually. Value range: [0, +∞). <br>If the value is less than 0, **0.86** is used. |
| float overlapDuration | Duration for animations to overlap, in seconds. When animations overlap, the **response**<br>values of these animations will transit smoothly over this duration if they are different. Value range: [0, +∞). <br>If the value is less than 0, **0.25** is used. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Pointer to the interpolation object of the curve. Returns NULL if a parameter error occurs. |

### OH_ArkUI_Curve_CreateInterpolatingSpring()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateInterpolatingSpring(float velocity, float mass, float stiffness, float damping)
```

**Description**

Creates an interpolating spring curve animated from 0 to 1. The actual animation value is calculated based on the curve.

> **Note**:
>
> The animation duration is subject to the curve parameters, rather than the <b>duration</b> parameter in <b>animation</b> or <b>animateTo</b>.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| float velocity | Initial velocity. It is applied by external factors to the spring animation, designed to help ensure the smooth transition from the previous motion state. The velocity is the normalized velocity, and its value is equal to the actual velocity at the beginning of the animation divided by the animation attribute change value. |
| float mass | Mass. It describes the inertia of the object in the elastic system, affecting the amplitude of oscillation and the speed of return to equilibrium. The greater the mass, the greater the amplitude of the oscillation, and the slower the speed of restoring to the equilibrium position. Value range: [0, +∞). <br>If the value is less than or equal to 0, **1** is used. |
| float stiffness | Stiffness. It is the degree to which an object deforms by resisting the force applied. The greater the stiffness, the stronger the ability to resist deformation, and the faster the speed of restoring to the equilibrium position. Value range: [0, +∞). <br>If the value is less than or equal to 0, **1** is used. |
| float damping | Damping. It is used to describe the oscillation and attenuation of the system after being disturbed. The larger the damping, the smaller the number of oscillations of elastic motion, and the smaller the oscillation amplitude. Value range: [0, +∞). <br>If the value is less than or equal to 0, **1** is used. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Pointer to the interpolation object of the curve. Returns NULL if a parameter error occurs. |

### OH_ArkUI_Curve_CreateCustomCurve()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateCustomCurve(void* userData, float (*interpolate)(float fraction, void* userdata))
```

**Description**

Creates a custom curve.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| oid\* userData | Pointer to user-defined data. |
| float (\*interpolate)(float fraction | Indicates the custom interpolation callback. <b>fraction</b> indicates the input x value for interpolation when the animation starts; value range: [0,1]. The return value is the y value of the curve; value range: [0,1]. If <b>fraction</b> is <b>0</b>, the return value <b>0</b> corresponds to the animation start point; any other return value means that the animation jumps at the start point. If <b>fraction</b> is <b>1</b>, the return value <b>1</b> corresponds to the animation end point; any other return value means that the end value of the animation is not the value of the state variable, which will result in an effect of transition from that end value to the value of the state variable. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Pointer to the interpolation object of the curve. Returns NULL if a parameter error occurs. |

### OH_ArkUI_Curve_DisposeCurve()

```c
void OH_ArkUI_Curve_DisposeCurve(ArkUI_CurveHandle curveHandle)
```

**Description**

Disposes of a custom curve.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) curveHandle | Pointer to the interpolation object of the curve. |

### OH_ArkUI_CreateOpacityTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateOpacityTransitionEffect(float opacity)
```

**Description**

Creates an opacity effect object for component transitions.

> **Note**:
>
> If the value specified is less than 0, the value <b>0</b> is used. If the value specified is greater than 1, the value <b>1</b> is used.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| float opacity | Opacity. Value range: [0, 1]. The default value is **1**. A value less than 0 is treated as 0. A value greater than 1 is treated as 1. The value **1** means fully opaque, and **0** means fully transparent. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TransitionEffect*](capi-arkui-nativemodule-arkui-transitioneffect.md) | Opacity effect object for component transitions. |

### OH_ArkUI_CreateTranslationTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateTranslationTransitionEffect(ArkUI_TranslationOptions* translate)
```

**Description**

Creates a translation effect object for component transitions.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_TranslationOptions* translate | Translation parameter object for component transitions. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TransitionEffect*](capi-arkui-nativemodule-arkui-transitioneffect.md) | Translation effect object for component transitions. Returns NULL if a parameter error occurs. |

### OH_ArkUI_CreateScaleTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateScaleTransitionEffect(ArkUI_ScaleOptions* scale)
```

**Description**

Creates a scaling effect object for component transitions.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ScaleOptions* scale | Scaling parameter object for component transitions. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TransitionEffect*](capi-arkui-nativemodule-arkui-transitioneffect.md) | Scaling effect object for component transitions. Returns NULL if a parameter error occurs. |

### OH_ArkUI_CreateRotationTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateRotationTransitionEffect(ArkUI_RotationOptions* rotate)
```

**Description**

Creates a rotation effect object for component transition.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_RotationOptions* rotate | Rotation parameter object for component transitions. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TransitionEffect*](capi-arkui-nativemodule-arkui-transitioneffect.md) | Rotation effect object for component transitions. Returns NULL if a parameter error occurs. |

### OH_ArkUI_CreateMovementTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateMovementTransitionEffect(ArkUI_TransitionEdge edge)
```

**Description**

Creates a movement transition effect object for the component.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_TransitionEdge edge | Movement transition type. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TransitionEffect*](capi-arkui-nativemodule-arkui-transitioneffect.md) | Translation effect object for component transitions. Returns NULL if a parameter error occurs. |

### OH_ArkUI_CreateAsymmetricTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateAsymmetricTransitionEffect(ArkUI_TransitionEffect* appear, ArkUI_TransitionEffect* disappear)
```

**Description**

Creates an asymmetric transition effect.

> **Note**:
>
> If the <b>asymmetric</b> function is not used for <b>TransitionEffect</b>, the transition effect takes effect for both appearance and disappearance of the component.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* appear | Transition effect for appearance. |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* disappear | Transition effect for disappearance. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TransitionEffect*](capi-arkui-nativemodule-arkui-transitioneffect.md) | Asymmetric transition effect. Returns NULL if a parameter error occurs. |

### OH_ArkUI_CreateIdentityTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateIdentityTransitionEffect(void)
```

**Description**

Create an identity transition effect. Identity transition effect performs no visual transition animation. It can alse be used as the appear or disappear parameter of OH_ArkUI_CreateAsymmetricTransitionEffect to indicate no animation on one side.

**Since**: 26.0.0

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TransitionEffect*](capi-arkui-nativemodule-arkui-transitioneffect.md) | Returns a pointer to the created transition effect object. |

### OH_ArkUI_TransitionEffect_Dispose()

```c
void OH_ArkUI_TransitionEffect_Dispose(ArkUI_TransitionEffect* effect)
```

**Description**

Disposes of a transition effect.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* effect | Pointer to the transition effect to be disposed. |

### OH_ArkUI_TransitionEffect_Combine()

```c
int32_t OH_ArkUI_TransitionEffect_Combine(ArkUI_TransitionEffect* firstEffect, ArkUI_TransitionEffect* secondEffect)
```

**Description**

Sets a combination of transition effects.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* firstEffect | Transition effect. |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* secondEffect | Combination of transition effects. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_TransitionEffect_SetAnimation()

```c
int32_t OH_ArkUI_TransitionEffect_SetAnimation(ArkUI_TransitionEffect* effect, ArkUI_AnimateOption* animation)
```

**Description**

Sets transition effect animation settings.

> **Note**:
>
> If <b>combine</b> is used for combining transition effects, the animation settings of a transition effect are applicable to the one following it.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* effect | Transition effect. |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* animation | Animation settings. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |


