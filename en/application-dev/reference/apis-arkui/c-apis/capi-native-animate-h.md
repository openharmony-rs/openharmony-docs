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
| [OH_ArkUI_PropertyAnimation](capi-arkui-nativemodule-oh-arkui-propertyanimation.md) | *OH_ArkUI_PropertyAnimationHandle | Defines the handle to a property animation. |
| [OH_ArkUI_KeyframeAnimation](capi-arkui-nativemodule-oh-arkui-keyframeanimation.md) | *OH_ArkUI_KeyframeAnimationHandle | Defines the handle to a keyframe animation. |
| [OH_ArkUI_PathAnimation](capi-arkui-nativemodule-oh-arkui-pathanimation.md) | *OH_ArkUI_PathAnimationHandle | Defines the handle to a path animation. |
| [OH_ArkUI_AnimationGroup](capi-arkui-nativemodule-oh-arkui-animationgroup.md) | *OH_ArkUI_AnimationGroupHandle | Defines the handle to an animation group. |

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
| [OH_ArkUI_PropertyAnimationHandle OH_ArkUI_NativeModule_PropertyAnimation_Create(OH_ArkUI_AnimationPropertyType propertyType)](#oh_arkui_nativemodule_propertyanimation_create) | Creates a property animation for a specific animatable property.<br> <b>propertyType</b> must be a valid [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype); otherwise, this API returns <b>NULL</b>. |
| [void OH_ArkUI_NativeModule_PropertyAnimation_Destroy(OH_ArkUI_PropertyAnimationHandle animation)](#oh_arkui_nativemodule_propertyanimation_destroy) | Destroys a property animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetFromValue(OH_ArkUI_PropertyAnimationHandle animation, const ArkUI_NumberValue *value, int32_t size)](#oh_arkui_nativemodule_propertyanimation_setfromvalue) | Sets the start value of a property animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetFromValue(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_NumberValue *value, int32_t size)](#oh_arkui_nativemodule_propertyanimation_getfromvalue) | Obtains the start value of a property animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetToValue(OH_ArkUI_PropertyAnimationHandle animation, const ArkUI_NumberValue *value, int32_t size)](#oh_arkui_nativemodule_propertyanimation_settovalue) | Sets the end value of a property animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetToValue(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_NumberValue *value, int32_t size)](#oh_arkui_nativemodule_propertyanimation_gettovalue) | Obtains the end value of a property animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetDuration(OH_ArkUI_PropertyAnimationHandle animation, int32_t duration)](#oh_arkui_nativemodule_propertyanimation_setduration) | Sets the duration for a property animation.<br> The actual effective animation duration is determined by priority: if the duration is set via this API, that value is used; otherwise, the duration set on the animation group via [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, **1000** ms is used. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetDuration(OH_ArkUI_PropertyAnimationHandle animation, int32_t *duration)](#oh_arkui_nativemodule_propertyanimation_getduration) | Obtains the duration of a property animation.<br> This API returns only the duration explicitly set on this animation; the value inherited from the animation group or the default is resolved at runtime and is not stored on this object. If the duration has not been set on this animation, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. The actual effective animation duration used at runtime is determined by priority: if set via [OH_ArkUI_NativeModule_PropertyAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setduration), that value is used; otherwise, the group's duration via [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, **1000** ms is used. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetDelay(OH_ArkUI_PropertyAnimationHandle animation, int32_t delay)](#oh_arkui_nativemodule_propertyanimation_setdelay) | Sets the delay for a property animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetDelay(OH_ArkUI_PropertyAnimationHandle animation, int32_t *delay)](#oh_arkui_nativemodule_propertyanimation_getdelay) | Obtains the delay of a property animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetCurve(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_CurveHandle curve)](#oh_arkui_nativemodule_propertyanimation_setcurve) | Sets the animation curve for a property animation.<br> The actual effective animation curve is determined by priority: if the curve is set via this API, that value is used; otherwise, the curve set on the animation group via [OH_ArkUI_NativeModule_AnimationGroup_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setcurve) is used; if neither is set, [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) is used. Spring curves (<b>springMotion</b>, <b>responsiveSpringMotion</b>, and <b>interpolatingSpring</b>) are supported. When a spring curve is set, the duration set via [OH_ArkUI_NativeModule_PropertyAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setduration) does not take effect; the animation duration is determined by the spring curve. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetCurve(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_CurveHandle *outBorrowedCurve)](#oh_arkui_nativemodule_propertyanimation_getcurve) | Obtains the animation curve of a property animation.<br> This API returns only the curve explicitly set on this animation; the value inherited from the animation group or the default is resolved at runtime and is not stored on this object. If the curve has not been set on this animation, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. The actual effective animation curve used at runtime is determined by priority: if set via [OH_ArkUI_NativeModule_PropertyAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setcurve), that value is used; otherwise, the group's curve via [OH_ArkUI_NativeModule_AnimationGroup_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setcurve) is used; if neither is set, [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) is used. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetTempo(OH_ArkUI_PropertyAnimationHandle animation, float tempo)](#oh_arkui_nativemodule_propertyanimation_settempo) | Sets the tempo for a property animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetTempo(OH_ArkUI_PropertyAnimationHandle animation, float *tempo)](#oh_arkui_nativemodule_propertyanimation_gettempo) | Obtains the tempo of a property animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetAutoReverse(OH_ArkUI_PropertyAnimationHandle animation, bool autoReverse)](#oh_arkui_nativemodule_propertyanimation_setautoreverse) | Sets whether to auto-reverse a property animation.<br> When auto-reverse is enabled, the animation plays forward and then backward alternately across iterations. The default value is <b>false</b>. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetAutoReverse(OH_ArkUI_PropertyAnimationHandle animation, bool *autoReverse)](#oh_arkui_nativemodule_propertyanimation_getautoreverse) | Obtains whether auto-reverse is enabled for a property animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetIterations(OH_ArkUI_PropertyAnimationHandle animation, int32_t iterations)](#oh_arkui_nativemodule_propertyanimation_setiterations) | Sets the number of iterations for a property animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetIterations(OH_ArkUI_PropertyAnimationHandle animation, int32_t *iterations)](#oh_arkui_nativemodule_propertyanimation_getiterations) | Obtains the number of iterations of a property animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_RenderNodeHandle targetNode)](#oh_arkui_nativemodule_propertyanimation_settargetnode) | Sets the target render node for a property animation.<br> The target node is the render node animated by this property animation. If <b>NULL</b> (the default), the animation inherits the group's default target set by [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode). A non-NULL target must belong to the same UIContext that the group is registered on; the check is performed when the group is registered by [OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetTargetNode(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_RenderNodeHandle *outBorrowedTargetNode)](#oh_arkui_nativemodule_propertyanimation_gettargetnode) | Obtains the target render node of a property animation. |
| [OH_ArkUI_KeyframeAnimationHandle OH_ArkUI_NativeModule_KeyframeAnimation_Create(OH_ArkUI_AnimationPropertyType propertyType, int32_t size)](#oh_arkui_nativemodule_keyframeanimation_create) | Creates a keyframe animation for a specific animatable property.<br> The key time of each keyframe defaults to being evenly distributed in [0, 1] by index (for example, when there are 3 keyframes, <b>0.0</b> for the first frame, <b>0.5</b> for the second frame, and <b>1.0</b> for the third frame). Use [OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTimes](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setkeytimes) or [OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTime](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setkeytime) to customize the key time points.<br> <b>propertyType</b> must be a valid [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype), and <b>size</b> must be at least 2; otherwise, this API returns <b>NULL</b>. |
| [void OH_ArkUI_NativeModule_KeyframeAnimation_Destroy(OH_ArkUI_KeyframeAnimationHandle animation)](#oh_arkui_nativemodule_keyframeanimation_destroy) | Destroys a keyframe animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTimes(OH_ArkUI_KeyframeAnimationHandle animation, const float *keyTimes, int32_t size)](#oh_arkui_nativemodule_keyframeanimation_setkeytimes) | Sets the keyframe key time points.<br> If this API is not called, the key time of each keyframe defaults to being evenly distributed in [0, 1] by index (for example, when there are 3 keyframes, <b>0.0</b> for the first frame, <b>0.5</b> for the second frame, and <b>1.0</b> for the third frame).<br> The elements in <b>keyTimes</b> must be non-decreasing, and <b>size</b> must equal the number of keyframes of the keyframe animation (the <b>size</b> value specified when the animation was created via [OH_ArkUI_NativeModule_KeyframeAnimation_Create](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_create)). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetKeyTime(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, float *keyTime)](#oh_arkui_nativemodule_keyframeanimation_getkeytime) | Obtains the key time point of a keyframe at the specified index. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTime(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, float keyTime)](#oh_arkui_nativemodule_keyframeanimation_setkeytime) | Sets the key time point of a keyframe at the specified index.<br> If this API is not called for a keyframe, its key time defaults to being evenly distributed in [0, 1] by index (for example, when there are 3 keyframes, <b>0.0</b> for the first frame, <b>0.5</b> for the second frame, and <b>1.0</b> for the third frame). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetValue(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, const ArkUI_NumberValue *value, int32_t size)](#oh_arkui_nativemodule_keyframeanimation_setvalue) | Sets the value of a keyframe at the specified index. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetValues(OH_ArkUI_KeyframeAnimationHandle animation, const ArkUI_NumberValue *values, int32_t size)](#oh_arkui_nativemodule_keyframeanimation_setvalues) | Sets the values for all keyframes at once.<br> The values are provided as a flat array. The number of elements per keyframe depends on [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype). For example, OPACITY requires 1 value per keyframe, and TRANSLATION requires 2 values per keyframe. The total number of elements must equal the number of keyframes multiplied by the number of values per keyframe. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetValue(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, ArkUI_NumberValue *value, int32_t size)](#oh_arkui_nativemodule_keyframeanimation_getvalue) | Obtains the value of a keyframe at the specified index. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetCurves(OH_ArkUI_KeyframeAnimationHandle animation, const ArkUI_CurveHandle *value, int32_t size)](#oh_arkui_nativemodule_keyframeanimation_setcurves) | Sets the animation curves for keyframes. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, ArkUI_CurveHandle curve)](#oh_arkui_nativemodule_keyframeanimation_setcurve) | Sets the animation curve for a keyframe at the specified index. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetCurve(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, ArkUI_CurveHandle *outBorrowedCurve)](#oh_arkui_nativemodule_keyframeanimation_getcurve) | Obtains the curve of a keyframe at the specified index.<br> This API returns only the curve explicitly set for the keyframe; the value inherited from the animation group or the default is resolved at runtime and is not stored on this object. If the curve has not been set for the keyframe, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. The actual effective animation curve used at runtime is determined by priority: if set for the keyframe via [OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setcurve) or [OH_ArkUI_NativeModule_KeyframeAnimation_SetCurves](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setcurves), that value is used; otherwise, the group's curve via [OH_ArkUI_NativeModule_AnimationGroup_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setcurve) is used; if neither is set, [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) is used. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration(OH_ArkUI_KeyframeAnimationHandle animation, int32_t duration)](#oh_arkui_nativemodule_keyframeanimation_setduration) | Sets the duration for a keyframe animation.<br> The actual effective animation duration is determined by priority: if the duration is set via this API, that value is used; otherwise, the duration set on the animation group via [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, **1000** ms is used. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetDuration(OH_ArkUI_KeyframeAnimationHandle animation, int32_t *duration)](#oh_arkui_nativemodule_keyframeanimation_getduration) | Obtains the duration of a keyframe animation.<br> This API returns only the duration explicitly set on this animation; the value inherited from the animation group or the default is resolved at runtime and is not stored on this object. If the duration has not been set on this animation, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. The actual effective animation duration used at runtime is determined by priority: if set via [OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setduration), that value is used; otherwise, the group's duration via [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, **1000** ms is used. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetDelay(OH_ArkUI_KeyframeAnimationHandle animation, int32_t delay)](#oh_arkui_nativemodule_keyframeanimation_setdelay) | Sets the delay for a keyframe animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetDelay(OH_ArkUI_KeyframeAnimationHandle animation, int32_t *delay)](#oh_arkui_nativemodule_keyframeanimation_getdelay) | Obtains the delay of a keyframe animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetTempo(OH_ArkUI_KeyframeAnimationHandle animation, float tempo)](#oh_arkui_nativemodule_keyframeanimation_settempo) | Sets the tempo for a keyframe animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetTempo(OH_ArkUI_KeyframeAnimationHandle animation, float *tempo)](#oh_arkui_nativemodule_keyframeanimation_gettempo) | Obtains the tempo of a keyframe animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetAutoReverse(OH_ArkUI_KeyframeAnimationHandle animation, bool autoReverse)](#oh_arkui_nativemodule_keyframeanimation_setautoreverse) | Sets whether to auto-reverse a keyframe animation.<br> When auto-reverse is enabled, the animation plays forward and then backward alternately across iterations. The default value is <b>false</b>. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetAutoReverse(OH_ArkUI_KeyframeAnimationHandle animation, bool *autoReverse)](#oh_arkui_nativemodule_keyframeanimation_getautoreverse) | Obtains whether auto-reverse is enabled for a keyframe animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetIterations(OH_ArkUI_KeyframeAnimationHandle animation, int32_t iterations)](#oh_arkui_nativemodule_keyframeanimation_setiterations) | Sets the number of iterations for a keyframe animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetIterations(OH_ArkUI_KeyframeAnimationHandle animation, int32_t *iterations)](#oh_arkui_nativemodule_keyframeanimation_getiterations) | Obtains the number of iterations of a keyframe animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode(OH_ArkUI_KeyframeAnimationHandle animation, ArkUI_RenderNodeHandle targetNode)](#oh_arkui_nativemodule_keyframeanimation_settargetnode) | Sets the target render node for a keyframe animation.<br> The target node is the render node animated by this keyframe animation. If <b>NULL</b> (the default), the animation inherits the group's default target set by [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode). A non-NULL target must belong to the same UIContext that the group is registered on; the check is performed when the group is registered by [OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetTargetNode(OH_ArkUI_KeyframeAnimationHandle animation, ArkUI_RenderNodeHandle *outBorrowedTargetNode)](#oh_arkui_nativemodule_keyframeanimation_gettargetnode) | Obtains the target render node of a keyframe animation. |
| [OH_ArkUI_PathAnimationHandle OH_ArkUI_NativeModule_PathAnimation_Create(const char *path)](#oh_arkui_nativemodule_pathanimation_create) | Creates a path animation that moves the component along a geometric path.<br> The path animation applies to the TRANSLATION property. |
| [void OH_ArkUI_NativeModule_PathAnimation_Destroy(OH_ArkUI_PathAnimationHandle animation)](#oh_arkui_nativemodule_pathanimation_destroy) | Destroys a path animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetDuration(OH_ArkUI_PathAnimationHandle animation, int32_t duration)](#oh_arkui_nativemodule_pathanimation_setduration) | Sets the duration for a path animation.<br> The actual effective animation duration is determined by priority: if the duration is set via this API, that value is used; otherwise, the duration set on the animation group via [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, **1000** ms is used. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetDuration(OH_ArkUI_PathAnimationHandle animation, int32_t *duration)](#oh_arkui_nativemodule_pathanimation_getduration) | Obtains the duration of a path animation.<br> This API returns only the duration explicitly set on this animation; the value inherited from the animation group or the default is resolved at runtime and is not stored on this object. If the duration has not been set on this animation, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. The actual effective animation duration used at runtime is determined by priority: if set via [OH_ArkUI_NativeModule_PathAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_setduration), that value is used; otherwise, the group's duration via [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, **1000** ms is used. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetDelay(OH_ArkUI_PathAnimationHandle animation, int32_t delay)](#oh_arkui_nativemodule_pathanimation_setdelay) | Sets the delay for a path animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetDelay(OH_ArkUI_PathAnimationHandle animation, int32_t *delay)](#oh_arkui_nativemodule_pathanimation_getdelay) | Obtains the delay of a path animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetCurve(OH_ArkUI_PathAnimationHandle animation, ArkUI_CurveHandle curve)](#oh_arkui_nativemodule_pathanimation_setcurve) | Sets the animation curve for a path animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetCurve(OH_ArkUI_PathAnimationHandle animation, ArkUI_CurveHandle *outBorrowedCurve)](#oh_arkui_nativemodule_pathanimation_getcurve) | Obtains the animation curve of a path animation.<br> This API returns only the curve explicitly set on this animation; the value inherited from the animation group or the default is resolved at runtime and is not stored on this object. If the curve has not been set on this animation, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. The actual effective animation curve used at runtime is determined by priority: if set via [OH_ArkUI_NativeModule_PathAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_setcurve), that value is used; otherwise, the group's curve via [OH_ArkUI_NativeModule_AnimationGroup_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setcurve) is used; if neither is set, [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) is used. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetTempo(OH_ArkUI_PathAnimationHandle animation, float tempo)](#oh_arkui_nativemodule_pathanimation_settempo) | Sets the tempo for a path animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetTempo(OH_ArkUI_PathAnimationHandle animation, float *tempo)](#oh_arkui_nativemodule_pathanimation_gettempo) | Obtains the tempo of a path animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetAutoReverse(OH_ArkUI_PathAnimationHandle animation, bool autoReverse)](#oh_arkui_nativemodule_pathanimation_setautoreverse) | Sets whether to auto-reverse a path animation.<br> When auto-reverse is enabled, the animation plays forward and then backward alternately across iterations. The default value is <b>false</b>. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetAutoReverse(OH_ArkUI_PathAnimationHandle animation, bool *autoReverse)](#oh_arkui_nativemodule_pathanimation_getautoreverse) | Obtains whether auto-reverse is enabled for a path animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetIterations(OH_ArkUI_PathAnimationHandle animation, int32_t iterations)](#oh_arkui_nativemodule_pathanimation_setiterations) | Sets the number of iterations for a path animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetIterations(OH_ArkUI_PathAnimationHandle animation, int32_t *iterations)](#oh_arkui_nativemodule_pathanimation_getiterations) | Obtains the number of iterations of a path animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetAutoRotation(OH_ArkUI_PathAnimationHandle animation, bool autoRotation)](#oh_arkui_nativemodule_pathanimation_setautorotation) | Sets whether the component auto-rotates to align with the path tangent during a path animation.<br> When auto-rotation is enabled, the component rotates so that its heading direction aligns with the tangent of the path at the current position. The default value is <b>false</b>. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetAutoRotation(OH_ArkUI_PathAnimationHandle animation, bool *autoRotation)](#oh_arkui_nativemodule_pathanimation_getautorotation) | Obtains whether auto-rotation is enabled for a path animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetTargetNode(OH_ArkUI_PathAnimationHandle animation, ArkUI_RenderNodeHandle targetNode)](#oh_arkui_nativemodule_pathanimation_settargetnode) | Sets the target render node for a path animation.<br> The target node is the render node animated by this path animation. If <b>NULL</b> (the default), the animation inherits the group's default target set by [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode). A non-NULL target must belong to the same UIContext that the group is registered on; the check is performed when the group is registered by [OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetTargetNode(OH_ArkUI_PathAnimationHandle animation, ArkUI_RenderNodeHandle *outBorrowedTargetNode)](#oh_arkui_nativemodule_pathanimation_gettargetnode) | Obtains the target render node of a path animation. |
| [OH_ArkUI_AnimationGroupHandle OH_ArkUI_NativeModule_AnimationGroup_Create(void)](#oh_arkui_nativemodule_animationgroup_create) | Creates an animation group. |
| [void OH_ArkUI_NativeModule_AnimationGroup_Destroy(OH_ArkUI_AnimationGroupHandle group)](#oh_arkui_nativemodule_animationgroup_destroy) | Destroys the frontend handle of an animation group.<br> This releases the frontend handle only. The backend (runtime) objects of a group that has been registered via [OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup) are released separately — automatically when the finish callback is invoked, or via [OH_ArkUI_NativeModule_RemoveAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_removeanimationgroup).<br> The child animations added to the group are not automatically destroyed. Call OH_ArkUI_NativeModule_PropertyAnimation_Destroy, OH_ArkUI_NativeModule_KeyframeAnimation_Destroy or OH_ArkUI_NativeModule_PathAnimation_Destroy separately. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetDuration(OH_ArkUI_AnimationGroupHandle group, int32_t duration)](#oh_arkui_nativemodule_animationgroup_setduration) | Sets the duration for an animation group.<br> The group's duration serves as the default duration for child animations that do not set their own duration via [OH_ArkUI_NativeModule_PropertyAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setduration), [OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setduration), or [OH_ArkUI_NativeModule_PathAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_setduration). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetDuration(OH_ArkUI_AnimationGroupHandle group, int32_t *duration)](#oh_arkui_nativemodule_animationgroup_getduration) | Obtains the duration of an animation group.<br> This API returns only the duration explicitly set on this animation group, and is not affected by the duration of child animations. If the duration has not been set on this group, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. At runtime, an unset group duration defaults to **1000** ms. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetDelay(OH_ArkUI_AnimationGroupHandle group, int32_t delay)](#oh_arkui_nativemodule_animationgroup_setdelay) | Sets the delay for an animation group. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetDelay(OH_ArkUI_AnimationGroupHandle group, int32_t *delay)](#oh_arkui_nativemodule_animationgroup_getdelay) | Obtains the delay of an animation group. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetCurve(OH_ArkUI_AnimationGroupHandle group, ArkUI_CurveHandle curve)](#oh_arkui_nativemodule_animationgroup_setcurve) | Sets the animation curve for an animation group.<br> The group's curve serves as the default curve for child animations that do not set their own curve via [OH_ArkUI_NativeModule_PropertyAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setcurve), [OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setcurve), or [OH_ArkUI_NativeModule_PathAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_setcurve). The <b>springMotion</b>, <b>responsiveSpringMotion</b>, and <b>interpolatingSpring</b> curves are not supported because they do not have effective duration settings. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetCurve(OH_ArkUI_AnimationGroupHandle group, ArkUI_CurveHandle *outBorrowedCurve)](#oh_arkui_nativemodule_animationgroup_getcurve) | Obtains the animation curve of an animation group.<br> This API returns only the curve explicitly set on this animation group, and is not affected by the curve of child animations. If the curve has not been set on this group, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. At runtime, an unset group curve defaults to [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetTempo(OH_ArkUI_AnimationGroupHandle group, float tempo)](#oh_arkui_nativemodule_animationgroup_settempo) | Sets the tempo for an animation group. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetTempo(OH_ArkUI_AnimationGroupHandle group, float *tempo)](#oh_arkui_nativemodule_animationgroup_gettempo) | Obtains the tempo of an animation group. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetAutoReverse(OH_ArkUI_AnimationGroupHandle group, bool autoReverse)](#oh_arkui_nativemodule_animationgroup_setautoreverse) | Sets whether to auto-reverse an animation group.<br> When auto-reverse is enabled, the animation group plays forward and then backward alternately across iterations. The default value is <b>false</b>. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetAutoReverse(OH_ArkUI_AnimationGroupHandle group, bool *autoReverse)](#oh_arkui_nativemodule_animationgroup_getautoreverse) | Obtains whether auto-reverse is enabled for an animation group. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetIterations(OH_ArkUI_AnimationGroupHandle group, int32_t iterations)](#oh_arkui_nativemodule_animationgroup_setiterations) | Sets the number of iterations for an animation group. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetIterations(OH_ArkUI_AnimationGroupHandle group, int32_t *iterations)](#oh_arkui_nativemodule_animationgroup_getiterations) | Obtains the number of iterations of an animation group. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetExpectedFrameRateRange(OH_ArkUI_AnimationGroupHandle group, const ArkUI_ExpectedFrameRateRange *frameRate)](#oh_arkui_nativemodule_animationgroup_setexpectedframeraterange) | Sets the expected frame rate range for an animation group. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetExpectedFrameRateRange(OH_ArkUI_AnimationGroupHandle group, ArkUI_ExpectedFrameRateRange *frameRate)](#oh_arkui_nativemodule_animationgroup_getexpectedframeraterange) | Obtains the expected frame rate range of an animation group. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_RegisterOnFinishCallback(OH_ArkUI_AnimationGroupHandle group, void *userData, void (\*callback)(void *userData))](#oh_arkui_nativemodule_animationgroup_registeronfinishcallback) | Registers a callback to be invoked when the animation group playback is complete.<br> An animation group has one finish callback. Registering another callback replaces the previous callback and userData pair. Registering the same callback and userData pair again succeeds without creating an additional registration. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode(OH_ArkUI_AnimationGroupHandle group, ArkUI_RenderNodeHandle targetNode)](#oh_arkui_nativemodule_animationgroup_settargetnode) | Sets the default target render node for an animation group.<br> The default target is the render node animated by child animations that do not set their own target via [OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_settargetnode), [OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_settargetnode), or [OH_ArkUI_NativeModule_PathAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_settargetnode). Every child must resolve to a non-NULL target (its own, or this group default) when the group is registered by [OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup); any resolved target must belong to the same UIContext that the group is registered on. The default value is <b>NULL</b>. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetTargetNode(OH_ArkUI_AnimationGroupHandle group, ArkUI_RenderNodeHandle *outBorrowedTargetNode)](#oh_arkui_nativemodule_animationgroup_gettargetnode) | Obtains the default target render node of an animation group. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_AddPropertyAnimation(OH_ArkUI_AnimationGroupHandle group, OH_ArkUI_PropertyAnimationHandle animation)](#oh_arkui_nativemodule_animationgroup_addpropertyanimation) | Adds a property animation to an animation group.<br> The target node of the animation is determined by [OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_settargetnode); if not set, the animation inherits the group's default target set by [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode). Every child must resolve to a non-NULL target when the group is registered. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_AddKeyframeAnimation(OH_ArkUI_AnimationGroupHandle group, OH_ArkUI_KeyframeAnimationHandle animation)](#oh_arkui_nativemodule_animationgroup_addkeyframeanimation) | Adds a keyframe animation to an animation group.<br> The target node of the animation is determined by [OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_settargetnode); if not set, the animation inherits the group's default target set by [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode). Every child must resolve to a non-NULL target when the group is registered. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_AddPathAnimation(OH_ArkUI_AnimationGroupHandle group, OH_ArkUI_PathAnimationHandle animation)](#oh_arkui_nativemodule_animationgroup_addpathanimation) | Adds a path animation to an animation group.<br> The target node of the animation is determined by [OH_ArkUI_NativeModule_PathAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_settargetnode); if not set, the animation inherits the group's default target set by [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode). Every child must resolve to a non-NULL target when the group is registered. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AddAnimationGroup(ArkUI_ContextHandle context, OH_ArkUI_AnimationGroupHandle group, const char *key)](#oh_arkui_nativemodule_addanimationgroup) | Registers an animation group on a UIContext with a specified key and starts playback.<br> The UIContext owns the group by <b>key</b>: once registered, the UIContext holds the group's backend (runtime) objects, and the caller may destroy the frontend group handle (and child animation handles) after registration since the backend runs independently by (UIContext, key). Keys are scoped per UIContext (instance): the same key in different UIContexts does not collide. Within one UIContext, if a group is already registered with the same key, the system removes the previous group first (releasing its backend objects) and then registers the new group. The group is later identified and managed by the same (UIContext, key) pair.<br> Each child animation added via [OH_ArkUI_NativeModule_AnimationGroup_AddPropertyAnimation](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_addpropertyanimation), [OH_ArkUI_NativeModule_AnimationGroup_AddKeyframeAnimation](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_addkeyframeanimation), or [OH_ArkUI_NativeModule_AnimationGroup_AddPathAnimation](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_addpathanimation) animates the target node set by its own <b>SetTargetNode</b> API; if that target is not set (or is <b>NULL</b>), it inherits the group's default target set by [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode). At registration, every child must resolve to a non-NULL target node (its own, or the group default), and every resolved target node must belong to the same UIContext as <b>context</b>; otherwise, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned.<br> Playback control and lifecycle APIs ([OH_ArkUI_NativeModule_RemoveAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_removeanimationgroup), [OH_ArkUI_NativeModule_GetAnimationGroupState](capi-native-animate-h.md#oh_arkui_nativemodule_getanimationgroupstate), [OH_ArkUI_NativeModule_HasAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_hasanimationgroup), [OH_ArkUI_NativeModule_PauseAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_pauseanimationgroup), [OH_ArkUI_NativeModule_ResumeAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_resumeanimationgroup), [OH_ArkUI_NativeModule_FinishAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_finishanimationgroup) are all keyed by the (UIContext, key) pair.<br> The finish callback (see [OH_ArkUI_NativeModule_AnimationGroup_RegisterOnFinishCallback](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_registeronfinishcallback)) is invoked exactly once after natural completion, [OH_ArkUI_NativeModule_FinishAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_finishanimationgroup), or destruction of a target node. If [OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup) returns an error, the finish callback is not invoked. After the callback returns, the system automatically removes the group from the UIContext and releases the backend (runtime) objects of the group and its child animations; the frontend handles (the group and its child animations) must still be destroyed by the caller via [OH_ArkUI_NativeModule_AnimationGroup_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_destroy), [OH_ArkUI_NativeModule_PropertyAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_destroy), [OH_ArkUI_NativeModule_KeyframeAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_destroy), or [OH_ArkUI_NativeModule_PathAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_destroy). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_RemoveAnimationGroup(ArkUI_ContextHandle context, const char *key)](#oh_arkui_nativemodule_removeanimationgroup) | Removes the animation group identified by the specified key from the UIContext.<br> Stops the group (if still running) and releases the backend (runtime) objects of the group and its child animations. The animated target nodes are restored to their state at the start of the animation. The frontend handles (the group and its child animations) are not freed by this call and must be destroyed by the caller via [OH_ArkUI_NativeModule_AnimationGroup_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_destroy), [OH_ArkUI_NativeModule_PropertyAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_destroy), [OH_ArkUI_NativeModule_KeyframeAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_destroy), or [OH_ArkUI_NativeModule_PathAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_destroy). Use this only for a group that has not stopped on its own (for example, a paused group); once the finish callback is invoked, the group is removed automatically. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_GetAnimationGroupState(ArkUI_ContextHandle context, const char *key, OH_ArkUI_AnimationGroupState *state)](#oh_arkui_nativemodule_getanimationgroupstate) | Obtains the playback state of an animation group identified by the specified key on the UIContext. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_HasAnimationGroup(ArkUI_ContextHandle context, const char *key, bool *exists)](#oh_arkui_nativemodule_hasanimationgroup) | Checks whether an animation group with the specified key exists on the UIContext. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PauseAnimationGroup(ArkUI_ContextHandle context, const char *key)](#oh_arkui_nativemodule_pauseanimationgroup) | Pauses the animation group identified by the specified key on the UIContext.<br> The animation group must be in the RUNNING state; otherwise, [ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ResumeAnimationGroup(ArkUI_ContextHandle context, const char *key)](#oh_arkui_nativemodule_resumeanimationgroup) | Resumes the animation group identified by the specified key on the UIContext.<br> The animation group must be in the PAUSED state; otherwise, [ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_FinishAnimationGroup(ArkUI_ContextHandle context, const char *key, OH_ArkUI_AnimationFinishMode mode)](#oh_arkui_nativemodule_finishanimationgroup) | Finishes the animation group identified by the specified key on the UIContext.<br> The animation group is finished according to the specified finish mode: jump to the end state, jump to the start state, or stay at the current value. The animation group must be in the RUNNING or PAUSED state; otherwise, [ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

## Function description

### OH_ArkUI_AnimateOption_Create()

```c
ArkUI_AnimateOption* OH_ArkUI_AnimateOption_Create()
```

**Description**

Creates an animation configuration.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration. <br>If **option** is set to **NULL**, the operation is invalid. |
| ArkUI_AnimationCurve value | Animation curve. Default value: [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve). You are advised to use [ARKUI_CURVE_EASE_IN_OUT](capi-native-type-visual-h.md#arkui_animationcurve) to obtain a smoother animation effect. <br>If the value is abnormal, the setting is invalid. |

### OH_ArkUI_AnimateOption_SetDelay()

```c
void OH_ArkUI_AnimateOption_SetDelay(ArkUI_AnimateOption* option, int32_t value)
```

**Description**

Sets the animation delay, in milliseconds.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration. <br>If **option** is set to **NULL**, the operation is invalid. |
| ArkUI_AnimationPlayMode value | Animation playback mode. Default value: [ARKUI_ANIMATION_PLAY_MODE_NORMAL](capi-native-type-visual-h.md#arkui_animationplaymode). <br>If the value is abnormal, the operation is invalid. |

### OH_ArkUI_AnimateOption_SetExpectedFrameRateRange()

```c
void OH_ArkUI_AnimateOption_SetExpectedFrameRateRange(ArkUI_AnimateOption* option, ArkUI_ExpectedFrameRateRange* value)
```

**Description**

Defines a struct for the expected frame rate range of the animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Keyframe animation parameters. <br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| int32_t value | Animation delay, in milliseconds. Value range: (-∞, +∞). Default value: **0**, indicating no animation delay. A value greater than 0 means to begin the animation after the specified amount of time has elapsed. A value less than 0 means to begin the animation in advance. If **value** is less than **0** and the absolute value of **value** is less than the actual animation duration, the animation starts its first frame from the state at the absolute value. If the absolute value of **value** is greater than or equal to the actual animation duration, the animation starts its first frame from the end state. The actual animation duration is equal to the duration of a single animation multiplied by the number of animation playback times. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_KeyframeAnimateOption_SetIterations()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_SetIterations(ArkUI_KeyframeAnimateOption* option, int32_t value)
```

**Description**

Sets the number of times that the keyframe animation is played. By default, the animation is played once. The value **-1** indicates that the animation is played for an unlimited number of times. The value **0** indicates that no animation is played.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Keyframe animation parameters. <br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| int32_t value | Number of times that the animation is played. Value range: [-1, +∞). If this parameter is set to **0**, the animation is not played. If this parameter is set to **-1**, the animation is played for an infinite number of times. Default value: **1**, indicating that the animation is played once. <br>If the value is less than **-1**, the operation is invalid, and the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_KeyframeAnimateOption_RegisterOnFinishCallback()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_RegisterOnFinishCallback(ArkUI_KeyframeAnimateOption* option, void* userData, void (*onFinish)(void* userData))
```

**Description**

Sets the callback invoked when the keyframe animation playback is complete. This function is called after the {@link keyframe animation} has played for the specified number of times.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_KeyframeAnimateOption\* option | Keyframe animation parameters. <br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| void\* userData | Pointer to a custom object. <br>Abnormal value processing is not involved. |
| void (\*onFinish)(void\* userData) | Indicates the callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_KeyframeAnimateOption_SetExpectedFrameRate()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_SetExpectedFrameRate(ArkUI_KeyframeAnimateOption* option, ArkUI_ExpectedFrameRateRange* frameRate)
```

**Description**

Sets the expected frame rate for a keyframe animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Keyframe animation parameters. <br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md)* frameRate | Expected frame rate for the keyframe animation. <br>If **frameRate** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_KeyframeAnimateOption_SetDuration()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_SetDuration(ArkUI_KeyframeAnimateOption* option, int32_t value, int32_t index)
```

**Description**

Sets the duration of a keyframe animation, in milliseconds.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Keyframe animation parameters. <br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| int32_t value | Keyframe animation duration, in ms. The default value is 1000 ms. Value range: [0, +∞). <br>If the value is less than 0, **0** is used. |
| int32_t index | Index of the keyframe state segment. <br>If the value of **index** is less than 0, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_KeyframeAnimateOption_SetCurve()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_SetCurve(ArkUI_KeyframeAnimateOption* option, ArkUI_CurveHandle value, int32_t index)
```

**Description**

Sets the animation curve for a specific keyframe animation segment.

> **Note**:
>
> Because the <b>springMotion</b>, <b>responsiveSpringMotion</b>, and <b>interpolatingSpring</b> curves do not have effective duration settings, they are not supported.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Keyframe animation parameters. <br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) value | Animation curve to set. Default value: [ARKUI_CURVE_EASE_IN_OUT](capi-native-type-visual-h.md#arkui_animationcurve). |
| int32_t index | Index of the keyframe state segment. Value range: [0, size – 1], where **size** indicates the number of keyframe animation states. <br>If the value of **index** is less than 0 or out of range, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_KeyframeAnimateOption_RegisterOnEventCallback()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_RegisterOnEventCallback(ArkUI_KeyframeAnimateOption* option, void* userData, void (*event)(void* userData), int32_t index)
```

**Description**

Sets the closure function of the state at the time of the keyframe, that is, the state to be reached at the time of the keyframe.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_KeyframeAnimateOption\* option | Keyframe animation parameters. <br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| void (\*event)(void\* userData) | Indicates a closure function. |
| void\* userData | Pointer to a user-defined object. <br>Abnormal value processing is not involved. |
| int32_t index | Index of the keyframe state segment. Value range: [0, size – 1], where **size** indicates the number of keyframe animation states. <br>If the value of **index** is less than 0 or out of range, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_KeyframeAnimateOption_GetDelay()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_GetDelay(ArkUI_KeyframeAnimateOption* option)
```

**Description**

Obtains the overall delay of a keyframe animation, in milliseconds.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| int32_t value | Playback duration, in ms. The default value is 0 ms. Value range: [0, +∞). <br>If the value is less than 0, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_SetDelay()

```c
int32_t OH_ArkUI_AnimatorOption_SetDelay(ArkUI_AnimatorOption* option, int32_t value)
```

**Description**

Sets the delay time of the animator playback, in milliseconds.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| int32_t value | Animation delay, in milliseconds. Value range: (-∞, +∞). Default value: **0**, indicating no animation delay. A value greater than 0 means to begin the animation after the specified amount of time has elapsed. A value less than 0 means to begin the animation in advance. If **value** is less than **0** and the absolute value of **value** is less than the actual animation duration, the animation starts its first frame from the state at the absolute value. If the absolute value of **value** is greater than or equal to the actual animation duration, the animation starts its first frame from the end state. The actual animation duration is equal to the duration of a single animation multiplied by the number of animation playback times. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_SetIterations()

```c
int32_t OH_ArkUI_AnimatorOption_SetIterations(ArkUI_AnimatorOption* option, int32_t value)
```

**Description**

Sets the number of times that an animator animation is played. By default, the animation is played once. The value **-1** indicates that the animation is played for an unlimited number of times. The value **0** indicates that no animation is played.

> **Note**:
>
> If this parameter is set to a negative value other than <b>-1</b>, the value is invalid. In this case, the animation is played once.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| int32_t value | Value range: [-1, +∞). If this parameter is set to **0**, the animation is not played. If this parameter is set to **-1**, the animation is played for an infinite number of times. Default value: **1** ( played once). <br>If the value is less than -1, the operation is invalid. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_SetFill()

```c
int32_t OH_ArkUI_AnimatorOption_SetFill(ArkUI_AnimatorOption* option, ArkUI_AnimationFillMode value)
```

**Description**

Sets the status of the component before and after the animator animation execution.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| ArkUI_AnimationFillMode value | Status of the component before and after the animator animation execution. Default value: [ARKUI_ANIMATION_FILL_MODE_FORWARDS](capi-native-type-visual-h.md#arkui_animationfillmode). <br>If the value is less than 0, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_SetDirection()

```c
int32_t OH_ArkUI_AnimatorOption_SetDirection(ArkUI_AnimatorOption* option, ArkUI_AnimationDirection value)
```

**Description**

Set the playback direction.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| ArkUI_AnimationDirection value | Animation playback direction. <br>If the value is less than 0, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_SetCurve()

```c
int32_t OH_ArkUI_AnimatorOption_SetCurve(ArkUI_AnimatorOption* option, ArkUI_CurveHandle value)
```

**Description**

Sets the interpolation curve for the animation of an animator.

> **Note**:
>
> <b>springCurve</b>, <b>springMotion</b>, <b>responsiveSpringMotion</b>, <b>interpolatingSpring</b>, and <b>customCurve</b> curves are not supported.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) value | Interpolation curve. Default value: [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve). You are advised to use [ARKUI_CURVE_EASE_IN_OUT](capi-native-type-visual-h.md#arkui_animationcurve) to obtain a smoother animation effect. <br>If **value** is set to **NULL**, the default curve [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) is used. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_SetBegin()

```c
int32_t OH_ArkUI_AnimatorOption_SetBegin(ArkUI_AnimatorOption* option, float value)
```

**Description**

Sets the interpolation start point of an animation.

> **Note**:
>
> This API does not take effect when the animation is a keyframe animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| float value | Interpolation start point of the animation. Value range: (-∞, +∞). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_SetEnd()

```c
int32_t OH_ArkUI_AnimatorOption_SetEnd(ArkUI_AnimatorOption* option, float value)
```

**Description**

Sets the interpolation end point for the animation of an animator.

> **Note**:
>
> This API does not take effect when the animation is a keyframe animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| float value | Interpolation end point of the animation. Value range: (-∞, +∞). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_SetExpectedFrameRateRange()

```c
int32_t OH_ArkUI_AnimatorOption_SetExpectedFrameRateRange(ArkUI_AnimatorOption* option, ArkUI_ExpectedFrameRateRange* value)
```

**Description**

Sets the expected frame rate range of an animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md)* value | Expected frame rate range. <br>If **value** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_SetKeyframe()

```c
int32_t OH_ArkUI_AnimatorOption_SetKeyframe(ArkUI_AnimatorOption* option, float time, float value, int32_t index)
```

**Description**

Sets the keyframe parameters of an animator animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| float time | Keyframe time. Value range: [0, 1]. The value must be in ascending order. Default value: evenly distributed by index (for example, **0.0** for the first frame, **0.5** for the second frame, and **1.0** for the third frame). <br>If the value of **time** is less than 0 or greater than 1, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| float value | Keyframe value. Value range: (-∞, +∞). |
| int32_t index | Keyframe index. <br>If the value of **index** is less than 0, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_SetKeyframeCurve()

```c
int32_t OH_ArkUI_AnimatorOption_SetKeyframeCurve(ArkUI_AnimatorOption* option, ArkUI_CurveHandle value, int32_t index)
```

**Description**

Sets the keyframe curve type for the animation of an animator.

> **Note**:
>
> <b>springCurve</b>, <b>springMotion</b>, <b>responsiveSpringMotion</b>, <b>interpolatingSpring</b>, and <b>customCurve</b> curves are not supported.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator parameters. <br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) value | Interpolation curve. Default value: **NULL**, indicating linear interpolation. |
| int32_t index | Keyframe index. <br>If the value of **index** is less than 0, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_GetDuration()

```c
int32_t OH_ArkUI_AnimatorOption_GetDuration(ArkUI_AnimatorOption* option)
```

**Description**

Obtains the duration for playing an animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_RegisterOnFinishCallback()

```c
int32_t OH_ArkUI_AnimatorOption_RegisterOnFinishCallback(ArkUI_AnimatorOption* option, void* userData, void (*callback)(ArkUI_AnimatorEvent* event))
```

**Description**

Sets the callback invoked when the animation playback is complete.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_RegisterOnCancelCallback()

```c
int32_t OH_ArkUI_AnimatorOption_RegisterOnCancelCallback(ArkUI_AnimatorOption* option, void* userData, void (*callback)(ArkUI_AnimatorEvent* event))
```

**Description**

Sets the callback invoked when the animation playback is canceled.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_AnimatorOption_RegisterOnRepeatCallback()

```c
int32_t OH_ArkUI_AnimatorOption_RegisterOnRepeatCallback(ArkUI_AnimatorOption* option, void* userData, void (*callback)(ArkUI_AnimatorEvent* event))
```

**Description**

Sets the callback invoked when the animation playback is repeated.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Animator_ResetAnimatorOption()

```c
int32_t OH_ArkUI_Animator_ResetAnimatorOption(ArkUI_AnimatorHandle animatorHandle, ArkUI_AnimatorOption* option)
```

**Description**

Resets the animation of an animator.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Animator object. |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Animator animation parameters. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Animator_Play()

```c
int32_t OH_ArkUI_Animator_Play(ArkUI_AnimatorHandle animatorHandle)
```

**Description**

Starts the animation of an animator.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Animator object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Animator_Finish()

```c
int32_t OH_ArkUI_Animator_Finish(ArkUI_AnimatorHandle animatorHandle)
```

**Description**

Ends the animation of an animator.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Animator object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Animator_Pause()

```c
int32_t OH_ArkUI_Animator_Pause(ArkUI_AnimatorHandle animatorHandle)
```

**Description**

Pauses the animation of an animator.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Animator object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Animator_Cancel()

```c
int32_t OH_ArkUI_Animator_Cancel(ArkUI_AnimatorHandle animatorHandle)
```

**Description**

Cancels the animation of an animator.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Animator object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Animator_Reverse()

```c
int32_t OH_ArkUI_Animator_Reverse(ArkUI_AnimatorHandle animatorHandle)
```

**Description**

Plays this animation in reverse order.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Animator object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Curve_CreateCurveByType()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateCurveByType(ArkUI_AnimationCurve curve)
```

**Description**

Implements initialization for the interpolation curve, which is used to create an interpolation curve based on the input parameter.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* firstEffect | Transition effect. |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* secondEffect | Combination of transition effects. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_TransitionEffect_SetAnimation()

```c
int32_t OH_ArkUI_TransitionEffect_SetAnimation(ArkUI_TransitionEffect* effect, ArkUI_AnimateOption* animation)
```

**Description**

Sets transition effect animation settings.

> **Note**:
>
> If <b>combine</b> is used for combining transition effects, the animation settings of a transition effect are applicable to the one following it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* effect | Transition effect. |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* animation | Animation settings. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PropertyAnimation_Create()

```c
OH_ArkUI_PropertyAnimationHandle OH_ArkUI_NativeModule_PropertyAnimation_Create(OH_ArkUI_AnimationPropertyType propertyType)
```

**Description**

Creates a property animation for a specific animatable property.<br> <b>propertyType</b> must be a valid [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype); otherwise, this API returns <b>NULL</b>.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationPropertyType propertyType | [in] Indicates the type of the property to animate. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle | Returns the handle to the property animation. The caller owns the returned          handle and must release it with [OH_ArkUI_NativeModule_PropertyAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_destroy). |

### OH_ArkUI_NativeModule_PropertyAnimation_Destroy()

```c
void OH_ArkUI_NativeModule_PropertyAnimation_Destroy(OH_ArkUI_PropertyAnimationHandle animation)
```

**Description**

Destroys a property animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] Indicates the property animation handle returned by [OH_ArkUI_NativeModule_PropertyAnimation_Create](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_create). Passing <b>NULL</b> has no effect. After this function returns for a non-NULL handle, the handle is invalid, is not reference-counted, and must not be used or destroyed again. |

### OH_ArkUI_NativeModule_PropertyAnimation_SetFromValue()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetFromValue(OH_ArkUI_PropertyAnimationHandle animation, const ArkUI_NumberValue *value, int32_t size)
```

**Description**

Sets the start value of a property animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] Indicates the property animation handle. |
| const ArkUI_NumberValue *value | [in] Indicates the start value. The number and type of elements depend on [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype). For example, OPACITY requires 1 f32 value, and TRANSLATION requires 2 f32 values (x, y). |
| int32_t size | [in] Indicates the number of elements in the value array. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PropertyAnimation_GetFromValue()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetFromValue(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_NumberValue *value, int32_t size)
```

**Description**

Obtains the start value of a property animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] Indicates the property animation handle. |
| ArkUI_NumberValue *value | [out] Indicates the pointer to receive the start value array of [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md). The number and type of elements depend on [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype). For example, OPACITY requires 1 f32 value, and TRANSLATION requires 2 f32 values (x, y). The values are written into the memory pointed to by this pointer. <br>This pointer must not be **NULL**. If **value** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| int32_t size | [in] Indicates the size of the output array. It must equal the number of elements required by [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype); otherwise, the error code [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the start value has not been set.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          <li>[ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the buffer size does not equal the required              buffer size.</li>          </ul> |

### OH_ArkUI_NativeModule_PropertyAnimation_SetToValue()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetToValue(OH_ArkUI_PropertyAnimationHandle animation, const ArkUI_NumberValue *value, int32_t size)
```

**Description**

Sets the end value of a property animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] Indicates the property animation handle. |
| const ArkUI_NumberValue *value | [in] Indicates the end value. The number and type of elements depend on [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype). For example, OPACITY requires 1 f32 value, and TRANSLATION requires 2 f32 values (x, y). |
| int32_t size | [in] Indicates the number of elements in the value array. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PropertyAnimation_GetToValue()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetToValue(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_NumberValue *value, int32_t size)
```

**Description**

Obtains the end value of a property animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] Indicates the property animation handle. |
| ArkUI_NumberValue *value | [out] Indicates the pointer to receive the end value array of [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md). The number and type of elements depend on [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype). For example, OPACITY requires 1 f32 value, and TRANSLATION requires 2 f32 values (x, y). The values are written into the memory pointed to by this pointer. <br>This pointer must not be **NULL**. If **value** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| int32_t size | [in] Indicates the size of the output array. It must equal the number of elements required by [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype); otherwise, the error code [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the end value has not been set.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          <li>[ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the buffer size does not equal the required              buffer size.</li>          </ul> |

### OH_ArkUI_NativeModule_PropertyAnimation_SetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetDuration(OH_ArkUI_PropertyAnimationHandle animation, int32_t duration)
```

**Description**

Sets the duration for a property animation.<br> The actual effective animation duration is determined by priority: if the duration is set via this API, that value is used; otherwise, the duration set on the animation group via [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, **1000** ms is used.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] Indicates the property animation handle. |
| int32_t duration | [in] Indicates the duration, in milliseconds. The value must be greater than 0. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PropertyAnimation_GetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetDuration(OH_ArkUI_PropertyAnimationHandle animation, int32_t *duration)
```

**Description**

Obtains the duration of a property animation.<br> This API returns only the duration explicitly set on this animation; the value inherited from the animation group or the default is resolved at runtime and is not stored on this object. If the duration has not been set on this animation, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. The actual effective animation duration used at runtime is determined by priority: if set via [OH_ArkUI_NativeModule_PropertyAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setduration), that value is used; otherwise, the group's duration via [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, **1000** ms is used.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] Indicates the property animation handle. |
| int32_t *duration | [out] Indicates the pointer to receive the duration value, in milliseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the duration has not been set.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PropertyAnimation_SetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetDelay(OH_ArkUI_PropertyAnimationHandle animation, int32_t delay)
```

**Description**

Sets the delay for a property animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] Indicates the property animation handle. |
| int32_t delay | [in] Indicates the delay, in milliseconds. The default value is <b>0</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PropertyAnimation_GetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetDelay(OH_ArkUI_PropertyAnimationHandle animation, int32_t *delay)
```

**Description**

Obtains the delay of a property animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] Indicates the property animation handle. |
| int32_t *delay | [out] Indicates the pointer to receive the delay value, in milliseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PropertyAnimation_SetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetCurve(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_CurveHandle curve)
```

**Description**

Sets the animation curve for a property animation.<br> The actual effective animation curve is determined by priority: if the curve is set via this API, that value is used; otherwise, the curve set on the animation group via [OH_ArkUI_NativeModule_AnimationGroup_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setcurve) is used; if neither is set, [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) is used. Spring curves (<b>springMotion</b>, <b>responsiveSpringMotion</b>, and <b>interpolatingSpring</b>) are supported. When a spring curve is set, the duration set via [OH_ArkUI_NativeModule_PropertyAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setduration) does not take effect; the animation duration is determined by the spring curve.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] Indicates the property animation handle. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) curve | [in] Indicates the animation curve. This API does not take ownership of the curve handle; the caller must ensure the curve remains valid when using this handle. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PropertyAnimation_GetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetCurve(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_CurveHandle *outBorrowedCurve)
```

**Description**

Obtains the animation curve of a property animation.<br> This API returns only the curve explicitly set on this animation; the value inherited from the animation group or the default is resolved at runtime and is not stored on this object. If the curve has not been set on this animation, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. The actual effective animation curve used at runtime is determined by priority: if set via [OH_ArkUI_NativeModule_PropertyAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setcurve), that value is used; otherwise, the group's curve via [OH_ArkUI_NativeModule_AnimationGroup_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setcurve) is used; if neither is set, [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) is used.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] Indicates the property animation handle. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) *outBorrowedCurve | [out] Receives a borrowed curve handle; the caller must not destroy it. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the curve has not been set.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PropertyAnimation_SetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetTempo(OH_ArkUI_PropertyAnimationHandle animation, float tempo)
```

**Description**

Sets the tempo for a property animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] Indicates the property animation handle. |
| float tempo | [in] Indicates the animation tempo. Value range: (0, +∞). The default value is <b>1</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PropertyAnimation_GetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetTempo(OH_ArkUI_PropertyAnimationHandle animation, float *tempo)
```

**Description**

Obtains the tempo of a property animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] Indicates the property animation handle. |
| float *tempo | [out] Indicates the pointer to receive the animation tempo. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PropertyAnimation_SetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetAutoReverse(OH_ArkUI_PropertyAnimationHandle animation, bool autoReverse)
```

**Description**

Sets whether to auto-reverse a property animation.<br> When auto-reverse is enabled, the animation plays forward and then backward alternately across iterations. The default value is <b>false</b>.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] Indicates the property animation handle. |
| bool autoReverse | [in] Indicates whether to enable auto-reverse. The default value is <b>false</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PropertyAnimation_GetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetAutoReverse(OH_ArkUI_PropertyAnimationHandle animation, bool *autoReverse)
```

**Description**

Obtains whether auto-reverse is enabled for a property animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] Indicates the property animation handle. |
| bool *autoReverse | [out] Indicates the pointer to receive the value. <b>true</b> if auto-reverse is enabled; <b>false</b> otherwise. The default value is <b>false</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PropertyAnimation_SetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetIterations(OH_ArkUI_PropertyAnimationHandle animation, int32_t iterations)
```

**Description**

Sets the number of iterations for a property animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] Indicates the property animation handle. |
| int32_t iterations | [in] Indicates the number of iterations. The value must be -1 or greater than or equal to 1; a value of <b>0</b> returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode). The value <b>-1</b> indicates unlimited iterations. The default value is <b>1</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PropertyAnimation_GetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetIterations(OH_ArkUI_PropertyAnimationHandle animation, int32_t *iterations)
```

**Description**

Obtains the number of iterations of a property animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] Indicates the property animation handle. |
| int32_t *iterations | [out] Indicates the pointer to receive the number of iterations. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_RenderNodeHandle targetNode)
```

**Description**

Sets the target render node for a property animation.<br> The target node is the render node animated by this property animation. If <b>NULL</b> (the default), the animation inherits the group's default target set by [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode). A non-NULL target must belong to the same UIContext that the group is registered on; the check is performed when the group is registered by [OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] Indicates the property animation handle. |
| ArkUI_RenderNodeHandle targetNode | [in] Indicates the render node to animate. <b>NULL</b> means inheriting the group's default target. The default value is <b>NULL</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PropertyAnimation_GetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetTargetNode(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_RenderNodeHandle *outBorrowedTargetNode)
```

**Description**

Obtains the target render node of a property animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] Indicates the property animation handle. |
| ArkUI_RenderNodeHandle *outBorrowedTargetNode | [out] Receives a borrowed render-node handle; the caller must not destroy it. <b>NULL</b> means inheriting the group's default target. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_Create()

```c
OH_ArkUI_KeyframeAnimationHandle OH_ArkUI_NativeModule_KeyframeAnimation_Create(OH_ArkUI_AnimationPropertyType propertyType, int32_t size)
```

**Description**

Creates a keyframe animation for a specific animatable property.<br> The key time of each keyframe defaults to being evenly distributed in [0, 1] by index (for example, when there are 3 keyframes, <b>0.0</b> for the first frame, <b>0.5</b> for the second frame, and <b>1.0</b> for the third frame). Use [OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTimes](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setkeytimes) or [OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTime](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setkeytime) to customize the key time points.<br> <b>propertyType</b> must be a valid [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype), and <b>size</b> must be at least 2; otherwise, this API returns <b>NULL</b>.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationPropertyType propertyType | [in] Indicates the type of the property to animate. |
| int32_t size | [in] Indicates the number of keyframes. The value must be greater than or equal to 2. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle | Returns the handle to the keyframe animation. The caller owns the returned          handle and must release it with [OH_ArkUI_NativeModule_KeyframeAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_destroy). |

### OH_ArkUI_NativeModule_KeyframeAnimation_Destroy()

```c
void OH_ArkUI_NativeModule_KeyframeAnimation_Destroy(OH_ArkUI_KeyframeAnimationHandle animation)
```

**Description**

Destroys a keyframe animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle returned by [OH_ArkUI_NativeModule_KeyframeAnimation_Create](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_create). Passing <b>NULL</b> has no effect. After this function returns for a non-NULL handle, the handle is invalid, is not reference-counted, and must not be used or destroyed again. |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTimes()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTimes(OH_ArkUI_KeyframeAnimationHandle animation, const float *keyTimes, int32_t size)
```

**Description**

Sets the keyframe key time points.<br> If this API is not called, the key time of each keyframe defaults to being evenly distributed in [0, 1] by index (for example, when there are 3 keyframes, <b>0.0</b> for the first frame, <b>0.5</b> for the second frame, and <b>1.0</b> for the third frame).<br> The elements in <b>keyTimes</b> must be non-decreasing, and <b>size</b> must equal the number of keyframes of the keyframe animation (the <b>size</b> value specified when the animation was created via [OH_ArkUI_NativeModule_KeyframeAnimation_Create](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_create)).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| const float *keyTimes | [in] Indicates the array of key time points. Value range of each element: [0, 1]. |
| int32_t size | [in] Indicates the number of key time points. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_GetKeyTime()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetKeyTime(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, float *keyTime)
```

**Description**

Obtains the key time point of a keyframe at the specified index.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| int32_t index | [in] Indicates the keyframe index. |
| float *keyTime | [out] Indicates the pointer to receive the key time point. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTime()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTime(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, float keyTime)
```

**Description**

Sets the key time point of a keyframe at the specified index.<br> If this API is not called for a keyframe, its key time defaults to being evenly distributed in [0, 1] by index (for example, when there are 3 keyframes, <b>0.0</b> for the first frame, <b>0.5</b> for the second frame, and <b>1.0</b> for the third frame).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| int32_t index | [in] Indicates the keyframe index. |
| float keyTime | [in] Indicates the key time point. Value range: [0, 1]. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetValue()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetValue(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, const ArkUI_NumberValue *value, int32_t size)
```

**Description**

Sets the value of a keyframe at the specified index.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| int32_t index | [in] Indicates the keyframe index. |
| const ArkUI_NumberValue *value | [in] Indicates the array of [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md). The number and type of elements depend on [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype). For example, OPACITY requires 1 f32 value, and TRANSLATION requires 2 f32 values (x, y). |
| int32_t size | [in] Indicates the number of elements in the value array. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetValues()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetValues(OH_ArkUI_KeyframeAnimationHandle animation, const ArkUI_NumberValue *values, int32_t size)
```

**Description**

Sets the values for all keyframes at once.<br> The values are provided as a flat array. The number of elements per keyframe depends on [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype). For example, OPACITY requires 1 value per keyframe, and TRANSLATION requires 2 values per keyframe. The total number of elements must equal the number of keyframes multiplied by the number of values per keyframe.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| const ArkUI_NumberValue *values | [in] Indicates the flat array of [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) for all keyframes. |
| int32_t size | [in] Indicates the total number of elements in the values array. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_GetValue()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetValue(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, ArkUI_NumberValue *value, int32_t size)
```

**Description**

Obtains the value of a keyframe at the specified index.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| int32_t index | [in] Indicates the keyframe index. |
| ArkUI_NumberValue *value | [out] Indicates the pointer to receive the value array of [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md). The number and type of elements depend on [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype). For example, OPACITY requires 1 f32 value, and TRANSLATION requires 2 f32 values (x, y). The values are written into the memory pointed to by this pointer. <br>This pointer must not be **NULL**. If **value** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| int32_t size | [in] Indicates the size of the output array. It must equal the number of elements required by [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype); otherwise, the error code [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the value of the keyframe has not been set.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          <li>[ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the buffer size does not equal the required              buffer size.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetCurves()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetCurves(OH_ArkUI_KeyframeAnimationHandle animation, const ArkUI_CurveHandle *value, int32_t size)
```

**Description**

Sets the animation curves for keyframes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| [const ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) *value | [in] Indicates the array of curve handles. This API does not take ownership of the curve handles; the caller must ensure all curves remain valid when using this handle. |
| int32_t size | [in] Indicates the number of curves. The <b>springMotion</b>, <b>responsiveSpringMotion</b>, and <b>interpolatingSpring</b> curves are not supported because they do not have effective duration settings. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, ArkUI_CurveHandle curve)
```

**Description**

Sets the animation curve for a keyframe at the specified index.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| int32_t index | [in] Indicates the keyframe index. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) curve | [in] Indicates the animation curve. This API does not take ownership of the curve handle; the caller must ensure the curve remains valid when using this handle. The <b>springMotion</b>, <b>responsiveSpringMotion</b>, and <b>interpolatingSpring</b> curves are not supported because they do not have effective duration settings. The actual effective animation curve is determined by priority: if the curve is set for the keyframe (via this API or [OH_ArkUI_NativeModule_KeyframeAnimation_SetCurves](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setcurves)), that value is used; otherwise, the curve set on the animation group via [OH_ArkUI_NativeModule_AnimationGroup_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setcurve) is used; if neither is set, [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) is used. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_GetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetCurve(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, ArkUI_CurveHandle *outBorrowedCurve)
```

**Description**

Obtains the curve of a keyframe at the specified index.<br> This API returns only the curve explicitly set for the keyframe; the value inherited from the animation group or the default is resolved at runtime and is not stored on this object. If the curve has not been set for the keyframe, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. The actual effective animation curve used at runtime is determined by priority: if set for the keyframe via [OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setcurve) or [OH_ArkUI_NativeModule_KeyframeAnimation_SetCurves](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setcurves), that value is used; otherwise, the group's curve via [OH_ArkUI_NativeModule_AnimationGroup_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setcurve) is used; if neither is set, [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) is used.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| int32_t index | [in] Indicates the keyframe index. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) *outBorrowedCurve | [out] Receives a borrowed curve handle; the caller must not destroy it. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the curve has not been set.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration(OH_ArkUI_KeyframeAnimationHandle animation, int32_t duration)
```

**Description**

Sets the duration for a keyframe animation.<br> The actual effective animation duration is determined by priority: if the duration is set via this API, that value is used; otherwise, the duration set on the animation group via [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, **1000** ms is used.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| int32_t duration | [in] Indicates the duration, in milliseconds. The value must be greater than 0. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_GetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetDuration(OH_ArkUI_KeyframeAnimationHandle animation, int32_t *duration)
```

**Description**

Obtains the duration of a keyframe animation.<br> This API returns only the duration explicitly set on this animation; the value inherited from the animation group or the default is resolved at runtime and is not stored on this object. If the duration has not been set on this animation, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. The actual effective animation duration used at runtime is determined by priority: if set via [OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setduration), that value is used; otherwise, the group's duration via [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, **1000** ms is used.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| int32_t *duration | [out] Indicates the pointer to receive the duration value, in milliseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the duration has not been set.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetDelay(OH_ArkUI_KeyframeAnimationHandle animation, int32_t delay)
```

**Description**

Sets the delay for a keyframe animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| int32_t delay | [in] Indicates the delay, in milliseconds. The default value is <b>0</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_GetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetDelay(OH_ArkUI_KeyframeAnimationHandle animation, int32_t *delay)
```

**Description**

Obtains the delay of a keyframe animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| int32_t *delay | [out] Indicates the pointer to receive the delay value, in milliseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetTempo(OH_ArkUI_KeyframeAnimationHandle animation, float tempo)
```

**Description**

Sets the tempo for a keyframe animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| float tempo | [in] Indicates the animation tempo. Value range: (0, +∞). The default value is <b>1</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_GetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetTempo(OH_ArkUI_KeyframeAnimationHandle animation, float *tempo)
```

**Description**

Obtains the tempo of a keyframe animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| float *tempo | [out] Indicates the pointer to receive the animation tempo. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetAutoReverse(OH_ArkUI_KeyframeAnimationHandle animation, bool autoReverse)
```

**Description**

Sets whether to auto-reverse a keyframe animation.<br> When auto-reverse is enabled, the animation plays forward and then backward alternately across iterations. The default value is <b>false</b>.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| bool autoReverse | [in] Indicates whether to enable auto-reverse. The default value is <b>false</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_GetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetAutoReverse(OH_ArkUI_KeyframeAnimationHandle animation, bool *autoReverse)
```

**Description**

Obtains whether auto-reverse is enabled for a keyframe animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| bool *autoReverse | [out] Indicates the pointer to receive the value. <b>true</b> if auto-reverse is enabled; <b>false</b> otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetIterations(OH_ArkUI_KeyframeAnimationHandle animation, int32_t iterations)
```

**Description**

Sets the number of iterations for a keyframe animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| int32_t iterations | [in] Indicates the number of iterations. The value must be -1 or greater than or equal to 1; a value of <b>0</b> returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode). The value <b>-1</b> indicates unlimited iterations. The default value is <b>1</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_GetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetIterations(OH_ArkUI_KeyframeAnimationHandle animation, int32_t *iterations)
```

**Description**

Obtains the number of iterations of a keyframe animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| int32_t *iterations | [out] Indicates the pointer to receive the number of iterations. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode(OH_ArkUI_KeyframeAnimationHandle animation, ArkUI_RenderNodeHandle targetNode)
```

**Description**

Sets the target render node for a keyframe animation.<br> The target node is the render node animated by this keyframe animation. If <b>NULL</b> (the default), the animation inherits the group's default target set by [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode). A non-NULL target must belong to the same UIContext that the group is registered on; the check is performed when the group is registered by [OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| ArkUI_RenderNodeHandle targetNode | [in] Indicates the render node to animate. <b>NULL</b> means inheriting the group's default target. The default value is <b>NULL</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_KeyframeAnimation_GetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetTargetNode(OH_ArkUI_KeyframeAnimationHandle animation, ArkUI_RenderNodeHandle *outBorrowedTargetNode)
```

**Description**

Obtains the target render node of a keyframe animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation handle. |
| ArkUI_RenderNodeHandle *outBorrowedTargetNode | [out] Receives a borrowed render-node handle; the caller must not destroy it. <b>NULL</b> means inheriting the group's default target. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PathAnimation_Create()

```c
OH_ArkUI_PathAnimationHandle OH_ArkUI_NativeModule_PathAnimation_Create(const char *path)
```

**Description**

Creates a path animation that moves the component along a geometric path.<br> The path animation applies to the TRANSLATION property.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *path | [in] Indicates the path string in SVG path syntax. The keywords <b>"start"</b> and <b>"end"</b> are not supported as position values. Returns <b>NULL</b> if <b>path</b> is <b>NULL</b>, is an empty string, or contains unsupported values. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_ArkUI_PathAnimationHandle | Returns the handle to the path animation. Returns <b>NULL</b> on invalid input.          The caller owns the returned handle and must release it with          [OH_ArkUI_NativeModule_PathAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_destroy). |

### OH_ArkUI_NativeModule_PathAnimation_Destroy()

```c
void OH_ArkUI_NativeModule_PathAnimation_Destroy(OH_ArkUI_PathAnimationHandle animation)
```

**Description**

Destroys a path animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] Indicates the path animation handle returned by [OH_ArkUI_NativeModule_PathAnimation_Create](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_create). Passing <b>NULL</b> has no effect. After this function returns for a non-NULL handle, the handle is invalid, is not reference-counted, and must not be used or destroyed again. |

### OH_ArkUI_NativeModule_PathAnimation_SetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetDuration(OH_ArkUI_PathAnimationHandle animation, int32_t duration)
```

**Description**

Sets the duration for a path animation.<br> The actual effective animation duration is determined by priority: if the duration is set via this API, that value is used; otherwise, the duration set on the animation group via [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, **1000** ms is used.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] Indicates the path animation handle. |
| int32_t duration | [in] Indicates the duration, in milliseconds. The value must be greater than 0. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PathAnimation_GetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetDuration(OH_ArkUI_PathAnimationHandle animation, int32_t *duration)
```

**Description**

Obtains the duration of a path animation.<br> This API returns only the duration explicitly set on this animation; the value inherited from the animation group or the default is resolved at runtime and is not stored on this object. If the duration has not been set on this animation, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. The actual effective animation duration used at runtime is determined by priority: if set via [OH_ArkUI_NativeModule_PathAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_setduration), that value is used; otherwise, the group's duration via [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, **1000** ms is used.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] Indicates the path animation handle. |
| int32_t *duration | [out] Indicates the pointer to receive the duration value, in milliseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the duration has not been set.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PathAnimation_SetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetDelay(OH_ArkUI_PathAnimationHandle animation, int32_t delay)
```

**Description**

Sets the delay for a path animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] Indicates the path animation handle. |
| int32_t delay | [in] Indicates the delay, in milliseconds. The default value is <b>0</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PathAnimation_GetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetDelay(OH_ArkUI_PathAnimationHandle animation, int32_t *delay)
```

**Description**

Obtains the delay of a path animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] Indicates the path animation handle. |
| int32_t *delay | [out] Indicates the pointer to receive the delay value, in milliseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PathAnimation_SetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetCurve(OH_ArkUI_PathAnimationHandle animation, ArkUI_CurveHandle curve)
```

**Description**

Sets the animation curve for a path animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] Indicates the path animation handle. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) curve | [in] Indicates the animation curve that controls the rate of motion along the path. This API does not take ownership of the curve handle; the caller must ensure the curve remains valid when using this handle. The <b>springMotion</b>, <b>responsiveSpringMotion</b>, and <b>interpolatingSpring</b> curves are not supported because they do not have effective duration settings. The actual effective animation curve is determined by priority: if the curve is set via this API, that value is used; otherwise, the curve set on the animation group via [OH_ArkUI_NativeModule_AnimationGroup_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setcurve) is used; if neither is set, [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) is used. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PathAnimation_GetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetCurve(OH_ArkUI_PathAnimationHandle animation, ArkUI_CurveHandle *outBorrowedCurve)
```

**Description**

Obtains the animation curve of a path animation.<br> This API returns only the curve explicitly set on this animation; the value inherited from the animation group or the default is resolved at runtime and is not stored on this object. If the curve has not been set on this animation, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. The actual effective animation curve used at runtime is determined by priority: if set via [OH_ArkUI_NativeModule_PathAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_setcurve), that value is used; otherwise, the group's curve via [OH_ArkUI_NativeModule_AnimationGroup_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setcurve) is used; if neither is set, [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) is used.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] Indicates the path animation handle. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) *outBorrowedCurve | [out] Receives a borrowed curve handle; the caller must not destroy it. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the curve has not been set.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PathAnimation_SetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetTempo(OH_ArkUI_PathAnimationHandle animation, float tempo)
```

**Description**

Sets the tempo for a path animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] Indicates the path animation handle. |
| float tempo | [in] Indicates the animation tempo. Value range: (0, +∞). The default value is <b>1</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PathAnimation_GetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetTempo(OH_ArkUI_PathAnimationHandle animation, float *tempo)
```

**Description**

Obtains the tempo of a path animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] Indicates the path animation handle. |
| float *tempo | [out] Indicates the pointer to receive the animation tempo. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PathAnimation_SetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetAutoReverse(OH_ArkUI_PathAnimationHandle animation, bool autoReverse)
```

**Description**

Sets whether to auto-reverse a path animation.<br> When auto-reverse is enabled, the animation plays forward and then backward alternately across iterations. The default value is <b>false</b>.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] Indicates the path animation handle. |
| bool autoReverse | [in] Indicates whether to enable auto-reverse. The default value is <b>false</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PathAnimation_GetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetAutoReverse(OH_ArkUI_PathAnimationHandle animation, bool *autoReverse)
```

**Description**

Obtains whether auto-reverse is enabled for a path animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] Indicates the path animation handle. |
| bool *autoReverse | [out] Indicates the pointer to receive the value. <b>true</b> if auto-reverse is enabled; <b>false</b> otherwise. The default value is <b>false</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PathAnimation_SetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetIterations(OH_ArkUI_PathAnimationHandle animation, int32_t iterations)
```

**Description**

Sets the number of iterations for a path animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] Indicates the path animation handle. |
| int32_t iterations | [in] Indicates the number of iterations. The value must be -1 or greater than or equal to 1; a value of <b>0</b> returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode). The value <b>-1</b> indicates unlimited iterations. The default value is <b>1</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PathAnimation_GetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetIterations(OH_ArkUI_PathAnimationHandle animation, int32_t *iterations)
```

**Description**

Obtains the number of iterations of a path animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] Indicates the path animation handle. |
| int32_t *iterations | [out] Indicates the pointer to receive the number of iterations. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PathAnimation_SetAutoRotation()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetAutoRotation(OH_ArkUI_PathAnimationHandle animation, bool autoRotation)
```

**Description**

Sets whether the component auto-rotates to align with the path tangent during a path animation.<br> When auto-rotation is enabled, the component rotates so that its heading direction aligns with the tangent of the path at the current position. The default value is <b>false</b>.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] Indicates the path animation handle. |
| bool autoRotation | [in] Indicates whether to enable auto-rotation. The default value is <b>false</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PathAnimation_GetAutoRotation()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetAutoRotation(OH_ArkUI_PathAnimationHandle animation, bool *autoRotation)
```

**Description**

Obtains whether auto-rotation is enabled for a path animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] Indicates the path animation handle. |
| bool *autoRotation | [out] Indicates the pointer to receive the value. <b>true</b> if auto-rotation is enabled; <b>false</b> otherwise. The default value is <b>false</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PathAnimation_SetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetTargetNode(OH_ArkUI_PathAnimationHandle animation, ArkUI_RenderNodeHandle targetNode)
```

**Description**

Sets the target render node for a path animation.<br> The target node is the render node animated by this path animation. If <b>NULL</b> (the default), the animation inherits the group's default target set by [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode). A non-NULL target must belong to the same UIContext that the group is registered on; the check is performed when the group is registered by [OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] Indicates the path animation handle. |
| ArkUI_RenderNodeHandle targetNode | [in] Indicates the render node to animate. <b>NULL</b> means inheriting the group's default target. The default value is <b>NULL</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_PathAnimation_GetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetTargetNode(OH_ArkUI_PathAnimationHandle animation, ArkUI_RenderNodeHandle *outBorrowedTargetNode)
```

**Description**

Obtains the target render node of a path animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] Indicates the path animation handle. |
| ArkUI_RenderNodeHandle *outBorrowedTargetNode | [out] Receives a borrowed render-node handle; the caller must not destroy it. <b>NULL</b> means inheriting the group's default target. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_AnimationGroup_Create()

```c
OH_ArkUI_AnimationGroupHandle OH_ArkUI_NativeModule_AnimationGroup_Create(void)
```

**Description**

Creates an animation group.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Returns**:

| Type | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle | Returns the handle to the animation group. The caller owns the returned          handle and must release it with [OH_ArkUI_NativeModule_AnimationGroup_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_destroy). |

### OH_ArkUI_NativeModule_AnimationGroup_Destroy()

```c
void OH_ArkUI_NativeModule_AnimationGroup_Destroy(OH_ArkUI_AnimationGroupHandle group)
```

**Description**

Destroys the frontend handle of an animation group.<br> This releases the frontend handle only. The backend (runtime) objects of a group that has been registered via [OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup) are released separately — automatically when the finish callback is invoked, or via [OH_ArkUI_NativeModule_RemoveAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_removeanimationgroup).<br> The child animations added to the group are not automatically destroyed. Call OH_ArkUI_NativeModule_PropertyAnimation_Destroy, OH_ArkUI_NativeModule_KeyframeAnimation_Destroy or OH_ArkUI_NativeModule_PathAnimation_Destroy separately.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle returned by [OH_ArkUI_NativeModule_AnimationGroup_Create](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_create). Passing <b>NULL</b> has no effect. After this function returns for a non-NULL handle, the handle is invalid, is not reference-counted, and must not be used or destroyed again. |

### OH_ArkUI_NativeModule_AnimationGroup_SetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetDuration(OH_ArkUI_AnimationGroupHandle group, int32_t duration)
```

**Description**

Sets the duration for an animation group.<br> The group's duration serves as the default duration for child animations that do not set their own duration via [OH_ArkUI_NativeModule_PropertyAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setduration), [OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setduration), or [OH_ArkUI_NativeModule_PathAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_setduration).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| int32_t duration | [in] Indicates the duration, in milliseconds. The value must be greater than 0. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_AnimationGroup_GetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetDuration(OH_ArkUI_AnimationGroupHandle group, int32_t *duration)
```

**Description**

Obtains the duration of an animation group.<br> This API returns only the duration explicitly set on this animation group, and is not affected by the duration of child animations. If the duration has not been set on this group, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. At runtime, an unset group duration defaults to **1000** ms.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| int32_t *duration | [out] Indicates the pointer to receive the duration value, in milliseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the duration has not been set.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_AnimationGroup_SetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetDelay(OH_ArkUI_AnimationGroupHandle group, int32_t delay)
```

**Description**

Sets the delay for an animation group.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| int32_t delay | [in] Indicates the delay, in milliseconds. The default value is <b>0</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_AnimationGroup_GetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetDelay(OH_ArkUI_AnimationGroupHandle group, int32_t *delay)
```

**Description**

Obtains the delay of an animation group.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| int32_t *delay | [out] Indicates the pointer to receive the delay value, in milliseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_AnimationGroup_SetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetCurve(OH_ArkUI_AnimationGroupHandle group, ArkUI_CurveHandle curve)
```

**Description**

Sets the animation curve for an animation group.<br> The group's curve serves as the default curve for child animations that do not set their own curve via [OH_ArkUI_NativeModule_PropertyAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setcurve), [OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setcurve), or [OH_ArkUI_NativeModule_PathAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_setcurve). The <b>springMotion</b>, <b>responsiveSpringMotion</b>, and <b>interpolatingSpring</b> curves are not supported because they do not have effective duration settings.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) curve | [in] Indicates the animation curve. This API does not take ownership of the curve handle; the caller must ensure the curve remains valid when using this handle. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_AnimationGroup_GetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetCurve(OH_ArkUI_AnimationGroupHandle group, ArkUI_CurveHandle *outBorrowedCurve)
```

**Description**

Obtains the animation curve of an animation group.<br> This API returns only the curve explicitly set on this animation group, and is not affected by the curve of child animations. If the curve has not been set on this group, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. At runtime, an unset group curve defaults to [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) *outBorrowedCurve | [out] Receives a borrowed curve handle; the caller must not destroy it. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the curve has not been set.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_AnimationGroup_SetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetTempo(OH_ArkUI_AnimationGroupHandle group, float tempo)
```

**Description**

Sets the tempo for an animation group.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| float tempo | [in] Indicates the animation tempo. Value range: (0, +∞). The default value is <b>1</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_AnimationGroup_GetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetTempo(OH_ArkUI_AnimationGroupHandle group, float *tempo)
```

**Description**

Obtains the tempo of an animation group.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| float *tempo | [out] Indicates the pointer to receive the animation tempo. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_AnimationGroup_SetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetAutoReverse(OH_ArkUI_AnimationGroupHandle group, bool autoReverse)
```

**Description**

Sets whether to auto-reverse an animation group.<br> When auto-reverse is enabled, the animation group plays forward and then backward alternately across iterations. The default value is <b>false</b>.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| bool autoReverse | [in] Indicates whether to enable auto-reverse. The default value is <b>false</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_AnimationGroup_GetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetAutoReverse(OH_ArkUI_AnimationGroupHandle group, bool *autoReverse)
```

**Description**

Obtains whether auto-reverse is enabled for an animation group.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| bool *autoReverse | [out] Indicates the pointer to receive the value. <b>true</b> if auto-reverse is enabled; <b>false</b> otherwise. The default value is <b>false</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_AnimationGroup_SetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetIterations(OH_ArkUI_AnimationGroupHandle group, int32_t iterations)
```

**Description**

Sets the number of iterations for an animation group.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| int32_t iterations | [in] Indicates the number of iterations. The value must be -1 or greater than or equal to 1; a value of <b>0</b> returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode). The value <b>-1</b> indicates unlimited iterations. The default value is <b>1</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_AnimationGroup_GetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetIterations(OH_ArkUI_AnimationGroupHandle group, int32_t *iterations)
```

**Description**

Obtains the number of iterations of an animation group.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| int32_t *iterations | [out] Indicates the pointer to receive the number of iterations. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_AnimationGroup_SetExpectedFrameRateRange()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetExpectedFrameRateRange(OH_ArkUI_AnimationGroupHandle group, const ArkUI_ExpectedFrameRateRange *frameRate)
```

**Description**

Sets the expected frame rate range for an animation group.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| [const ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md) *frameRate | [in] Indicates the expected frame rate range. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_AnimationGroup_GetExpectedFrameRateRange()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetExpectedFrameRateRange(OH_ArkUI_AnimationGroupHandle group, ArkUI_ExpectedFrameRateRange *frameRate)
```

**Description**

Obtains the expected frame rate range of an animation group.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md) *frameRate | [out] Indicates the pointer used to receive the expected frame rate range. The values of the [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md) object are written into the memory pointed to by this pointer. <br>This pointer must not be **NULL**. If **frameRate** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_AnimationGroup_RegisterOnFinishCallback()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_RegisterOnFinishCallback(OH_ArkUI_AnimationGroupHandle group, void *userData, void (*callback)(void *userData))
```

**Description**

Registers a callback to be invoked when the animation group playback is complete.<br> An animation group has one finish callback. Registering another callback replaces the previous callback and userData pair. Registering the same callback and userData pair again succeeds without creating an additional registration.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| void \*userData | [in] Caller-owned data passed unchanged to the callback. It may be <b>NULL</b>, must remain valid until the callback returns, and is never freed by the library. |
| void (\*callback)(void \*userData) | [in] Non-NULL finish callback invoked once and serially on the UI main thread. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode(OH_ArkUI_AnimationGroupHandle group, ArkUI_RenderNodeHandle targetNode)
```

**Description**

Sets the default target render node for an animation group.<br> The default target is the render node animated by child animations that do not set their own target via [OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_settargetnode), [OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_settargetnode), or [OH_ArkUI_NativeModule_PathAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_settargetnode). Every child must resolve to a non-NULL target (its own, or this group default) when the group is registered by [OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup); any resolved target must belong to the same UIContext that the group is registered on. The default value is <b>NULL</b>.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| ArkUI_RenderNodeHandle targetNode | [in] Indicates the default render node to animate. <b>NULL</b> means no group-level default. The default value is <b>NULL</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_AnimationGroup_GetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetTargetNode(OH_ArkUI_AnimationGroupHandle group, ArkUI_RenderNodeHandle *outBorrowedTargetNode)
```

**Description**

Obtains the default target render node of an animation group.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| ArkUI_RenderNodeHandle *outBorrowedTargetNode | [out] Receives a borrowed render-node handle; the caller must not destroy it. <b>NULL</b> means no group-level default is set. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_AnimationGroup_AddPropertyAnimation()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_AddPropertyAnimation(OH_ArkUI_AnimationGroupHandle group, OH_ArkUI_PropertyAnimationHandle animation)
```

**Description**

Adds a property animation to an animation group.<br> The target node of the animation is determined by [OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_settargetnode); if not set, the animation inherits the group's default target set by [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode). Every child must resolve to a non-NULL target when the group is registered.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| OH_ArkUI_PropertyAnimationHandle animation | [in] Indicates the property animation to add. This API does not take ownership of the animation handle; the caller must ensure the animation remains valid when using this group. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li><br>        <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li><br>        <li>[ARKUI_ERROR_CODE_SUB_ANIMATION_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the parameters of the              {@link OH_ArkUI_PropertyAnimationHandle} are invalid.</li>          </ul> |

### OH_ArkUI_NativeModule_AnimationGroup_AddKeyframeAnimation()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_AddKeyframeAnimation(OH_ArkUI_AnimationGroupHandle group, OH_ArkUI_KeyframeAnimationHandle animation)
```

**Description**

Adds a keyframe animation to an animation group.<br> The target node of the animation is determined by [OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_settargetnode); if not set, the animation inherits the group's default target set by [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode). Every child must resolve to a non-NULL target when the group is registered.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] Indicates the keyframe animation to add. This API does not take ownership of the animation handle; the caller must ensure the animation remains valid when using this group. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li><br>        <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li><br>        <li>[ARKUI_ERROR_CODE_SUB_ANIMATION_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the parameters of the              {@link OH_ArkUI_KeyframeAnimationHandle} are invalid.</li>          </ul> |

### OH_ArkUI_NativeModule_AnimationGroup_AddPathAnimation()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_AddPathAnimation(OH_ArkUI_AnimationGroupHandle group, OH_ArkUI_PathAnimationHandle animation)
```

**Description**

Adds a path animation to an animation group.<br> The target node of the animation is determined by [OH_ArkUI_NativeModule_PathAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_settargetnode); if not set, the animation inherits the group's default target set by [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode). Every child must resolve to a non-NULL target when the group is registered.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| OH_ArkUI_PathAnimationHandle animation | [in] Indicates the path animation to add. This API does not take ownership of the animation handle; the caller must ensure the animation remains valid when using this group. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li><br>        <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li><br>        <li>[ARKUI_ERROR_CODE_SUB_ANIMATION_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the parameters of the              {@link OH_ArkUI_PathAnimationHandle} are invalid.</li>          </ul> |

### OH_ArkUI_NativeModule_AddAnimationGroup()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AddAnimationGroup(ArkUI_ContextHandle context, OH_ArkUI_AnimationGroupHandle group, const char *key)
```

**Description**

Registers an animation group on a UIContext with a specified key and starts playback.<br> The UIContext owns the group by <b>key</b>: once registered, the UIContext holds the group's backend (runtime) objects, and the caller may destroy the frontend group handle (and child animation handles) after registration since the backend runs independently by (UIContext, key). Keys are scoped per UIContext (instance): the same key in different UIContexts does not collide. Within one UIContext, if a group is already registered with the same key, the system removes the previous group first (releasing its backend objects) and then registers the new group. The group is later identified and managed by the same (UIContext, key) pair.<br> Each child animation added via [OH_ArkUI_NativeModule_AnimationGroup_AddPropertyAnimation](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_addpropertyanimation), [OH_ArkUI_NativeModule_AnimationGroup_AddKeyframeAnimation](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_addkeyframeanimation), or [OH_ArkUI_NativeModule_AnimationGroup_AddPathAnimation](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_addpathanimation) animates the target node set by its own <b>SetTargetNode</b> API; if that target is not set (or is <b>NULL</b>), it inherits the group's default target set by [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode). At registration, every child must resolve to a non-NULL target node (its own, or the group default), and every resolved target node must belong to the same UIContext as <b>context</b>; otherwise, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned.<br> Playback control and lifecycle APIs ([OH_ArkUI_NativeModule_RemoveAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_removeanimationgroup), [OH_ArkUI_NativeModule_GetAnimationGroupState](capi-native-animate-h.md#oh_arkui_nativemodule_getanimationgroupstate), [OH_ArkUI_NativeModule_HasAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_hasanimationgroup), [OH_ArkUI_NativeModule_PauseAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_pauseanimationgroup), [OH_ArkUI_NativeModule_ResumeAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_resumeanimationgroup), [OH_ArkUI_NativeModule_FinishAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_finishanimationgroup) are all keyed by the (UIContext, key) pair.<br> The finish callback (see [OH_ArkUI_NativeModule_AnimationGroup_RegisterOnFinishCallback](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_registeronfinishcallback)) is invoked exactly once after natural completion, [OH_ArkUI_NativeModule_FinishAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_finishanimationgroup), or destruction of a target node. If [OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup) returns an error, the finish callback is not invoked. After the callback returns, the system automatically removes the group from the UIContext and releases the backend (runtime) objects of the group and its child animations; the frontend handles (the group and its child animations) must still be destroyed by the caller via [OH_ArkUI_NativeModule_AnimationGroup_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_destroy), [OH_ArkUI_NativeModule_PropertyAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_destroy), [OH_ArkUI_NativeModule_KeyframeAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_destroy), or [OH_ArkUI_NativeModule_PathAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_destroy).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle context | [in] Indicates the [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) (UIContext) on which the animation group is registered and played. |
| OH_ArkUI_AnimationGroupHandle group | [in] Indicates the animation group handle. |
| const char *key | [in] Indicates the key used to identify the animation group on the UIContext. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs, or a resolved target node              does not belong to the same UIContext as <b>context</b>.</li>          <li>[ARKUI_ERROR_CODE_SUB_ANIMATION_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a child animation has no resolvable target node.</li>          <li>[ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a re-entrant call is detected on              the same thread.</li>          </ul> |

### OH_ArkUI_NativeModule_RemoveAnimationGroup()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_RemoveAnimationGroup(ArkUI_ContextHandle context, const char *key)
```

**Description**

Removes the animation group identified by the specified key from the UIContext.<br> Stops the group (if still running) and releases the backend (runtime) objects of the group and its child animations. The animated target nodes are restored to their state at the start of the animation. The frontend handles (the group and its child animations) are not freed by this call and must be destroyed by the caller via [OH_ArkUI_NativeModule_AnimationGroup_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_destroy), [OH_ArkUI_NativeModule_PropertyAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_destroy), [OH_ArkUI_NativeModule_KeyframeAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_destroy), or [OH_ArkUI_NativeModule_PathAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_destroy). Use this only for a group that has not stopped on its own (for example, a paused group); once the finish callback is invoked, the group is removed automatically.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle context | [in] Indicates the UIContext on which the animation group was registered. |
| const char *key | [in] Indicates the key of the animation group to remove. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          <li>[ARKUI_ERROR_CODE_ANIMATION_GROUP_NOT_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the animation group identified by              <b>key</b> is not found on the UIContext.</li>          <li>[ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a re-entrant call is detected on              the same thread.</li>          </ul> |

### OH_ArkUI_NativeModule_GetAnimationGroupState()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_GetAnimationGroupState(ArkUI_ContextHandle context, const char *key, OH_ArkUI_AnimationGroupState *state)
```

**Description**

Obtains the playback state of an animation group identified by the specified key on the UIContext.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle context | [in] Indicates the UIContext. |
| const char *key | [in] Indicates the key of the animation group. |
| OH_ArkUI_AnimationGroupState *state | [out] Indicates the pointer to receive the state value. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          <li>[ARKUI_ERROR_CODE_ANIMATION_GROUP_NOT_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the animation group identified by              <b>key</b> is not found on the UIContext.</li>          <li>[ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a re-entrant call is detected on              the same thread.</li>          </ul> |

### OH_ArkUI_NativeModule_HasAnimationGroup()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_HasAnimationGroup(ArkUI_ContextHandle context, const char *key, bool *exists)
```

**Description**

Checks whether an animation group with the specified key exists on the UIContext.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle context | [in] Indicates the UIContext. |
| const char *key | [in] Indicates the key of the animation group. |
| bool *exists | [in] Indicates the pointer to receive the value. <b>true</b> if the animation group exists; <b>false</b> otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          <li>[ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a re-entrant call is detected on              the same thread.</li>          </ul> |

### OH_ArkUI_NativeModule_PauseAnimationGroup()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PauseAnimationGroup(ArkUI_ContextHandle context, const char *key)
```

**Description**

Pauses the animation group identified by the specified key on the UIContext.<br> The animation group must be in the RUNNING state; otherwise, [ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle context | [in] Indicates the UIContext. |
| const char *key | [in] Indicates the key of the animation group. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          <li>[ARKUI_ERROR_CODE_ANIMATION_GROUP_NOT_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the animation group identified by              <b>key</b> is not found on the UIContext.</li>          <li>[ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the animation group is not in the              RUNNING state.</li>          <li>[ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a re-entrant call is detected on              the same thread.</li>          </ul> |

### OH_ArkUI_NativeModule_ResumeAnimationGroup()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ResumeAnimationGroup(ArkUI_ContextHandle context, const char *key)
```

**Description**

Resumes the animation group identified by the specified key on the UIContext.<br> The animation group must be in the PAUSED state; otherwise, [ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle context | [in] Indicates the UIContext. |
| const char *key | [in] Indicates the key of the animation group. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          <li>[ARKUI_ERROR_CODE_ANIMATION_GROUP_NOT_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the animation group identified by              <b>key</b> is not found on the UIContext.</li>          <li>[ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the animation group is not in the              PAUSED state.</li>          <li>[ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a re-entrant call is detected on              the same thread.</li>          </ul> |

### OH_ArkUI_NativeModule_FinishAnimationGroup()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_FinishAnimationGroup(ArkUI_ContextHandle context, const char *key, OH_ArkUI_AnimationFinishMode mode)
```

**Description**

Finishes the animation group identified by the specified key on the UIContext.<br> The animation group is finished according to the specified finish mode: jump to the end state, jump to the start state, or stay at the current value. The animation group must be in the RUNNING or PAUSED state; otherwise, [ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle context | [in] Indicates the UIContext. |
| const char *key | [in] Indicates the key of the animation group. |
| OH_ArkUI_AnimationFinishMode mode | [in] Indicates the finish mode. The value is an enum of [OH_ArkUI_AnimationFinishMode](capi-native-type-visual-h.md#oh_arkui_animationfinishmode). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs,              for example when <b>context</b> or <b>key</b> is invalid, or <b>mode</b> is not a valid              value of [OH_ArkUI_AnimationFinishMode](capi-native-type-visual-h.md#oh_arkui_animationfinishmode).</li>          <li>[ARKUI_ERROR_CODE_ANIMATION_GROUP_NOT_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the animation group identified by              <b>key</b> is not found on the UIContext.</li>          <li>[ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the animation group is not in the              RUNNING or PAUSED state.</li>          <li>[ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a re-entrant call is detected on              the same thread.</li>          </ul> |


