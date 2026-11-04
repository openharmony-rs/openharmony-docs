# native_animate.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=7d5188956273f69fd8f9bca5f8c28b1536d0dc21 translatedAt=2026-10-30T11:44:53.586Z pushedAt=2026-11-04T08:10:51.238Z nl=1 -->

## Overview

Defines a set of animation APIs of ArkUI on the native side. The APIs in **native_animate.h** must be called in the main thread.

**File to include**: <arkui/native_animate.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample**: <!--RP1-->[AnimationNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/AnimationNDK)<!--RP1End-->

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md) | ArkUI_ExpectedFrameRateRange | Defines the expected frame rate range of an animation. This struct defines the frame rate range through the **min**, **max**, and **expected** fields, and the system tries to meet the expected frame rate. |
| [ArkUI_AnimateCompleteCallback](capi-arkui-nativemodule-arkui-animatecompletecallback.md) | ArkUI_AnimateCompleteCallback | Defines the callback type for when the animation playback is complete, which is used to notify you that the animation has ended when the animation playback is complete. You can specify the callback trigger mode through the **type** field, set a custom callback function through the **callback** field, and pass user-defined data to the callback function through the **userData** field. |
| [ArkUI_NativeAnimateAPI_1](capi-arkui-nativemodule-arkui-nativeanimateapi-1.md) | ArkUI_NativeAnimateAPI_1 | Defines a set of animation APIs of ArkUI on the native side. |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md) | ArkUI_AnimateOption | Defines an animation effect configuration, which is used to set the related attributes of the animation. |
| [ArkUI_Curve](capi-arkui-nativemodule-arkui-curve.md) | ArkUI_Curve | Defines the interpolation object of an animation curve, which is used for interpolation calculation of animation attribute values. |
| [ArkUI_Curve*](capi-arkui-nativemodule-arkui-curve8h.md) | ArkUI_CurveHandle | Defines the pointer to a curve interpolation object. Curve interpolation is used to control how animation attribute values change over time, and different types of interpolation curves can achieve different animation transition effects. |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md) | ArkUI_KeyframeAnimateOption | Defines a keyframe animation parameter object, which is used as an input parameter of the keyframe animation APIs. The related APIs must be called on the main thread. |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md) | ArkUI_AnimatorOption | Defines an animator animation parameter object, which is used to set animation attributes when creating an animator animation. |
| [ArkUI_Animator*](capi-arkui-nativemodule-arkui-animator8h.md) | ArkUI_AnimatorHandle | Defines the pointer to an animator animation object, which is used to operate and control the animation object of ArkUI. |
| [ArkUI_AnimatorEvent](capi-arkui-nativemodule-arkui-animatorevent.md) | ArkUI_AnimatorEvent | Defines an animator callback event object, which is used to receive events in the animation state change callback. |
| [ArkUI_AnimatorOnFrameEvent](capi-arkui-nativemodule-arkui-animatoronframeevent.md) | ArkUI_AnimatorOnFrameEvent | Defines the event data object for frame-by-frame callbacks during animator animation playback. |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md) | ArkUI_TransitionEffect | Defines the transition effect parameter object of the **transition** attribute, which is used to configure the transition animation effect when a component appears or disappears. |
| [OH_ArkUI_PropertyAnimation*](capi-arkui-nativemodule-arkui-propertyanimation8h.md) | OH_ArkUI_PropertyAnimationHandle | Defines the handle of a property animation. |
| [OH_ArkUI_KeyframeAnimation*](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) | OH_ArkUI_KeyframeAnimationHandle | Defines the handle of a keyframe animation. |
| [OH_ArkUI_PathAnimation*](capi-arkui-nativemodule-arkui-pathanimation8h.md) | OH_ArkUI_PathAnimationHandle | Defines the handle of a path animation. |
| [OH_ArkUI_AnimationGroup*](capi-arkui-nativemodule-arkui-animationgroup8h.md) | OH_ArkUI_AnimationGroupHandle | Defines the handle of an animation group. |

### Functions

<!--Table: 40%; 60%-->
| Name| Description|
| -- | -- |
| [ArkUI_AnimateOption* OH_ArkUI_AnimateOption_Create()](#oh_arkui_animateoption_create) | Creates an animation configuration.|
| [void OH_ArkUI_AnimateOption_Dispose(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_dispose) | Disposes of an animation configuration.|
| [uint32_t OH_ArkUI_AnimateOption_GetDuration(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_getduration) | Obtains the animation duration, in milliseconds.|
| [float OH_ArkUI_AnimateOption_GetTempo(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_gettempo) | Obtains the playback tempo of an animation. |
| [ArkUI_AnimationCurve OH_ArkUI_AnimateOption_GetCurve(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_getcurve) | Obtains an animation curve.|
| [int32_t OH_ArkUI_AnimateOption_GetDelay(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_getdelay) | Obtains the animation delay, in milliseconds.|
| [int32_t OH_ArkUI_AnimateOption_GetIterations(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_getiterations) | Obtains the number of times that an animation is played.|
| [ArkUI_AnimationPlayMode OH_ArkUI_AnimateOption_GetPlayMode(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_getplaymode) | Obtains the playback mode of an animation.|
| [ArkUI_ExpectedFrameRateRange* OH_ArkUI_AnimateOption_GetExpectedFrameRateRange(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_getexpectedframeraterange) | Obtains the expected frame rate range of an animation.|
| [void OH_ArkUI_AnimateOption_SetDuration(ArkUI_AnimateOption* option, int32_t value)](#oh_arkui_animateoption_setduration) | Sets the animation duration, in milliseconds.|
| [void OH_ArkUI_AnimateOption_SetTempo(ArkUI_AnimateOption* option, float value)](#oh_arkui_animateoption_settempo) | Sets the playback tempo of an animation. |
| [void OH_ArkUI_AnimateOption_SetCurve(ArkUI_AnimateOption* option, ArkUI_AnimationCurve value)](#oh_arkui_animateoption_setcurve) | Sets the custom curve of an animation. |
| [void OH_ArkUI_AnimateOption_SetDelay(ArkUI_AnimateOption* option, int32_t value)](#oh_arkui_animateoption_setdelay) | Sets the animation delay, in milliseconds.|
| [void OH_ArkUI_AnimateOption_SetIterations(ArkUI_AnimateOption* option, int32_t value)](#oh_arkui_animateoption_setiterations) | Sets the number of times that an animation is played.|
| [void OH_ArkUI_AnimateOption_SetPlayMode(ArkUI_AnimateOption* option, ArkUI_AnimationPlayMode value)](#oh_arkui_animateoption_setplaymode) | Sets the playback mode for an animation.|
| [void OH_ArkUI_AnimateOption_SetExpectedFrameRateRange(ArkUI_AnimateOption* option, ArkUI_ExpectedFrameRateRange* value)](#oh_arkui_animateoption_setexpectedframeraterange) | Sets the expected frame rate range of the animation.|
| [void OH_ArkUI_AnimateOption_SetICurve(ArkUI_AnimateOption* option, ArkUI_CurveHandle value)](#oh_arkui_animateoption_seticurve) | Sets the interpolation curve of an animation. |
| [ArkUI_CurveHandle OH_ArkUI_AnimateOption_GetICurve(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_geticurve) | Obtains the interpolation curve of the animation. |
| [ArkUI_KeyframeAnimateOption* OH_ArkUI_KeyframeAnimateOption_Create(int32_t size)](#oh_arkui_keyframeanimateoption_create) | Creates a keyframe animation parameter object.|
| [void OH_ArkUI_KeyframeAnimateOption_Dispose(ArkUI_KeyframeAnimateOption* option)](#oh_arkui_keyframeanimateoption_dispose) | Disposes of a keyframe animation parameter object.|
| [int32_t OH_ArkUI_KeyframeAnimateOption_SetDelay(ArkUI_KeyframeAnimateOption* option, int32_t value)](#oh_arkui_keyframeanimateoption_setdelay) | Sets the overall delay of a keyframe animation, in ms. By default, playback is not delayed. |
| [int32_t OH_ArkUI_KeyframeAnimateOption_SetIterations(ArkUI_KeyframeAnimateOption* option, int32_t value)](#oh_arkui_keyframeanimateoption_setiterations) | Sets the number of times that the keyframe animation is played. By default, the animation is played once. The value **-1** indicates that the animation is played for an unlimited number of times. The value **0** indicates that no animation is played. |
| [int32_t OH_ArkUI_KeyframeAnimateOption_RegisterOnFinishCallback(ArkUI_KeyframeAnimateOption* option, void* userData, void (\*onFinish)(void* userData))](#oh_arkui_keyframeanimateoption_registeronfinishcallback) | Sets the callback invoked when the keyframe animation playback is complete. This API is called after the keyframe animation ([ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)) has played for the specified number of times. |
| [int32_t OH_ArkUI_KeyframeAnimateOption_SetExpectedFrameRate(ArkUI_KeyframeAnimateOption* option, ArkUI_ExpectedFrameRateRange* frameRate)](#oh_arkui_keyframeanimateoption_setexpectedframerate) | Sets the expected frame rate for a keyframe animation.|
| [int32_t OH_ArkUI_KeyframeAnimateOption_SetDuration(ArkUI_KeyframeAnimateOption* option, int32_t value, int32_t index)](#oh_arkui_keyframeanimateoption_setduration) | Sets the duration of a keyframe animation, in milliseconds.|
| [int32_t OH_ArkUI_KeyframeAnimateOption_SetCurve(ArkUI_KeyframeAnimateOption* option, ArkUI_CurveHandle value, int32_t index)](#oh_arkui_keyframeanimateoption_setcurve) | Sets the animation curve for a specific keyframe animation segment.|
| [int32_t OH_ArkUI_KeyframeAnimateOption_RegisterOnEventCallback(ArkUI_KeyframeAnimateOption* option, void* userData, void (\*event)(void* userData), int32_t index)](#oh_arkui_keyframeanimateoption_registeroneventcallback) | Sets the closure function of the state at the time of the keyframe, that is, the state to be reached at the time of the keyframe.|
| [int32_t OH_ArkUI_KeyframeAnimateOption_GetDelay(ArkUI_KeyframeAnimateOption* option)](#oh_arkui_keyframeanimateoption_getdelay) | Obtains the overall delay of the keyframe animation, in ms. |
| [int32_t OH_ArkUI_KeyframeAnimateOption_GetIterations(ArkUI_KeyframeAnimateOption* option)](#oh_arkui_keyframeanimateoption_getiterations) | Obtains the number of times that a keyframe animation is played.|
| [ArkUI_ExpectedFrameRateRange* OH_ArkUI_KeyframeAnimateOption_GetExpectedFrameRate(ArkUI_KeyframeAnimateOption* option)](#oh_arkui_keyframeanimateoption_getexpectedframerate) | Obtains the expected frame rate from keyframe animation parameters.|
| [int32_t OH_ArkUI_KeyframeAnimateOption_GetDuration(ArkUI_KeyframeAnimateOption* option, int32_t index)](#oh_arkui_keyframeanimateoption_getduration) | Obtains the duration of a specific state in a keyframe animation, in milliseconds.|
| [ArkUI_CurveHandle OH_ArkUI_KeyframeAnimateOption_GetCurve(ArkUI_KeyframeAnimateOption* option, int32_t index)](#oh_arkui_keyframeanimateoption_getcurve) | Obtains the animation curve of a specific state in a keyframe animation.|
| [ArkUI_AnimatorOption* OH_ArkUI_AnimatorOption_Create(int32_t keyframeSize)](#oh_arkui_animatoroption_create) | Creates an **AnimatorOption** object.|
| [void OH_ArkUI_AnimatorOption_Dispose(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_dispose) | Disposes of the **AnimatorOption** object.|
| [int32_t OH_ArkUI_AnimatorOption_SetDuration(ArkUI_AnimatorOption* option, int32_t value)](#oh_arkui_animatoroption_setduration) | Sets the duration of the animator animation playback, in milliseconds.|
| [int32_t OH_ArkUI_AnimatorOption_SetDelay(ArkUI_AnimatorOption* option, int32_t value)](#oh_arkui_animatoroption_setdelay) | Sets the delay time of the animator animation playback, in ms. |
| [int32_t OH_ArkUI_AnimatorOption_SetIterations(ArkUI_AnimatorOption* option, int32_t value)](#oh_arkui_animatoroption_setiterations) | Sets the number of times that an animator animation is played. By default, the animation is played once. The value **-1** indicates that the animation is played for an unlimited number of times. The value **0** indicates that no animation is played.|
| [int32_t OH_ArkUI_AnimatorOption_SetFill(ArkUI_AnimatorOption* option, ArkUI_AnimationFillMode value)](#oh_arkui_animatoroption_setfill) | Sets the state retained by the component before the animation starts and after it ends. |
| [int32_t OH_ArkUI_AnimatorOption_SetDirection(ArkUI_AnimatorOption* option, ArkUI_AnimationDirection value)](#oh_arkui_animatoroption_setdirection) | Sets the playback direction.|
| [int32_t OH_ArkUI_AnimatorOption_SetCurve(ArkUI_AnimatorOption* option, ArkUI_CurveHandle value)](#oh_arkui_animatoroption_setcurve) | Sets the interpolation curve for the animation of an animator.|
| [int32_t OH_ArkUI_AnimatorOption_SetBegin(ArkUI_AnimatorOption* option, float value)](#oh_arkui_animatoroption_setbegin) | Sets the interpolation start point of an animation.|
| [int32_t OH_ArkUI_AnimatorOption_SetEnd(ArkUI_AnimatorOption* option, float value)](#oh_arkui_animatoroption_setend) | Sets the interpolation end point for the animation of an animator.|
| [int32_t OH_ArkUI_AnimatorOption_SetExpectedFrameRateRange(ArkUI_AnimatorOption* option, ArkUI_ExpectedFrameRateRange* value)](#oh_arkui_animatoroption_setexpectedframeraterange) | Sets the expected frame rate range of an animator animation.|
| [int32_t OH_ArkUI_AnimatorOption_SetKeyframe(ArkUI_AnimatorOption* option, float time, float value, int32_t index)](#oh_arkui_animatoroption_setkeyframe) | Sets the keyframe parameters of an animator animation.|
| [int32_t OH_ArkUI_AnimatorOption_SetKeyframeCurve(ArkUI_AnimatorOption* option, ArkUI_CurveHandle value, int32_t index)](#oh_arkui_animatoroption_setkeyframecurve) | Sets the keyframe curve type for the animation of an animator.|
| [int32_t OH_ArkUI_AnimatorOption_GetDuration(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getduration) | Obtains the playback duration of the animator animation, in ms. |
| [int32_t OH_ArkUI_AnimatorOption_GetDelay(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getdelay) | Obtains the delay for playing an animator animation, in ms. |
| [int32_t OH_ArkUI_AnimatorOption_GetIterations(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getiterations) | Obtains the number of times that an animator animation is played.|
| [ArkUI_AnimationFillMode OH_ArkUI_AnimatorOption_GetFill(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getfill) | Obtains the status of the component before and after the animator animation execution.|
| [ArkUI_AnimationDirection OH_ArkUI_AnimatorOption_GetDirection(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getdirection) | Obtains the playback direction of an animator animation.|
| [ArkUI_CurveHandle OH_ArkUI_AnimatorOption_GetCurve(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getcurve) | Obtains the interpolation curve of an animator animation.|
| [float OH_ArkUI_AnimatorOption_GetBegin(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getbegin) | Obtains the interpolation start point of an animator animation. When the animator animation is a keyframe animation, the value returned by this API is meaningless. |
| [float OH_ArkUI_AnimatorOption_GetEnd(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getend) | Obtains the interpolation end point of an animator animation. When the animator animation is a keyframe animation, the value returned by this API is meaningless. |
| [ArkUI_ExpectedFrameRateRange* OH_ArkUI_AnimatorOption_GetExpectedFrameRateRange(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getexpectedframeraterange) | Obtains the expected frame rate range of an animator animation.|
| [float OH_ArkUI_AnimatorOption_GetKeyframeTime(ArkUI_AnimatorOption* option, int32_t index)](#oh_arkui_animatoroption_getkeyframetime) | Obtains the keyframe time of the animator playback, in milliseconds.|
| [float OH_ArkUI_AnimatorOption_GetKeyframeValue(ArkUI_AnimatorOption* option, int32_t index)](#oh_arkui_animatoroption_getkeyframevalue) | Obtains the interpolation target value of the animator animation at the keyframe position. |
| [ArkUI_CurveHandle OH_ArkUI_AnimatorOption_GetKeyframeCurve(ArkUI_AnimatorOption* option, int32_t index)](#oh_arkui_animatoroption_getkeyframecurve) | Obtains the interpolation curve for a keyframe in the animation of an animator.|
| [void* OH_ArkUI_AnimatorEvent_GetUserData(ArkUI_AnimatorEvent* event)](#oh_arkui_animatorevent_getuserdata) | Obtains the user-defined object in an animation event object.|
| [void* OH_ArkUI_AnimatorOnFrameEvent_GetUserData(ArkUI_AnimatorOnFrameEvent* event)](#oh_arkui_animatoronframeevent_getuserdata) | Obtains the user-defined object in the frame event of an animation.|
| [float OH_ArkUI_AnimatorOnFrameEvent_GetValue(ArkUI_AnimatorOnFrameEvent* event)](#oh_arkui_animatoronframeevent_getvalue) | Obtains the interpolation result in the animation frame callback event object.|
| [int32_t OH_ArkUI_AnimatorOption_RegisterOnFrameCallback(ArkUI_AnimatorOption* option, void* userData, void (\*callback)(ArkUI_AnimatorOnFrameEvent* event))](#oh_arkui_animatoroption_registeronframecallback) | Sets the callback invoked when the animator receives a frame.|
| [int32_t OH_ArkUI_AnimatorOption_RegisterOnFinishCallback(ArkUI_AnimatorOption* option, void* userData, void (\*callback)(ArkUI_AnimatorEvent* event))](#oh_arkui_animatoroption_registeronfinishcallback) | Sets the callback invoked when the animation playback is complete. This API is called after the animator animation has played for the specified number of times or when [OH_ArkUI_Animator_Finish](#oh_arkui_animator_finish) is called to end the animation. |
| [int32_t OH_ArkUI_AnimatorOption_RegisterOnCancelCallback(ArkUI_AnimatorOption* option, void* userData, void (\*callback)(ArkUI_AnimatorEvent* event))](#oh_arkui_animatoroption_registeroncancelcallback) | Sets the callback invoked when the animation playback is canceled.|
| [int32_t OH_ArkUI_AnimatorOption_RegisterOnRepeatCallback(ArkUI_AnimatorOption* option, void* userData, void (\*callback)(ArkUI_AnimatorEvent* event))](#oh_arkui_animatoroption_registeronrepeatcallback) | Sets the callback invoked when the animation playback is repeated.|
| [int32_t OH_ArkUI_Animator_ResetAnimatorOption(ArkUI_AnimatorHandle animatorHandle, ArkUI_AnimatorOption* option)](#oh_arkui_animator_resetanimatoroption) | Resets the configuration of the animator animation. |
| [int32_t OH_ArkUI_Animator_Play(ArkUI_AnimatorHandle animatorHandle)](#oh_arkui_animator_play) | Starts the animation of an animator.|
| [int32_t OH_ArkUI_Animator_Finish(ArkUI_AnimatorHandle animatorHandle)](#oh_arkui_animator_finish) | Finishes the animator animation, so that the animation jumps to the end state. The difference from **OH_ArkUI_Animator_Cancel** is: **Finish** completes the animation to the end state, while **Cancel** interrupts the animation and returns it to the initial state. |
| [int32_t OH_ArkUI_Animator_Pause(ArkUI_AnimatorHandle animatorHandle)](#oh_arkui_animator_pause) | Pauses the animation of an animator.|
| [int32_t OH_ArkUI_Animator_Cancel(ArkUI_AnimatorHandle animatorHandle)](#oh_arkui_animator_cancel) | Cancels the animation of an animator.|
| [int32_t OH_ArkUI_Animator_Reverse(ArkUI_AnimatorHandle animatorHandle)](#oh_arkui_animator_reverse) | Plays this animation in reverse order.|
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateCurveByType(ArkUI_AnimationCurve curve)](#oh_arkui_curve_createcurvebytype) | Implements initialization for the interpolation curve, which is used to create an interpolation curve based on the input parameter.|
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateStepsCurve(int32_t count, bool end)](#oh_arkui_curve_createstepscurve) | Creates a step curve.|
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateCubicBezierCurve(float x1, float y1, float x2, float y2)](#oh_arkui_curve_createcubicbeziercurve) | Creates a cubic Bezier curve object. The animation duration is controlled by the duration parameter in the animation parameters. |
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateSpringCurve(float velocity, float mass, float stiffness, float damping)](#oh_arkui_curve_createspringcurve) | Creates a spring curve object. The curve shape is determined by the spring parameters, and the animation duration is controlled by the duration parameter in the animation parameters. |
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateSpringMotion(float response, float dampingFraction, float overlapDuration)](#oh_arkui_curve_createspringmotion) | Creates a spring animation curve. If multiple spring animations are applied to the same attribute of an object, each animation replaces their predecessor and inherits the velocity. |
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateResponsiveSpringMotion(float response, float dampingFraction, float overlapDuration)](#oh_arkui_curve_createresponsivespringmotion) | Creates a responsive spring animation curve object, which is a special case of **springMotion** with only different default parameters and can be used together with **springMotion**. If multiple spring animations are applied to the same attribute of the same object, each animation replaces their predecessor and inherits the velocity. |
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateInterpolatingSpring(float velocity, float mass, float stiffness, float damping)](#oh_arkui_curve_createinterpolatingspring) | Creates an interpolating spring curve animated from 0 to 1. The actual animation value is calculated based on the curve.|
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateCustomCurve(void* userData, float (\*interpolate)(float fraction, void* userdata))](#oh_arkui_curve_createcustomcurve) | Creates a custom curve.|
| [void OH_ArkUI_Curve_DisposeCurve(ArkUI_CurveHandle curveHandle)](#oh_arkui_curve_disposecurve) | Disposes of a custom curve.|
| [ArkUI_TransitionEffect* OH_ArkUI_CreateOpacityTransitionEffect(float opacity)](#oh_arkui_createopacitytransitioneffect) | Creates an opacity effect object for component transition.|
| [ArkUI_TransitionEffect* OH_ArkUI_CreateTranslationTransitionEffect(ArkUI_TranslationOptions* translate)](#oh_arkui_createtranslationtransitioneffect) | Creates a translation effect object for component transition.|
| [ArkUI_TransitionEffect* OH_ArkUI_CreateScaleTransitionEffect(ArkUI_ScaleOptions* scale)](#oh_arkui_createscaletransitioneffect) | Creates a scaling object for component transition.|
| [ArkUI_TransitionEffect* OH_ArkUI_CreateRotationTransitionEffect(ArkUI_RotationOptions* rotate)](#oh_arkui_createrotationtransitioneffect) | Creates a rotation effect object for component transition.|
| [ArkUI_TransitionEffect* OH_ArkUI_CreateMovementTransitionEffect(ArkUI_TransitionEdge edge)](#oh_arkui_createmovementtransitioneffect) | Creates a movement transition effect object for a component, which is used for the transition effect of the component sliding in or out from a specified edge and is suitable for simple scenarios where only the sliding direction needs to be specified. The difference from [OH_ArkUI_CreateTranslationTransitionEffect](#oh_arkui_createtranslationtransitioneffect) is that the latter supports custom precise translation parameters in the x, y, and z directions and is suitable for scenarios where a specific displacement distance needs to be specified. |
| [ArkUI_TransitionEffect* OH_ArkUI_CreateAsymmetricTransitionEffect(ArkUI_TransitionEffect* appear, ArkUI_TransitionEffect* disappear)](#oh_arkui_createasymmetrictransitioneffect) | Creates an asymmetric transition effect.|
| [ArkUI_TransitionEffect* OH_ArkUI_CreateIdentityTransitionEffect(void)](#oh_arkui_createidentitytransitioneffect) | Creates an effect object with no transition.|
| [void OH_ArkUI_TransitionEffect_Dispose(ArkUI_TransitionEffect* effect)](#oh_arkui_transitioneffect_dispose) | Disposes of a transition effect.|
| [int32_t OH_ArkUI_TransitionEffect_Combine(ArkUI_TransitionEffect* firstEffect, ArkUI_TransitionEffect* secondEffect)](#oh_arkui_transitioneffect_combine) | Sets a combination of transition effects.|
| [int32_t OH_ArkUI_TransitionEffect_SetAnimation(ArkUI_TransitionEffect* effect, ArkUI_AnimateOption* animation)](#oh_arkui_transitioneffect_setanimation) | Sets transition effect animation settings.|
| [OH_ArkUI_PropertyAnimationHandle OH_ArkUI_NativeModule_PropertyAnimation_Create(OH_ArkUI_AnimationPropertyType propertyType)](#oh_arkui_nativemodule_propertyanimation_create) | Creates a property animation for a specified animatable property.<br>The value of **propertyType** must be a valid one of [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype); otherwise, this API returns **NULL**. |
| [void OH_ArkUI_NativeModule_PropertyAnimation_Destroy(OH_ArkUI_PropertyAnimationHandle animation)](#oh_arkui_nativemodule_propertyanimation_destroy) | Destroys a property animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetFromValue(OH_ArkUI_PropertyAnimationHandle animation, const ArkUI_NumberValue *value, int32_t size)](#oh_arkui_nativemodule_propertyanimation_setfromvalue) | Sets the start value of a property animation.<br>It is recommended to set the start value. If it is not set, the animation starts from the current property value by default. If the start value is not set and the corresponding property has never been assigned a value, the property animation cannot be generated because there is no valid start state. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetFromValue(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_NumberValue *value, int32_t size)](#oh_arkui_nativemodule_propertyanimation_getfromvalue) | Obtains the start value of a property animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetToValue(OH_ArkUI_PropertyAnimationHandle animation, const ArkUI_NumberValue *value, int32_t size)](#oh_arkui_nativemodule_propertyanimation_settovalue) | Sets the end value of a property animation.<br>The end value must be set; otherwise, the property animation handle is meaningless. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetToValue(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_NumberValue *value, int32_t size)](#oh_arkui_nativemodule_propertyanimation_gettovalue) | Obtains the end value of a property animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetDuration(OH_ArkUI_PropertyAnimationHandle animation, int32_t duration)](#oh_arkui_nativemodule_propertyanimation_setduration) | Sets the duration of a property animation.<br>The effective animation duration is determined by the following priority: if the duration of the child animation is set through this API, that value is used; otherwise, the duration set on the animation group through [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, the default value of 1,000 milliseconds is used. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetDuration(OH_ArkUI_PropertyAnimationHandle animation, int32_t *duration)](#oh_arkui_nativemodule_propertyanimation_getduration) | Obtains the duration of a property animation.<br>This API returns only the duration explicitly set on this animation. The value inherited from an animation group or the default value is resolved at runtime and is not stored on this object. If no duration is set on this animation, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. The duration that actually takes effect at runtime is determined by the following priority: if a duration is set through [OH_ArkUI_NativeModule_PropertyAnimation_SetDuration](#oh_arkui_nativemodule_propertyanimation_setduration), that value is used; otherwise, the animation group's duration set through [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, the default value of 1,000 milliseconds is used. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetDelay(OH_ArkUI_PropertyAnimationHandle animation, int32_t delay)](#oh_arkui_nativemodule_propertyanimation_setdelay) | Sets the delay of a property animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetDelay(OH_ArkUI_PropertyAnimationHandle animation, int32_t *delay)](#oh_arkui_nativemodule_propertyanimation_getdelay) | Obtains the delay of a property animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetCurve(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_CurveHandle curve)](#oh_arkui_nativemodule_propertyanimation_setcurve) | Sets the animation curve of a property animation.<br>The animation curve that actually takes effect is determined by the following priority: if a curve is set through this API, that value is used; otherwise, the curve set on the animation group through [OH_ArkUI_NativeModule_AnimationGroup_SetCurve](#oh_arkui_nativemodule_animationgroup_setcurve) is used; if neither is set, [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) is used. Spring curves (**springMotion**, **responsiveSpringMotion**, and **interpolatingSpring**) are supported. When a spring curve is set, the duration set through [OH_ArkUI_NativeModule_PropertyAnimation_SetDuration](#oh_arkui_nativemodule_propertyanimation_setduration) does not take effect, and the animation duration is determined by the spring curve. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetCurve(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_CurveHandle *outBorrowedCurve)](#oh_arkui_nativemodule_propertyanimation_getcurve) | Obtains the animation curve of a property animation.<br>This API returns only the curve explicitly set on this animation. The value inherited from an animation group or the default value is resolved at runtime and is not stored on this object. If no curve is set on this animation, **outBorrowedCurve** is output as **NULL**. The animation curve that actually takes effect at runtime is determined by the following priority: if a curve is set through [OH_ArkUI_NativeModule_PropertyAnimation_SetCurve](#oh_arkui_nativemodule_propertyanimation_setcurve), that value is used; otherwise, the animation group's curve set through [OH_ArkUI_NativeModule_AnimationGroup_SetCurve](#oh_arkui_nativemodule_animationgroup_setcurve) is used; if neither is set, [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) is used. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetTempo(OH_ArkUI_PropertyAnimationHandle animation, float tempo)](#oh_arkui_nativemodule_propertyanimation_settempo) | Sets the playback tempo of a property animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetTempo(OH_ArkUI_PropertyAnimationHandle animation, float *tempo)](#oh_arkui_nativemodule_propertyanimation_gettempo) | Obtains the playback tempo of a property animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetAutoReverse(OH_ArkUI_PropertyAnimationHandle animation, bool autoReverse)](#oh_arkui_nativemodule_propertyanimation_setautoreverse) | Sets whether to automatically reverse a property animation.<br>When auto-reverse is enabled, the animation alternates between forward and reverse playback in each playback cycle. The default value is **false**. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetAutoReverse(OH_ArkUI_PropertyAnimationHandle animation, bool *autoReverse)](#oh_arkui_nativemodule_propertyanimation_getautoreverse) | Obtains whether auto-reverse is enabled for a property animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetIterations(OH_ArkUI_PropertyAnimationHandle animation, int32_t iterations)](#oh_arkui_nativemodule_propertyanimation_setiterations) | Sets the number of times that a property animation is played. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetIterations(OH_ArkUI_PropertyAnimationHandle animation, int32_t *iterations)](#oh_arkui_nativemodule_propertyanimation_getiterations) | Obtains the number of times that a property animation is played. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_RenderNodeHandle targetNode)](#oh_arkui_nativemodule_propertyanimation_settargetnode) | Sets the target render node of a property animation.<br>The target node is the render node driven by this property animation. If it is **NULL** (default value), the animation inherits the default target of the animation group set through [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](#oh_arkui_nativemodule_animationgroup_settargetnode). A non-**NULL** target must belong to the same UIContext registered by the animation group. This check is performed when the animation group is registered through [OH_ArkUI_NativeModule_AddAnimationGroup](#oh_arkui_nativemodule_addanimationgroup). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetTargetNode(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_RenderNodeHandle *outBorrowedTargetNode)](#oh_arkui_nativemodule_propertyanimation_gettargetnode) | Obtains the target render node of a property animation. |
| [OH_ArkUI_KeyframeAnimationHandle OH_ArkUI_NativeModule_KeyframeAnimation_Create(OH_ArkUI_AnimationPropertyType propertyType, int32_t size)](#oh_arkui_nativemodule_keyframeanimation_create) | Creates a keyframe animation for a specified animatable property.<br>By default, the keyframe time points of each keyframe are evenly distributed in the range [0, 1] by index (for example, when there are three keyframes, the first frame is 0.0, the second frame is 0.5, and the third frame is 1.0). Use [OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTimes](#oh_arkui_nativemodule_keyframeanimation_setkeytimes) or [OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTime](#oh_arkui_nativemodule_keyframeanimation_setkeytime) to customize the keyframe time points.<br>The value of **propertyType** must be a valid one of [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype), and the value of **size** must be at least **2**; otherwise, this API returns **NULL**. |
| [void OH_ArkUI_NativeModule_KeyframeAnimation_Destroy(OH_ArkUI_KeyframeAnimationHandle animation)](#oh_arkui_nativemodule_keyframeanimation_destroy) | Destroys a keyframe animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTimes(OH_ArkUI_KeyframeAnimationHandle animation, const float *keyTimes, int32_t size)](#oh_arkui_nativemodule_keyframeanimation_setkeytimes) | Sets the keyframe time points of keyframes.<br>If this API is not called, the keyframe time point of each keyframe is evenly distributed in the range [0, 1] by index by default (for example, when there are three keyframes, the first frame is 0.0, the second frame is 0.5, and the third frame is 1.0).<br>The elements in **keyTimes** must be non-decreasing, and **size** must be equal to the number of keyframes of the keyframe animation (that is, the **size** value specified when creating the animation through [OH_ArkUI_NativeModule_KeyframeAnimation_Create](#oh_arkui_nativemodule_keyframeanimation_create)). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetKeyTime(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, float *keyTime)](#oh_arkui_nativemodule_keyframeanimation_getkeytime) | Obtains the keyframe time point of the keyframe at the specified index. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTime(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, float keyTime)](#oh_arkui_nativemodule_keyframeanimation_setkeytime) | Sets the keyframe time point of the keyframe at the specified index.<br>If this API is not called to set a keyframe, its keyframe time point is evenly distributed in the range [0, 1] by index by default (for example, when there are three keyframes, the first frame is 0.0, the second frame is 0.5, and the third frame is 1.0).|
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetValue(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, const ArkUI_NumberValue *value, int32_t size)](#oh_arkui_nativemodule_keyframeanimation_setvalue) | Sets the value of the keyframe at the specified index. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetValues(OH_ArkUI_KeyframeAnimationHandle animation, const ArkUI_NumberValue *values, int32_t size)](#oh_arkui_nativemodule_keyframeanimation_setvalues) | Sets the values of all keyframes at once.<br>The values are provided as a flattened array. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetValue(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, ArkUI_NumberValue *value, int32_t size)](#oh_arkui_nativemodule_keyframeanimation_getvalue) | Obtains the value of the keyframe at the specified index. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetCurves(OH_ArkUI_KeyframeAnimationHandle animation, const ArkUI_CurveHandle *value, int32_t size)](#oh_arkui_nativemodule_keyframeanimation_setcurves) | Sets the animation curve of a keyframe. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, ArkUI_CurveHandle curve)](#oh_arkui_nativemodule_keyframeanimation_setcurve) | Sets the animation curve for a keyframe at a specified index. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetCurve(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, ArkUI_CurveHandle *outBorrowedCurve)](#oh_arkui_nativemodule_keyframeanimation_getcurve) | Obtains the animation curve of a keyframe at a specified index.<br>This API returns only the curve explicitly set for the keyframe. The value inherited from the animation group or the default value is resolved at runtime and is not stored on this object. If no curve is set for the keyframe, **outBorrowedCurve** is output as **NULL**. The animation curve that actually takes effect at runtime is determined by the following priority: if a curve is set for the keyframe through [OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve](#oh_arkui_nativemodule_keyframeanimation_setcurve) or [OH_ArkUI_NativeModule_KeyframeAnimation_SetCurves](#oh_arkui_nativemodule_keyframeanimation_setcurves), that value is used; otherwise, the animation group's curve set through [OH_ArkUI_NativeModule_AnimationGroup_SetCurve](#oh_arkui_nativemodule_animationgroup_setcurve) is used; if neither is set, [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) is used. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration(OH_ArkUI_KeyframeAnimationHandle animation, int32_t duration)](#oh_arkui_nativemodule_keyframeanimation_setduration) | Sets the duration for a keyframe animation.<br>The effective animation duration is determined by the following priority: if a duration is set through this API, that value is used; otherwise, the duration set on the animation group through [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, the default value of 1,000 milliseconds is used. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetDuration(OH_ArkUI_KeyframeAnimationHandle animation, int32_t *duration)](#oh_arkui_nativemodule_keyframeanimation_getduration) | Obtains the duration of a keyframe animation.<br>This API returns only the duration explicitly set on this animation. The value inherited from an animation group or the default value is resolved at runtime and is not stored on this object. If no duration is set on this animation, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. The animation duration that actually takes effect at runtime is determined by the following priority: if a duration is set through [OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration](#oh_arkui_nativemodule_keyframeanimation_setduration), that value is used; otherwise, the animation group's duration set through [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, the default value of 1,000 milliseconds is used. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetDelay(OH_ArkUI_KeyframeAnimationHandle animation, int32_t delay)](#oh_arkui_nativemodule_keyframeanimation_setdelay) | Sets the delay for a keyframe animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetDelay(OH_ArkUI_KeyframeAnimationHandle animation, int32_t *delay)](#oh_arkui_nativemodule_keyframeanimation_getdelay) | Obtains the delay of a keyframe animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetTempo(OH_ArkUI_KeyframeAnimationHandle animation, float tempo)](#oh_arkui_nativemodule_keyframeanimation_settempo) | Sets the playback tempo for a keyframe animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetTempo(OH_ArkUI_KeyframeAnimationHandle animation, float *tempo)](#oh_arkui_nativemodule_keyframeanimation_gettempo) | Obtains the playback tempo of a keyframe animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetAutoReverse(OH_ArkUI_KeyframeAnimationHandle animation, bool autoReverse)](#oh_arkui_nativemodule_keyframeanimation_setautoreverse) | Sets whether to automatically reverse a keyframe animation.<br>When auto-reverse is enabled, the animation alternates between forward and reverse playback in each playback cycle. The default value is **false**. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetAutoReverse(OH_ArkUI_KeyframeAnimationHandle animation, bool *autoReverse)](#oh_arkui_nativemodule_keyframeanimation_getautoreverse) | Obtains whether auto-reverse is enabled for a keyframe animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetIterations(OH_ArkUI_KeyframeAnimationHandle animation, int32_t iterations)](#oh_arkui_nativemodule_keyframeanimation_setiterations) | Sets the number of times that a keyframe animation is played. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetIterations(OH_ArkUI_KeyframeAnimationHandle animation, int32_t *iterations)](#oh_arkui_nativemodule_keyframeanimation_getiterations) | Obtains the number of times that a keyframe animation is played. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode(OH_ArkUI_KeyframeAnimationHandle animation, ArkUI_RenderNodeHandle targetNode)](#oh_arkui_nativemodule_keyframeanimation_settargetnode) | Sets the target render node for a keyframe animation.<br>The target node is the render node driven by this keyframe animation. If it is **NULL** (default value), the animation inherits the default target of the animation group set through [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](#oh_arkui_nativemodule_animationgroup_settargetnode). A non-**NULL** target must belong to the same UIContext registered by the animation group. This check is performed when the animation group is registered through [OH_ArkUI_NativeModule_AddAnimationGroup](#oh_arkui_nativemodule_addanimationgroup). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetTargetNode(OH_ArkUI_KeyframeAnimationHandle animation, ArkUI_RenderNodeHandle *outBorrowedTargetNode)](#oh_arkui_nativemodule_keyframeanimation_gettargetnode) | Obtains the target render node for a keyframe animation. |
| [OH_ArkUI_PathAnimationHandle OH_ArkUI_NativeModule_PathAnimation_Create(const char *path)](#oh_arkui_nativemodule_pathanimation_create) | Creates a path animation to move a component along a geometric path.<br>The path animation applies to the [OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION](capi-native-type-visual-h.md#oh_arkui_animationpropertytype) property.<br>The path animation does not support setting a curve. It always uses [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) at runtime and does not inherit the animation group's curve. |
| [void OH_ArkUI_NativeModule_PathAnimation_Destroy(OH_ArkUI_PathAnimationHandle animation)](#oh_arkui_nativemodule_pathanimation_destroy) | Destroys a path animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetDuration(OH_ArkUI_PathAnimationHandle animation, int32_t duration)](#oh_arkui_nativemodule_pathanimation_setduration) | Sets the duration of a path animation.<br>The effective animation duration is determined by the following priority: if a duration is set through this API, that value is used; otherwise, the duration set on the animation group through [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, the default value of 1,000 milliseconds is used. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetDuration(OH_ArkUI_PathAnimationHandle animation, int32_t *duration)](#oh_arkui_nativemodule_pathanimation_getduration) | Obtains the duration of a path animation.<br>This API returns only the duration explicitly set on this animation. The value inherited from an animation group or the default value is resolved at runtime and is not stored on this object. If no duration is set on this animation, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. The animation duration that actually takes effect at runtime is determined by the following priority: if a duration is set through [OH_ArkUI_NativeModule_PathAnimation_SetDuration](#oh_arkui_nativemodule_pathanimation_setduration), that value is used; otherwise, the animation group's duration set through [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, the default value of 1,000 milliseconds is used. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetDelay(OH_ArkUI_PathAnimationHandle animation, int32_t delay)](#oh_arkui_nativemodule_pathanimation_setdelay) | Sets the delay for a path animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetDelay(OH_ArkUI_PathAnimationHandle animation, int32_t *delay)](#oh_arkui_nativemodule_pathanimation_getdelay) | Obtains the delay for a path animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetTempo(OH_ArkUI_PathAnimationHandle animation, float tempo)](#oh_arkui_nativemodule_pathanimation_settempo) | Sets the playback tempo of a path animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetTempo(OH_ArkUI_PathAnimationHandle animation, float *tempo)](#oh_arkui_nativemodule_pathanimation_gettempo) | Obtains the playback tempo of a path animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetAutoReverse(OH_ArkUI_PathAnimationHandle animation, bool autoReverse)](#oh_arkui_nativemodule_pathanimation_setautoreverse) | Sets whether to automatically reverse a path animation.<br>When auto-reverse is enabled, the animation alternates between forward and reverse playback in each playback cycle. The default value is **false**. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetAutoReverse(OH_ArkUI_PathAnimationHandle animation, bool *autoReverse)](#oh_arkui_nativemodule_pathanimation_getautoreverse) | Obtains whether auto-reverse is enabled for a path animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetIterations(OH_ArkUI_PathAnimationHandle animation, int32_t iterations)](#oh_arkui_nativemodule_pathanimation_setiterations) | Sets the number of times that a path animation is played. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetIterations(OH_ArkUI_PathAnimationHandle animation, int32_t *iterations)](#oh_arkui_nativemodule_pathanimation_getiterations) | Obtains the number of times that a path animation is played. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetAutoRotation(OH_ArkUI_PathAnimationHandle animation, bool autoRotation)](#oh_arkui_nativemodule_pathanimation_setautorotation) | Sets whether the component automatically rotates along the tangent direction of the path during path animation.<br>When auto-rotation is enabled, the component rotates so that its orientation aligns with the tangent of the path at the current position. The default value is **false**. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetAutoRotation(OH_ArkUI_PathAnimationHandle animation, bool *autoRotation)](#oh_arkui_nativemodule_pathanimation_getautorotation) | Obtains whether auto-rotation is enabled for a path animation. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetTargetNode(OH_ArkUI_PathAnimationHandle animation, ArkUI_RenderNodeHandle targetNode)](#oh_arkui_nativemodule_pathanimation_settargetnode) | Sets the target render node for a path animation.<br>The target node is the render node driven by this path animation. If it is **NULL** (default value), the animation inherits the default target of the animation group set through [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](#oh_arkui_nativemodule_animationgroup_settargetnode). A non-**NULL** target must belong to the same UIContext registered by the animation group. This check is performed when the animation group is registered through [OH_ArkUI_NativeModule_AddAnimationGroup](#oh_arkui_nativemodule_addanimationgroup). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetTargetNode(OH_ArkUI_PathAnimationHandle animation, ArkUI_RenderNodeHandle *outBorrowedTargetNode)](#oh_arkui_nativemodule_pathanimation_gettargetnode) | Obtains the target render node of a path animation. |
| [OH_ArkUI_AnimationGroupHandle OH_ArkUI_NativeModule_AnimationGroup_Create()](#oh_arkui_nativemodule_animationgroup_create) | Creates an animation group. |
| [void OH_ArkUI_NativeModule_AnimationGroup_Destroy(OH_ArkUI_AnimationGroupHandle group)](#oh_arkui_nativemodule_animationgroup_destroy) | Destroys the frontend handle of an animation group.<br>This API releases only the frontend handle. The backend (runtime) object of the animation group registered through [OH_ArkUI_NativeModule_AddAnimationGroup](#oh_arkui_nativemodule_addanimationgroup) is released separately — automatically when the **finish** callback is triggered, or through [OH_ArkUI_NativeModule_RemoveAnimationGroup](#oh_arkui_nativemodule_removeanimationgroup).<br>Child animations added to the animation group are not destroyed automatically. You need to call [OH_ArkUI_NativeModule_PropertyAnimation_Destroy](#oh_arkui_nativemodule_propertyanimation_destroy), [OH_ArkUI_NativeModule_KeyframeAnimation_Destroy](#oh_arkui_nativemodule_keyframeanimation_destroy), or [OH_ArkUI_NativeModule_PathAnimation_Destroy](#oh_arkui_nativemodule_pathanimation_destroy) separately. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetDuration(OH_ArkUI_AnimationGroupHandle group, int32_t duration)](#oh_arkui_nativemodule_animationgroup_setduration) | Sets the duration of an animation group.<br>The duration of the animation group serves as the default duration for child animations that do not set their own duration through [OH_ArkUI_NativeModule_PropertyAnimation_SetDuration](#oh_arkui_nativemodule_propertyanimation_setduration), [OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration](#oh_arkui_nativemodule_keyframeanimation_setduration), or [OH_ArkUI_NativeModule_PathAnimation_SetDuration](#oh_arkui_nativemodule_pathanimation_setduration). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetDuration(OH_ArkUI_AnimationGroupHandle group, int32_t *duration)](#oh_arkui_nativemodule_animationgroup_getduration) |Obtains the duration of an animation group.<br>This API returns only the duration explicitly set on this animation group, and is not affected by the duration of child animations. If no duration is set on this animation group, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. At runtime, the duration of an animation group with no duration set defaults to 1,000 milliseconds.|
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetDelay(OH_ArkUI_AnimationGroupHandle group, int32_t delay)](#oh_arkui_nativemodule_animationgroup_setdelay) | Sets the delay for an animation group. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetDelay(OH_ArkUI_AnimationGroupHandle group, int32_t *delay)](#oh_arkui_nativemodule_animationgroup_getdelay) | Obtains the delay for an animation group.  |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetCurve(OH_ArkUI_AnimationGroupHandle group, ArkUI_CurveHandle curve)](#oh_arkui_nativemodule_animationgroup_setcurve) | Sets the animation curve for an animation group.<br>The curve of the animation group serves as the default curve for child animations that do not set their own curves through [OH_ArkUI_NativeModule_PropertyAnimation_SetCurve](#oh_arkui_nativemodule_propertyanimation_setcurve) or [OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve](#oh_arkui_nativemodule_keyframeanimation_setcurve). The **springMotion**, **responsiveSpringMotion**, and **interpolatingSpring** curves are not supported because these curves do not have a valid duration setting. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetCurve(OH_ArkUI_AnimationGroupHandle group, ArkUI_CurveHandle *outBorrowedCurve)](#oh_arkui_nativemodule_animationgroup_getcurve) | Obtains the animation curve of an animation group.<br>This API returns only the curve explicitly set on this animation group and is not affected by the curves of child animations. If no curve is set on this animation group, **outBorrowedCurve** is output as **NULL**. At runtime, the curve of an animation group without a curve set defaults to [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetTempo(OH_ArkUI_AnimationGroupHandle group, float tempo)](#oh_arkui_nativemodule_animationgroup_settempo) | Sets the playback tempo of an animation group. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetTempo(OH_ArkUI_AnimationGroupHandle group, float *tempo)](#oh_arkui_nativemodule_animationgroup_gettempo) | Obtains the playback tempo of an animation group. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetAutoReverse(OH_ArkUI_AnimationGroupHandle group, bool autoReverse)](#oh_arkui_nativemodule_animationgroup_setautoreverse) | Sets whether to automatically reverse an animation group.<br>When auto-reverse is enabled, the animation group alternates between forward and reverse playback in each playback cycle. The default value is **false**. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetAutoReverse(OH_ArkUI_AnimationGroupHandle group, bool *autoReverse)](#oh_arkui_nativemodule_animationgroup_getautoreverse) | Obtains whether the animation group is auto-reversed. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetIterations(OH_ArkUI_AnimationGroupHandle group, int32_t iterations)](#oh_arkui_nativemodule_animationgroup_setiterations) | Sets the number of times that an animation group is played. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetIterations(OH_ArkUI_AnimationGroupHandle group, int32_t *iterations)](#oh_arkui_nativemodule_animationgroup_getiterations) | Obtains the number of times that an animation group is played. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetExpectedFrameRateRange(OH_ArkUI_AnimationGroupHandle group, const ArkUI_ExpectedFrameRateRange *frameRate)](#oh_arkui_nativemodule_animationgroup_setexpectedframeraterange) | Sets the expected frame rate range for an animation group. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetExpectedFrameRateRange(OH_ArkUI_AnimationGroupHandle group, ArkUI_ExpectedFrameRateRange *frameRate)](#oh_arkui_nativemodule_animationgroup_getexpectedframeraterange) | Obtains the expected frame rate range for an animation group. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_RegisterOnFinishCallback(OH_ArkUI_AnimationGroupHandle group, void *userData, void (*callback)(void *userData))](#oh_arkui_nativemodule_animationgroup_registeronfinishcallback) | Registers the callback invoked when the animation group playback is complete.<br>An animation group has only one completion callback. Registering another callback replaces the previous callback and **userData** pair. Registering the same callback and **userData** pair again succeeds but does not create an additional registration.|
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode(OH_ArkUI_AnimationGroupHandle group, ArkUI_RenderNodeHandle targetNode)](#oh_arkui_nativemodule_animationgroup_settargetnode) | Sets the default target render node for an animation group.<br>The default target is the render node driven by child animations that do not set their own targets through [OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode](#oh_arkui_nativemodule_propertyanimation_settargetnode), [OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode](#oh_arkui_nativemodule_keyframeanimation_settargetnode), or [OH_ArkUI_NativeModule_PathAnimation_SetTargetNode](#oh_arkui_nativemodule_pathanimation_settargetnode). When the animation group is registered through [OH_ArkUI_NativeModule_AddAnimationGroup](#oh_arkui_nativemodule_addanimationgroup), each child animation must resolve to a non-**NULL** target (either its own target or the default target of the animation group); any resolved target must belong to the same UIContext on which the animation group is registered. The default value is **NULL**.|
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetTargetNode(OH_ArkUI_AnimationGroupHandle group, ArkUI_RenderNodeHandle *outBorrowedTargetNode)](#oh_arkui_nativemodule_animationgroup_gettargetnode) | Obtains the default target render node of an animation group. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_AddPropertyAnimation(OH_ArkUI_AnimationGroupHandle group, OH_ArkUI_PropertyAnimationHandle animation)](#oh_arkui_nativemodule_animationgroup_addpropertyanimation) | Adds a property animation to an animation group.<br>The target node of the animation is determined by [OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode](#oh_arkui_nativemodule_propertyanimation_settargetnode); if it is not set, the animation inherits the default target of the animation group set through [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](#oh_arkui_nativemodule_animationgroup_settargetnode). When the animation group is registered, each child animation must resolve to a non-**NULL** target. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_AddKeyframeAnimation(OH_ArkUI_AnimationGroupHandle group, OH_ArkUI_KeyframeAnimationHandle animation)](#oh_arkui_nativemodule_animationgroup_addkeyframeanimation) | Adds a keyframe animation to an animation group.<br>The target node of the animation is determined by [OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode](#oh_arkui_nativemodule_keyframeanimation_settargetnode). If it is not set, the animation inherits the default target of the animation group set through [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](#oh_arkui_nativemodule_animationgroup_settargetnode). When the animation group is registered, each child animation must resolve to a non-**NULL** target. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_AddPathAnimation(OH_ArkUI_AnimationGroupHandle group, OH_ArkUI_PathAnimationHandle animation)](#oh_arkui_nativemodule_animationgroup_addpathanimation) | Adds a path animation to an animation group.<br>The target node of the animation is determined by [OH_ArkUI_NativeModule_PathAnimation_SetTargetNode](#oh_arkui_nativemodule_pathanimation_settargetnode); if it is not set, the animation inherits the default target of the animation group set through [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](#oh_arkui_nativemodule_animationgroup_settargetnode). When the animation group is registered, each child animation must resolve to a non-**NULL** target. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AddAnimationGroup(ArkUI_ContextHandle context, OH_ArkUI_AnimationGroupHandle group, const char *key)](#oh_arkui_nativemodule_addanimationgroup) | Registers an animation group with a specified key on the UIContext and starts playback.<br>The UIContext owns the animation group through the key: after registration, the UIContext holds the backend (runtime) object of the animation group, and the caller can destroy the frontend animation group handle (and child animation handles) after registration because the backend runs independently through the (UIContext, key) pair. The key is scoped per UIContext (instance): the same key in different UIContexts does not conflict. Within a UIContext, if an animation group has already been registered with the same key, the system first removes the previous animation group (releasing its backend object) and then registers the new one. The animation group is subsequently identified and managed through the same (UIContext, key) pair.<br>Each child animation added through [OH_ArkUI_NativeModule_AnimationGroup_AddPropertyAnimation](#oh_arkui_nativemodule_animationgroup_addpropertyanimation), [OH_ArkUI_NativeModule_AnimationGroup_AddKeyframeAnimation](#oh_arkui_nativemodule_animationgroup_addkeyframeanimation), or [OH_ArkUI_NativeModule_AnimationGroup_AddPathAnimation](#oh_arkui_nativemodule_animationgroup_addpathanimation) drives its own target node; if that target is not set (or is **NULL**), it inherits the animation group default target set through [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](#oh_arkui_nativemodule_animationgroup_settargetnode). At registration, each child animation must resolve to a non-**NULL** target node (its own or the animation group default). If a child animation has no resolvable target node, [ARKUI_ERROR_CODE_SUB_ANIMATION_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. Each resolved target node must belong to the same UIContext as context; otherwise, the error code [ARKUI_ERROR_CODE_TARGET_NODE_NOT_IN_SAME_CONTEXT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.<br>The playback control and lifecycle APIs ([OH_ArkUI_NativeModule_RemoveAnimationGroup](#oh_arkui_nativemodule_removeanimationgroup), [OH_ArkUI_NativeModule_GetAnimationGroupState](#oh_arkui_nativemodule_getanimationgroupstate), [OH_ArkUI_NativeModule_HasAnimationGroup](#oh_arkui_nativemodule_hasanimationgroup), [OH_ArkUI_NativeModule_PauseAnimationGroup](#oh_arkui_nativemodule_pauseanimationgroup), [OH_ArkUI_NativeModule_ResumeAnimationGroup](#oh_arkui_nativemodule_resumeanimationgroup), [OH_ArkUI_NativeModule_FinishAnimationGroup](#oh_arkui_nativemodule_finishanimationgroup)) all use the (UIContext, key) pair as the key.<br>The **finish** callback (see [OH_ArkUI_NativeModule_AnimationGroup_RegisterOnFinishCallback](#oh_arkui_nativemodule_animationgroup_registeronfinishcallback)) is triggered only once, by the event that stops the animation - natural completion, call of [OH_ArkUI_NativeModule_FinishAnimationGroup](#oh_arkui_nativemodule_finishanimationgroup), or destruction of the target node. If [OH_ArkUI_NativeModule_AddAnimationGroup](#oh_arkui_nativemodule_addanimationgroup) returns an error, the animation creation fails and the **finish** callback is not triggered. After the callback returns, the system automatically removes the animation group from the UIContext and releases the backend (runtime) objects of the animation group and its child animations; the frontend handles (of the animation group and its child animations) must still be destroyed by the caller through [OH_ArkUI_NativeModule_AnimationGroup_Destroy](#oh_arkui_nativemodule_animationgroup_destroy), [OH_ArkUI_NativeModule_PropertyAnimation_Destroy](#oh_arkui_nativemodule_propertyanimation_destroy), [OH_ArkUI_NativeModule_KeyframeAnimation_Destroy](#oh_arkui_nativemodule_keyframeanimation_destroy), or [OH_ArkUI_NativeModule_PathAnimation_Destroy](#oh_arkui_nativemodule_pathanimation_destroy). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_RemoveAnimationGroup(ArkUI_ContextHandle context, const char *key)](#oh_arkui_nativemodule_removeanimationgroup) | Removes the animation group identified by the specified key from the UIContext.<br>Stop the animation group (if it is still running) and release the backend (runtime) objects of the animation group and its child animations. The target node being animated is restored to the state it was in when the animation started. The frontend handles (the animation group and its child animations) are not released by this call and must be destroyed by the caller through [OH_ArkUI_NativeModule_AnimationGroup_Destroy](#oh_arkui_nativemodule_animationgroup_destroy), [OH_ArkUI_NativeModule_PropertyAnimation_Destroy](#oh_arkui_nativemodule_propertyanimation_destroy), [OH_ArkUI_NativeModule_KeyframeAnimation_Destroy](#oh_arkui_nativemodule_keyframeanimation_destroy), or [OH_ArkUI_NativeModule_PathAnimation_Destroy](#oh_arkui_nativemodule_pathanimation_destroy). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_GetAnimationGroupState(ArkUI_ContextHandle context, const char *key, OH_ArkUI_AnimationGroupState *state)](#oh_arkui_nativemodule_getanimationgroupstate) | Obtains the playback state of the animation group identified by the specified key on the UIContext. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_HasAnimationGroup(ArkUI_ContextHandle context, const char *key, bool *exists)](#oh_arkui_nativemodule_hasanimationgroup) | Checks whether an animation group with the specified key exists on the UIContext. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PauseAnimationGroup(ArkUI_ContextHandle context, const char *key)](#oh_arkui_nativemodule_pauseanimationgroup) | Pauses the animation group identified by the specified key on the UIContext.<br>When this API is called, the animation group must be in the [OH_ARKUI_ANIMATION_GROUP_STATE_RUNNING](capi-native-type-visual-h.md#oh_arkui_animationgroupstate) state; otherwise, [ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. You can call [OH_ArkUI_NativeModule_GetAnimationGroupState](#oh_arkui_nativemodule_getanimationgroupstate) to query the playback state of the animation group. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ResumeAnimationGroup(ArkUI_ContextHandle context, const char *key)](#oh_arkui_nativemodule_resumeanimationgroup) | Resumes the animation group identified by the specified key on the UIContext.<br>When this API is called, the animation group must be in the [OH_ARKUI_ANIMATION_GROUP_STATE_PAUSED](capi-native-type-visual-h.md#oh_arkui_animationgroupstate) state; otherwise, [ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. You can call [OH_ArkUI_NativeModule_GetAnimationGroupState](#oh_arkui_nativemodule_getanimationgroupstate) to query the playback state of the animation group. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_FinishAnimationGroup(ArkUI_ContextHandle context, const char *key, OH_ArkUI_AnimationFinishMode mode)](#oh_arkui_nativemodule_finishanimationgroup) | Finishes the animation group identified by the specified key on the UIContext.<br>Finish the animation group in the specified finish mode: jump to the end state, jump to the start state, or keep the current value. The animation group must be in the [OH_ARKUI_ANIMATION_GROUP_STATE_RUNNING](capi-native-type-visual-h.md#oh_arkui_animationgroupstate) or [OH_ARKUI_ANIMATION_GROUP_STATE_PAUSED](capi-native-type-visual-h.md#oh_arkui_animationgroupstate) state; otherwise, [ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. You can call [OH_ArkUI_NativeModule_GetAnimationGroupState](#oh_arkui_nativemodule_getanimationgroupstate) to query the playback state of the animation group. |


## Function Description

### OH_ArkUI_AnimateOption_Create()

```c
ArkUI_AnimateOption* OH_ArkUI_AnimateOption_Create()
```

**Description**


Creates an animation configuration.

**Since**: 12

**Return value**

| Type                      | Description|
|--------------------------| -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* | Pointer to the created animation configuration.|

### OH_ArkUI_AnimateOption_Dispose()

```c
void OH_ArkUI_AnimateOption_Dispose(ArkUI_AnimateOption* option)
```

**Description**


Disposes of an animation configuration.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration.<br>If **option** is set to **NULL**, the operation is invalid.|

### OH_ArkUI_AnimateOption_GetDuration()

```c
uint32_t OH_ArkUI_AnimateOption_GetDuration(ArkUI_AnimateOption* option)
```


**Description**


Obtains the animation duration, in milliseconds.


**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration.<br>If **option** is set to **NULL**, **0** is returned.|

**Return value**

| Type| Description|
| -- | -- |
| uint32_t | Animation duration, in milliseconds. If **option** is invalid, **0** is returned.|

### OH_ArkUI_AnimateOption_GetTempo()

```c
float OH_ArkUI_AnimateOption_GetTempo(ArkUI_AnimateOption* option)
```

**Description**


Obtains the playback tempo of an animation.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration.<br>If **option** is set to **NULL**, **0.0** is returned.|

**Return value**

| Type| Description|
| -- | -- |
| float | Animation playback tempo. Value range: [0, +∞). If **option** is invalid, **0.0** is returned. |

### OH_ArkUI_AnimateOption_GetCurve()

```c
ArkUI_AnimationCurve OH_ArkUI_AnimateOption_GetCurve(ArkUI_AnimateOption* option)
```

**Description**


Obtains an animation curve.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration.<br>If **option** is set to **NULL**, **-1** is returned.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve) | Animation curve. The return values include: **ARKUI_CURVE_LINEAR** (0, linear curve), **ARKUI_CURVE_EASE** (1, ease curve), **ARKUI_CURVE_EASE_IN** (2, ease-in curve), **ARKUI_CURVE_EASE_OUT** (3, ease-out curve), **ARKUI_CURVE_EASE_IN_OUT** (4, ease-in-out curve), **ARKUI_CURVE_FAST_OUT_SLOW_IN** (5, standard curve), **ARKUI_CURVE_LINEAR_OUT_SLOW_IN** (6, deceleration curve), **ARKUI_CURVE_FAST_OUT_LINEAR_IN** (7, acceleration curve), **ARKUI_CURVE_EXTREME_DECELERATION** (8, extreme deceleration curve), **ARKUI_CURVE_SHARP** (9, sharp curve), **ARKUI_CURVE_RHYTHM** (10, rhythm curve), **ARKUI_CURVE_SMOOTH** (11, smooth curve), **ARKUI_CURVE_FRICTION** (12, friction curve). If **option** is invalid, **-1** is returned. |

### OH_ArkUI_AnimateOption_GetDelay()

```c
int32_t OH_ArkUI_AnimateOption_GetDelay(ArkUI_AnimateOption* option)
```

**Description**


Obtains the animation delay, in milliseconds.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration.<br>If **option** is set to **NULL**, **0** is returned.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Delay of animation playback, in ms. If **option** is invalid, **0** is returned. |

### OH_ArkUI_AnimateOption_GetIterations()

```c
int32_t OH_ArkUI_AnimateOption_GetIterations(ArkUI_AnimateOption* option)
```

**Description**


Obtains the number of times that an animation is played.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration.<br>If **option** is set to **NULL**, **0** is returned.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Number of times that the animation is played. If **option** is invalid, **0** is returned.|

### OH_ArkUI_AnimateOption_GetPlayMode()

```c
ArkUI_AnimationPlayMode OH_ArkUI_AnimateOption_GetPlayMode(ArkUI_AnimateOption* option)
```

**Description**


Obtains the playback mode of an animation.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration.<br>If **option** is set to **NULL**, **-1** is returned.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode) | Animation playback mode. The return values include: **ARKUI_ANIMATION_PLAY_MODE_NORMAL** (0, forward playback), **ARKUI_ANIMATION_PLAY_MODE_REVERSE** (1, reverse playback), **ARKUI_ANIMATION_PLAY_MODE_ALTERNATE** (2, alternate playback), and **ARKUI_ANIMATION_PLAY_MODE_ALTERNATE_REVERSE** (3, reverse alternate playback). If **option** is invalid, **-1** is returned. |

### OH_ArkUI_AnimateOption_GetExpectedFrameRateRange()

```c
ArkUI_ExpectedFrameRateRange* OH_ArkUI_AnimateOption_GetExpectedFrameRateRange(ArkUI_AnimateOption* option)
```

**Description**


Obtains the expected frame rate range of the animation, in fps.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration.<br>If **option** is set to **NULL**, **NULL** is returned.|

**Return value**

| Type                               | Description|
|-----------------------------------| -- |
| [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md)* | Pointer to the expected frame rate range of the animation, in fps. If **option** is invalid, **NULL** is returned.|

### OH_ArkUI_AnimateOption_SetDuration()

```c
void OH_ArkUI_AnimateOption_SetDuration(ArkUI_AnimateOption* option, int32_t value)
```

**Description**


Sets the animation duration, in milliseconds.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration.<br>If **option** is set to **NULL**, the operation is invalid.|
| int32_t value | Animation duration, in ms. The default value is 1000 ms. Value range: [0, +∞).<br>If value is less than 0, 0 is used. |

### OH_ArkUI_AnimateOption_SetTempo()

```c
void OH_ArkUI_AnimateOption_SetTempo(ArkUI_AnimateOption* option, float value)
```

**Description**


Sets the playback tempo of an animation.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration.<br>If **option** is set to **NULL**, the operation is invalid.|
| float value | Playback tempo. The default value is **1.0**. The value range is [0, +∞).<br>**NOTE**<br>If the value is less than 0, the default value **1** is used. |


### OH_ArkUI_AnimateOption_SetCurve()

```c
void OH_ArkUI_AnimateOption_SetCurve(ArkUI_AnimateOption* option, ArkUI_AnimationCurve value)
```

**Description**


Sets a custom curve for the animation.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration.<br>If **option** is set to **NULL**, the operation is invalid.|
| [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve) value | Animation curve. Default value: [ARKUI_CURVE_EASE_IN_OUT](capi-native-type-visual-h.md#arkui_animationcurve). You are advised to use **ARKUI_CURVE_EASE_IN_OUT** for a smoother animation effect.<br>If the value is abnormal, the setting does not take effect.<br>**Note:** If [OH_ArkUI_AnimateOption_SetICurve](#oh_arkui_animateoption_seticurve) is also set, **SetICurve** takes precedence and this setting does not take effect.|

### OH_ArkUI_AnimateOption_SetDelay()

```c
void OH_ArkUI_AnimateOption_SetDelay(ArkUI_AnimateOption* option, int32_t value)
```

**Description**


Sets the animation delay, in milliseconds.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration.<br>If **option** is set to **NULL**, the operation is invalid.|
| int32_t value | Animation delay, in milliseconds. Value range: (-∞, +∞). Default value: **0**, indicating no animation delay. A value greater than 0 means to begin the animation after the specified amount of time has elapsed. A value less than 0 means to begin the animation in advance. If **value** is less than **0** and the absolute value of **value** is less than the actual animation duration, the animation starts its first frame from the state at the absolute value. If the absolute value of **value** is greater than or equal to the actual animation duration, the animation starts its first frame from the end state. The actual animation duration is equal to the duration of a single animation multiplied by the number of animation playback times.|

### OH_ArkUI_AnimateOption_SetIterations()

```c
void OH_ArkUI_AnimateOption_SetIterations(ArkUI_AnimateOption* option, int32_t value)
```

**Description**


Sets the number of times that an animation is played.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration.<br>If **option** is set to **NULL**, the operation is invalid.|
| int32_t value | Number of times that the animation is played. Value range: [-1, +∞). If this parameter is set to **0**, the animation is not played. If this parameter is set to **-1**, the animation is played for an infinite number of times. Default value: **1** (played once).<br>If the value is less than -1, the operation is invalid.|

### OH_ArkUI_AnimateOption_SetPlayMode()

```c
void OH_ArkUI_AnimateOption_SetPlayMode(ArkUI_AnimateOption* option, ArkUI_AnimationPlayMode value)
```

**Description**


Sets the playback mode for an animation.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration.<br>If **option** is set to **NULL**, the operation is invalid.|
| [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode) value | Animation playback mode. Default value: [ARKUI_ANIMATION_PLAY_MODE_NORMAL](capi-native-type-visual-h.md#arkui_animationplaymode). The value options include: **ARKUI_ANIMATION_PLAY_MODE_NORMAL** indicates forward playback, **ARKUI_ANIMATION_PLAY_MODE_REVERSE** indicates reverse playback, **ARKUI_ANIMATION_PLAY_MODE_ALTERNATE** indicates playback in alternating mode, and **ARKUI_ANIMATION_PLAY_MODE_ALTERNATE_REVERSE** indicates playback in reverse alternating mode, with reverse playback on odd iterations and forward playback on even iterations.<br>If the value is abnormal, the operation is invalid. |

### OH_ArkUI_AnimateOption_SetExpectedFrameRateRange()

```c
void OH_ArkUI_AnimateOption_SetExpectedFrameRateRange(ArkUI_AnimateOption* option, ArkUI_ExpectedFrameRateRange* value)
```

**Description**


Sets the expected frame rate range of the animation.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration.<br>If **option** is set to **NULL**, the operation is invalid.|
| [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md)* value | Pointer to the expected frame rate range of the animation, in fps.<br>If **value** is set to **NULL**, the operation is invalid.|

### OH_ArkUI_AnimateOption_SetICurve()

```c
void OH_ArkUI_AnimateOption_SetICurve(ArkUI_AnimateOption* option, ArkUI_CurveHandle value)
```

**Description**


Sets the interpolation curve for the animation.

> **NOTE**
>
> This API takes precedence over [OH_ArkUI_AnimateOption_SetCurve](#oh_arkui_animateoption_setcurve).

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration.<br>If **option** is set to **NULL**, the operation is invalid. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) value | Animation curve parameters.<br>If **value** is set to **NULL**, the operation is invalid.|

### OH_ArkUI_AnimateOption_GetICurve()

```c
ArkUI_CurveHandle OH_ArkUI_AnimateOption_GetICurve(ArkUI_AnimateOption* option)
```

**Description**


Obtains the interpolation curve of the animation.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | Pointer to an animation configuration.<br>If **option** is set to **NULL**, **NULL** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Interpolation curve of the animation. **NULL** is returned if the **option** parameter is invalid. |

### OH_ArkUI_KeyframeAnimateOption_Create()

```c
ArkUI_KeyframeAnimateOption* OH_ArkUI_KeyframeAnimateOption_Create(int32_t size)
```

**Description**


Creates a keyframe animation parameter object.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| int32_t size | Number of keyframe animation states. Value range: [0, +∞). A positive integer is required to produce an animation effect.<br>**NULL** is returned if the value of **size** is less than 0. |

**Return value**

| Type                              | Description|
|----------------------------------| -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* | Pointer to the keyframe animation parameter object. If the value of **size** is less than 0 or if **option** is abnormal, **NULL** is returned.|

### OH_ArkUI_KeyframeAnimateOption_Dispose()

```c
void OH_ArkUI_KeyframeAnimateOption_Dispose(ArkUI_KeyframeAnimateOption* option)
```

**Description**


Disposes of a keyframe animation parameter object.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Pointer to the keyframe animation parameter object.<br>If **option** is set to **NULL**, the operation is invalid.|

### OH_ArkUI_KeyframeAnimateOption_SetDelay()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_SetDelay(ArkUI_KeyframeAnimateOption* option, int32_t value)
```

**Description**


Sets the overall delay of a keyframe animation, in ms. By default, playback is not delayed.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Keyframe animation parameters.<br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|
| int32_t value | Animation delay, in milliseconds. Value range: (-∞, +∞). Default value: **0**, indicating no animation delay. A value greater than 0 means to begin the animation after the specified amount of time has elapsed. A value less than 0 means to begin the animation in advance. If **value** is less than **0** and the absolute value of **value** is less than the actual animation duration, the animation starts its first frame from the state at the absolute value. If the absolute value of **value** is greater than or equal to the actual animation duration, the animation starts its first frame from the end state. The actual animation duration is equal to the duration of a single animation multiplied by the number of animation playback times.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. Possible cause: The **option** parameter is **NULL**. To solve this issue, ensure that **option** is a valid pointer to an animation parameter object. |

### OH_ArkUI_KeyframeAnimateOption_SetIterations()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_SetIterations(ArkUI_KeyframeAnimateOption* option, int32_t value)
```

**Description**


Sets the number of times that the keyframe animation is played. By default, the animation is played once. The value **-1** indicates that the animation is played for an unlimited number of times. The value **0** indicates that no animation is played.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Pointer to a keyframe animation configuration.<br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|
| int32_t value | Number of times that the animation is played. Value range: [-1, +∞). If this parameter is set to **0**, the animation is not played. If this parameter is set to **-1**, the animation is played for an infinite number of times. Default value: **1**, indicating that the animation is played once.<br>If the value is less than -1, the operation is invalid, and the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|


**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_KeyframeAnimateOption_RegisterOnFinishCallback()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_RegisterOnFinishCallback(ArkUI_KeyframeAnimateOption* option, void* userData, void (*onFinish)(void* userData))
```

**Description**


Sets the callback invoked when the keyframe animation playback is complete. This API is called after the [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md) has played for the specified number of times.

**Since**: 12


**Parameters**

| Name                                    | Description|
|-----------------------------------------| -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Pointer to a keyframe animation configuration.<br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|
| void* userData                          | Pointer to a user-defined object.<br>Abnormal value processing is not involved.|
| void (\*onFinish)(void\* userData)                                | Pointer to the callback function.<br>**userData**: input parameter of the callback, which is a custom object pointer.<br>If **onFinish** is **NULL**, the operation is invalid. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t  | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_KeyframeAnimateOption_SetExpectedFrameRate()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_SetExpectedFrameRate(ArkUI_KeyframeAnimateOption* option, ArkUI_ExpectedFrameRateRange* frameRate)
```

**Description**


Sets the expected frame rate for a keyframe animation.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Pointer to a keyframe animation configuration.<br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|
| [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md)* frameRate | Pointer to the expected frame rate for the keyframe animation.<br>If **frameRate** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_KeyframeAnimateOption_SetDuration()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_SetDuration(ArkUI_KeyframeAnimateOption* option, int32_t value, int32_t index)
```

**Description**


Sets the duration of a keyframe animation, in milliseconds.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Pointer to a keyframe animation configuration.<br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|
| int32_t value | Keyframe animation duration, in ms. The default value is 1000 ms. Value range: [0, +∞).<br>If the value is less than 0, **0** is used.|
| int32_t index | State index. The value range is [0, size-1], where **size** is the number of keyframe animation states.<br>If **index** is out of range, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_KeyframeAnimateOption_SetCurve()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_SetCurve(ArkUI_KeyframeAnimateOption* option, ArkUI_CurveHandle value, int32_t index)
```

**Description**


Sets the animation curve for a specific keyframe animation segment.

> **NOTE**
>
> Because the duration does not take effect for the [springMotion](#oh_arkui_curve_createspringmotion), [responsiveSpringMotion](#oh_arkui_curve_createresponsivespringmotion), and [interpolatingSpring](#oh_arkui_curve_createinterpolatingspring) curves, these three curves are not supported. The keyframe animation supports the [springCurve](#oh_arkui_curve_createspringcurve) and [customCurve](#oh_arkui_curve_createcustomcurve) curves.


**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Pointer to a keyframe animation configuration.<br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) value | Animation curve to set. Default value: [ARKUI_CURVE_EASE_IN_OUT](capi-native-type-visual-h.md#arkui_animationcurve).|
| int32_t index | Index of the keyframe state segment. Value range: [0, size – 1], where **size** indicates the number of keyframe animation states.<br>If the value of **index** is less than 0 or out of range, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_KeyframeAnimateOption_RegisterOnEventCallback()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_RegisterOnEventCallback(ArkUI_KeyframeAnimateOption* option, void* userData, void (*event)(void* userData), int32_t index)
```

**Description**


Sets the closure function of the state at the time of the keyframe, that is, the state to be reached at the time of the keyframe.

**Since**: 12


**Parameters**

| Name                                    | Description|
|-----------------------------------------| -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Pointer to a keyframe animation configuration.<br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|
| void* userData                          | Pointer to a user-defined object.<br>Abnormal value processing is not involved.|
| void (\*event)(void\* userData)                                   | Pointer to the closure function.<br>**userData**: input parameter of the callback function, which is a pointer to a user-defined object.<br>The operation is invalid when **event** is **NULL**. |
| int32_t index                           | Index of the keyframe state segment. Value range: [0, size – 1], where **size** indicates the number of keyframe animation states.<br>If the value of **index** is less than 0 or out of range, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t  | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_KeyframeAnimateOption_GetDelay()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_GetDelay(ArkUI_KeyframeAnimateOption* option)
```

**Description**


Obtains the overall delay of the keyframe animation, in ms.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Pointer to a keyframe animation configuration.<br>If **option** is set to **NULL**, **0** is returned.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Overall delay, in ms. The value **0** is returned when **option** is invalid. |

### OH_ArkUI_KeyframeAnimateOption_GetIterations()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_GetIterations(ArkUI_KeyframeAnimateOption* option)
```

**Description**


Obtains the number of times that a keyframe animation is played.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Pointer to a keyframe animation configuration.<br>If **option** is set to **NULL**, **0** is returned.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Number of times that the animation is played. If **option** is invalid, **0** is returned.|

### OH_ArkUI_KeyframeAnimateOption_GetExpectedFrameRate()

```c
ArkUI_ExpectedFrameRateRange* OH_ArkUI_KeyframeAnimateOption_GetExpectedFrameRate(ArkUI_KeyframeAnimateOption* option)
```

**Description**


Obtains the expected frame rate from keyframe animation parameters.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Pointer to a keyframe animation configuration.<br>If **option** is set to **NULL**, **NULL** is returned.|

**Return value**

| Type                               | Description|
|-----------------------------------| -- |
| [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md)* | Pointer to the expected frame rate obtained. If **option** is invalid, **NULL** is returned.|

### OH_ArkUI_KeyframeAnimateOption_GetDuration()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_GetDuration(ArkUI_KeyframeAnimateOption* option, int32_t index)
```

**Description**


Obtains the duration of a specific state in a keyframe animation, in milliseconds.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Pointer to a keyframe animation configuration.<br>If **option** is set to **NULL**, **0** is returned.|
| int32_t index | State index. The value range is [0, size-1], where **size** indicates the number of keyframe animation states.<br>If **index** is out of range, **0** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Duration, in milliseconds. If **option** is invalid, **0** is returned.|

### OH_ArkUI_KeyframeAnimateOption_GetCurve()

```c
ArkUI_CurveHandle OH_ArkUI_KeyframeAnimateOption_GetCurve(ArkUI_KeyframeAnimateOption* option, int32_t index)
```

**Description**


Obtains the animation curve of a specific state in a keyframe animation.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | Pointer to a keyframe animation configuration.<br>If **option** is set to **NULL**, **NULL** is returned.|
| int32_t index | State index. The value range is [0, size-1], where **size** indicates the number of keyframe animation states.<br>If **index** is out of the value range, **NULL** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Animation curve. If the parameter is abnormal, **NULL** is returned.|

### OH_ArkUI_AnimatorOption_Create()

```c
ArkUI_AnimatorOption* OH_ArkUI_AnimatorOption_Create(int32_t keyframeSize)
```

**Description**


Creates an **AnimatorOption** object.

> **NOTE**
>
> When the value of **keyframeSize** is greater than 0, the interpolation start point of the animation is 0 by default, and the interpolation end point is 1 by default. They cannot be set.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| int32_t keyframeSize | Number of keyframes to create.<br>**NULL** is returned if the value of **keyframeSize** is less than 0. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* | Pointer to the animator parameter object. **NULL** is returned if the value of **keyframeSize** is less than 0 or if **option** is invalid. |

### OH_ArkUI_AnimatorOption_Dispose()

```c
void OH_ArkUI_AnimatorOption_Dispose(ArkUI_AnimatorOption* option)
```

**Description**


Disposes of an **AnimatorOption** object.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration.<br>If **option** is set to **NULL**, the operation is invalid.|

### OH_ArkUI_AnimatorOption_SetDuration()

```c
int32_t OH_ArkUI_AnimatorOption_SetDuration(ArkUI_AnimatorOption* option, int32_t value)
```

**Description**


Sets the playback duration of the animator animation, in ms.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration.<br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|
| int32_t value | Playback duration, in ms. The default value is 0 ms. Value range: [0, +∞).<br>If the value is less than 0, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_AnimatorOption_SetDelay()

```c
int32_t OH_ArkUI_AnimatorOption_SetDelay(ArkUI_AnimatorOption* option, int32_t value)
```

**Description**


Sets the delay time of the animator animation playback, in ms.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration.<br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|
| int32_t value | Animation delay, in milliseconds. Value range: (-∞, +∞). Default value: **0**, indicating no animation delay. A value greater than 0 means to begin the animation after the specified amount of time has elapsed. A value less than 0 means to begin the animation in advance. If **value** is less than **0** and the absolute value of **value** is less than the actual animation duration, the animation starts its first frame from the state at the absolute value. If the absolute value of **value** is greater than or equal to the actual animation duration, the animation starts its first frame from the end state. The actual animation duration is equal to the duration of a single animation multiplied by the number of animation playback times.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_AnimatorOption_SetIterations()

```c
int32_t OH_ArkUI_AnimatorOption_SetIterations(ArkUI_AnimatorOption* option, int32_t value)
```

**Description**


Sets the number of times that an animator animation is played. By default, the animation is played once. The value **-1** indicates that the animation is played for an unlimited number of times. The value **0** indicates that no animation is played.

> **NOTE**
>
> If this parameter is set to a negative value other than **-1**, the value is invalid. In this case, the animation is played once.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration.<br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|
| int32_t value | Value range: [-1, +∞). If this parameter is set to **0**, the animation is not played. If this parameter is set to **-1**, the animation is played for an infinite number of times. Default value: **1** (played once).<br>If the value is less than -1, the operation is invalid.|


**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_AnimatorOption_SetFill()

```c
int32_t OH_ArkUI_AnimatorOption_SetFill(ArkUI_AnimatorOption* option, ArkUI_AnimationFillMode value)
```

**Description**


Sets the state retained by the component before the animation starts and after it ends.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration.<br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|
| [ArkUI_AnimationFillMode](capi-native-type-visual-h.md#arkui_animationfillmode) value | State of the component before the animation starts and after it ends during animation execution. Default value: [ARKUI_ANIMATION_FILL_MODE_FORWARDS](capi-native-type-visual-h.md#arkui_animationfillmode).<br>The value options include: **ARKUI_ANIMATION_FILL_MODE_NONE** (0) indicates that the component restores to the initial state both before and after the animation. **ARKUI_ANIMATION_FILL_MODE_FORWARDS** (1) indicates that the component retains the end state after the animation ends. **ARKUI_ANIMATION_FILL_MODE_BACKWARDS** (2) indicates that the component retains the start state before the animation starts. **ARKUI_ANIMATION_FILL_MODE_BOTH** (3) indicates that the component retains the corresponding state both before and after the animation.<br>If the value is less than 0, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_AnimatorOption_SetDirection()

```c
int32_t OH_ArkUI_AnimatorOption_SetDirection(ArkUI_AnimatorOption* option, ArkUI_AnimationDirection value)
```

**Description**


Sets the playback direction.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration.<br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|
| [ArkUI_AnimationDirection](capi-native-type-visual-h.md#arkui_animationdirection) value | Animation playback direction. Default value: [ARKUI_ANIMATION_DIRECTION_NORMAL](capi-native-type-visual-h.md#arkui_animationdirection).<br>The value options include: **ARKUI_ANIMATION_DIRECTION_NORMAL** (0) indicates forward playback, **ARKUI_ANIMATION_DIRECTION_REVERSE** (1) indicates reverse playback, **ARKUI_ANIMATION_DIRECTION_ALTERNATE** (2) indicates playback in alternating mode, with forward playback on odd iterations and reverse playback on even iterations, and **ARKUI_ANIMATION_DIRECTION_ALTERNATE_REVERSE** (3) indicates playback in reverse alternating mode, with reverse playback on odd iterations and forward playback on even iterations.<br>If the value is out of the valid range, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_AnimatorOption_SetCurve()

```c
int32_t OH_ArkUI_AnimatorOption_SetCurve(ArkUI_AnimatorOption* option, ArkUI_CurveHandle value)
```

**Description**


Sets the interpolation curve for the animation of an animator.

> **NOTE**
>
> The [springCurve](#oh_arkui_curve_createspringcurve), [springMotion](#oh_arkui_curve_createspringmotion), [responsiveSpringMotion](#oh_arkui_curve_createresponsivespringmotion), [interpolatingSpring](#oh_arkui_curve_createinterpolatingspring), and [customCurve](#oh_arkui_curve_createcustomcurve) animation curves are not supported.


**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration.<br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) value | Interpolation curve. Default value: [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve). You are advised to use [ARKUI_CURVE_EASE_IN_OUT](capi-native-type-visual-h.md#arkui_animationcurve) to obtain a smoother animation effect.<br>If **value** is set to **NULL**, the default curve [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) is used.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_AnimatorOption_SetBegin()

```c
int32_t OH_ArkUI_AnimatorOption_SetBegin(ArkUI_AnimatorOption* option, float value)
```

**Description**


Sets the interpolation start point of an animation.

> **NOTE**
>
> When the animator animation is a keyframe animation, this API returns the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode).

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration.<br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|
| float value | Start point of the animation interpolation. The default value is **0.0**. Value range: (-∞, +∞). |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_AnimatorOption_SetEnd()

```c
int32_t OH_ArkUI_AnimatorOption_SetEnd(ArkUI_AnimatorOption* option, float value)
```

**Description**


Sets the interpolation end point for the animation of an animator.

> **NOTE**
>
> When the animator animation is a keyframe animation, this API returns the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode).

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration.<br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|
| float value | End point of the animation interpolation. Value range: (-∞, +∞). Default value: **1**. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_AnimatorOption_SetExpectedFrameRateRange()

```c
int32_t OH_ArkUI_AnimatorOption_SetExpectedFrameRateRange(ArkUI_AnimatorOption* option, ArkUI_ExpectedFrameRateRange* value)
```

**Description**


Sets the expected frame rate range of an animation.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration.<br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|
| [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md)* value | Pointer to the expected frame rate range.<br>If the value is **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_AnimatorOption_SetKeyframe()

```c
int32_t OH_ArkUI_AnimatorOption_SetKeyframe(ArkUI_AnimatorOption* option, float time, float value, int32_t index)
```

**Description**


Sets the keyframe parameters of an animator animation.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration.<br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|
| float time | Keyframe time. Value range: [0, 1]. The time of each keyframe must increase in sequence, that is, the time value of a later keyframe must be greater than that of the previous keyframe. Default value: evenly distributed by index (for example, **0.0** for the first frame, **0.5** for the second frame, and **1.0** for the third frame).<br>If the value of **time** is less than 0 or greater than 1, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |
| float value | Interpolation target value corresponding to the keyframe, indicating the attribute value to be reached at the keyframe moment. Value range: (-∞, +∞). |
| int32_t index | Keyframe index.<br>If the value of **index** is less than 0, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_AnimatorOption_SetKeyframeCurve()

```c
int32_t OH_ArkUI_AnimatorOption_SetKeyframeCurve(ArkUI_AnimatorOption* option, ArkUI_CurveHandle value, int32_t index)
```

**Description**


Sets the keyframe curve type for the animation of an animator.

> **NOTE**
>
> The [springCurve](#oh_arkui_curve_createspringcurve), [springMotion](#oh_arkui_curve_createspringmotion), [responsiveSpringMotion](#oh_arkui_curve_createresponsivespringmotion), [interpolatingSpring](#oh_arkui_curve_createinterpolatingspring), and [customCurve](#oh_arkui_curve_createcustomcurve) animation curves are not supported.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration.<br>If **option** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.|
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) value | Interpolation curve. Default value: **NULL**, indicating linear interpolation.|
| int32_t index | Index of the keyframe. The value range is [0, keyframeSize-1], where **keyframeSize** indicates the number of keyframes.<br>If **index** is out of range, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_AnimatorOption_GetDuration()

```c
int32_t OH_ArkUI_AnimatorOption_GetDuration(ArkUI_AnimatorOption* option)
```

**Description**


Obtains the playback duration of the animator animation, in ms.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration.<br>If **option** is **NULL**, **-1** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Duration of the animation playback, in ms. If **option** is invalid, **0** is returned. |

### OH_ArkUI_AnimatorOption_GetDelay()

```c
int32_t OH_ArkUI_AnimatorOption_GetDelay(ArkUI_AnimatorOption* option)
```

**Description**


Obtains the delay for playing an animation, in ms.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration. If **option** is set to **NULL**, **0** is returned.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Delay for playing the animation, in ms. If **option** is invalid, **0** is returned. |

### OH_ArkUI_AnimatorOption_GetIterations()

```c
int32_t OH_ArkUI_AnimatorOption_GetIterations(ArkUI_AnimatorOption* option)
```

**Description**


Obtains the number of times that an animator animation is played.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration. If **option** is **NULL**, **0** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Number of times that the animation is played. If **option** is invalid, **0** is returned.|

### OH_ArkUI_AnimatorOption_GetFill()

```c
ArkUI_AnimationFillMode OH_ArkUI_AnimatorOption_GetFill(ArkUI_AnimatorOption* option)
```

**Description**


Obtains the status of the component before and after the animator animation execution.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration. If **option** is **NULL**, **-1** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_AnimationFillMode](capi-native-type-visual-h.md#arkui_animationfillmode) | State of the component before the animation starts and after it ends during animation execution. The return values include: **ARKUI_ANIMATION_FILL_MODE_NONE** (0, restores the initial state after playback is complete), **ARKUI_ANIMATION_FILL_MODE_FORWARDS** (1, retains the end state after playback is complete), **ARKUI_ANIMATION_FILL_MODE_BACKWARDS** (2, retains the start state during delayed playback), and **ARKUI_ANIMATION_FILL_MODE_BOTH** (3, applies both the **FORWARDS** and **BACKWARDS** effects). If **option** is invalid, **-1** is returned. |

### OH_ArkUI_AnimatorOption_GetDirection()

```c
ArkUI_AnimationDirection OH_ArkUI_AnimatorOption_GetDirection(ArkUI_AnimatorOption* option)
```

**Description**


Obtains the playback direction of an animator animation.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_AnimationDirection](capi-native-type-visual-h.md#arkui_animationdirection) | Animation playback direction. The return values include: **ARKUI_ANIMATION_DIRECTION_NORMAL** (0, forward playback), **ARKUI_ANIMATION_DIRECTION_REVERSE** (1, reverse playback), **ARKUI_ANIMATION_DIRECTION_ALTERNATE** (2, playback in alternating mode, with forward playback on odd iterations and reverse playback on even iterations), and **ARKUI_ANIMATION_DIRECTION_ALTERNATE_REVERSE** (3, playback in reverse alternating mode, with reverse playback on odd iterations and forward playback on even iterations). If **option** is invalid, **-1** is returned. |

### OH_ArkUI_AnimatorOption_GetCurve()

```c
ArkUI_CurveHandle OH_ArkUI_AnimatorOption_GetCurve(ArkUI_AnimatorOption* option)
```

**Description**


Obtains the interpolation curve of the animation of an animator.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Interpolation curve. If **option** is invalid, **NULL** is returned.|

### OH_ArkUI_AnimatorOption_GetBegin()

```c
float OH_ArkUI_AnimatorOption_GetBegin(ArkUI_AnimatorOption* option)
```

**Description**


Obtains the interpolation start point of an animation.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration.|

**Return value**

| Type| Description|
| -- | -- |
| float | Interpolation start point of the animation. If **option** is invalid, **0.0** is returned.|

### OH_ArkUI_AnimatorOption_GetEnd()

```c
float OH_ArkUI_AnimatorOption_GetEnd(ArkUI_AnimatorOption* option)
```

**Description**


Obtains the interpolation end point of an animation.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration.|

**Return value**

| Type| Description|
| -- | -- |
| float | Interpolation end point of the animation. If **option** is invalid, **0.0** is returned.|

### OH_ArkUI_AnimatorOption_GetExpectedFrameRateRange()

```c
ArkUI_ExpectedFrameRateRange* OH_ArkUI_AnimatorOption_GetExpectedFrameRateRange(ArkUI_AnimatorOption* option)
```

**Description**


Obtains the expected frame rate range of an animator animation.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration. If **option** is **NULL**, **NULL** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md)* | Pointer to the expected frame rate range object. Returns **NULL** if a parameter error occurs.|

### OH_ArkUI_AnimatorOption_GetKeyframeTime()

```c
float OH_ArkUI_AnimatorOption_GetKeyframeTime(ArkUI_AnimatorOption* option, int32_t index)
```

**Description**


Obtains the keyframe time of the animator animation. The value range is [0, 1] and is a normalized time ratio.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration.|
| int32_t index | Index of the keyframe. The value range is [0, keyframeSize-1], where **keyframeSize** indicates the number of keyframes.<br>**NULL** is returned if **index** is out of range. |

**Return value**

| Type| Description|
| -- | -- |
| float | Keyframe time. The value range is [0, 1], which is a normalized time ratio. |

### OH_ArkUI_AnimatorOption_GetKeyframeValue()

```c
float OH_ArkUI_AnimatorOption_GetKeyframeValue(ArkUI_AnimatorOption* option, int32_t index)
```

**Description**


Obtains the keyframe value of an animation.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration. If **option** is **NULL**, **0.0** is returned. |
| int32_t index | Index of the keyframe. The value range is [0, keyframeSize-1], where **keyframeSize** indicates the number of keyframes.<br>If **index** is out of range, **0.0** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| float | Keyframe value.|

### OH_ArkUI_AnimatorOption_GetKeyframeCurve()

```c
ArkUI_CurveHandle OH_ArkUI_AnimatorOption_GetKeyframeCurve(ArkUI_AnimatorOption* option, int32_t index)
```

**Description**


Obtains the interpolation curve for a keyframe in the animation of an animator.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration. If **option** is **NULL**, a null pointer is returned. |
| int32_t index | Index of the keyframe. The value range is [0, keyframeSize-1], where **keyframeSize** indicates the number of keyframes.<br>If **index** is out of range, a null pointer is returned. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Interpolation curve. Returns **NULL** if a parameter error occurs.|

### OH_ArkUI_AnimatorEvent_GetUserData()

```c
void* OH_ArkUI_AnimatorEvent_GetUserData(ArkUI_AnimatorEvent* event)
```

**Description**


Obtains the user-defined object in an animation event object.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorEvent](capi-arkui-nativemodule-arkui-animatorevent.md)* event | Pointer to the animation event object. If **event** is **NULL**, **NULL** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| void* | Pointer to the user-defined object.|

### OH_ArkUI_AnimatorOnFrameEvent_GetUserData()

```c
void* OH_ArkUI_AnimatorOnFrameEvent_GetUserData(ArkUI_AnimatorOnFrameEvent* event)
```

**Description**

Obtains the user-defined object in the frame event of an animation.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOnFrameEvent](capi-arkui-nativemodule-arkui-animatoronframeevent.md)* event | Pointer to the animation event object. If **event** is **NULL**, **NULL** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| void* | Pointer to the user-defined object.|

### OH_ArkUI_AnimatorOnFrameEvent_GetValue()

```c
float OH_ArkUI_AnimatorOnFrameEvent_GetValue(ArkUI_AnimatorOnFrameEvent* event)
```

**Description**


Obtains the interpolation result in the animation frame callback event object.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOnFrameEvent](capi-arkui-nativemodule-arkui-animatoronframeevent.md)* event | Pointer to the animation event object. If **event** is **NULL**, **0.0** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| float | Animation interpolation result.<br>**NOTE**<br>During the animation, the interpolation result changes between the interpolation start point ([OH_ArkUI_AnimatorOption_SetBegin](#oh_arkui_animatoroption_setbegin)) and the interpolation end point ([OH_ArkUI_AnimatorOption_SetEnd](#oh_arkui_animatoroption_setend)) based on the animation parameters. |

### OH_ArkUI_AnimatorOption_RegisterOnFrameCallback()

```c
int32_t OH_ArkUI_AnimatorOption_RegisterOnFrameCallback(ArkUI_AnimatorOption* option, void* userData, void (*callback)(ArkUI_AnimatorOnFrameEvent* event))
```

**Description**


Sets the callback invoked when the animator receives a frame.

**Since**: 12


**Parameters**

| Name                             | Description|
|----------------------------------| -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration. If **option** is **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |
| void* userData                         | Pointer to a user-defined configuration.|
| void (\*callback)(ArkUI_AnimatorOnFrameEvent\* event)                         | Pointer to the callback function.<br>- **event**: input parameter of the callback function, which is an animation event object.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t  | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_AnimatorOption_RegisterOnFinishCallback()

```c
int32_t OH_ArkUI_AnimatorOption_RegisterOnFinishCallback(ArkUI_AnimatorOption* option, void* userData, void (*callback)(ArkUI_AnimatorEvent* event))
```

**Description**


Sets the callback invoked when the animation playback is complete.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration. If **option** is **NULL**, [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |
| void* userData | Pointer to a user-defined configuration.|
| void (\*callback)(ArkUI_AnimatorEvent\* event) | Pointer to the callback function. <br>- **event**: input parameter of the callback function, which is the animation event object. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t  | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_AnimatorOption_RegisterOnCancelCallback()

```c
int32_t OH_ArkUI_AnimatorOption_RegisterOnCancelCallback(ArkUI_AnimatorOption* option, void* userData, void (*callback)(ArkUI_AnimatorEvent* event))
```

**Description**


Sets the callback invoked when the animation playback is canceled.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration. If **option** is **NULL**, [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |
| void* userData | Pointer to a user-defined configuration.|
| void (\*callback)(ArkUI_AnimatorEvent\* event) | Pointer to the callback function. <br>- **event**: input parameter of the callback function, which is the animation event object. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t  | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_AnimatorOption_RegisterOnRepeatCallback()

```c
int32_t OH_ArkUI_AnimatorOption_RegisterOnRepeatCallback(ArkUI_AnimatorOption* option, void* userData, void (*callback)(ArkUI_AnimatorEvent* event))
```

**Description**


Sets the callback invoked when the animation playback is repeated.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration. If **option** is **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |
| void* userData | Pointer to a user-defined configuration.|
| void (\*callback)(ArkUI_AnimatorEvent\* event) | Pointer to the callback function. <br>- **event**: input parameter of the callback function, which is the animation event object. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t  | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_Animator_ResetAnimatorOption()

```c
int32_t OH_ArkUI_Animator_ResetAnimatorOption(ArkUI_AnimatorHandle animatorHandle, ArkUI_AnimatorOption* option)
```

**Description**


Resets the configuration of the animator animation.

**Since**: 12


**Parameters**

| Name                                                                            | Description|
|---------------------------------------------------------------------------------| -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Pointer to the animator animation object.<br>When **animatorHandle** is **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | Pointer to an animator animation configuration.<br>If **option** is **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_Animator_Play()

```c
int32_t OH_ArkUI_Animator_Play(ArkUI_AnimatorHandle animatorHandle)
```

**Description**


Starts the animator animation. This API must be called on the main thread.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Animator animation object. If **animatorHandle** is **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_Animator_Finish()

```c
int32_t OH_ArkUI_Animator_Finish(ArkUI_AnimatorHandle animatorHandle)
```

**Description**


Finishes the animator animation. The animation jumps to the end state and then stops. The difference from [OH_ArkUI_Animator_Cancel](#oh_arkui_animator_cancel) is: **Cancel** immediately interrupts the animation and returns to the initial state, whereas **Finish** makes the animation jump directly to the end state and then stop. This API must be called on the main thread.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Animator animation object. If **animatorHandle** is **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_Animator_Pause()

```c
int32_t OH_ArkUI_Animator_Pause(ArkUI_AnimatorHandle animatorHandle)
```

**Description**


Pauses the animation of an animator.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Animator animation object. If **animatorHandle** is **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_Animator_Cancel()

```c
int32_t OH_ArkUI_Animator_Cancel(ArkUI_AnimatorHandle animatorHandle)
```

**Description**


Cancels the animation of an animator.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Animator animation object. If **animatorHandle** is **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_Animator_Reverse()

```c
int32_t OH_ArkUI_Animator_Reverse(ArkUI_AnimatorHandle animatorHandle)
```

**Description**


Plays this animation in reverse order.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | Animator animation object. If **animatorHandle** is **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_Curve_CreateCurveByType()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateCurveByType(ArkUI_AnimationCurve curve)
```

**Description**


Implements initialization for the interpolation curve, which is used to create an interpolation curve based on the input parameter.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve) curve | Curve type. **NULL** is returned if the curve value is invalid. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Pointer to the interpolation curve object, used for interpolation calculation of animation attribute values. **NULL** is returned when the curve value is abnormal. |

### OH_ArkUI_Curve_CreateStepsCurve()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateStepsCurve(int32_t count, bool end)
```

**Description**


Creates a step curve.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| int32_t count | Number of steps. The value must be a positive integer. Value range: [1, +∞).<br>If the value of **count** is abnormal, the operation is invalid.|
| bool end | Whether the step change occurs at the start or end of each interval. **true**: The step change occurs at the end of each interval. **false**: The step change occurs at the start of each interval.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Pointer to the step curve object. **NULL** is returned if the parameter is invalid. |

### OH_ArkUI_Curve_CreateCubicBezierCurve()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateCubicBezierCurve(float x1, float y1, float x2, float y2)
```

**Description**


Creates a cubic Bezier curve.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| float x1 | X-coordinate of the first point on the Bezier curve. Value range: [0, 1]. A value less than 0 is treated as **0**. A value greater than 1 is treated as **1**.|
| float y1 | Y-coordinate of the first point on the Bezier curve. Value range: (-∞, +∞). |
| float x2 | X-coordinate of the second point on the Bezier curve. Value range: [0, 1]. A value less than 0 is treated as **0**. A value greater than 1 is treated as **1**.|
| float y2 | Y-coordinate of the second point on the Bezier curve.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Pointer to the cubic Bezier curve object. |

### OH_ArkUI_Curve_CreateSpringCurve()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateSpringCurve(float velocity, float mass, float stiffness, float damping)
```

**Description**


Creates a spring curve. The curve shape is determined by the spring parameters, and the animation duration is determined by the duration parameter in the animation parameters.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| float velocity | Initial velocity. It is a parameter that reflects the impact of external factors on the spring motion, and its purpose is to ensure that the object smoothly transitions from the previous motion state to the spring motion. This velocity is a normalized velocity, whose value equals the actual velocity at the start of the animation divided by the change value of the animation attribute. |
| float mass | Mass. It is the object on which the force acts in the spring system, and it produces an inertial effect on the spring system. The greater the mass, the larger the oscillation amplitude and the slower the speed of returning to the equilibrium position. Value range: [0, +∞).<br>If the value is less than or equal to 0, **1** is used. |
| float stiffness | Stiffness. It is the degree to which an object deforms by resisting the force applied. In a spring system, the greater the stiffness, the stronger the ability to resist deformation, and the faster the speed of restoring to the equilibrium position. Value range: [0, +∞).<br>If the value is less than or equal to 0, **1** is used.|
| float damping | Damping. It is used to describe the oscillation and attenuation of the system after being disturbed. The greater the damping, the fewer the oscillation times and the smaller the oscillation amplitude of the spring motion. Value range: [0, +∞).<br>If the value is less than or equal to 0, **1** is used. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Pointer to the interpolation object of the interpolator spring curve, used to perform interpolation calculation based on the spring physical model to generate an animation curve from 0 to 1. **NULL** is returned if the parameter is invalid. |

### OH_ArkUI_Curve_CreateSpringMotion()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateSpringMotion(float response, float dampingFraction, float overlapDuration)
```

**Description**


Creates a spring animation curve. If multiple spring animations are applied to the same attribute of an object, each animation replaces their predecessor and inherits the velocity.

> **NOTE**
>
> The animation duration is determined by the curve parameters, rather than the **duration** parameter in [animation](#oh_arkui_transitioneffect_setanimation) or [animateTo](./capi-arkui-nativemodule-arkui-nativeanimateapi-1.md#animateto).

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| float response | Natural vibration period of the spring, which determines the speed at which the spring resets, in seconds. Value range: (0, +∞).<br>If the value is less than or equal to 0, **0.55** is used. |
| float dampingFraction | Damping coefficient. > 0 and < 1: underdamped. In this case, the spring overshoots the equilibrium position. **1**: critically damped. > 1: overdamped. In this case, the spring approaches equilibrium gradually. Value range: (0, +∞).<br>If the value is less than or equal to 0, **0.825** is used.|
| float overlapDuration | Overlap duration of the spring animation, in seconds. When animation inheritance occurs, if the response values of the two spring animations differ, the response parameter transitions smoothly within the **overlapDuration** period. Value range: [0, +∞).<br>If the value is less than 0, **0** is used. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Pointer to the interpolation object of the spring animation curve. The curve is constructed using responsive parameters, and velocity inheritance between animations is supported. **NULL** is returned if the parameter is invalid. |

### OH_ArkUI_Curve_CreateResponsiveSpringMotion()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateResponsiveSpringMotion(float response, float dampingFraction, float overlapDuration)
```

**Description**


Creates a responsive spring animation curve. It is a special case of **springMotion**, with the only difference in the default values. It can be used together with **springMotion**.

> **NOTE**
>
> The animation duration is determined by the curve parameters, rather than the **duration** parameter in [animation](#oh_arkui_transitioneffect_setanimation) or [animateTo](./capi-arkui-nativemodule-arkui-nativeanimateapi-1.md#animateto).

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| float response | Natural vibration period of the spring, which determines the speed at which the spring returns to its resting state, in seconds. Value range: (0, +∞).<br>If the value is less than or equal to 0, **0.15** is used. |
| float dampingFraction | Damping coefficient. > 0 and < 1: underdamped. In this case, the spring overshoots the equilibrium position. **1**: critically damped. > 1: overdamped. In this case, the spring approaches equilibrium gradually. Value range: [0, +∞).<br>If the value is less than 0, **0.86** is used.|
| float overlapDuration | Overlap duration of the spring animation, in seconds. When animation inheritance occurs, if the response values of the two spring animations differ, the response parameter transitions smoothly within the **overlapDuration** period. Value range: [0, +∞).<br>If the value is less than 0, **0.25** is used. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Pointer to the interpolation object of the responsive spring animation curve. It is a special case of **springMotion**, differing only in the default parameters. **NULL** is returned if the parameter is invalid. |

### OH_ArkUI_Curve_CreateInterpolatingSpring()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateInterpolatingSpring(float velocity, float mass, float stiffness, float damping)
```

**Description**


Creates an interpolating spring curve animated from 0 to 1. The actual animation value is calculated based on the curve.

> **NOTE**
>
> The animation duration is determined by the curve parameters, rather than the **duration** parameter in [animation](#oh_arkui_transitioneffect_setanimation) or [animateTo](./capi-arkui-nativemodule-arkui-nativeanimateapi-1.md#animateto).

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| float velocity | Initial velocity. It is applied by external factors to the spring animation, designed to help ensure the smooth transition from the previous motion state. This is a normalized velocity, and it is calculated as the actual initial velocity divided by the change in the animation attribute. Value range: (-∞, +∞). |
| float mass | Mass. It is the object on which the force acts in the spring system, which produces an inertial effect on the spring system. The greater the mass, the larger the oscillation amplitude and the slower the speed of returning to the equilibrium position. Value range: [0, +∞).<br>If the value is less than or equal to 0, **1** is used. |
| float stiffness | Stiffness. It is the degree to which an object deforms by resisting the force applied. The greater the stiffness, the stronger the ability to resist deformation, and the faster the speed of restoring to the equilibrium position. Value range: [0, +∞).<br>If the value is less than or equal to 0, **1** is used.|
| float damping | Damping. It describes how the system oscillates and decays after being disturbed. The greater the damping, the fewer the oscillation cycles and the smaller the oscillation amplitude of the spring motion. Value range: [0, +∞).<br>If the value is less than or equal to 0, **1** is used. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Pointer to the interpolation object of the curve. Returns **NULL** if a parameter error occurs.|

### OH_ArkUI_Curve_CreateCustomCurve()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateCustomCurve(void* userData, float (*interpolate)(float fraction, void* userdata))
```

**Description**


Creates a custom curve.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| void* userData | Pointer to user-defined data.|
| float (\*interpolate)(float fraction, void\* userdata) | Pointer to the user-defined interpolation callback. **fraction** indicates the input x value for interpolation when the animation starts; value range: [0, 1]. The return value is the **y** value of the curve. value range: [0, 1]. If **fraction** is **0**, the return value **0** corresponds to the animation start point; any other return value means that the animation jumps at the start point. If **fraction** is **1**, the return value **1** corresponds to the animation end point; any other return value means that the end value of the animation is not the value of the state variable, which will result in an effect of transition from that end value to the value of the state variable.|

**Return value**

| Type                   | Description|
|-----------------------| -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | Pointer to the interpolation object of the curve. Returns **NULL** if a parameter error occurs.|

### OH_ArkUI_Curve_DisposeCurve()

```c
void OH_ArkUI_Curve_DisposeCurve(ArkUI_CurveHandle curveHandle)
```

**Description**


Disposes of a custom curve.

**Since**: 12


**Parameters**

| Name                                                                | Description|
|---------------------------------------------------------------------| -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) curveHandle | Pointer to the interpolation object of the curve.<br>The operation is invalid when **curveHandle** is **NULL**. |

### OH_ArkUI_CreateOpacityTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateOpacityTransitionEffect(float opacity)
```

**Description**


Creates an opacity effect object for component transition.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| float opacity | Opacity. Value range: [0, 1]. The default value is **1**. A value less than 0 is treated as 0. A value greater than 1 is treated as 1. The value **1** means fully opaque, and **0** means fully transparent.|

**Return value**

| Type                         | Description|
|-----------------------------| -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* | Pointer to the opacity effect object for component transition.|

### OH_ArkUI_CreateTranslationTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateTranslationTransitionEffect(ArkUI_TranslationOptions* translate)
```

**Description**


Creates a translation effect object for component transition.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TranslationOptions](capi-arkui-nativemodule-arkui-translationoptions.md)* translate | Pointer to the translation parameter object for component transition.<br>If **translate** is **NULL**, **NULL** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* | Pointer to the translation effect object for component transition. Returns **NULL** if a parameter error occurs.|

### OH_ArkUI_CreateScaleTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateScaleTransitionEffect(ArkUI_ScaleOptions* scale)
```

**Description**


Creates a scaling effect object for component transitions.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ScaleOptions](capi-arkui-nativemodule-arkui-scaleoptions.md)* scale | Scale parameter object for the component transition. **NULL** is returned if **scale** is **NULL**. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* | Pointer to the scaling effect object for component transition. **NULL** is returned if a parameter error occurs.|

### OH_ArkUI_CreateRotationTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateRotationTransitionEffect(ArkUI_RotationOptions* rotate)
```

**Description**


Creates a rotation effect object for component transition.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_RotationOptions](capi-arkui-nativemodule-arkui-rotationoptions.md)* rotate | Pointer to the rotation options object for component transition. If **rotate** is **NULL**, **NULL** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* | Pointer to the rotation effect object for component transition. Returns **NULL** if a parameter error occurs.|

### OH_ArkUI_CreateMovementTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateMovementTransitionEffect(ArkUI_TransitionEdge edge)
```

**Description**


Creates a movement transition effect object for the component. The slide-in and slide-out directions of the component are controlled by specifying the edge direction (top, bottom, left, or right). This API is suitable for simple scenarios where only the sliding direction needs to be specified. The difference from **OH_ArkUI_CreateTranslationTransitionEffect** is that the latter supports precise translation parameters in the x, y, and z directions and is suitable for scenarios where a specific displacement distance needs to be specified.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TransitionEdge](capi-native-type-visual-h.md#arkui_transitionedge) edge | Movement transition type, which determines the translation direction when the component appears and disappears. If the edge value is invalid, [ARKUI_TRANSITION_EDGE_START](capi-native-type-visual-h.md#arkui_transitionedge) is used.<br>The value options include: **ARKUI_TRANSITION_EDGE_TOP** (0) indicates sliding in/out from the top, **ARKUI_TRANSITION_EDGE_BOTTOM** (1) indicates sliding in/out from the bottom, **ARKUI_TRANSITION_EDGE_START** (2) indicates sliding in/out from the left, and **ARKUI_TRANSITION_EDGE_END** (3) indicates sliding in/out from the right. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* | Pointer to the translation effect object for component transition. Returns **NULL** if a parameter error occurs.|

### OH_ArkUI_CreateAsymmetricTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateAsymmetricTransitionEffect(ArkUI_TransitionEffect* appear, ArkUI_TransitionEffect* disappear)
```

**Description**


Creates an asymmetric transition effect.

> **NOTE**
>
> If this function is not used for [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md), the transition effect takes effect for both appearance and disappearance of the component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* appear | Pointer to the transition effect when the component appears. If **appear** is **NULL**, **NULL** is returned. |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* disappear | Pointer to the transition effect when the component disappears. If **disappear** is **NULL**, **NULL** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* | Pointer to the asymmetric transition effect. Returns **NULL** if a parameter error occurs.|

### OH_ArkUI_CreateIdentityTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateIdentityTransitionEffect(void)
```

**Description**


Creates an effect object with no transition.

**Since:** 26.0.0


**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* | Pointer to the effect object with no transition. The caller needs to call [OH_ArkUI_TransitionEffect_Dispose](#oh_arkui_transitioneffect_dispose) to release the object.|

### OH_ArkUI_TransitionEffect_Dispose()

```c
void OH_ArkUI_TransitionEffect_Dispose(ArkUI_TransitionEffect* effect)
```

**Description**


Disposes of a transition effect.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* effect | Pointer to the transition effect object.<br>The operation is invalid when **effect** is **NULL**. |

### OH_ArkUI_TransitionEffect_Combine()

```c
int32_t OH_ArkUI_TransitionEffect_Combine(ArkUI_TransitionEffect* firstEffect, ArkUI_TransitionEffect* secondEffect)
```

**Description**


Sets a combination of transition effects.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* firstEffect | Pointer to the preceding transition effect in the chain, which will be combined with **secondEffect** to form a **TransitionEffect** containing multiple transition effects.<br>If **firstEffect** is **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* secondEffect | Pointer to the following transition effect to be combined, which will be chained with **firstEffect** to form a **TransitionEffect** containing multiple transition effects.<br>If **secondEffect** is **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TransitionEffect_SetAnimation()

```c
int32_t OH_ArkUI_TransitionEffect_SetAnimation(ArkUI_TransitionEffect* effect, ArkUI_AnimateOption* animation)
```

**Description**


Sets transition effect animation settings.

> **NOTE**
>
> If [OH_ArkUI_TransitionEffect_Combine](#oh_arkui_transitioneffect_combine) is used to combine transition effects, the animation parameter settings of a transition effect are applicable to the one following it.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* effect | Pointer to the transition effect object for which animation parameters are to be set.<br>If **effect** is **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* animation | Pointer to the animator animation configuration.<br>If **animation** is **NULL**, the animation parameters are set to empty. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_NativeModule_PropertyAnimation_Create()

```c
OH_ArkUI_PropertyAnimationHandle OH_ArkUI_NativeModule_PropertyAnimation_Create(OH_ArkUI_AnimationPropertyType propertyType)
```

**Description**

Creates a property animation for a specified animatable property.

The value of **propertyType** must be a valid one of [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype); otherwise, this API returns **NULL**.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype) propertyType | [Input parameter] Type of the property to animate. |

**Return value**

| Type | Description |
| -- | -- |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) | Handle to the property animation. The caller owns the returned handle and must call [OH_ArkUI_NativeModule_PropertyAnimation_Destroy](#oh_arkui_nativemodule_propertyanimation_destroy) to release it when it is no longer needed. |


### OH_ArkUI_NativeModule_PropertyAnimation_Destroy()

```c
void OH_ArkUI_NativeModule_PropertyAnimation_Destroy(OH_ArkUI_PropertyAnimationHandle animation)
```

**Description**

Destroys a property animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) animation | [Input parameter] Property animation handle returned by [OH_ArkUI_NativeModule_PropertyAnimation_Create](#oh_arkui_nativemodule_propertyanimation_create). Passing **NULL** has no effect. After this API returns for a non-**NULL** handle, the handle becomes invalid and must not be used or destroyed again. |


### OH_ArkUI_NativeModule_PropertyAnimation_SetFromValue()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetFromValue(OH_ArkUI_PropertyAnimationHandle animation, const ArkUI_NumberValue *value, int32_t size)
```

**Description**

Sets the start value of a property animation.

It is recommended to set the start value. If it is not set, the animation starts from the current property value by default. If the start value is not set and the corresponding property has never been assigned a value, the property animation cannot be generated because there is no valid start state.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) animation | [Input parameter] Property animation handle. |
| const [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) *value | [Input parameter] Pointer to the start value. The number and types of elements in **value** depend on the value of [propertyType](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_create) passed in when the property animation is created. For details, see the enumeration description of [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype). For example, if the value is [OH_ARKUI_ANIMATION_PROPERTY_OPACITY](capi-native-type-visual-h.md#oh_arkui_animationpropertytype), **value** must contain one f32 value. |
| int32_t size | [Input parameter] Number of elements in the **value** array. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PropertyAnimation_GetFromValue()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetFromValue(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_NumberValue *value, int32_t size)
```

**Description**

Obtains the start value of a property animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) animation | [Input parameter] Property animation handle. |
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) *value | [Output parameter] Pointer to the array used to receive the start values specified by [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md).<br>The number and types of elements in **value** depend on the value of [propertyType](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_create) passed in when the property animation is created. For details, see the enumeration description of [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype). For example, if the value is [OH_ARKUI_ANIMATION_PROPERTY_OPACITY](capi-native-type-visual-h.md#oh_arkui_animationpropertytype), **value** must contain one f32 value. The values are written to the memory pointed to by this pointer.<br>This pointer cannot be **NULL**. If **value** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |
| int32_t size | [Input parameter] Size of the output array. It must be equal to the number of elements required by [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype); otherwise, the error code [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the start value is not set.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the array size is inconsistent with the required size. |


### OH_ArkUI_NativeModule_PropertyAnimation_SetToValue()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetToValue(OH_ArkUI_PropertyAnimationHandle animation, const ArkUI_NumberValue *value, int32_t size)
```

**Description**

Sets the end value of a property animation.

The end value must be set; otherwise, the property animation handle is meaningless.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) animation | [Input parameter] Property animation handle. |
| const [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) *value | [Input parameter] Pointer to the end value. The number and types of elements in **value** depend on the value of [propertyType](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_create) passed in when the property animation is created. For details, see the enumeration description of [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype). For example, if the value is [OH_ARKUI_ANIMATION_PROPERTY_OPACITY](capi-native-type-visual-h.md#oh_arkui_animationpropertytype), **value** must contain one f32 value. |
| int32_t size | [Input parameter] Number of elements in the **value** array. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PropertyAnimation_GetToValue()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetToValue(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_NumberValue *value, int32_t size)
```

**Description**

Obtains the end value of a property animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) animation | [Input parameter] Property animation handle. |
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) *value | [Output parameter] Pointer to the array used to receive the end values specified by [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md).<br>The number and types of elements in **value** depend on the value of [propertyType](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_create) passed in when the property animation is created. For details, see the enumeration description of [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype). For example, if the value is [OH_ARKUI_ANIMATION_PROPERTY_OPACITY](capi-native-type-visual-h.md#oh_arkui_animationpropertytype), **value** must contain one f32 value. The values are written to the memory pointed to by this pointer.<br>This pointer cannot be **NULL**. If **value** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |
| int32_t size | [Input parameter] Size of the output array. It must be equal to the number of elements required by [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype); otherwise, the error code [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the end value is not set.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the array size is inconsistent with the required size. |


### OH_ArkUI_NativeModule_PropertyAnimation_SetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetDuration(OH_ArkUI_PropertyAnimationHandle animation, int32_t duration)
```

**Description**

Sets the duration of a property animation.

The effective animation duration is determined by the following priority: if the duration of the child animation is set through this API, that duration is used; otherwise, the duration set on the animation group through [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, the default value of 1,000 milliseconds is used.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) animation | [Input parameter] Property animation handle. |
| int32_t duration | [Input parameter] Duration, in milliseconds. The value must be greater than 0. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PropertyAnimation_GetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetDuration(OH_ArkUI_PropertyAnimationHandle animation, int32_t *duration)
```

**Description**

Obtains the duration of a property animation.

This API returns only the duration explicitly set on this animation. The value inherited from an animation group or the default value is resolved at runtime and is not stored on this object. If no duration is set on this animation, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. The duration that actually takes effect at runtime is determined by the following priority: if a duration is set through [OH_ArkUI_NativeModule_PropertyAnimation_SetDuration](#oh_arkui_nativemodule_propertyanimation_setduration), that value is used; otherwise, the animation group's duration set through [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, the default value of 1,000 milliseconds is used.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) animation | [Input parameter] Handle to the property animation. |
| int32_t *duration | [Output parameter] Pointer to the duration, in milliseconds. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the duration is not set.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PropertyAnimation_SetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetDelay(OH_ArkUI_PropertyAnimationHandle animation, int32_t delay)
```

**Description**

Sets the delay of a property animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) animation | [Input parameter] Handle to the property animation. |
| int32_t delay | [Input parameter] Delay, in milliseconds. The default value is **0**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PropertyAnimation_GetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetDelay(OH_ArkUI_PropertyAnimationHandle animation, int32_t *delay)
```

**Description**

Obtains the delay of a property animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) animation | [Input parameter] Property animation handle. |
| int32_t *delay | [Output parameter] Pointer to the delay, in milliseconds. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PropertyAnimation_SetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetCurve(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_CurveHandle curve)
```

**Description**

Sets the animation curve of a property animation.

The animation curve that actually takes effect is determined by the following priority: if a curve is set through this API, that value is used; otherwise, the curve set on the animation group through [OH_ArkUI_NativeModule_AnimationGroup_SetCurve](#oh_arkui_nativemodule_animationgroup_setcurve) is used; if neither is set, [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) is used. Spring curves (**springMotion**, **responsiveSpringMotion**, and **interpolatingSpring**) are supported. When a spring curve is set, the duration set through [OH_ArkUI_NativeModule_PropertyAnimation_SetDuration](#oh_arkui_nativemodule_propertyanimation_setduration) does not take effect, and the animation duration is determined by the spring curve.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) animation | [Input parameter] Property animation handle. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) curve | [Input parameter] Animation curve. **NULL** indicates inheriting the animation group curve set through [OH_ArkUI_NativeModule_AnimationGroup_SetCurve](#oh_arkui_nativemodule_animationgroup_setcurve). This API does not take over the ownership of the curve handle; the caller must ensure that the curve remains valid while the animation handle is in use. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PropertyAnimation_GetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetCurve(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_CurveHandle *outBorrowedCurve)
```

**Description**

Obtains the animation curve of a property animation.

This API returns only the curve explicitly set on this animation. The value inherited from an animation group or the default value is resolved at runtime and is not stored on this object. If no curve is set on this animation, **outBorrowedCurve** is output as **NULL**. The animation curve that actually takes effect at runtime is determined by the following priority: if a curve is set through [OH_ArkUI_NativeModule_PropertyAnimation_SetCurve](#oh_arkui_nativemodule_propertyanimation_setcurve), that value is used; otherwise, the animation group's curve set through [OH_ArkUI_NativeModule_AnimationGroup_SetCurve](#oh_arkui_nativemodule_animationgroup_setcurve) is used; if neither is set, [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) is used.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) animation | [Input parameter] Property animation handle. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) *outBorrowedCurve | [Output parameter] Pointer to the animation curve. The caller must not destroy this handle. **NULL** indicates that no curve is set on this animation, and the curve of the animation group will be inherited at runtime. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PropertyAnimation_SetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetTempo(OH_ArkUI_PropertyAnimationHandle animation, float tempo)
```

**Description**

Sets the playback tempo of a property animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) animation | [Input parameter] Property animation handle. |
| float tempo | [Input parameter] Animation playback tempo. Value range: (0, +∞). Default value: **1**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PropertyAnimation_GetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetTempo(OH_ArkUI_PropertyAnimationHandle animation, float *tempo)
```

**Description**

Obtains the playback tempo of a property animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) animation | [Input parameter] Property animation handle. |
| float *tempo | [Output parameter] Pointer to the animation playback tempo. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PropertyAnimation_SetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetAutoReverse(OH_ArkUI_PropertyAnimationHandle animation, bool autoReverse)
```

**Description**

Sets whether to automatically reverse a property animation.

When auto-reverse is enabled, the animation alternates between forward and reverse playback in each playback cycle. The default value is **false**.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) animation | [Input parameter] Handle to the property animation. |
| bool autoReverse | [Input parameter] Whether to enable auto-reverse. The value **true** means to enable auto-reverse, in which case the animation alternates between forward and reverse playback in each playback cycle; the value **false** means to disable auto-reverse, in which case the animation plays forward only. The default value is **false**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PropertyAnimation_GetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetAutoReverse(OH_ArkUI_PropertyAnimationHandle animation, bool *autoReverse)
```

**Description**

Obtains whether auto-reverse is enabled for a property animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) animation | [Input parameter] Property animation handle. |
| bool *autoReverse | [Output parameter] Pointer to the parameter indicating whether auto-reverse is enabled. The value is **true** if auto-reverse is enabled; **false** otherwise. The default value is **false**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PropertyAnimation_SetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetIterations(OH_ArkUI_PropertyAnimationHandle animation, int32_t iterations)
```

**Description**

Sets the number of times that a property animation is played.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) animation | [Input parameter] Handle to the property animation. |
| int32_t iterations | [Input parameter] Number of times that a property animation is played. The value must be **-1** or greater than or equal to 1. If the value is **0**, [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. The value **-1** indicates infinite playback. The default value is **1**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PropertyAnimation_GetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetIterations(OH_ArkUI_PropertyAnimationHandle animation, int32_t *iterations)
```

**Description**

Obtains the number of times that a property animation is played.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) animation | [Input parameter] Handle to the property animation. |
| int32_t *iterations | [Output parameter] Pointer to the number of times that a property animation is played. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_RenderNodeHandle targetNode)
```

**Description**

Sets the target render node of a property animation.

The target node is the render node driven by this property animation. If it is **NULL** (default value), the animation inherits the default target of the animation group set through [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](#oh_arkui_nativemodule_animationgroup_settargetnode). A non-**NULL** target must belong to the same UIContext registered by the animation group. This check is performed when the animation group is registered through [OH_ArkUI_NativeModule_AddAnimationGroup](#oh_arkui_nativemodule_addanimationgroup).

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) animation | [Input parameter] Handle to the property animation. |
| [ArkUI_RenderNodeHandle](capi-arkui-nativemodule-arkui-rendernodehandle.md) targetNode | [Input parameter] Render node to animate. **NULL** indicates inheriting the default target of the animation group. The default value is **NULL**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PropertyAnimation_GetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetTargetNode(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_RenderNodeHandle *outBorrowedTargetNode)
```

**Description**

Obtains the target render node of a property animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) animation | [Input parameter] Handle to the property animation. |
| [ArkUI_RenderNodeHandle](capi-arkui-nativemodule-arkui-rendernodehandle.md) *outBorrowedTargetNode | [Output parameter] Pointer to the target render node. The caller must not destroy this handle. **NULL** indicates inheriting the default target of the animation group. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_KeyframeAnimation_Create()

```c
OH_ArkUI_KeyframeAnimationHandle OH_ArkUI_NativeModule_KeyframeAnimation_Create(OH_ArkUI_AnimationPropertyType propertyType, int32_t size)
```

**Description**

Creates a keyframe animation for a specified animatable property.

By default, the keyframe time points of each keyframe are evenly distributed in the range [0, 1] by index (for example, when there are three keyframes, the first frame is 0.0, the second frame is 0.5, and the third frame is 1.0). Use [OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTimes](#oh_arkui_nativemodule_keyframeanimation_setkeytimes) or [OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTime](#oh_arkui_nativemodule_keyframeanimation_setkeytime) to customize the keyframe time points.

The value of **propertyType** must be a valid one of [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype), and the value of **size** must be greater than or equal to **2**; otherwise, this API returns **NULL**.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype) propertyType | [Input parameter] Type of the property to animate. |
| int32_t size | [Input parameter] Number of keyframes. The value must be greater than or equal to 2. |

**Return value**

| Type | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) | Handle to the keyframe animation. The caller owns the returned handle and must call [OH_ArkUI_NativeModule_KeyframeAnimation_Destroy](#oh_arkui_nativemodule_keyframeanimation_destroy) to release it when it is no longer used. |


### OH_ArkUI_NativeModule_KeyframeAnimation_Destroy()

```c
void OH_ArkUI_NativeModule_KeyframeAnimation_Destroy(OH_ArkUI_KeyframeAnimationHandle animation)
```

**Description**

Destroys a keyframe animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation returned by [OH_ArkUI_NativeModule_KeyframeAnimation_Create](#oh_arkui_nativemodule_keyframeanimation_create).<br>Passing **NULL** has no effect. After this API returns for a non-**NULL** handle, the handle becomes invalid and must not be used or destroyed again. |


### OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTimes()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTimes(OH_ArkUI_KeyframeAnimationHandle animation, const float *keyTimes, int32_t size)
```

**Description**

Sets the keyframe time points of keyframes.

If this API is not called, the keyframe time point of each keyframe is evenly distributed in the range [0, 1] by index by default (for example, when there are three keyframes, the first frame is 0.0, the second frame is 0.5, and the third frame is 1.0).

The elements in **keyTimes** must be non-decreasing, and **size** must be equal to the number of keyframes of the keyframe animation (that is, the **size** value specified when creating the animation through [OH_ArkUI_NativeModule_KeyframeAnimation_Create](#oh_arkui_nativemodule_keyframeanimation_create)).

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation. |
| const float *keyTimes | [Input parameter] Pointer to the array of keyframe time points, which are normalized time ratios in the range [0, 1]. |
| int32_t size | [Input parameter] Number of keyframe time points. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_KeyframeAnimation_GetKeyTime()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetKeyTime(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, float *keyTime)
```

**Description**

Obtains the keyframe time point of the keyframe at the specified index.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation. |
| int32_t index | [Input parameter] Keyframe index. |
| float *keyTime | [Output parameter] Pointer to the keyframe time point, which is a normalized time ratio in the range [0, 1]. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTime()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTime(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, float keyTime)
```

**Description**

Sets the keyframe time point of the keyframe at the specified index.

If this API is not called to set a keyframe, its keyframe time point is evenly distributed in the range [0, 1] by index by default (for example, when there are three keyframes, the first frame is 0.0, the second frame is 0.5, and the third frame is 1.0).

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation. |
| int32_t index | [Input parameter] Keyframe index. |
| float keyTime | [Input parameter] Keyframe time point, which is a normalized time ratio in the range [0, 1]. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_KeyframeAnimation_SetValue()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetValue(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, const ArkUI_NumberValue *value, int32_t size)
```

**Description**

Sets the value of the keyframe at the specified index.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation. |
| int32_t index | [Input parameter] Keyframe index. |
| const [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) *value | [Input parameter] Pointer to the [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) array.<br>The number and types of elements in **value** depend on the value of [propertyType](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_create) passed in when the keyframe animation is created. For details, see the enumeration description of [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype). For example, if the value is [OH_ARKUI_ANIMATION_PROPERTY_OPACITY](capi-native-type-visual-h.md#oh_arkui_animationpropertytype), **value** must contain one f32 value. |
| int32_t size | [Input parameter] Number of elements in the **value** array. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_KeyframeAnimation_SetValues()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetValues(OH_ArkUI_KeyframeAnimationHandle animation, const ArkUI_NumberValue *values, int32_t size)
```

**Description**

Sets the values of all keyframes at once.

The values are provided as a flattened array.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation. |
| const [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) *values | [Input parameter] Pointer to the flattened array of [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) for all keyframes. The number of elements per keyframe depends on the value of [propertyType](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_create) passed in when the keyframe animation is created. For example, [OH_ARKUI_ANIMATION_PROPERTY_OPACITY](capi-native-type-visual-h.md#oh_arkui_animationpropertytype) requires one value per keyframe, and [OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION](capi-native-type-visual-h.md#oh_arkui_animationpropertytype) requires two values per keyframe. The total number of elements must equal the number of keyframes multiplied by the number of values per keyframe. |
| int32_t size | [Input parameter] Total number of elements in the **values** array. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_KeyframeAnimation_GetValue()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetValue(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, ArkUI_NumberValue *value, int32_t size)
```

**Description**

Obtains the value of the keyframe at the specified index.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation. |
| int32_t index | [Input parameter] Keyframe index. |
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) *value | [Output parameter] Pointer to the array used to receive the [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) values.<br>The number and types of elements in **value** depend on the value of [propertyType](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_create) passed in when the keyframe animation is created. For details, see the enumeration description of [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype). For example, if the value is [OH_ARKUI_ANIMATION_PROPERTY_OPACITY](capi-native-type-visual-h.md#oh_arkui_animationpropertytype), **value** must contain one f32 value. The values are written to the memory pointed to by this pointer.<br>This pointer cannot be **NULL**. If **value** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |
| int32_t size | [Input parameter] Size of the output array. It must be equal to the number of elements required by [OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype); otherwise, the error code [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the value of the keyframe is not set.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the array size is inconsistent with the required size. |


### OH_ArkUI_NativeModule_KeyframeAnimation_SetCurves()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetCurves(OH_ArkUI_KeyframeAnimationHandle animation, const ArkUI_CurveHandle *value, int32_t size)
```

**Description**

Sets the animation curve of a keyframe.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation. |
| const [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) *value | [Input parameter] Pointer to the array of curve handles. This API does not take ownership of the curve handles; the caller must ensure that all curves remain valid while the animation handle is in use. The **springMotion**, **responsiveSpringMotion**, and **interpolatingSpring** curves are not supported because they do not have a valid duration setting. |
| int32_t size | [Input parameter] Number of curves. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, ArkUI_CurveHandle curve)
```

**Description**

Sets the animation curve for a keyframe at a specified index.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation. |
| int32_t index | [Input parameter] Keyframe index. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) curve | [Input parameter] Animation curve. **NULL** indicates inheriting the animation group curve set through [OH_ArkUI_NativeModule_AnimationGroup_SetCurve](#oh_arkui_nativemodule_animationgroup_setcurve). This API does not take ownership of the curve handle; the caller must ensure that the curve remains valid while the animation handle is in use. The **springMotion**, **responsiveSpringMotion**, and **interpolatingSpring** curves are not supported because they do not have a valid duration setting. The animation curve that actually takes effect is determined by the following priority: if a curve is set for the keyframe through this API or [OH_ArkUI_NativeModule_KeyframeAnimation_SetCurves](#oh_arkui_nativemodule_keyframeanimation_setcurves), that value is used; otherwise, the curve set on the animation group through [OH_ArkUI_NativeModule_AnimationGroup_SetCurve](#oh_arkui_nativemodule_animationgroup_setcurve) is used; if neither is set, [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) is used. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_KeyframeAnimation_GetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetCurve(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, ArkUI_CurveHandle *outBorrowedCurve)
```

**Description**

Obtains the animation curve of a keyframe at a specified index.

This API returns only the curve explicitly set for the keyframe. The value inherited from the animation group or the default value is resolved at runtime and is not stored on this object. If no curve is set for the keyframe, **outBorrowedCurve** is output as **NULL**. The animation curve that actually takes effect at runtime is determined by the following priority: if a curve is set for the keyframe through [OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve](#oh_arkui_nativemodule_keyframeanimation_setcurve) or [OH_ArkUI_NativeModule_KeyframeAnimation_SetCurves](#oh_arkui_nativemodule_keyframeanimation_setcurves), that value is used; otherwise, the animation group's curve set through [OH_ArkUI_NativeModule_AnimationGroup_SetCurve](#oh_arkui_nativemodule_animationgroup_setcurve) is used; if neither is set, [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) is used.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation. |
| int32_t index | [Input parameter] Keyframe index. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) *outBorrowedCurve | [Output parameter] Pointer to the animation curve. The caller must not destroy this handle. **NULL** indicates that no curve is set for the keyframe, and the curve of the animation group will be inherited at runtime. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration(OH_ArkUI_KeyframeAnimationHandle animation, int32_t duration)
```

**Description**

Sets the duration of a keyframe animation.

The effective animation duration is determined by the following priority: if a duration is set through this API, that value is used; otherwise, the duration set on the animation group through [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, the default value of 1,000 milliseconds is used.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation. |
| int32_t duration | [Input parameter] Duration, in milliseconds. The value must be greater than 0. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_KeyframeAnimation_GetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetDuration(OH_ArkUI_KeyframeAnimationHandle animation, int32_t *duration)
```

**Description**

Obtains the duration of a keyframe animation.

This API returns only the duration explicitly set on this animation. The value inherited from an animation group or the default value is resolved at runtime and is not stored on this object. If no duration is set on this animation, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. The animation duration that actually takes effect at runtime is determined by the following priority: if a duration is set through [OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration](#oh_arkui_nativemodule_keyframeanimation_setduration), that value is used; otherwise, the animation group's duration set through [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, the default value of 1,000 milliseconds is used.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation. |
| int32_t *duration | [Output parameter] Pointer to the duration, in milliseconds. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the duration is not set.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_KeyframeAnimation_SetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetDelay(OH_ArkUI_KeyframeAnimationHandle animation, int32_t delay)
```

**Description**

Sets the delay of a keyframe animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation. |
| int32_t delay | [Input parameter] Delay, in milliseconds. The default value is **0**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_KeyframeAnimation_GetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetDelay(OH_ArkUI_KeyframeAnimationHandle animation, int32_t *delay)
```

**Description**

Obtains the delay of a keyframe animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation. |
| int32_t *delay | [Output parameter] Pointer to the delay, in milliseconds. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_KeyframeAnimation_SetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetTempo(OH_ArkUI_KeyframeAnimationHandle animation, float tempo)
```

**Description**

Sets the playback tempo of a keyframe animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation. |
| float tempo | [Input parameter] Animation playback tempo. Value range: (0, +∞). The default value is **1**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_KeyframeAnimation_GetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetTempo(OH_ArkUI_KeyframeAnimationHandle animation, float *tempo)
```

**Description**

Obtains the playback tempo of a keyframe animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation. |
| float *tempo | [Output parameter] Pointer to the animation playback tempo. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_KeyframeAnimation_SetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetAutoReverse(OH_ArkUI_KeyframeAnimationHandle animation, bool autoReverse)
```

**Description**

Sets whether to automatically reverse a keyframe animation.

When auto-reverse is enabled, the animation alternates between forward and reverse playback in each playback cycle. The default value is **false**.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation. |
| bool autoReverse | [Input parameter] Whether to enable auto-reverse. The value **true** indicates to enable auto-reverse, and the animation alternates between forward and reverse playback in each playback cycle; the value **false** indicates to disable auto-reverse, and the animation plays forward only. The default value is **false**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_KeyframeAnimation_GetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetAutoReverse(OH_ArkUI_KeyframeAnimationHandle animation, bool *autoReverse)
```

**Description**

Obtains whether auto-reverse is enabled for a keyframe animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation. |
| bool *autoReverse | [Output parameter] Pointer to the parameter indicating whether auto-reverse is enabled. The value is **true** if auto-reverse is enabled; **false** otherwise. The default value is **false**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_KeyframeAnimation_SetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetIterations(OH_ArkUI_KeyframeAnimationHandle animation, int32_t iterations)
```

**Description**

Sets the number of times that a keyframe animation is played.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation. |
| int32_t iterations | [Input parameter] Number of times that a keyframe animation is played. The value must be **-1** or greater than or equal to 1. If the value is **0**, [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. The value **-1** indicates infinite playback. The default value is **1**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_KeyframeAnimation_GetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetIterations(OH_ArkUI_KeyframeAnimationHandle animation, int32_t *iterations)
```

**Description**

Obtains the number of times that a keyframe animation is played.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation. |
| int32_t *iterations | [Output parameter] Pointer to the number of times that a keyframe animation is played. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode(OH_ArkUI_KeyframeAnimationHandle animation, ArkUI_RenderNodeHandle targetNode)
```

**Description**

Sets the target render node of a keyframe animation.

The target node is the render node driven by this keyframe animation. If it is **NULL** (default value), the animation inherits the default target of the animation group set through [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](#oh_arkui_nativemodule_animationgroup_settargetnode). A non-**NULL** target must belong to the same UIContext registered by the animation group. This check is performed when the animation group is registered through [OH_ArkUI_NativeModule_AddAnimationGroup](#oh_arkui_nativemodule_addanimationgroup).

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle of the keyframe animation. |
| [ArkUI_RenderNodeHandle](capi-arkui-nativemodule-arkui-rendernodehandle.md) targetNode | [Input parameter] Render node to animate. **NULL** indicates inheriting the default target of the animation group. The default value is **NULL**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_KeyframeAnimation_GetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetTargetNode(OH_ArkUI_KeyframeAnimationHandle animation, ArkUI_RenderNodeHandle *outBorrowedTargetNode)
```

**Description**

Obtains the target render node of a keyframe animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Handle to the keyframe animation. |
| [ArkUI_RenderNodeHandle](capi-arkui-nativemodule-arkui-rendernodehandle.md) *outBorrowedTargetNode | [Output parameter] Pointer to the target render node; the caller must not destroy this handle. **NULL** indicates inheriting the default target of the animation group. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PathAnimation_Create()

```c
OH_ArkUI_PathAnimationHandle OH_ArkUI_NativeModule_PathAnimation_Create(const char *path)
```

**Description**

Creates a path animation to move a component along a geometric path.

The path animation applies to the [OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION](capi-native-type-visual-h.md#oh_arkui_animationpropertytype) property.

The path animation does not support setting a curve. At runtime, it always uses [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) and does not inherit the curve of the animation group.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| const char *path | [Input parameter] Pointer to the path string in SVG path syntax. The **"start"** and **"end"** keywords are not supported as position values. If **path** is **NULL**, an empty string, or contains unsupported values, **NULL** is returned. |

**Return value**

| Type | Description |
| -- | -- |
| [OH_ArkUI_PathAnimationHandle](capi-arkui-nativemodule-arkui-pathanimation8h.md) | Handle to the path animation. **NULL** is returned if the input is invalid. The caller owns the returned handle and must call [OH_ArkUI_NativeModule_PathAnimation_Destroy](#oh_arkui_nativemodule_pathanimation_destroy) to release it when it is no longer needed. |


### OH_ArkUI_NativeModule_PathAnimation_Destroy()

```c
void OH_ArkUI_NativeModule_PathAnimation_Destroy(OH_ArkUI_PathAnimationHandle animation)
```

**Description**

Destroys a path animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PathAnimationHandle](capi-arkui-nativemodule-arkui-pathanimation8h.md) animation | [Input parameter] Path animation handle returned by [OH_ArkUI_NativeModule_PathAnimation_Create](#oh_arkui_nativemodule_pathanimation_create). Passing **NULL** has no effect. After this API returns for a non-**NULL** handle, the handle becomes invalid and must not be used or destroyed again. |


### OH_ArkUI_NativeModule_PathAnimation_SetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetDuration(OH_ArkUI_PathAnimationHandle animation, int32_t duration)
```

**Description**

Sets the duration of a path animation.

The effective animation duration is determined by the following priority: if a duration is set through this API, that value is used; otherwise, the duration set on the animation group through [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, the default value of 1,000 milliseconds is used.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PathAnimationHandle](capi-arkui-nativemodule-arkui-pathanimation8h.md) animation | [Input parameter] Handle to the path animation. |
| int32_t duration | [Input parameter] Duration, in milliseconds. The value must be greater than 0. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PathAnimation_GetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetDuration(OH_ArkUI_PathAnimationHandle animation, int32_t *duration)
```

**Description**

Obtains the duration of a path animation.

This API returns only the duration explicitly set on this animation. The value inherited from an animation group or the default value is resolved at runtime and is not stored on this object. If no duration is set on this animation, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. The animation duration that actually takes effect at runtime is determined by the following priority: if a duration is set through [OH_ArkUI_NativeModule_PathAnimation_SetDuration](#oh_arkui_nativemodule_pathanimation_setduration), that value is used; otherwise, the animation group's duration set through [OH_ArkUI_NativeModule_AnimationGroup_SetDuration](#oh_arkui_nativemodule_animationgroup_setduration) is used; if neither is set, the default value of 1,000 milliseconds is used.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PathAnimationHandle](capi-arkui-nativemodule-arkui-pathanimation8h.md) animation | [Input parameter] Handle to the path animation. |
| int32_t *duration | [Output parameter] Pointer to the duration, in milliseconds. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if no duration is set.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PathAnimation_SetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetDelay(OH_ArkUI_PathAnimationHandle animation, int32_t delay)
```

**Description**

Sets the delay of a path animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PathAnimationHandle](capi-arkui-nativemodule-arkui-pathanimation8h.md) animation | [Input parameter] Handle to the path animation. |
| int32_t delay | [Input parameter] Delay, in milliseconds. The default value is **0**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PathAnimation_GetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetDelay(OH_ArkUI_PathAnimationHandle animation, int32_t *delay)
```

**Description**

Obtains the delay of a path animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PathAnimationHandle](capi-arkui-nativemodule-arkui-pathanimation8h.md) animation | [Input parameter] Handle to the path animation. |
| int32_t *delay | [Output parameter] Pointer to the delay, in milliseconds. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PathAnimation_SetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetTempo(OH_ArkUI_PathAnimationHandle animation, float tempo)
```

**Description**

Sets the playback tempo of a path animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PathAnimationHandle](capi-arkui-nativemodule-arkui-pathanimation8h.md) animation | [Input parameter] Handle to the path animation. |
| float tempo | [Input parameter] Animation playback tempo. Value range: (0, +∞). Default value: **1**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PathAnimation_GetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetTempo(OH_ArkUI_PathAnimationHandle animation, float *tempo)
```

**Description**

Obtains the playback tempo of a path animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PathAnimationHandle](capi-arkui-nativemodule-arkui-pathanimation8h.md) animation | [Input parameter] Handle to the path animation. |
| float *tempo | [Output parameter] Pointer to the playback tempo of the animation. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PathAnimation_SetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetAutoReverse(OH_ArkUI_PathAnimationHandle animation, bool autoReverse)
```

**Description**

Sets whether to automatically reverse a path animation.

When auto-reverse is enabled, the animation alternates between forward and reverse playback in each playback cycle. The default value is **false**.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PathAnimationHandle](capi-arkui-nativemodule-arkui-pathanimation8h.md) animation | [Input parameter] Handle to the path animation. |
| bool autoReverse | [Input parameter] Whether to enable auto-reverse. The value **true** means to enable auto-reverse, in which case the animation alternates between forward and reverse playback in each playback cycle; the value **false** means to disable auto-reverse, in which case the animation plays forward only. The default value is **false**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PathAnimation_GetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetAutoReverse(OH_ArkUI_PathAnimationHandle animation, bool *autoReverse)
```

**Description**

Obtains whether auto-reverse is enabled for a path animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PathAnimationHandle](capi-arkui-nativemodule-arkui-pathanimation8h.md) animation | [Input parameter] Handle to the path animation. |
| bool *autoReverse | [Output parameter] Pointer to the parameter indicating whether auto-reverse is enabled for a path animation. The value is **true** if auto-reverse is enabled; **false** otherwise. The default value is **false**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PathAnimation_SetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetIterations(OH_ArkUI_PathAnimationHandle animation, int32_t iterations)
```

**Description**

Sets the number of times that a path animation is played.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PathAnimationHandle](capi-arkui-nativemodule-arkui-pathanimation8h.md) animation | [Input parameter] Handle to the path animation. |
| int32_t iterations | [Input parameter] Number of times that the path animation is played. The value must be **-1** or greater than or equal to 1. If the value is **0**, [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. The value **-1** indicates infinite playback. The default value is **1**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PathAnimation_GetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetIterations(OH_ArkUI_PathAnimationHandle animation, int32_t *iterations)
```

**Description**

Obtains the number of times that a path animation is played.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PathAnimationHandle](capi-arkui-nativemodule-arkui-pathanimation8h.md) animation | [Input parameter] Handle to the path animation. |
| int32_t *iterations | [Output parameter] Pointer to the number of times that a path animation is played. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PathAnimation_SetAutoRotation()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetAutoRotation(OH_ArkUI_PathAnimationHandle animation, bool autoRotation)
```

**Description**

Sets whether the component automatically rotates along the tangent direction of the path during path animation.

When auto-rotation is enabled, the component rotates so that its orientation aligns with the tangent of the path at the current position. The default value is **false**.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PathAnimationHandle](capi-arkui-nativemodule-arkui-pathanimation8h.md) animation | [Input parameter] Handle to the path animation. |
| bool autoRotation | [Input parameter] Whether to enable auto-rotation. The value **true** means to enable auto rotation, in which case the component rotates so that its orientation aligns with the tangent of the path at the current position; the value **false** means to disable auto rotation, in which case the component does not rotate with the path tangent. The default value is **false**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PathAnimation_GetAutoRotation()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetAutoRotation(OH_ArkUI_PathAnimationHandle animation, bool *autoRotation)
```

**Description**

Obtains whether auto-rotation is enabled for a path animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PathAnimationHandle](capi-arkui-nativemodule-arkui-pathanimation8h.md) animation | [Input parameter] Handle to the path animation. |
| bool *autoRotation | [Output parameter] Pointer to the parameter indicating whether auto-rotation is enabled. The value is **true** if auto-rotation is enabled and **false** otherwise. The default value is **false**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PathAnimation_SetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetTargetNode(OH_ArkUI_PathAnimationHandle animation, ArkUI_RenderNodeHandle targetNode)
```

**Description**

Sets the target render node for a path animation.

The target node is the render node driven by this path animation. If it is **NULL** (default value), the animation inherits the default target of the animation group set through [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](#oh_arkui_nativemodule_animationgroup_settargetnode). A non-**NULL** target must belong to the same UIContext registered by the animation group. This check is performed when the animation group is registered through [OH_ArkUI_NativeModule_AddAnimationGroup](#oh_arkui_nativemodule_addanimationgroup).

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PathAnimationHandle](capi-arkui-nativemodule-arkui-pathanimation8h.md) animation | [Input parameter] Handle to the path animation. |
| [ArkUI_RenderNodeHandle](capi-arkui-nativemodule-arkui-rendernodehandle.md) targetNode | [Input parameter] Render node to animate. **NULL** indicates inheriting the default target of the animation group. The default value is **NULL**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_PathAnimation_GetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetTargetNode(OH_ArkUI_PathAnimationHandle animation, ArkUI_RenderNodeHandle *outBorrowedTargetNode)
```

**Description**

Obtains the target render node of a path animation.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_PathAnimationHandle](capi-arkui-nativemodule-arkui-pathanimation8h.md) animation | [Input parameter] Handle to the path animation. |
| [ArkUI_RenderNodeHandle](capi-arkui-nativemodule-arkui-rendernodehandle.md) *outBorrowedTargetNode | [Output parameter] Pointer to the target render node; the caller must not destroy this handle. **NULL** indicates that the default target of the animation group is inherited. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_AnimationGroup_Create()

```c
OH_ArkUI_AnimationGroupHandle OH_ArkUI_NativeModule_AnimationGroup_Create(void)
```

**Description**

Creates an animation group.

**Since:** 26.0.1


**Return value**

| Type | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) | Handle to the animation group. The caller owns the returned handle and must call [OH_ArkUI_NativeModule_AnimationGroup_Destroy](#oh_arkui_nativemodule_animationgroup_destroy) to release it when it is no longer needed. |


### OH_ArkUI_NativeModule_AnimationGroup_Destroy()

```c
void OH_ArkUI_NativeModule_AnimationGroup_Destroy(OH_ArkUI_AnimationGroupHandle group)
```

**Description**

Destroys the frontend handle of an animation group.

This API releases only the frontend handle. The backend (runtime) object of the animation group registered through [OH_ArkUI_NativeModule_AddAnimationGroup](#oh_arkui_nativemodule_addanimationgroup) is released separately — automatically when the **finish** callback is triggered, or through [OH_ArkUI_NativeModule_RemoveAnimationGroup](#oh_arkui_nativemodule_removeanimationgroup).

Child animations added to the animation group are not destroyed automatically. You need to call [OH_ArkUI_NativeModule_PropertyAnimation_Destroy](#oh_arkui_nativemodule_propertyanimation_destroy), [OH_ArkUI_NativeModule_KeyframeAnimation_Destroy](#oh_arkui_nativemodule_keyframeanimation_destroy), or [OH_ArkUI_NativeModule_PathAnimation_Destroy](#oh_arkui_nativemodule_pathanimation_destroy) separately.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group returned by [OH_ArkUI_NativeModule_AnimationGroup_Create](#oh_arkui_nativemodule_animationgroup_create).<br>Passing **NULL** has no effect. After this API returns for a non-**NULL** handle, the handle becomes invalid and must not be used or destroyed again. |


### OH_ArkUI_NativeModule_AnimationGroup_SetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetDuration(OH_ArkUI_AnimationGroupHandle group, int32_t duration)
```

**Description**

Sets the duration of an animation group.

The duration of the animation group serves as the default duration for child animations that do not set their own duration through [OH_ArkUI_NativeModule_PropertyAnimation_SetDuration](#oh_arkui_nativemodule_propertyanimation_setduration), [OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration](#oh_arkui_nativemodule_keyframeanimation_setduration), or [OH_ArkUI_NativeModule_PathAnimation_SetDuration](#oh_arkui_nativemodule_pathanimation_setduration).

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| int32_t duration | [Input parameter] Duration, in milliseconds. The value must be greater than 0. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_AnimationGroup_GetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetDuration(OH_ArkUI_AnimationGroupHandle group, int32_t *duration)
```

**Description**

Obtains the duration of an animation group.

This API returns only the duration explicitly set on this animation group, and is not affected by the duration of child animations. If no duration is set on this animation group, [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. At runtime, the duration of an animation group with no duration set defaults to 1,000 milliseconds.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| int32_t *duration | [Output parameter] Pointer to the duration, in milliseconds. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if no duration is set.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_AnimationGroup_SetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetDelay(OH_ArkUI_AnimationGroupHandle group, int32_t delay)
```

**Description**

Sets the delay of an animation group.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| int32_t delay | [Input parameter] Delay, in milliseconds. The default value is **0**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_AnimationGroup_GetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetDelay(OH_ArkUI_AnimationGroupHandle group, int32_t *delay)
```

**Description**

Obtains the delay of an animation group.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| int32_t *delay | [Output parameter] Pointer to the delay, in milliseconds. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_AnimationGroup_SetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetCurve(OH_ArkUI_AnimationGroupHandle group, ArkUI_CurveHandle curve)
```

**Description**

Sets the animation curve for an animation group.

The curve of the animation group serves as the default curve for child animations that do not set their own curves through [OH_ArkUI_NativeModule_PropertyAnimation_SetCurve](#oh_arkui_nativemodule_propertyanimation_setcurve) or [OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve](#oh_arkui_nativemodule_keyframeanimation_setcurve). The **springMotion**, **responsiveSpringMotion**, and **interpolatingSpring** curves are not supported because these curves do not have a valid duration setting.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) curve | [Input parameter] Animation curve. **NULL** indicates that the animation group uses the default value [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) at runtime. This API does not take over the ownership of the curve handle; the caller must ensure that the curve remains valid while the animation handle is in use. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_AnimationGroup_GetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetCurve(OH_ArkUI_AnimationGroupHandle group, ArkUI_CurveHandle *outBorrowedCurve)
```

**Description**

Obtains the animation curve of an animation group.

This API returns only the curve explicitly set on this animation group and is not affected by the curves of child animations. If no curve is set on this animation group, **outBorrowedCurve** is output as **NULL**. At runtime, the curve of an animation group without a curve set defaults to [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve).

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) *outBorrowedCurve | [Output parameter] Pointer to the animation curve. The caller must not destroy this handle. **NULL** indicates that no curve is set on this animation group, and [ARKUI_CURVE_LINEAR](capi-native-type-visual-h.md#arkui_animationcurve) is used by default at runtime. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_AnimationGroup_SetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetTempo(OH_ArkUI_AnimationGroupHandle group, float tempo)
```

**Description**

Sets the playback tempo of an animation group.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| float tempo | [Input parameter] Playback tempo of the animation. Value range: (0, +∞). The default value is **1**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_AnimationGroup_GetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetTempo(OH_ArkUI_AnimationGroupHandle group, float *tempo)
```

**Description**

Obtains the playback tempo of an animation group.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| float *tempo | [Output parameter] Pointer to the playback tempo of the animation. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_AnimationGroup_SetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetAutoReverse(OH_ArkUI_AnimationGroupHandle group, bool autoReverse)
```

**Description**

Sets whether to automatically reverse an animation group.

When auto-reverse is enabled, the animation group alternates between forward and reverse playback in each playback cycle. The default value is **false**.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| bool autoReverse | [Input parameter] Whether to enable auto-reverse. The value **true** indicates to enable auto-reverse, in which case the animation alternates between forward and reverse playback in each playback cycle; the value **false** indicates to disable auto-reverse, in which case the animation plays forward only. The default value is **false**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_AnimationGroup_GetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetAutoReverse(OH_ArkUI_AnimationGroupHandle group, bool *autoReverse)
```

**Description**

Obtains whether auto-reverse is enabled for an animation group.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| bool *autoReverse | [Output parameter] Pointer to the parameter indicating whether auto-reverse is enabled for an animation group. The value is **true** if auto-reverse is enabled and **false** otherwise. The default value is **false**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_AnimationGroup_SetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetIterations(OH_ArkUI_AnimationGroupHandle group, int32_t iterations)
```

**Description**

Sets the number of times that an animation group is played.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| int32_t iterations | [Input parameter] Number of times that the animation group is played. The value must be **-1** or greater than or equal to 1. If the value is **0**, [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. The value **-1** indicates infinite playback. The default value is **1**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_AnimationGroup_GetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetIterations(OH_ArkUI_AnimationGroupHandle group, int32_t *iterations)
```

**Description**

Obtains the number of times that an animation group is played.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| int32_t *iterations | [Output parameter] Pointer to the number of times that an animation group is played. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_AnimationGroup_SetExpectedFrameRateRange()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetExpectedFrameRateRange(OH_ArkUI_AnimationGroupHandle group, const ArkUI_ExpectedFrameRateRange *frameRate)
```

**Description**

Sets the expected frame rate range of an animation group.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| const [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md) *frameRate | [Input parameter] Pointer to the expected frame rate range. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_AnimationGroup_GetExpectedFrameRateRange()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetExpectedFrameRateRange(OH_ArkUI_AnimationGroupHandle group, ArkUI_ExpectedFrameRateRange *frameRate)
```

**Description**

Obtains the expected frame rate range of an animation group.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md) *frameRate | [Output parameter] Pointer to the expected frame rate range.<br>The value of the [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md) object is written to the memory pointed to by this pointer.<br>This pointer cannot be **NULL**. If **frameRate** is set to **NULL**, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_AnimationGroup_RegisterOnFinishCallback()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_RegisterOnFinishCallback(OH_ArkUI_AnimationGroupHandle group, void *userData, void (*callback)(void *userData))
```

**Description**

Registers the callback invoked when the animation group playback is complete.

An animation group has only one completion callback. Registering another callback replaces the previous callback and **userData** pair. Registering the same callback and **userData** pair again succeeds but does not create an additional registration.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| void *userData | [Input parameter] Pointer to the custom data owned by the caller, passed to the callback as is. It can be **NULL** and must remain valid until the callback returns. This API does not release the data. |
| void (*callback)(void *userData) | [Input parameter] Pointer to the completion callback. It cannot be **NULL** and is invoked once serially on the UI main thread. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode(OH_ArkUI_AnimationGroupHandle group, ArkUI_RenderNodeHandle targetNode)
```

**Description**

Sets the default target render node for an animation group.

The default target is the render node driven by child animations that do not set their own targets through [OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode](#oh_arkui_nativemodule_propertyanimation_settargetnode), [OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode](#oh_arkui_nativemodule_keyframeanimation_settargetnode), or [OH_ArkUI_NativeModule_PathAnimation_SetTargetNode](#oh_arkui_nativemodule_pathanimation_settargetnode). When the animation group is registered through [OH_ArkUI_NativeModule_AddAnimationGroup](#oh_arkui_nativemodule_addanimationgroup), each child animation must resolve to a non-**NULL** target (either its own target or the default target of the animation group); any resolved target must belong to the same UIContext on which the animation group is registered. The default value is **NULL**.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| [ArkUI_RenderNodeHandle](capi-arkui-nativemodule-arkui-rendernodehandle.md) targetNode | [Input parameter] Default render node to animate. **NULL** indicates that there is no animation-group-level default value. The default value is **NULL**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_AnimationGroup_GetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetTargetNode(OH_ArkUI_AnimationGroupHandle group, ArkUI_RenderNodeHandle *outBorrowedTargetNode)
```

**Description**

Obtains the default target render node of an animation group.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| [ArkUI_RenderNodeHandle](capi-arkui-nativemodule-arkui-rendernodehandle.md) *outBorrowedTargetNode | [Output parameter] Pointer to the default target node. The caller must not destroy this handle. **NULL** indicates that there is no animation-group-level default value. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_NativeModule_AnimationGroup_AddPropertyAnimation()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_AddPropertyAnimation(OH_ArkUI_AnimationGroupHandle group, OH_ArkUI_PropertyAnimationHandle animation)
```

**Description**

Adds a property animation to an animation group.

The target node of the animation is determined by [OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode](#oh_arkui_nativemodule_propertyanimation_settargetnode); if it is not set, the animation inherits the default target of the animation group set through [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](#oh_arkui_nativemodule_animationgroup_settargetnode). When the animation group is registered, each child animation must resolve to a non-**NULL** target.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| [OH_ArkUI_PropertyAnimationHandle](capi-arkui-nativemodule-arkui-propertyanimation8h.md) animation | [Input parameter] Property animation to add. This API does not take ownership of the animation handle; the caller must ensure that the animation remains valid while the animation group handle is in use. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_SUB_ANIMATION_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the **OH_ArkUI_PropertyAnimationHandle** parameter is invalid. |


### OH_ArkUI_NativeModule_AnimationGroup_AddKeyframeAnimation()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_AddKeyframeAnimation(OH_ArkUI_AnimationGroupHandle group, OH_ArkUI_KeyframeAnimationHandle animation)
```

**Description**

Adds a keyframe animation to an animation group.

The target node of the animation is determined by [OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode](#oh_arkui_nativemodule_keyframeanimation_settargetnode). If it is not set, the animation inherits the default target of the animation group set through [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](#oh_arkui_nativemodule_animationgroup_settargetnode). When the animation group is registered, each child animation must resolve to a non-**NULL** target.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| [OH_ArkUI_KeyframeAnimationHandle](capi-arkui-nativemodule-arkui-keyframeanimation8h.md) animation | [Input parameter] Keyframe animation to add. This API does not take ownership of the animation handle; the caller must ensure that the animation remains valid while the animation group handle is in use. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_SUB_ANIMATION_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the **OH_ArkUI_KeyframeAnimationHandle** parameter is invalid. |


### OH_ArkUI_NativeModule_AnimationGroup_AddPathAnimation()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_AddPathAnimation(OH_ArkUI_AnimationGroupHandle group, OH_ArkUI_PathAnimationHandle animation)
```

**Description**

Adds a path animation to an animation group.

The target node of the animation is determined by [OH_ArkUI_NativeModule_PathAnimation_SetTargetNode](#oh_arkui_nativemodule_pathanimation_settargetnode); if it is not set, the animation inherits the default target of the animation group set through [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](#oh_arkui_nativemodule_animationgroup_settargetnode). When the animation group is registered, each child animation must resolve to a non-**NULL** target.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| [OH_ArkUI_PathAnimationHandle](capi-arkui-nativemodule-arkui-pathanimation8h.md) animation | [Input parameter] Path animation to add. This API does not take ownership of the animation handle; the caller must ensure that the animation remains valid while the animation group handle is in use. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_SUB_ANIMATION_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the **OH_ArkUI_PathAnimationHandle** parameter is invalid. |


### OH_ArkUI_NativeModule_AddAnimationGroup()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AddAnimationGroup(ArkUI_ContextHandle context, OH_ArkUI_AnimationGroupHandle group, const char *key)
```

**Description**

Registers an animation group with a specified key on the UIContext and starts playback.

The UIContext owns the animation group through the key: after registration, the UIContext holds the backend (runtime) object of the animation group, and the caller can destroy the frontend animation group handle (and child animation handles) after registration because the backend runs independently through the (UIContext, key) pair. The key is scoped per UIContext (instance): the same key in different UIContexts does not conflict. Within a UIContext, if an animation group has already been registered with the same key, the system first removes the previous animation group (releasing its backend object) and then registers the new one. The animation group is subsequently identified and managed through the same (UIContext, key) pair.

Each child animation added through [OH_ArkUI_NativeModule_AnimationGroup_AddPropertyAnimation](#oh_arkui_nativemodule_animationgroup_addpropertyanimation), [OH_ArkUI_NativeModule_AnimationGroup_AddKeyframeAnimation](#oh_arkui_nativemodule_animationgroup_addkeyframeanimation), or [OH_ArkUI_NativeModule_AnimationGroup_AddPathAnimation](#oh_arkui_nativemodule_animationgroup_addpathanimation) drives its own target node; if that target is not set (or is **NULL**), it inherits the animation group default target set through [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](#oh_arkui_nativemodule_animationgroup_settargetnode). At registration, each child animation must resolve to a non-**NULL** target node (its own or the animation group default). If a child animation has no resolvable target node, [ARKUI_ERROR_CODE_SUB_ANIMATION_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. Each resolved target node must belong to the same UIContext as context; otherwise, the error code [ARKUI_ERROR_CODE_TARGET_NODE_NOT_IN_SAME_CONTEXT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned.

The playback control and lifecycle APIs ([OH_ArkUI_NativeModule_RemoveAnimationGroup](#oh_arkui_nativemodule_removeanimationgroup), [OH_ArkUI_NativeModule_GetAnimationGroupState](#oh_arkui_nativemodule_getanimationgroupstate), [OH_ArkUI_NativeModule_HasAnimationGroup](#oh_arkui_nativemodule_hasanimationgroup), [OH_ArkUI_NativeModule_PauseAnimationGroup](#oh_arkui_nativemodule_pauseanimationgroup), [OH_ArkUI_NativeModule_ResumeAnimationGroup](#oh_arkui_nativemodule_resumeanimationgroup), [OH_ArkUI_NativeModule_FinishAnimationGroup](#oh_arkui_nativemodule_finishanimationgroup)) all use the (UIContext, key) pair as the key.

The **finish** callback (see [OH_ArkUI_NativeModule_AnimationGroup_RegisterOnFinishCallback](#oh_arkui_nativemodule_animationgroup_registeronfinishcallback)) is triggered only once, by the event that stops the animation - natural completion, call of [OH_ArkUI_NativeModule_FinishAnimationGroup](#oh_arkui_nativemodule_finishanimationgroup), or destruction of the target node. If [OH_ArkUI_NativeModule_AddAnimationGroup](#oh_arkui_nativemodule_addanimationgroup) returns an error, the animation creation fails and the **finish** callback is not triggered. After the callback returns, the system automatically removes the animation group from the UIContext and releases the backend (runtime) objects of the animation group and its child animations; the frontend handles (of the animation group and its child animations) must still be destroyed by the caller through [OH_ArkUI_NativeModule_AnimationGroup_Destroy](#oh_arkui_nativemodule_animationgroup_destroy), [OH_ArkUI_NativeModule_PropertyAnimation_Destroy](#oh_arkui_nativemodule_propertyanimation_destroy), [OH_ArkUI_NativeModule_KeyframeAnimation_Destroy](#oh_arkui_nativemodule_keyframeanimation_destroy), or [OH_ArkUI_NativeModule_PathAnimation_Destroy](#oh_arkui_nativemodule_pathanimation_destroy).

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | [Input parameter] [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) (UIContext) in which the animation group is registered and played. |
| [OH_ArkUI_AnimationGroupHandle](capi-arkui-nativemodule-arkui-animationgroup8h.md) group | [Input parameter] Handle to the animation group. |
| const char *key | [Input parameter] Pointer to the key used to identify the animation group on the UIContext. The key is a user-defined string and must be unique within the same UIContext. If an animation group has already been registered with the same key, the system first removes the previous animation group and then registers the new one. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_TARGET_NODE_NOT_IN_SAME_CONTEXT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the resolved target node does not belong to the same UIContext as context.<br>         Returns [ARKUI_ERROR_CODE_SUB_ANIMATION_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the child animation has no resolvable target node or the child animation parameter is invalid.<br>         Returns [ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a re-entrant call is detected on the same thread. |


### OH_ArkUI_NativeModule_RemoveAnimationGroup()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_RemoveAnimationGroup(ArkUI_ContextHandle context, const char *key)
```

**Description**

Removes the animation group identified by the specified key from the UIContext.

Stop the animation group (if it is still running) and release the backend (runtime) objects of the animation group and its child animations. The target node being animated is restored to the state it was in when the animation started. The frontend handles (the animation group and its child animations) are not released by this call and must be destroyed by the caller through [OH_ArkUI_NativeModule_AnimationGroup_Destroy](#oh_arkui_nativemodule_animationgroup_destroy), [OH_ArkUI_NativeModule_PropertyAnimation_Destroy](#oh_arkui_nativemodule_propertyanimation_destroy), [OH_ArkUI_NativeModule_KeyframeAnimation_Destroy](#oh_arkui_nativemodule_keyframeanimation_destroy), or [OH_ArkUI_NativeModule_PathAnimation_Destroy](#oh_arkui_nativemodule_pathanimation_destroy).

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | [Input parameter] UIContext on which the animation group is registered. |
| const char *key | [Input parameter] Pointer to the key of the animation group to remove. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_ANIMATION_GROUP_NOT_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the animation group identified by the key is not found on the UIContext.<br>         Returns [ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a re-entrant call is detected on the same thread. |


### OH_ArkUI_NativeModule_GetAnimationGroupState()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_GetAnimationGroupState(ArkUI_ContextHandle context, const char *key, OH_ArkUI_AnimationGroupState *state)
```

**Description**

Obtains the playback state of the animation group identified by the specified key on the UIContext.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | [Input parameter] UIContext. |
| const char *key | [Input parameter] Pointer to the key of the animation group. |
| [OH_ArkUI_AnimationGroupState](capi-native-type-visual-h.md#oh_arkui_animationgroupstate) *state | [Output parameter] Pointer to the state. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_ANIMATION_GROUP_NOT_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the animation group identified by the key is not found on the UIContext.<br>         Returns [ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a re-entrant call is detected on the same thread. |


### OH_ArkUI_NativeModule_HasAnimationGroup()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_HasAnimationGroup(ArkUI_ContextHandle context, const char *key, bool *exists)
```

**Description**

Checks whether an animation group with the specified key exists on the UIContext.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | [Input parameter] UIContext. |
| const char *key | [Input parameter] Pointer to the key of the animation group. |
| bool *exists | [Input parameter] Pointer to the parameter indicating whether an animation group with the specified key exists on the UIContext. The value is **true** if the animation group exists and **false** otherwise. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a re-entrant call is detected on the same thread. |


### OH_ArkUI_NativeModule_PauseAnimationGroup()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PauseAnimationGroup(ArkUI_ContextHandle context, const char *key)
```

**Description**

Pauses the animation group identified by the specified key on the UIContext.

When this API is called, the animation group must be in the [OH_ARKUI_ANIMATION_GROUP_STATE_RUNNING](capi-native-type-visual-h.md#oh_arkui_animationgroupstate) state; otherwise, [ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. You can call [OH_ArkUI_NativeModule_GetAnimationGroupState](#oh_arkui_nativemodule_getanimationgroupstate) to query the playback state of the animation group.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | [Input parameter] UIContext. |
| const char *key | [Input parameter] Pointer to the key of the animation group. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_ANIMATION_GROUP_NOT_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the animation group identified by the key is not found on the UIContext.<br>         Returns [ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the animation group is not in the [OH_ARKUI_ANIMATION_GROUP_STATE_RUNNING](capi-native-type-visual-h.md#oh_arkui_animationgroupstate) state.<br>         Returns [ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a re-entrant call is detected on the same thread. |


### OH_ArkUI_NativeModule_ResumeAnimationGroup()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ResumeAnimationGroup(ArkUI_ContextHandle context, const char *key)
```

**Description**

Resumes the animation group identified by the specified key on the UIContext.

When this API is called, the animation group must be in the [OH_ARKUI_ANIMATION_GROUP_STATE_PAUSED](capi-native-type-visual-h.md#oh_arkui_animationgroupstate) state; otherwise, [ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. You can call [OH_ArkUI_NativeModule_GetAnimationGroupState](#oh_arkui_nativemodule_getanimationgroupstate) to query the playback state of the animation group.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | [Input parameter] UIContext. |
| const char *key | [Input parameter] Pointer to the key of the animation group. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_ANIMATION_GROUP_NOT_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the animation group identified by the key is not found on the UIContext.<br>         Returns [ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the animation group is not in the [OH_ARKUI_ANIMATION_GROUP_STATE_PAUSED](capi-native-type-visual-h.md#oh_arkui_animationgroupstate) state.<br>         Returns [ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a re-entrant call is detected on the same thread. |


### OH_ArkUI_NativeModule_FinishAnimationGroup()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_FinishAnimationGroup(ArkUI_ContextHandle context, const char *key, OH_ArkUI_AnimationFinishMode mode)
```

**Description**

Finishes the animation group identified by the specified key on the UIContext.

Finish the animation group in the specified finish mode: jump to the end state, jump to the start state, or keep the current value. The animation group must be in the [OH_ARKUI_ANIMATION_GROUP_STATE_RUNNING](capi-native-type-visual-h.md#oh_arkui_animationgroupstate) or [OH_ARKUI_ANIMATION_GROUP_STATE_PAUSED](capi-native-type-visual-h.md#oh_arkui_animationgroupstate) state; otherwise, [ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. You can call [OH_ArkUI_NativeModule_GetAnimationGroupState](#oh_arkui_nativemodule_getanimationgroupstate) to query the playback state of the animation group.

**Since:** 26.0.1


**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | [Input parameter] UIContext. |
| const char *key | [Input parameter] Pointer to the key of the animation group. |
| [OH_ArkUI_AnimationFinishMode](capi-native-type-visual-h.md#oh_arkui_animationfinishmode) mode | [Input parameter] Finish mode. The value is an enumerated value of [OH_ArkUI_AnimationFinishMode](capi-native-type-visual-h.md#oh_arkui_animationfinishmode). |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs, for example, **context** or **key** is invalid, or the value of **mode** is not a valid one of **OH_ArkUI_AnimationFinishMode**.<br>         Returns [ARKUI_ERROR_CODE_ANIMATION_GROUP_NOT_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the animation group identified by key is not found on the UIContext.<br>         Returns [ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the animation group is not in the [OH_ARKUI_ANIMATION_GROUP_STATE_RUNNING](capi-native-type-visual-h.md#oh_arkui_animationgroupstate) or [OH_ARKUI_ANIMATION_GROUP_STATE_PAUSED](capi-native-type-visual-h.md#oh_arkui_animationgroupstate) state.<br>         Returns [ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a re-entrant call is detected on the same thread. |
