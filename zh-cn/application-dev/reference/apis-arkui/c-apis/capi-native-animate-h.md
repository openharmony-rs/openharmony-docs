# native_animate.h

## 概述

提供ArkUI（方舟UI框架）在Native侧的动画接口定义集合。native_animate.h中的接口需要在主线程上调用。

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md) | ArkUI_ExpectedFrameRateRange | 设置动画的期望帧率。该结构体通过min、max和expected三个字段定义帧率范围，系统尽可能满足期望帧率。 |
| [ArkUI_AnimateCompleteCallback](capi-arkui-nativemodule-arkui-animatecompletecallback.md) | ArkUI_AnimateCompleteCallback | 动画播放结束回调类型，用于在动画播放完成时通知开发者动画已结束。开发者可通过type字段指定回调触发方式，通过callback字段设置自定义回调函数，并通过userData字段传递自定义数据至回调函数中。 |
| [ArkUI_NativeAnimateAPI_1](capi-arkui-nativemodule-arkui-nativeanimateapi-1.md) | ArkUI_NativeAnimateAPI_1 | ArkUI（方舟UI框架）提供的Native侧动画接口集合。 |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md) | ArkUI_AnimateOption | 定义动画效果的配置参数，用于配置动画的相关属性。 |
| [ArkUI_Curve](capi-arkui-nativemodule-arkui-curve.md) | ArkUI_Curve | 提供动画曲线的插值对象定义，用于动画属性值的插值计算。 |
| [ArkUI_Curve*](capi-arkui-nativemodule-arkui-curve8h.md) | ArkUI_CurveHandle | 曲线插值对象的指针类型定义。曲线插值用于控制动画属性值随时间的变化规律，不同类型的插值曲线可实现不同的动画过渡效果。 |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md) | ArkUI_KeyframeAnimateOption | 定义关键帧动画参数对象，作为关键帧动画接口的输入参数使用。相关接口需要在主线程上调用。 |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md) | ArkUI_AnimatorOption | 定义animator动画参数对象，用于创建animator动画时配置动画属性参数。 |
| [ArkUI_Animator*](capi-arkui-nativemodule-arkui-animator8h.md) | ArkUI_AnimatorHandle | 定义animator动画对象指针，用于对ArkUI（方舟UI框架）动画对象进行操作和控制。 |
| [ArkUI_AnimatorEvent](capi-arkui-nativemodule-arkui-animatorevent.md) | ArkUI_AnimatorEvent | 定义animator回调事件对象，用于在动画状态变化回调中接收事件。 |
| [ArkUI_AnimatorOnFrameEvent](capi-arkui-nativemodule-arkui-animatoronframeevent.md) | ArkUI_AnimatorOnFrameEvent | 定义animator动画播放过程中逐帧回调的事件数据对象。 |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md) | ArkUI_TransitionEffect | 定义transition属性的转场效果参数对象，用于配置组件出现或消失时的过渡动画效果。 |
| [OH_ArkUI_PropertyAnimation](capi-arkui-nativemodule-oh-arkui-propertyanimation.md) | *OH_ArkUI_PropertyAnimationHandle | 定义属性动画的句柄。 |
| [OH_ArkUI_KeyframeAnimation](capi-arkui-nativemodule-oh-arkui-keyframeanimation.md) | *OH_ArkUI_KeyframeAnimationHandle | 定义关键帧动画的句柄。 |
| [OH_ArkUI_PathAnimation](capi-arkui-nativemodule-oh-arkui-pathanimation.md) | *OH_ArkUI_PathAnimationHandle | 定义路径动画的句柄。 |
| [OH_ArkUI_AnimationGroup](capi-arkui-nativemodule-oh-arkui-animationgroup.md) | *OH_ArkUI_AnimationGroupHandle | 定义动画组的句柄。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [ArkUI_AnimateOption* OH_ArkUI_AnimateOption_Create()](#oh_arkui_animateoption_create) | 创建动画效果参数。 |
| [void OH_ArkUI_AnimateOption_Dispose(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_dispose) | 销毁动画效果参数指针。 |
| [uint32_t OH_ArkUI_AnimateOption_GetDuration(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_getduration) | 获取动画持续时间，单位为ms（毫秒）。 |
| [float OH_ArkUI_AnimateOption_GetTempo(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_gettempo) | 获取动画播放速度。 |
| [ArkUI_AnimationCurve OH_ArkUI_AnimateOption_GetCurve(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_getcurve) | 获取动画曲线。 |
| [int32_t OH_ArkUI_AnimateOption_GetDelay(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_getdelay) | 获取动画延迟播放时间，单位为ms（毫秒）。 |
| [int32_t OH_ArkUI_AnimateOption_GetIterations(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_getiterations) | 获取动画播放次数。 |
| [ArkUI_AnimationPlayMode OH_ArkUI_AnimateOption_GetPlayMode(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_getplaymode) | 获取动画播放模式。 |
| [ArkUI_ExpectedFrameRateRange* OH_ArkUI_AnimateOption_GetExpectedFrameRateRange(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_getexpectedframeraterange) | 获取动画的期望帧率，单位为帧/秒（fps）。 |
| [void OH_ArkUI_AnimateOption_SetDuration(ArkUI_AnimateOption* option, int32_t value)](#oh_arkui_animateoption_setduration) | 设置动画持续时间，单位为ms（毫秒）。 |
| [void OH_ArkUI_AnimateOption_SetTempo(ArkUI_AnimateOption* option, float value)](#oh_arkui_animateoption_settempo) | 设置动画播放速度。 |
| [void OH_ArkUI_AnimateOption_SetCurve(ArkUI_AnimateOption* option, ArkUI_AnimationCurve value)](#oh_arkui_animateoption_setcurve) | 设置动画自定义曲线。 |
| [void OH_ArkUI_AnimateOption_SetDelay(ArkUI_AnimateOption* option, int32_t value)](#oh_arkui_animateoption_setdelay) | 设置动画延迟播放时间，单位为ms（毫秒）。 |
| [void OH_ArkUI_AnimateOption_SetIterations(ArkUI_AnimateOption* option, int32_t value)](#oh_arkui_animateoption_setiterations) | 设置动画播放次数。 |
| [void OH_ArkUI_AnimateOption_SetPlayMode(ArkUI_AnimateOption* option, ArkUI_AnimationPlayMode value)](#oh_arkui_animateoption_setplaymode) | 设置动画播放模式。 |
| [void OH_ArkUI_AnimateOption_SetExpectedFrameRateRange(ArkUI_AnimateOption* option, ArkUI_ExpectedFrameRateRange* value)](#oh_arkui_animateoption_setexpectedframeraterange) | 设置动画的期望帧率。 |
| [void OH_ArkUI_AnimateOption_SetICurve(ArkUI_AnimateOption* option, ArkUI_CurveHandle value)](#oh_arkui_animateoption_seticurve) | 设置动画的插值曲线。 |
| [ArkUI_CurveHandle OH_ArkUI_AnimateOption_GetICurve(ArkUI_AnimateOption* option)](#oh_arkui_animateoption_geticurve) | 获取动画的插值曲线。 |
| [ArkUI_KeyframeAnimateOption* OH_ArkUI_KeyframeAnimateOption_Create(int32_t size)](#oh_arkui_keyframeanimateoption_create) | 创建关键帧动画参数。 |
| [void OH_ArkUI_KeyframeAnimateOption_Dispose(ArkUI_KeyframeAnimateOption* option)](#oh_arkui_keyframeanimateoption_dispose) | 销毁关键帧动画参数。 |
| [int32_t OH_ArkUI_KeyframeAnimateOption_SetDelay(ArkUI_KeyframeAnimateOption* option, int32_t value)](#oh_arkui_keyframeanimateoption_setdelay) | 设置关键帧动画的整体延迟时间，单位为ms（毫秒），默认不延迟播放。 |
| [int32_t OH_ArkUI_KeyframeAnimateOption_SetIterations(ArkUI_KeyframeAnimateOption* option, int32_t value)](#oh_arkui_keyframeanimateoption_setiterations) | 设置关键帧动画播放次数。默认播放一次，设置为-1时表示无限次播放，设置为0时表示无动画效果。 |
| [int32_t OH_ArkUI_KeyframeAnimateOption_RegisterOnFinishCallback(ArkUI_KeyframeAnimateOption* option, void* userData, void (\*onFinish)(void* userData))](#oh_arkui_keyframeanimateoption_registeronfinishcallback) | 设置关键帧动画播放完成回调。当关键帧动画[ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)所有次数播放完成后调用。 |
| [int32_t OH_ArkUI_KeyframeAnimateOption_SetExpectedFrameRate(ArkUI_KeyframeAnimateOption* option, ArkUI_ExpectedFrameRateRange* frameRate)](#oh_arkui_keyframeanimateoption_setexpectedframerate) | 设置关键帧动画期望帧率。 |
| [int32_t OH_ArkUI_KeyframeAnimateOption_SetDuration(ArkUI_KeyframeAnimateOption* option, int32_t value, int32_t index)](#oh_arkui_keyframeanimateoption_setduration) | 设置关键帧动画某段关键帧动画的持续时间，单位为ms（毫秒）。 |
| [int32_t OH_ArkUI_KeyframeAnimateOption_SetCurve(ArkUI_KeyframeAnimateOption* option, ArkUI_CurveHandle value, int32_t index)](#oh_arkui_keyframeanimateoption_setcurve) | 设置关键帧动画某段关键帧使用的动画曲线。 |
| [int32_t OH_ArkUI_KeyframeAnimateOption_RegisterOnEventCallback(ArkUI_KeyframeAnimateOption* option, void* userData, void (\*event)(void* userData), int32_t index)](#oh_arkui_keyframeanimateoption_registeroneventcallback) | 设置关键帧时刻状态的闭包函数，即在该关键帧时刻要达到的状态。 |
| [int32_t OH_ArkUI_KeyframeAnimateOption_GetDelay(ArkUI_KeyframeAnimateOption* option)](#oh_arkui_keyframeanimateoption_getdelay) | 获取关键帧整体延迟时间，单位为ms（毫秒）。 |
| [int32_t OH_ArkUI_KeyframeAnimateOption_GetIterations(ArkUI_KeyframeAnimateOption* option)](#oh_arkui_keyframeanimateoption_getiterations) | 获取关键帧动画播放次数。 |
| [ArkUI_ExpectedFrameRateRange* OH_ArkUI_KeyframeAnimateOption_GetExpectedFrameRate(ArkUI_KeyframeAnimateOption* option)](#oh_arkui_keyframeanimateoption_getexpectedframerate) | 获取关键帧动画参数的期望帧率。 |
| [int32_t OH_ArkUI_KeyframeAnimateOption_GetDuration(ArkUI_KeyframeAnimateOption* option, int32_t index)](#oh_arkui_keyframeanimateoption_getduration) | 获取关键帧动画某段状态持续时间，单位为ms（毫秒）。 |
| [ArkUI_CurveHandle OH_ArkUI_KeyframeAnimateOption_GetCurve(ArkUI_KeyframeAnimateOption* option, int32_t index)](#oh_arkui_keyframeanimateoption_getcurve) | 获取关键帧动画某段状态动画曲线。 |
| [ArkUI_AnimatorOption* OH_ArkUI_AnimatorOption_Create(int32_t keyframeSize)](#oh_arkui_animatoroption_create) | 创建animator动画对象参数。 |
| [void OH_ArkUI_AnimatorOption_Dispose(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_dispose) | 销毁animator动画对象参数。 |
| [int32_t OH_ArkUI_AnimatorOption_SetDuration(ArkUI_AnimatorOption* option, int32_t value)](#oh_arkui_animatoroption_setduration) | 设置animator动画播放的时长，单位为ms（毫秒）。 |
| [int32_t OH_ArkUI_AnimatorOption_SetDelay(ArkUI_AnimatorOption* option, int32_t value)](#oh_arkui_animatoroption_setdelay) | 设置animator动画延迟播放的时间，单位为ms（毫秒）。 |
| [int32_t OH_ArkUI_AnimatorOption_SetIterations(ArkUI_AnimatorOption* option, int32_t value)](#oh_arkui_animatoroption_setiterations) | 设置animator动画播放次数。默认播放一次，设置为-1时表示无限次播放，设置为0时表示无动画效果。 |
| [int32_t OH_ArkUI_AnimatorOption_SetFill(ArkUI_AnimatorOption* option, ArkUI_AnimationFillMode value)](#oh_arkui_animatoroption_setfill) | 设置组件在动画开始前和结束后保持的状态。 |
| [int32_t OH_ArkUI_AnimatorOption_SetDirection(ArkUI_AnimatorOption* option, ArkUI_AnimationDirection value)](#oh_arkui_animatoroption_setdirection) | 设置animator动画播放方向。 |
| [int32_t OH_ArkUI_AnimatorOption_SetCurve(ArkUI_AnimatorOption* option, ArkUI_CurveHandle value)](#oh_arkui_animatoroption_setcurve) | 设置animator动画插值曲线。 |
| [int32_t OH_ArkUI_AnimatorOption_SetBegin(ArkUI_AnimatorOption* option, float value)](#oh_arkui_animatoroption_setbegin) | 设置animator动画插值起点。 |
| [int32_t OH_ArkUI_AnimatorOption_SetEnd(ArkUI_AnimatorOption* option, float value)](#oh_arkui_animatoroption_setend) | 设置animator动画插值终点。 |
| [int32_t OH_ArkUI_AnimatorOption_SetExpectedFrameRateRange(ArkUI_AnimatorOption* option, ArkUI_ExpectedFrameRateRange* value)](#oh_arkui_animatoroption_setexpectedframeraterange) | 设置animator动画期望的帧率范围。 |
| [int32_t OH_ArkUI_AnimatorOption_SetKeyframe(ArkUI_AnimatorOption* option, float time, float value, int32_t index)](#oh_arkui_animatoroption_setkeyframe) | 设置animator动画关键帧参数。 |
| [int32_t OH_ArkUI_AnimatorOption_SetKeyframeCurve(ArkUI_AnimatorOption* option, ArkUI_CurveHandle value, int32_t index)](#oh_arkui_animatoroption_setkeyframecurve) | 设置animator动画关键帧曲线类型。 |
| [int32_t OH_ArkUI_AnimatorOption_GetDuration(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getduration) | 获取animator动画播放的时长，单位为ms（毫秒）。 |
| [int32_t OH_ArkUI_AnimatorOption_GetDelay(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getdelay) | 获取animator动画延迟播放时长，单位为ms（毫秒）。 |
| [int32_t OH_ArkUI_AnimatorOption_GetIterations(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getiterations) | 获取animator动画播放次数。 |
| [ArkUI_AnimationFillMode OH_ArkUI_AnimatorOption_GetFill(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getfill) | 获取animator动画执行时组件在动画开始前和结束后的状态。 |
| [ArkUI_AnimationDirection OH_ArkUI_AnimatorOption_GetDirection(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getdirection) | 获取animator动画播放方向。 |
| [ArkUI_CurveHandle OH_ArkUI_AnimatorOption_GetCurve(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getcurve) | 获取animator动画插值曲线。 |
| [float OH_ArkUI_AnimatorOption_GetBegin(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getbegin) | 获取animator动画插值起点。 |
| [float OH_ArkUI_AnimatorOption_GetEnd(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getend) | 获取animator动画插值终点。 |
| [ArkUI_ExpectedFrameRateRange* OH_ArkUI_AnimatorOption_GetExpectedFrameRateRange(ArkUI_AnimatorOption* option)](#oh_arkui_animatoroption_getexpectedframeraterange) | 获取animator动画期望的帧率范围。 |
| [float OH_ArkUI_AnimatorOption_GetKeyframeTime(ArkUI_AnimatorOption* option, int32_t index)](#oh_arkui_animatoroption_getkeyframetime) | 获取animator动画关键帧时间，取值范围[0, 1]，为归一化时间比例。 |
| [float OH_ArkUI_AnimatorOption_GetKeyframeValue(ArkUI_AnimatorOption* option, int32_t index)](#oh_arkui_animatoroption_getkeyframevalue) | 获取animator动画关键帧数值。 |
| [ArkUI_CurveHandle OH_ArkUI_AnimatorOption_GetKeyframeCurve(ArkUI_AnimatorOption* option, int32_t index)](#oh_arkui_animatoroption_getkeyframecurve) | 获取animator动画关键帧动画插值曲线。 |
| [void* OH_ArkUI_AnimatorEvent_GetUserData(ArkUI_AnimatorEvent* event)](#oh_arkui_animatorevent_getuserdata) | 获取动画事件对象中的用户自定义对象。 |
| [void* OH_ArkUI_AnimatorOnFrameEvent_GetUserData(ArkUI_AnimatorOnFrameEvent* event)](#oh_arkui_animatoronframeevent_getuserdata) | 获取动画的帧事件中的用户自定义对象。 |
| [float OH_ArkUI_AnimatorOnFrameEvent_GetValue(ArkUI_AnimatorOnFrameEvent* event)](#oh_arkui_animatoronframeevent_getvalue) | 获取动画帧回调事件对象中的插值结果。 |
| [int32_t OH_ArkUI_AnimatorOption_RegisterOnFrameCallback(ArkUI_AnimatorOption* option, void* userData, void (\*callback)(ArkUI_AnimatorOnFrameEvent* event))](#oh_arkui_animatoroption_registeronframecallback) | 设置animator动画接收到帧时回调。 |
| [int32_t OH_ArkUI_AnimatorOption_RegisterOnFinishCallback(ArkUI_AnimatorOption* option, void* userData, void (\*callback)(ArkUI_AnimatorEvent* event))](#oh_arkui_animatoroption_registeronfinishcallback) | 设置animator动画完成时回调。 |
| [int32_t OH_ArkUI_AnimatorOption_RegisterOnCancelCallback(ArkUI_AnimatorOption* option, void* userData, void (\*callback)(ArkUI_AnimatorEvent* event))](#oh_arkui_animatoroption_registeroncancelcallback) | 设置animator动画被取消时回调。 |
| [int32_t OH_ArkUI_AnimatorOption_RegisterOnRepeatCallback(ArkUI_AnimatorOption* option, void* userData, void (\*callback)(ArkUI_AnimatorEvent* event))](#oh_arkui_animatoroption_registeronrepeatcallback) | 设置animator动画重复时回调。 |
| [int32_t OH_ArkUI_Animator_ResetAnimatorOption(ArkUI_AnimatorHandle animatorHandle, ArkUI_AnimatorOption* option)](#oh_arkui_animator_resetanimatoroption) | 重置animator动画的配置参数。 |
| [int32_t OH_ArkUI_Animator_Play(ArkUI_AnimatorHandle animatorHandle)](#oh_arkui_animator_play) | 启动animator动画。需要在主线程上调用。 |
| [int32_t OH_ArkUI_Animator_Finish(ArkUI_AnimatorHandle animatorHandle)](#oh_arkui_animator_finish) | 结束animator动画，动画将跳到终点状态后停止。与[OH_ArkUI_Animator_Cancel](capi-native-animate-h.md#oh_arkui_animator_cancel)的区别：Cancel会立即中断动画并回到初始状态，Finish会让动画直接跳到终点状态后停止。 需要在主线程上调用。 |
| [int32_t OH_ArkUI_Animator_Pause(ArkUI_AnimatorHandle animatorHandle)](#oh_arkui_animator_pause) | 暂停animator动画。 |
| [int32_t OH_ArkUI_Animator_Cancel(ArkUI_AnimatorHandle animatorHandle)](#oh_arkui_animator_cancel) | 取消animator动画。 |
| [int32_t OH_ArkUI_Animator_Reverse(ArkUI_AnimatorHandle animatorHandle)](#oh_arkui_animator_reverse) | 以相反的顺序播放animator动画。 |
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateCurveByType(ArkUI_AnimationCurve curve)](#oh_arkui_curve_createcurvebytype) | 插值曲线的初始化函数，可以根据入参创建一个插值曲线对象。 |
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateStepsCurve(int32_t count, bool end)](#oh_arkui_curve_createstepscurve) | 构造阶梯曲线对象。 |
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateCubicBezierCurve(float x1, float y1, float x2, float y2)](#oh_arkui_curve_createcubicbeziercurve) | 构造三阶贝塞尔曲线对象。 |
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateSpringCurve(float velocity, float mass, float stiffness, float damping)](#oh_arkui_curve_createspringcurve) | 构造弹簧曲线对象，曲线形状由弹簧参数决定，动画时长受动画参数中的时长参数控制。 |
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateSpringMotion(float response, float dampingFraction, float overlapDuration)](#oh_arkui_curve_createspringmotion) | 构造弹性动画曲线对象。如果对同一对象的同一属性进行多个弹性动画，每个动画会替换掉前一个动画，并继承之前的速度。 |
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateResponsiveSpringMotion(float response, float dampingFraction, float overlapDuration)](#oh_arkui_curve_createresponsivespringmotion) | 构造弹性跟手动画曲线对象，是springMotion的一种特例，仅默认参数不同，可与springMotion混合使用。 |
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateInterpolatingSpring(float velocity, float mass, float stiffness, float damping)](#oh_arkui_curve_createinterpolatingspring) | 构造插值器弹簧曲线对象，生成一条从0到1的动画曲线，实际动画值根据曲线进行插值计算。 |
| [ArkUI_CurveHandle OH_ArkUI_Curve_CreateCustomCurve(void* userData, float (\*interpolate)(float fraction, void* userdata))](#oh_arkui_curve_createcustomcurve) | 构造自定义曲线对象。 |
| [void OH_ArkUI_Curve_DisposeCurve(ArkUI_CurveHandle curveHandle)](#oh_arkui_curve_disposecurve) | 销毁自定义曲线对象。 |
| [ArkUI_TransitionEffect* OH_ArkUI_CreateOpacityTransitionEffect(float opacity)](#oh_arkui_createopacitytransitioneffect) | 创建组件转场时的透明度效果对象。 |
| [ArkUI_TransitionEffect* OH_ArkUI_CreateTranslationTransitionEffect(ArkUI_TranslationOptions* translate)](#oh_arkui_createtranslationtransitioneffect) | 创建组件转场时的平移效果对象。 |
| [ArkUI_TransitionEffect* OH_ArkUI_CreateScaleTransitionEffect(ArkUI_ScaleOptions* scale)](#oh_arkui_createscaletransitioneffect) | 创建组件转场时的缩放效果对象。 |
| [ArkUI_TransitionEffect* OH_ArkUI_CreateRotationTransitionEffect(ArkUI_RotationOptions* rotate)](#oh_arkui_createrotationtransitioneffect) | 创建组件转场时的旋转效果对象。 |
| [ArkUI_TransitionEffect* OH_ArkUI_CreateMovementTransitionEffect(ArkUI_TransitionEdge edge)](#oh_arkui_createmovementtransitioneffect) | 创建组件平移效果对象，通过指定边缘方向（上、下、左、右）控制组件的滑入滑出方向，适用于仅需指定滑动方向的简单场景。与OH_ArkUI_CreateTranslationTransitionEffect不同： 后者支持自定义x/y/z方向的精确平移参数，适用于需要指定具体位移距离的场景。 |
| [ArkUI_TransitionEffect* OH_ArkUI_CreateAsymmetricTransitionEffect(ArkUI_TransitionEffect* appear, ArkUI_TransitionEffect* disappear)](#oh_arkui_createasymmetrictransitioneffect) | 创建非对称的转场效果对象。 |
| [ArkUI_TransitionEffect* OH_ArkUI_CreateIdentityTransitionEffect(void)](#oh_arkui_createidentitytransitioneffect) | 创建无转场效果对象。 |
| [void OH_ArkUI_TransitionEffect_Dispose(ArkUI_TransitionEffect* effect)](#oh_arkui_transitioneffect_dispose) | 销毁转场效果对象。 |
| [int32_t OH_ArkUI_TransitionEffect_Combine(ArkUI_TransitionEffect* firstEffect, ArkUI_TransitionEffect* secondEffect)](#oh_arkui_transitioneffect_combine) | 设置转场效果链式组合，以形成包含多种转场效果的TransitionEffect。 |
| [int32_t OH_ArkUI_TransitionEffect_SetAnimation(ArkUI_TransitionEffect* effect, ArkUI_AnimateOption* animation)](#oh_arkui_transitioneffect_setanimation) | 设置转场效果动画参数。 |
| [OH_ArkUI_PropertyAnimationHandle OH_ArkUI_NativeModule_PropertyAnimation_Create(OH_ArkUI_AnimationPropertyType propertyType)](#oh_arkui_nativemodule_propertyanimation_create) | 为指定的可动画属性创建属性动画。 <br> <b>propertyType</b>必须是有效的[OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype)，否则本接口返回<b>NULL</b>。 |
| [void OH_ArkUI_NativeModule_PropertyAnimation_Destroy(OH_ArkUI_PropertyAnimationHandle animation)](#oh_arkui_nativemodule_propertyanimation_destroy) | 销毁属性动画。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetFromValue(OH_ArkUI_PropertyAnimationHandle animation, const ArkUI_NumberValue *value, int32_t size)](#oh_arkui_nativemodule_propertyanimation_setfromvalue) | 设置属性动画的起始值。<br> 推荐设置起始值，若未设置则默认从当前属性值开始产生动画。但需注意：如果未设置起始值且对应属性从未被赋值，由于缺少有效的起始状态，属性动画将无法产生。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetFromValue(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_NumberValue *value, int32_t size)](#oh_arkui_nativemodule_propertyanimation_getfromvalue) | 获取属性动画的起始值。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetToValue(OH_ArkUI_PropertyAnimationHandle animation, const ArkUI_NumberValue *value, int32_t size)](#oh_arkui_nativemodule_propertyanimation_settovalue) | 设置属性动画的结束值。<br> 必须设置结束值，否则属性动画句柄无实际意义。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetToValue(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_NumberValue *value, int32_t size)](#oh_arkui_nativemodule_propertyanimation_gettovalue) | 获取属性动画的结束值。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetDuration(OH_ArkUI_PropertyAnimationHandle animation, int32_t duration)](#oh_arkui_nativemodule_propertyanimation_setduration) | 设置属性动画的持续时间。<br> 实际生效的动画持续时间按以下优先级确定：如果通过本接口设置了子动画的持续时间，则使用该值； 否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration)在动画组上设置的持续时间；如果两者都未设置，则使用默认值**1000**毫秒。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetDuration(OH_ArkUI_PropertyAnimationHandle animation, int32_t *duration)](#oh_arkui_nativemodule_propertyanimation_getduration) | 获取属性动画的持续时间。 <br> 本接口仅返回在本动画上显式设置的持续时间；从动画组继承的值或默认值在运行时解析，不存储在本对象上。 如果本动画未设置持续时间，则返回[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 运行时实际生效的动画持续时间按以下优先级确定：如果通过[OH_ArkUI_NativeModule_PropertyAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setduration)设置了持续时间， 则使用该值；否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration)设置的动画组持续时间；如果两者都未设置，则使用默认值**1000**毫秒。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetDelay(OH_ArkUI_PropertyAnimationHandle animation, int32_t delay)](#oh_arkui_nativemodule_propertyanimation_setdelay) | 设置属性动画的延迟时间。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetDelay(OH_ArkUI_PropertyAnimationHandle animation, int32_t *delay)](#oh_arkui_nativemodule_propertyanimation_getdelay) | 获取属性动画的延迟时间。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetCurve(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_CurveHandle curve)](#oh_arkui_nativemodule_propertyanimation_setcurve) | 设置属性动画的动画曲线。 <br> 实际生效的动画曲线按以下优先级确定：如果通过本接口设置了曲线，则使用该值； 否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setcurve)在动画组上设置的曲线；如果两者都未设置，则使用[ARKUI_CURVE_LINEAR](capi-native-type-h.md#arkui_animationcurve)。 支持弹簧曲线（<b>springMotion</b>、<b>responsiveSpringMotion</b>和<b>interpolatingSpring</b>）。 设置弹簧曲线时，通过[OH_ArkUI_NativeModule_PropertyAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setduration)设置的持续时间不生效，动画持续时间由弹簧曲线决定。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetCurve(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_CurveHandle *outBorrowedCurve)](#oh_arkui_nativemodule_propertyanimation_getcurve) | 获取属性动画的动画曲线。 <br> 本接口仅返回在本动画上显式设置的曲线；从动画组继承的值或默认值在运行时解析，不存储在本对象上。 如果本动画未设置曲线，则返回[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 运行时实际生效的动画曲线按以下优先级确定：如果通过[OH_ArkUI_NativeModule_PropertyAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setcurve)设置了曲线，则使用该值； 否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setcurve)设置的动画组曲线；如果两者都未设置，则使用[ARKUI_CURVE_LINEAR](capi-native-type-h.md#arkui_animationcurve)。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetTempo(OH_ArkUI_PropertyAnimationHandle animation, float tempo)](#oh_arkui_nativemodule_propertyanimation_settempo) | 设置属性动画的播放速率。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetTempo(OH_ArkUI_PropertyAnimationHandle animation, float *tempo)](#oh_arkui_nativemodule_propertyanimation_gettempo) | 获取属性动画的播放速率。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetAutoReverse(OH_ArkUI_PropertyAnimationHandle animation, bool autoReverse)](#oh_arkui_nativemodule_propertyanimation_setautoreverse) | 设置属性动画是否自动反转。<br> 启用自动反转后，动画在每轮播放中交替正向播放和反向播放。默认值为<b>false</b>。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetAutoReverse(OH_ArkUI_PropertyAnimationHandle animation, bool *autoReverse)](#oh_arkui_nativemodule_propertyanimation_getautoreverse) | 获取属性动画是否启用自动反转。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetIterations(OH_ArkUI_PropertyAnimationHandle animation, int32_t iterations)](#oh_arkui_nativemodule_propertyanimation_setiterations) | 设置属性动画的播放次数。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetIterations(OH_ArkUI_PropertyAnimationHandle animation, int32_t *iterations)](#oh_arkui_nativemodule_propertyanimation_getiterations) | 获取属性动画的播放次数。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_RenderNodeHandle targetNode)](#oh_arkui_nativemodule_propertyanimation_settargetnode) | 设置属性动画的目标渲染节点。<br> 目标节点是被该属性动画驱动的渲染节点。 如果为<b>NULL</b>（默认值），则动画继承通过[OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode)设置的动画组默认目标。 非NULL目标必须属于动画组注册的同一UIContext，该检查在通过[OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup)注册动画组时执行。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetTargetNode(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_RenderNodeHandle *outBorrowedTargetNode)](#oh_arkui_nativemodule_propertyanimation_gettargetnode) | 获取属性动画的目标渲染节点。 |
| [OH_ArkUI_KeyframeAnimationHandle OH_ArkUI_NativeModule_KeyframeAnimation_Create(OH_ArkUI_AnimationPropertyType propertyType, int32_t size)](#oh_arkui_nativemodule_keyframeanimation_create) | 为指定的可动画属性创建关键帧动画。 <br> 每个关键帧的关键时间默认按索引在[0, 1]区间均匀分布（例如，当有3个关键帧时，第一帧为<b>0.0</b>，第二帧为<b>0.5</b>，第三帧为<b>1.0</b>）。 使用[OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTimes](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setkeytimes)或 [OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTime](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setkeytime)自定义关键时间点。 <br> <b>propertyType</b>必须是有效的[OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype)，且<b>size</b>必须大于等于2；否则，本接口返回<b>NULL</b>。 |
| [void OH_ArkUI_NativeModule_KeyframeAnimation_Destroy(OH_ArkUI_KeyframeAnimationHandle animation)](#oh_arkui_nativemodule_keyframeanimation_destroy) | 销毁关键帧动画。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTimes(OH_ArkUI_KeyframeAnimationHandle animation, const float *keyTimes, int32_t size)](#oh_arkui_nativemodule_keyframeanimation_setkeytimes) | 设置关键帧的关键时间点。 <br> 如果不调用本接口，每个关键帧的关键时间默认按索引在[0, 1]区间均匀分布（例如，当有3个关键帧时，第一帧为<b>0.0</b>，第二帧为<b>0.5</b>，第三帧为<b>1.0</b>）。 <br> <b>keyTimes</b>中的元素必须非递减， 且<b>size</b>必须等于关键帧动画的关键帧数量（即通过[OH_ArkUI_NativeModule_KeyframeAnimation_Create](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_create)创建动画时指定的<b>size</b>值）。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetKeyTime(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, float *keyTime)](#oh_arkui_nativemodule_keyframeanimation_getkeytime) | 获取指定索引处关键帧的关键时间点。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTime(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, float keyTime)](#oh_arkui_nativemodule_keyframeanimation_setkeytime) | 设置指定索引处关键帧的关键时间点。 <br> 如果不调用本接口设置某个关键帧，其关键时间默认按索引在[0, 1]区间均匀分布（例如，当有3个关键帧时，第一帧为<b>0.0</b>，第二帧为<b>0.5</b>，第三帧为<b>1.0</b>）。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetValue(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, const ArkUI_NumberValue *value, int32_t size)](#oh_arkui_nativemodule_keyframeanimation_setvalue) | 设置指定索引处关键帧的值。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetValues(OH_ArkUI_KeyframeAnimationHandle animation, const ArkUI_NumberValue *values, int32_t size)](#oh_arkui_nativemodule_keyframeanimation_setvalues) | 一次性设置所有关键帧的值。 <br> 值以扁平数组形式提供。每个关键帧的元素数量取决于[OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype)。 例如，OH_ARKUI_ANIMATION_PROPERTY_OPACITY每个关键帧需要1个值，OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION每个关键帧需要2个值。 元素总数必须等于关键帧数量乘以每个关键帧的值数量。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetValue(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, ArkUI_NumberValue *value, int32_t size)](#oh_arkui_nativemodule_keyframeanimation_getvalue) | 获取指定索引处关键帧的值。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetCurves(OH_ArkUI_KeyframeAnimationHandle animation, const ArkUI_CurveHandle *value, int32_t size)](#oh_arkui_nativemodule_keyframeanimation_setcurves) | 设置关键帧的动画曲线。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, ArkUI_CurveHandle curve)](#oh_arkui_nativemodule_keyframeanimation_setcurve) | 设置指定索引处关键帧的动画曲线。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetCurve(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, ArkUI_CurveHandle *outBorrowedCurve)](#oh_arkui_nativemodule_keyframeanimation_getcurve) | 获取指定索引处关键帧的动画曲线。 <br> 本接口仅返回为关键帧显式设置的曲线；从动画组继承的值或默认值在运行时解析，不存储在本对象上。 如果关键帧未设置曲线，则返回[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 运行时实际生效的动画曲线按以下优先级确定：如果通过[OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setcurve)或 [OH_ArkUI_NativeModule_KeyframeAnimation_SetCurves](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setcurves)为关键帧设置了曲线，则使用该值； 否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setcurve)设置的动画组曲线；如果两者都未设置，则使用[ARKUI_CURVE_LINEAR](capi-native-type-h.md#arkui_animationcurve)。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration(OH_ArkUI_KeyframeAnimationHandle animation, int32_t duration)](#oh_arkui_nativemodule_keyframeanimation_setduration) | 设置关键帧动画的持续时间。 <br> 实际生效的动画持续时间按以下优先级确定：如果通过本接口设置了持续时间，则使用该值； 否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration)在动画组上设置的持续时间；如果两者都未设置，则使用默认值**1000**毫秒。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetDuration(OH_ArkUI_KeyframeAnimationHandle animation, int32_t *duration)](#oh_arkui_nativemodule_keyframeanimation_getduration) | 获取关键帧动画的持续时间。 <br> 本接口仅返回在本动画上显式设置的持续时间；从动画组继承的值或默认值在运行时解析，不存储在本对象上。 如果本动画未设置持续时间，则返回[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 运行时实际生效的动画持续时间按以下优先级确定：如果通过[OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setduration)设置了持续时间，则使用该值； 否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration)设置的动画组持续时间；如果两者都未设置，则使用默认值**1000**毫秒。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetDelay(OH_ArkUI_KeyframeAnimationHandle animation, int32_t delay)](#oh_arkui_nativemodule_keyframeanimation_setdelay) | 设置关键帧动画的延迟时间。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetDelay(OH_ArkUI_KeyframeAnimationHandle animation, int32_t *delay)](#oh_arkui_nativemodule_keyframeanimation_getdelay) | 获取关键帧动画的延迟时间。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetTempo(OH_ArkUI_KeyframeAnimationHandle animation, float tempo)](#oh_arkui_nativemodule_keyframeanimation_settempo) | 设置关键帧动画的播放速率。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetTempo(OH_ArkUI_KeyframeAnimationHandle animation, float *tempo)](#oh_arkui_nativemodule_keyframeanimation_gettempo) | 获取关键帧动画的播放速率。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetAutoReverse(OH_ArkUI_KeyframeAnimationHandle animation, bool autoReverse)](#oh_arkui_nativemodule_keyframeanimation_setautoreverse) | 设置关键帧动画是否自动反转。 <br> 启用自动反转后，动画在每轮播放中交替正向播放和反向播放。默认值为<b>false</b>。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetAutoReverse(OH_ArkUI_KeyframeAnimationHandle animation, bool *autoReverse)](#oh_arkui_nativemodule_keyframeanimation_getautoreverse) | 获取关键帧动画是否启用自动反转。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetIterations(OH_ArkUI_KeyframeAnimationHandle animation, int32_t iterations)](#oh_arkui_nativemodule_keyframeanimation_setiterations) | 设置关键帧动画的播放次数。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetIterations(OH_ArkUI_KeyframeAnimationHandle animation, int32_t *iterations)](#oh_arkui_nativemodule_keyframeanimation_getiterations) | 获取关键帧动画的播放次数。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode(OH_ArkUI_KeyframeAnimationHandle animation, ArkUI_RenderNodeHandle targetNode)](#oh_arkui_nativemodule_keyframeanimation_settargetnode) | 设置关键帧动画的目标渲染节点。 <br> 目标节点是被该关键帧动画驱动的渲染节点。如果为<b>NULL</b>（默认值），则动画继承通过[OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode)设置的动画组默认目标。 非NULL目标必须属于动画组注册的同一UIContext，该检查在通过[OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup)注册动画组时执行。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetTargetNode(OH_ArkUI_KeyframeAnimationHandle animation, ArkUI_RenderNodeHandle *outBorrowedTargetNode)](#oh_arkui_nativemodule_keyframeanimation_gettargetnode) | 获取关键帧动画的目标渲染节点。 |
| [OH_ArkUI_PathAnimationHandle OH_ArkUI_NativeModule_PathAnimation_Create(const char *path)](#oh_arkui_nativemodule_pathanimation_create) | 创建路径动画，使组件沿几何路径移动。 <br> 路径动画作用于OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION属性。 |
| [void OH_ArkUI_NativeModule_PathAnimation_Destroy(OH_ArkUI_PathAnimationHandle animation)](#oh_arkui_nativemodule_pathanimation_destroy) | 销毁路径动画。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetDuration(OH_ArkUI_PathAnimationHandle animation, int32_t duration)](#oh_arkui_nativemodule_pathanimation_setduration) | 设置路径动画的持续时间。 <br> 实际生效的动画持续时间按以下优先级确定：如果通过本接口设置了持续时间，则使用该值； 否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration)在动画组上设置的持续时间；如果两者都未设置，则使用默认值**1000**毫秒。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetDuration(OH_ArkUI_PathAnimationHandle animation, int32_t *duration)](#oh_arkui_nativemodule_pathanimation_getduration) | 获取路径动画的持续时间。 <br> 本接口仅返回在本动画上显式设置的持续时间；从动画组继承的值或默认值在运行时解析，不存储在本对象上。 如果本动画未设置持续时间，则返回[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 运行时实际生效的动画持续时间按以下优先级确定：如果通过[OH_ArkUI_NativeModule_PathAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_setduration)设置了持续时间，则使用该值； 否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration)设置的动画组持续时间；如果两者都未设置，则使用默认值**1000**毫秒。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetDelay(OH_ArkUI_PathAnimationHandle animation, int32_t delay)](#oh_arkui_nativemodule_pathanimation_setdelay) | 设置路径动画的延迟时间。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetDelay(OH_ArkUI_PathAnimationHandle animation, int32_t *delay)](#oh_arkui_nativemodule_pathanimation_getdelay) | 获取路径动画的延迟时间。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetCurve(OH_ArkUI_PathAnimationHandle animation, ArkUI_CurveHandle curve)](#oh_arkui_nativemodule_pathanimation_setcurve) | 设置路径动画的动画曲线。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetCurve(OH_ArkUI_PathAnimationHandle animation, ArkUI_CurveHandle *outBorrowedCurve)](#oh_arkui_nativemodule_pathanimation_getcurve) | 获取路径动画的动画曲线。 <br> 本接口仅返回在本动画上显式设置的曲线；从动画组继承的值或默认值在运行时解析，不存储在本对象上。 如果本动画未设置曲线，则返回[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 运行时实际生效的动画曲线按以下优先级确定：如果通过[OH_ArkUI_NativeModule_PathAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_setcurve)设置了曲线，则使用该值； 否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setcurve)设置的动画组曲线；如果两者都未设置，则使用[ARKUI_CURVE_LINEAR](capi-native-type-h.md#arkui_animationcurve)。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetTempo(OH_ArkUI_PathAnimationHandle animation, float tempo)](#oh_arkui_nativemodule_pathanimation_settempo) | 设置路径动画的播放速率。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetTempo(OH_ArkUI_PathAnimationHandle animation, float *tempo)](#oh_arkui_nativemodule_pathanimation_gettempo) | 获取路径动画的播放速率。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetAutoReverse(OH_ArkUI_PathAnimationHandle animation, bool autoReverse)](#oh_arkui_nativemodule_pathanimation_setautoreverse) | 设置路径动画是否自动反转。 <br> 启用自动反转后，动画在每轮播放中交替正向播放和反向播放。默认值为<b>false</b>。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetAutoReverse(OH_ArkUI_PathAnimationHandle animation, bool *autoReverse)](#oh_arkui_nativemodule_pathanimation_getautoreverse) | 获取路径动画是否启用自动反转。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetIterations(OH_ArkUI_PathAnimationHandle animation, int32_t iterations)](#oh_arkui_nativemodule_pathanimation_setiterations) | 设置路径动画的播放次数。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetIterations(OH_ArkUI_PathAnimationHandle animation, int32_t *iterations)](#oh_arkui_nativemodule_pathanimation_getiterations) | 获取路径动画的播放次数。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetAutoRotation(OH_ArkUI_PathAnimationHandle animation, bool autoRotation)](#oh_arkui_nativemodule_pathanimation_setautorotation) | 设置路径动画过程中组件是否沿路径切线方向自动旋转。 <br> 启用自动旋转后，组件将旋转使其朝向方向与当前位置的路径切线对齐。默认值为<b>false</b>。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetAutoRotation(OH_ArkUI_PathAnimationHandle animation, bool *autoRotation)](#oh_arkui_nativemodule_pathanimation_getautorotation) | 获取路径动画是否启用自动旋转。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetTargetNode(OH_ArkUI_PathAnimationHandle animation, ArkUI_RenderNodeHandle targetNode)](#oh_arkui_nativemodule_pathanimation_settargetnode) | 设置路径动画的目标渲染节点。 <br> 目标节点是被该路径动画驱动的渲染节点。 如果为<b>NULL</b>（默认值），则动画继承通过[OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode)设置的动画组默认目标。 非NULL目标必须属于动画组注册的同一UIContext，该检查在通过[OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup)注册动画组时执行。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetTargetNode(OH_ArkUI_PathAnimationHandle animation, ArkUI_RenderNodeHandle *outBorrowedTargetNode)](#oh_arkui_nativemodule_pathanimation_gettargetnode) | 获取路径动画的目标渲染节点。 |
| [OH_ArkUI_AnimationGroupHandle OH_ArkUI_NativeModule_AnimationGroup_Create(void)](#oh_arkui_nativemodule_animationgroup_create) | 创建动画组。 |
| [void OH_ArkUI_NativeModule_AnimationGroup_Destroy(OH_ArkUI_AnimationGroupHandle group)](#oh_arkui_nativemodule_animationgroup_destroy) | 销毁动画组的前端句柄。<br> 本接口仅释放前端句柄。 通过[OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup)注册的动画组的后端（运行时）对象将被单独释放——在finish回调触发时自动释放， 或通过[OH_ArkUI_NativeModule_RemoveAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_removeanimationgroup)释放。<br> 添加到动画组的子动画不会被自动销毁。 需要分别调用[OH_ArkUI_NativeModule_PropertyAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_destroy)、 [OH_ArkUI_NativeModule_KeyframeAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_destroy)或[OH_ArkUI_NativeModule_PathAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_destroy)。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetDuration(OH_ArkUI_AnimationGroupHandle group, int32_t duration)](#oh_arkui_nativemodule_animationgroup_setduration) | 设置动画组的持续时间。<br> 动画组的持续时间作为未通过[OH_ArkUI_NativeModule_PropertyAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setduration)、 [OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setduration)或[OH_ArkUI_NativeModule_PathAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_setduration) 设置自身持续时间的子动画的默认持续时间。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetDuration(OH_ArkUI_AnimationGroupHandle group, int32_t *duration)](#oh_arkui_nativemodule_animationgroup_getduration) | 获取动画组的持续时间。 <br> 本接口仅返回在本动画组上显式设置的持续时间，不受子动画的持续时间影响。 如果本动画组未设置持续时间，则返回[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。运行时，未设置的动画组持续时间默认为**1000**毫秒。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetDelay(OH_ArkUI_AnimationGroupHandle group, int32_t delay)](#oh_arkui_nativemodule_animationgroup_setdelay) | 设置动画组的延迟时间。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetDelay(OH_ArkUI_AnimationGroupHandle group, int32_t *delay)](#oh_arkui_nativemodule_animationgroup_getdelay) | 获取动画组的延迟时间。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetCurve(OH_ArkUI_AnimationGroupHandle group, ArkUI_CurveHandle curve)](#oh_arkui_nativemodule_animationgroup_setcurve) | 设置动画组的动画曲线。 <br> 动画组的曲线作为未通过[OH_ArkUI_NativeModule_PropertyAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setcurve)、 [OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setcurve)或[OH_ArkUI_NativeModule_PathAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_setcurve) 设置自身曲线的子动画的默认曲线。 不支持<b>springMotion</b>、<b>responsiveSpringMotion</b>和<b>interpolatingSpring</b>曲线，因为这些曲线没有有效的持续时间设置。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetCurve(OH_ArkUI_AnimationGroupHandle group, ArkUI_CurveHandle *outBorrowedCurve)](#oh_arkui_nativemodule_animationgroup_getcurve) | 获取动画组的动画曲线。<br> 本接口仅返回在本动画组上显式设置的曲线，不受子动画的曲线影响。 如果本动画组未设置曲线，则返回[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 运行时，未设置的动画组曲线默认为[ARKUI_CURVE_LINEAR](capi-native-type-h.md#arkui_animationcurve)。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetTempo(OH_ArkUI_AnimationGroupHandle group, float tempo)](#oh_arkui_nativemodule_animationgroup_settempo) | 设置动画组的播放速率。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetTempo(OH_ArkUI_AnimationGroupHandle group, float *tempo)](#oh_arkui_nativemodule_animationgroup_gettempo) | 获取动画组的播放速率。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetAutoReverse(OH_ArkUI_AnimationGroupHandle group, bool autoReverse)](#oh_arkui_nativemodule_animationgroup_setautoreverse) | 设置动画组是否自动反转。<br> 启用自动反转后，动画组在每轮播放中交替正向播放和反向播放。默认值为<b>false</b>。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetAutoReverse(OH_ArkUI_AnimationGroupHandle group, bool *autoReverse)](#oh_arkui_nativemodule_animationgroup_getautoreverse) | 获取动画组是否启用自动反转。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetIterations(OH_ArkUI_AnimationGroupHandle group, int32_t iterations)](#oh_arkui_nativemodule_animationgroup_setiterations) | 设置动画组的播放次数。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetIterations(OH_ArkUI_AnimationGroupHandle group, int32_t *iterations)](#oh_arkui_nativemodule_animationgroup_getiterations) | 获取动画组的播放次数。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetExpectedFrameRateRange(OH_ArkUI_AnimationGroupHandle group, const ArkUI_ExpectedFrameRateRange *frameRate)](#oh_arkui_nativemodule_animationgroup_setexpectedframeraterange) | 设置动画组的期望帧率范围。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetExpectedFrameRateRange(OH_ArkUI_AnimationGroupHandle group, ArkUI_ExpectedFrameRateRange *frameRate)](#oh_arkui_nativemodule_animationgroup_getexpectedframeraterange) | 获取动画组的期望帧率范围。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_RegisterOnFinishCallback(OH_ArkUI_AnimationGroupHandle group, void *userData, void (\*callback)(void *userData))](#oh_arkui_nativemodule_animationgroup_registeronfinishcallback) | 注册动画组播放完成时的回调函数。 <br> 动画组只有一个完成回调。注册另一个回调会替换之前的回调和userData对。再次注册相同的回调和userData对会成功，但不会创建额外的注册。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode(OH_ArkUI_AnimationGroupHandle group, ArkUI_RenderNodeHandle targetNode)](#oh_arkui_nativemodule_animationgroup_settargetnode) | 设置动画组的默认目标渲染节点。 <br> 默认目标是被未通过[OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_settargetnode)、 [OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_settargetnode)或 [OH_ArkUI_NativeModule_PathAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_settargetnode)设置自身目标的子动画驱动的渲染节点。 在通过[OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup)注册动画组时，每个子动画必须解析为非NULL目标（自身的目标或动画组默认目标）； 任何解析后的目标必须属于动画组注册的同一UIContext。默认值为<b>NULL</b>。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetTargetNode(OH_ArkUI_AnimationGroupHandle group, ArkUI_RenderNodeHandle *outBorrowedTargetNode)](#oh_arkui_nativemodule_animationgroup_gettargetnode) | 获取动画组的默认目标渲染节点。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_AddPropertyAnimation(OH_ArkUI_AnimationGroupHandle group, OH_ArkUI_PropertyAnimationHandle animation)](#oh_arkui_nativemodule_animationgroup_addpropertyanimation) | 将属性动画添加到动画组中。<br> 动画的目标节点由[OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_settargetnode)确定； 如果未设置，则动画继承通过[OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode)设置的动画组默认目标。 在注册动画组时，每个子动画必须解析为非NULL目标。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_AddKeyframeAnimation(OH_ArkUI_AnimationGroupHandle group, OH_ArkUI_KeyframeAnimationHandle animation)](#oh_arkui_nativemodule_animationgroup_addkeyframeanimation) | 将关键帧动画添加到动画组中。 <br> 动画的目标节点由[OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_settargetnode)确定； 如果未设置，则动画继承通过[OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode)设置的动画组默认目标。 在注册动画组时，每个子动画必须解析为非NULL目标。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_AddPathAnimation(OH_ArkUI_AnimationGroupHandle group, OH_ArkUI_PathAnimationHandle animation)](#oh_arkui_nativemodule_animationgroup_addpathanimation) | 将路径动画添加到动画组中。 <br> 动画的目标节点由[OH_ArkUI_NativeModule_PathAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_settargetnode)确定； 如果未设置，则动画继承通过[OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode)设置的动画组默认目标。 在注册动画组时，每个子动画必须解析为非NULL目标。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_AddAnimationGroup(ArkUI_ContextHandle context, OH_ArkUI_AnimationGroupHandle group, const char *key)](#oh_arkui_nativemodule_addanimationgroup) | 在UIContext上以指定key注册动画组并开始播放。 <br> UIContext通过<b>key</b>拥有动画组：注册后，UIContext持有动画组的后端（运行时）对象，调用者可以在注册后销毁前端动画组句柄（及子动画句柄）， 因为后端通过(UIContext, key)独立运行。 key按UIContext（实例）划分作用域：不同UIContext中的相同key不会冲突。 在一个UIContext内，如果已用相同key注册了动画组，系统会先移除前一个动画组（释放其后端对象）再注册新动画组。 动画组随后通过相同的(UIContext, key)对进行标识和管理。 <br> 通过[OH_ArkUI_NativeModule_AnimationGroup_AddPropertyAnimation](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_addpropertyanimation)、 [OH_ArkUI_NativeModule_AnimationGroup_AddKeyframeAnimation](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_addkeyframeanimation)或 [OH_ArkUI_NativeModule_AnimationGroup_AddPathAnimation](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_addpathanimation)添加的每个子动画， 驱动由其自身<b>SetTargetNode</b>接口设置的目标节点；如果该目标未设置（或为<b>NULL</b>）， 则继承通过[OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode)设置的动画组默认目标。 注册时，每个子动画必须解析为非NULL目标节点（自身的或动画组默认的），且每个解析后的目标节点必须属于与<b>context</b>相同的UIContext； 否则返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 <br> 播放控制和生命周期接口（[OH_ArkUI_NativeModule_RemoveAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_removeanimationgroup)、 [OH_ArkUI_NativeModule_GetAnimationGroupState](capi-native-animate-h.md#oh_arkui_nativemodule_getanimationgroupstate)、 [OH_ArkUI_NativeModule_HasAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_hasanimationgroup)、 [OH_ArkUI_NativeModule_PauseAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_pauseanimationgroup)、 [OH_ArkUI_NativeModule_ResumeAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_resumeanimationgroup)、 [OH_ArkUI_NativeModule_FinishAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_finishanimationgroup)）均以(UIContext, key)对为键。 <br> finish回调（见[OH_ArkUI_NativeModule_AnimationGroup_RegisterOnFinishCallback](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_registeronfinishcallback)）仅触发一次， 由停止动画的事件触发——自然结束、[OH_ArkUI_NativeModule_FinishAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_finishanimationgroup)或目标节点销毁。 如果[OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup)返回错误，动画创建失败，finish回调不会被触发。 回调返回后，系统自动从UIContext移除动画组并释放动画组及其子动画的后端（运行时）对象； 前端句柄（动画组及其子动画）仍需由调用者通过[OH_ArkUI_NativeModule_AnimationGroup_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_destroy)、 [OH_ArkUI_NativeModule_PropertyAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_destroy)、 [OH_ArkUI_NativeModule_KeyframeAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_destroy)或[OH_ArkUI_NativeModule_PathAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_destroy)销毁。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_RemoveAnimationGroup(ArkUI_ContextHandle context, const char *key)](#oh_arkui_nativemodule_removeanimationgroup) | 从UIContext中移除指定key标识的动画组。 <br> 停止动画组（如果仍在运行）并释放动画组及其子动画的后端（运行时）对象。被动画的目标节点将恢复到动画开始时的状态。 前端句柄（动画组及其子动画）不会被本调用释放，需要由调用者通过[OH_ArkUI_NativeModule_AnimationGroup_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_destroy)、 [OH_ArkUI_NativeModule_PropertyAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_destroy)、 [OH_ArkUI_NativeModule_KeyframeAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_destroy)或[OH_ArkUI_NativeModule_PathAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_destroy)销毁。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_GetAnimationGroupState(ArkUI_ContextHandle context, const char *key, OH_ArkUI_AnimationGroupState *state)](#oh_arkui_nativemodule_getanimationgroupstate) | 获取UIContext上指定key标识的动画组的播放状态。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_HasAnimationGroup(ArkUI_ContextHandle context, const char *key, bool *exists)](#oh_arkui_nativemodule_hasanimationgroup) | 检查UIContext上是否存在指定key的动画组。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_PauseAnimationGroup(ArkUI_ContextHandle context, const char *key)](#oh_arkui_nativemodule_pauseanimationgroup) | 暂停UIContext上指定key标识的动画组。 <br> 调用此接口时动画组必须处于RUNNING状态；否则返回[ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ResumeAnimationGroup(ArkUI_ContextHandle context, const char *key)](#oh_arkui_nativemodule_resumeanimationgroup) | 恢复UIContext上指定key标识的动画组。<br> 调用此接口时动画组必须处于PAUSED状态；否则返回[ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_FinishAnimationGroup(ArkUI_ContextHandle context, const char *key, OH_ArkUI_AnimationFinishMode mode)](#oh_arkui_nativemodule_finishanimationgroup) | 结束UIContext上指定key标识的动画组。 <br> 根据指定的结束模式结束动画组：跳转到结束状态、跳转到起始状态或保持当前值。 动画组必须处于RUNNING或PAUSED状态；否则返回[ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

## 函数说明

### OH_ArkUI_AnimateOption_Create()

```c
ArkUI_AnimateOption* OH_ArkUI_AnimateOption_Create()
```

**描述：**

创建动画效果参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_AnimateOption*](capi-arkui-nativemodule-arkui-animateoption.md) | 新的动画效果参数指针。 |

### OH_ArkUI_AnimateOption_Dispose()

```c
void OH_ArkUI_AnimateOption_Dispose(ArkUI_AnimateOption* option)
```

**描述：**

销毁动画效果参数指针。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | 动画效果参数。 <br>option为NULL时，操作无效。 |

### OH_ArkUI_AnimateOption_GetDuration()

```c
uint32_t OH_ArkUI_AnimateOption_GetDuration(ArkUI_AnimateOption* option)
```

**描述：**

获取动画持续时间，单位为ms（毫秒）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | 动画效果参数。 <br>option为NULL时，返回0。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | 动画持续时间，单位为ms（毫秒）。option异常时返回0。 |

### OH_ArkUI_AnimateOption_GetTempo()

```c
float OH_ArkUI_AnimateOption_GetTempo(ArkUI_AnimateOption* option)
```

**描述：**

获取动画播放速度。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | 动画效果参数。 <br>option为NULL时，返回0.0。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| float | 动画播放速度。取值范围：[0, +∞)。option异常时返回0.0。 |

### OH_ArkUI_AnimateOption_GetCurve()

```c
ArkUI_AnimationCurve OH_ArkUI_AnimateOption_GetCurve(ArkUI_AnimateOption* option)
```

**描述：**

获取动画曲线。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | 动画效果参数。 <br>option为NULL时，返回-1。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_AnimationCurve | 动画曲线。返回值包括：ARKUI_CURVE_LINEAR（0，线性曲线）、ARKUI_CURVE_EASE（1，缓动曲线）、ARKUI_CURVE_EASE_IN（2，加速曲线）、      ARKUI_CURVE_EASE_OUT（3，减速曲线）、ARKUI_CURVE_EASE_IN_OUT（4，先加速后减速曲线）、ARKUI_CURVE_FAST_OUT_SLOW_IN（5，标准曲线）、      ARKUI_CURVE_LINEAR_OUT_SLOW_IN（6，减速曲线）、ARKUI_CURVE_FAST_OUT_LINEAR_IN（7，加速曲线）、ARKUI_CURVE_EXTREME_DECELERATION（8，      急减速曲线）、ARKUI_CURVE_SHARP（9，锐利曲线）、ARKUI_CURVE_RHYTHM（10，节奏曲线）、ARKUI_CURVE_SMOOTH（11，平滑曲线）、ARKUI_CURVE_FRICTION（12，      阻尼曲线）。option异常时返回-1。 |

### OH_ArkUI_AnimateOption_GetDelay()

```c
int32_t OH_ArkUI_AnimateOption_GetDelay(ArkUI_AnimateOption* option)
```

**描述：**

获取动画延迟播放时间，单位为ms（毫秒）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | 动画效果参数。 <br>option为NULL时，返回0。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 动画延迟播放时间，单位为ms（毫秒）。option异常时返回0。 |

### OH_ArkUI_AnimateOption_GetIterations()

```c
int32_t OH_ArkUI_AnimateOption_GetIterations(ArkUI_AnimateOption* option)
```

**描述：**

获取动画播放次数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | 动画效果参数。 <br>option为NULL时，返回0。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 动画播放次数。option异常时返回0。 |

### OH_ArkUI_AnimateOption_GetPlayMode()

```c
ArkUI_AnimationPlayMode OH_ArkUI_AnimateOption_GetPlayMode(ArkUI_AnimateOption* option)
```

**描述：**

获取动画播放模式。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | 动画效果参数。 <br>option为NULL时，返回-1。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_AnimationPlayMode | 动画播放模式。返回值包括：ARKUI_ANIMATION_PLAY_MODE_NORMAL（0，正向播放）、ARKUI_ANIMATION_PLAY_MODE_REVERSE（1，反向播放）、      ARKUI_ANIMATION_PLAY_MODE_ALTERNATE（2，交替播放）、ARKUI_ANIMATION_PLAY_MODE_ALTERNATE_REVERSE（3，反向交替播放）。option异常时返回-1。 |

### OH_ArkUI_AnimateOption_GetExpectedFrameRateRange()

```c
ArkUI_ExpectedFrameRateRange* OH_ArkUI_AnimateOption_GetExpectedFrameRateRange(ArkUI_AnimateOption* option)
```

**描述：**

获取动画的期望帧率，单位为帧/秒（fps）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | 动画效果参数。 <br>option为NULL时，返回NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ExpectedFrameRateRange*](capi-arkui-nativemodule-arkui-expectedframeraterange.md) | 动画的期望帧率，单位为帧/秒（fps）。option异常时返回NULL。 |

### OH_ArkUI_AnimateOption_SetDuration()

```c
void OH_ArkUI_AnimateOption_SetDuration(ArkUI_AnimateOption* option, int32_t value)
```

**描述：**

设置动画持续时间，单位为ms（毫秒）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | 动画效果参数。 <br>option为NULL时，操作无效。 |
| int32_t value | 动画持续时间，单位为ms（毫秒），默认值1000ms。取值范围：[0, +∞)。 <br>value小于0时，按0处理。 |

### OH_ArkUI_AnimateOption_SetTempo()

```c
void OH_ArkUI_AnimateOption_SetTempo(ArkUI_AnimateOption* option, float value)
```

**描述：**

设置动画播放速度。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | 动画效果参数。 <br>option为NULL时，操作无效。 |
| float value | 动画播放速度，默认值1.0。取值范围：[0, +∞)。 <br>**说明：**<br><br>传入小于0的数值，会默认设置为1。 |

### OH_ArkUI_AnimateOption_SetCurve()

```c
void OH_ArkUI_AnimateOption_SetCurve(ArkUI_AnimateOption* option, ArkUI_AnimationCurve value)
```

**描述：**

设置动画自定义曲线。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | 动画效果参数。 <br>option为NULL时，操作无效。 |
| ArkUI_AnimationCurve value | 动画曲线。默认值：[ARKUI_CURVE_EASE_IN_OUT](capi-native-type-h.md#arkui_animationcurve)，建议使用ARKUI_CURVE_EASE_IN_OUT获得更平滑的动画效果。 <br>value值异常时，设置无效。 <br>**说明：**若同时设置了[OH_ArkUI_AnimateOption_SetICurve](capi-native-animate-h.md#oh_arkui_animateoption_seticurve)，则SetICurve优先生效，本设置不生效。 |

### OH_ArkUI_AnimateOption_SetDelay()

```c
void OH_ArkUI_AnimateOption_SetDelay(ArkUI_AnimateOption* option, int32_t value)
```

**描述：**

设置动画延迟播放时间，单位为ms（毫秒）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | 动画效果参数。 <br>option为NULL时，操作无效。 |
| int32_t value | 动画延迟播放时间，单位为ms（毫秒）。取值范围：(-∞, +∞)。默认值：0，表示不延迟。value大于0时表示延迟播放，小于0表示提前播放。value小于0时，如果value的绝对值小于实际动画时长， 动画将在开始后第一帧直接运动到value绝对值的时刻的状态；如果value的绝对值大于等于实际动画时长，动画将在开始后第一帧直接运动到终点状态。其中实际动画时长等于单次动画时长乘以动画播放次数。 |

### OH_ArkUI_AnimateOption_SetIterations()

```c
void OH_ArkUI_AnimateOption_SetIterations(ArkUI_AnimateOption* option, int32_t value)
```

**描述：**

设置动画播放次数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | 动画效果参数。 <br>option为NULL时，操作无效。 |
| int32_t value | 动画播放次数。取值范围：[-1, +∞)，其中设置为0时不播放，-1表示无限次播放。默认值：1（播放一次）。 <br>value小于-1时，操作无效。 |

### OH_ArkUI_AnimateOption_SetPlayMode()

```c
void OH_ArkUI_AnimateOption_SetPlayMode(ArkUI_AnimateOption* option, ArkUI_AnimationPlayMode value)
```

**描述：**

设置动画播放模式。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | 动画效果参数。 <br>option为NULL时，操作无效。 |
| ArkUI_AnimationPlayMode value | 动画播放模式。默认值：[ARKUI_ANIMATION_PLAY_MODE_NORMAL](capi-native-type-h.md#arkui_animationplaymode)。ARKUI_ANIMATION_PLAY_MODE_NORMAL表示正向播放， ARKUI_ANIMATION_PLAY_MODE_REVERSE表示反向播放，ARKUI_ANIMATION_PLAY_MODE_ALTERNATE表示交替正反向播放， ARKUI_ANIMATION_PLAY_MODE_ALTERNATE_REVERSE表示交替反向和正向播放，奇数次反向，偶数次正向。 <br>value值异常时，操作无效。 |

### OH_ArkUI_AnimateOption_SetExpectedFrameRateRange()

```c
void OH_ArkUI_AnimateOption_SetExpectedFrameRateRange(ArkUI_AnimateOption* option, ArkUI_ExpectedFrameRateRange* value)
```

**描述：**

设置动画的期望帧率。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | 动画效果参数。 <br>option为NULL时，操作无效。 |
| [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md)* value | 动画的期望帧率，单位为帧/秒（fps）。 <br>value为NULL时，操作无效。 |

### OH_ArkUI_AnimateOption_SetICurve()

```c
void OH_ArkUI_AnimateOption_SetICurve(ArkUI_AnimateOption* option, ArkUI_CurveHandle value)
```

**描述：**

设置动画的插值曲线。

> **说明：**
>
> 此方法优先于[OH_ArkUI_AnimateOption_SetCurve](capi-native-animate-h.md#oh_arkui_animateoption_setcurve)生效。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | 动画效果参数。 <br>option为NULL时，操作无效。 |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) value | 动画曲线参数。 <br>value为NULL时，操作无效。 |

### OH_ArkUI_AnimateOption_GetICurve()

```c
ArkUI_CurveHandle OH_ArkUI_AnimateOption_GetICurve(ArkUI_AnimateOption* option)
```

**描述：**

获取动画的插值曲线。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option | 动画效果参数。 <br>option为NULL时，返回NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | 动画的插值曲线。参数option异常时返回NULL。 |

### OH_ArkUI_KeyframeAnimateOption_Create()

```c
ArkUI_KeyframeAnimateOption* OH_ArkUI_KeyframeAnimateOption_Create(int32_t size)
```

**描述：**

创建关键帧动画参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t size | 关键帧动画状态数。取值范围：[0, +∞)，需要为正整数才能产生动画效果。 <br>size小于0时返回NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_KeyframeAnimateOption*](capi-arkui-nativemodule-arkui-keyframeanimateoption.md) | 关键帧动画参数对象。size小于0时返回NULL，option异常时返回NULL。 |

### OH_ArkUI_KeyframeAnimateOption_Dispose()

```c
void OH_ArkUI_KeyframeAnimateOption_Dispose(ArkUI_KeyframeAnimateOption* option)
```

**描述：**

销毁关键帧动画参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | 关键帧动画参数对象。 <br>option为NULL时，操作无效。 |

### OH_ArkUI_KeyframeAnimateOption_SetDelay()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_SetDelay(ArkUI_KeyframeAnimateOption* option, int32_t value)
```

**描述：**

设置关键帧动画的整体延迟时间，单位为ms（毫秒），默认不延迟播放。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | 关键帧动画参数。 <br>option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| int32_t value | 动画延迟播放时间，单位为ms（毫秒）。取值范围：(-∞, +∞)。默认值：0，表示不延迟。value大于0为延迟播放，value小于0表示提前播放。对于value小于0的情况： 当value的绝对值小于实际动画时长，动画将在开始后第一帧直接运动到value绝对值的时刻的状态；当value的绝对值大于等于实际动画时长，动画将在开始后第一帧直接运动到终点状态。 其中实际动画时长等于单次动画时长乘以动画播放次数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。可能原因：option为NULL。解决措施：请确保option为有效的动画参数对象指针。 |

### OH_ArkUI_KeyframeAnimateOption_SetIterations()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_SetIterations(ArkUI_KeyframeAnimateOption* option, int32_t value)
```

**描述：**

设置关键帧动画播放次数。默认播放一次，设置为-1时表示无限次播放，设置为0时表示无动画效果。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | 关键帧动画参数。 <br>option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| int32_t value | 动画播放次数。取值范围：[-1, +∞)，其中设置为0时不播放，-1表示无限次播放。默认值：1，表示播放一次。 <br>value小于-1时，操作无效，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_KeyframeAnimateOption_RegisterOnFinishCallback()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_RegisterOnFinishCallback(ArkUI_KeyframeAnimateOption* option, void* userData, void (*onFinish)(void* userData))
```

**描述：**

设置关键帧动画播放完成回调。当关键帧动画[ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)所有次数播放完成后调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_KeyframeAnimateOption\* option | 关键帧动画参数。 <br>option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| void\* userData | 用户自定义对象指针。 <br>不涉及异常值处理。 |
| 回调函数。 | <br>userData：回调函数的入参，用户自定义对象指针。 <br>onFinish为NULL时，操作无效。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_KeyframeAnimateOption_SetExpectedFrameRate()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_SetExpectedFrameRate(ArkUI_KeyframeAnimateOption* option, ArkUI_ExpectedFrameRateRange* frameRate)
```

**描述：**

设置关键帧动画期望帧率。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | 关键帧动画参数。 <br>option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md)* frameRate | 关键帧动画的期望帧率。 <br>frameRate为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_KeyframeAnimateOption_SetDuration()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_SetDuration(ArkUI_KeyframeAnimateOption* option, int32_t value, int32_t index)
```

**描述：**

设置关键帧动画某段关键帧动画的持续时间，单位为ms（毫秒）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | 关键帧动画参数。 <br>option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| int32_t value | 关键帧动画的持续时间，单位为ms（毫秒），默认值1000ms。取值范围：[0, +∞)。 <br>value小于0时，按0处理。 |
| int32_t index | 状态索引值。取值范围：[0, size-1]，其中size为关键帧动画状态数。 <br>index超出范围时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_KeyframeAnimateOption_SetCurve()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_SetCurve(ArkUI_KeyframeAnimateOption* option, ArkUI_CurveHandle value, int32_t index)
```

**描述：**

设置关键帧动画某段关键帧使用的动画曲线。

> **说明：**
>
> 由于{@link springMotion}、{@link responsiveSpringMotion}、{@link interpolatingSpring}曲线时长不生效，故不支持这三种曲线。关键帧动画支持 {@link springCurve}和{@link customCurve}曲线。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | 关键帧动画参数。 <br>option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) value | 该关键帧使用的动画曲线。默认值：[ARKUI_CURVE_EASE_IN_OUT](capi-native-type-h.md#arkui_animationcurve)。 |
| int32_t index | 状态索引值。取值范围：[0, size-1]，其中size为关键帧动画状态数。 <br>index小于0或index超出范围时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_KeyframeAnimateOption_RegisterOnEventCallback()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_RegisterOnEventCallback(ArkUI_KeyframeAnimateOption* option, void* userData, void (*event)(void* userData), int32_t index)
```

**描述：**

设置关键帧时刻状态的闭包函数，即在该关键帧时刻要达到的状态。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_KeyframeAnimateOption\* option | 关键帧动画参数。 <br>option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| void (\*event)(void\* userData) | 闭包函数。 <br>userData：回调函数的入参，用户自定义对象指针。 <br>event为NULL时，操作无效。 |
| void\* userData | 用户定义对象指针。 <br>不涉及异常值处理。 |
| int32_t index | 状态索引值。取值范围：[0, size-1]，其中size为关键帧动画状态数。 <br>index小于0或index超出范围时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_KeyframeAnimateOption_GetDelay()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_GetDelay(ArkUI_KeyframeAnimateOption* option)
```

**描述：**

获取关键帧整体延迟时间，单位为ms（毫秒）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | 关键帧动画参数。 <br>option为NULL时，返回0。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 整体延迟时间，单位为ms（毫秒）。option异常时返回0。 |

### OH_ArkUI_KeyframeAnimateOption_GetIterations()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_GetIterations(ArkUI_KeyframeAnimateOption* option)
```

**描述：**

获取关键帧动画播放次数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | 关键帧动画参数。 <br>option为NULL时，返回0。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 动画播放次数。option异常时返回0。 |

### OH_ArkUI_KeyframeAnimateOption_GetExpectedFrameRate()

```c
ArkUI_ExpectedFrameRateRange* OH_ArkUI_KeyframeAnimateOption_GetExpectedFrameRate(ArkUI_KeyframeAnimateOption* option)
```

**描述：**

获取关键帧动画参数的期望帧率。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | 关键帧动画参数。 <br>option为NULL时，返回NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ExpectedFrameRateRange*](capi-arkui-nativemodule-arkui-expectedframeraterange.md) | 关键帧动画参数的期望帧率。option异常时返回NULL。 |

### OH_ArkUI_KeyframeAnimateOption_GetDuration()

```c
int32_t OH_ArkUI_KeyframeAnimateOption_GetDuration(ArkUI_KeyframeAnimateOption* option, int32_t index)
```

**描述：**

获取关键帧动画某段状态持续时间，单位为ms（毫秒）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | 关键帧动画参数。 <br>option为NULL时，返回0。 |
| int32_t index | 状态索引值。取值范围：[0, size-1]，其中size为关键帧动画状态数。 <br>index不在取值范围内时，返回0。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 持续时间，单位为ms（毫秒）。option异常时返回0。 |

### OH_ArkUI_KeyframeAnimateOption_GetCurve()

```c
ArkUI_CurveHandle OH_ArkUI_KeyframeAnimateOption_GetCurve(ArkUI_KeyframeAnimateOption* option, int32_t index)
```

**描述：**

获取关键帧动画某段状态动画曲线。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option | 关键帧动画参数。 <br>option为NULL时，返回NULL。 |
| int32_t index | 状态索引值。取值范围：[0, size-1]，其中size为关键帧动画状态数。 <br>index不在取值范围内时，返回NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | 动画曲线。参数异常时返回NULL。 |

### OH_ArkUI_AnimatorOption_Create()

```c
ArkUI_AnimatorOption* OH_ArkUI_AnimatorOption_Create(int32_t keyframeSize)
```

**描述：**

创建animator动画对象参数。

> **说明：**
>
> keyframeSize大于0时，动画插值起点默认是0，动画插值终点默认值是1。不支持设置。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t keyframeSize | 需要创建的关键帧个数。 <br>keyframeSize小于0时返回NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_AnimatorOption*](capi-arkui-nativemodule-arkui-animatoroption.md) | animator动画对象参数指针。keyframeSize小于0时返回NULL，option异常时返回NULL。 |

### OH_ArkUI_AnimatorOption_Dispose()

```c
void OH_ArkUI_AnimatorOption_Dispose(ArkUI_AnimatorOption* option)
```

**描述：**

销毁animator动画对象参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画对象参数。 <br>option为NULL时，操作无效。 |

### OH_ArkUI_AnimatorOption_SetDuration()

```c
int32_t OH_ArkUI_AnimatorOption_SetDuration(ArkUI_AnimatorOption* option, int32_t value)
```

**描述：**

设置animator动画播放的时长，单位为ms（毫秒）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画对象参数。 <br>option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| int32_t value | 播放的时长，单位为ms（毫秒），默认值0ms。取值范围：[0, +∞)。 <br>value小于0时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_AnimatorOption_SetDelay()

```c
int32_t OH_ArkUI_AnimatorOption_SetDelay(ArkUI_AnimatorOption* option, int32_t value)
```

**描述：**

设置animator动画延迟播放的时间，单位为ms（毫秒）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画对象参数。 <br>option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| int32_t value | 动画延迟播放时间，单位为ms（毫秒）。取值范围：(-∞, +∞)。默认值：0，表示不延迟。value大于0为延迟播放，value小于0表示提前播放。对于value小于0的情况： 当value的绝对值小于实际动画时长，动画将在开始后第一帧直接运动到value绝对值的时刻的状态；当value的绝对值大于等于实际动画时长，动画将在开始后第一帧直接运动到终点状态。 其中实际动画时长等于单次动画时长乘以动画播放次数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_AnimatorOption_SetIterations()

```c
int32_t OH_ArkUI_AnimatorOption_SetIterations(ArkUI_AnimatorOption* option, int32_t value)
```

**描述：**

设置animator动画播放次数。默认播放一次，设置为-1时表示无限次播放，设置为0时表示无动画效果。

> **说明：**
>
> 设置为除-1外其他负数视为无效取值，无效取值动画默认播放1次。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画对象参数。 <br>option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| int32_t value | 取值范围：[-1, +∞)，其中设置为0时不播放，-1表示无限次播放。默认值：1（播放一次）。 <br>value小于-1时，操作无效。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_AnimatorOption_SetFill()

```c
int32_t OH_ArkUI_AnimatorOption_SetFill(ArkUI_AnimatorOption* option, ArkUI_AnimationFillMode value)
```

**描述：**

设置组件在动画开始前和结束后保持的状态。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画对象参数。 <br>option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| ArkUI_AnimationFillMode value | 动画执行时组件在动画开始前和结束后的状态。默认值：[ARKUI_ANIMATION_FILL_MODE_FORWARDS](capi-native-type-h.md#arkui_animationfillmode)。 <br>ARKUI_ANIMATION_FILL_MODE_NONE（0）表示动画前后均恢复初始状态，ARKUI_ANIMATION_FILL_MODE_FORWARDS（1）表示动画结束后保持终点状态， ARKUI_ANIMATION_FILL_MODE_BACKWARDS（2）表示动画开始前保持起点状态，ARKUI_ANIMATION_FILL_MODE_BOTH（3）表示动画前后均保持对应状态。 <br>value小于0时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_AnimatorOption_SetDirection()

```c
int32_t OH_ArkUI_AnimatorOption_SetDirection(ArkUI_AnimatorOption* option, ArkUI_AnimationDirection value)
```

**描述：**

设置animator动画播放方向。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画对象参数。 <br>option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| ArkUI_AnimationDirection value | 动画播放方向。默认值：[ARKUI_ANIMATION_DIRECTION_NORMAL](capi-native-type-h.md#arkui_animationdirection)。 <br>ARKUI_ANIMATION_DIRECTION_NORMAL（0）表示正向播放，ARKUI_ANIMATION_DIRECTION_REVERSE（1）表示反向播放， ARKUI_ANIMATION_DIRECTION_ALTERNATE（2）表示交替正向和反向播放，奇数次正向，偶数次反向，ARKUI_ANIMATION_DIRECTION_ALTERNATE_REVERSE（3） 表示交替反向和正向播放，奇数次反向，偶数次正向。 <br>value超出取值范围时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_AnimatorOption_SetCurve()

```c
int32_t OH_ArkUI_AnimatorOption_SetCurve(ArkUI_AnimatorOption* option, ArkUI_CurveHandle value)
```

**描述：**

设置animator动画插值曲线。

> **说明：**
>
> 不支持{@link springCurve}、{@link springMotion}、{@link responsiveSpringMotion}、{@link interpolatingSpring}、 {@link customCurve}动画曲线。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画对象参数。 <br>option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) value | 动画插值曲线。默认值：[ARKUI_CURVE_LINEAR](capi-native-type-h.md#arkui_animationcurve)，建议使用[ARKUI_CURVE_EASE_IN_OUT](capi-native-type-h.md#arkui_animationcurve)获得更平滑的动画效果。 <br>value为NULL时，使用默认曲线[ARKUI_CURVE_LINEAR](capi-native-type-h.md#arkui_animationcurve)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_AnimatorOption_SetBegin()

```c
int32_t OH_ArkUI_AnimatorOption_SetBegin(ArkUI_AnimatorOption* option, float value)
```

**描述：**

设置animator动画插值起点。

> **说明：**
>
> 当animator动画为关键帧动画时，此方法返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画对象参数。 <br>option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| float value | 动画插值起点，默认值0.0。取值范围：(-∞, +∞)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_AnimatorOption_SetEnd()

```c
int32_t OH_ArkUI_AnimatorOption_SetEnd(ArkUI_AnimatorOption* option, float value)
```

**描述：**

设置animator动画插值终点。

> **说明：**
>
> 当animator动画为关键帧动画时，此方法返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画对象参数。 <br>option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| float value | 动画插值终点。取值范围：(-∞, +∞)。默认值：1。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_AnimatorOption_SetExpectedFrameRateRange()

```c
int32_t OH_ArkUI_AnimatorOption_SetExpectedFrameRateRange(ArkUI_AnimatorOption* option, ArkUI_ExpectedFrameRateRange* value)
```

**描述：**

设置animator动画期望的帧率范围。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画对象参数。 <br>option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md)* value | 期望的帧率范围对象。 <br>value为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_AnimatorOption_SetKeyframe()

```c
int32_t OH_ArkUI_AnimatorOption_SetKeyframe(ArkUI_AnimatorOption* option, float time, float value, int32_t index)
```

**描述：**

设置animator动画关键帧参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画对象参数。 <br>option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| float time | 关键帧时间。取值范围：[0, 1], 各关键帧时间必须依次递增，即后一关键帧的time值大于前一关键帧的time值。默认值：按索引均匀分布（如第1帧为0.0，第2帧为0.5，第3帧为1.0）。 <br>time小于0或time大于1时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| float value | 关键帧对应的插值目标值，表示动画在该关键帧时刻要达到的属性值。取值范围：(-∞, +∞)。 |
| int32_t index | 关键帧的索引值。 <br>index小于0时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_AnimatorOption_SetKeyframeCurve()

```c
int32_t OH_ArkUI_AnimatorOption_SetKeyframeCurve(ArkUI_AnimatorOption* option, ArkUI_CurveHandle value, int32_t index)
```

**描述：**

设置animator动画关键帧曲线类型。

> **说明：**
>
> 不支持{@link springCurve}、{@link springMotion}、{@link responsiveSpringMotion}、{@link interpolatingSpring}、 {@link customCurve}动画曲线。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画对象参数。 <br>option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) value | 动画插值曲线。默认值：NULL，表示线性插值。 |
| int32_t index | 关键帧的索引值。取值范围：[0, keyframeSize-1]，其中keyframeSize为关键帧个数。 <br>index超出取值范围时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_AnimatorOption_GetDuration()

```c
int32_t OH_ArkUI_AnimatorOption_GetDuration(ArkUI_AnimatorOption* option)
```

**描述：**

获取animator动画播放的时长，单位为ms（毫秒）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画参数。 <br>option为NULL时，返回-1。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 动画播放的时长，单位为ms（毫秒）。option异常时返回0。 |

### OH_ArkUI_AnimatorOption_GetDelay()

```c
int32_t OH_ArkUI_AnimatorOption_GetDelay(ArkUI_AnimatorOption* option)
```

**描述：**

获取animator动画延迟播放时长，单位为ms（毫秒）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画参数。option为NULL时，返回0。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 动画延迟播放时长，单位为ms（毫秒）。option异常时返回0。 |

### OH_ArkUI_AnimatorOption_GetIterations()

```c
int32_t OH_ArkUI_AnimatorOption_GetIterations(ArkUI_AnimatorOption* option)
```

**描述：**

获取animator动画播放次数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画对象参数。option为NULL时，返回0。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 动画播放次数。option异常时返回0。 |

### OH_ArkUI_AnimatorOption_GetFill()

```c
ArkUI_AnimationFillMode OH_ArkUI_AnimatorOption_GetFill(ArkUI_AnimatorOption* option)
```

**描述：**

获取animator动画执行时组件在动画开始前和结束后的状态。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画参数。option为NULL时，返回-1。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_AnimationFillMode | 动画执行时组件在动画开始前和结束后的状态。返回值包括：ARKUI_ANIMATION_FILL_MODE_NONE（0，播放完成后恢复初始状态）、ARKUI_ANIMATION_FILL_MODE_FORWARDS（      1，播放完成后保持终点状态）、ARKUI_ANIMATION_FILL_MODE_BACKWARDS（2，延时播放时保持起点状态）、ARKUI_ANIMATION_FILL_MODE_BOTH（3，      同时应用FORWARDS和BACKWARDS效果）。option异常时返回-1。 |

### OH_ArkUI_AnimatorOption_GetDirection()

```c
ArkUI_AnimationDirection OH_ArkUI_AnimatorOption_GetDirection(ArkUI_AnimatorOption* option)
```

**描述：**

获取animator动画播放方向。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画参数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_AnimationDirection | 动画播放方向。返回值包括：ARKUI_ANIMATION_DIRECTION_NORMAL（0，正向播放）、ARKUI_ANIMATION_DIRECTION_REVERSE（1，反向播放）、      ARKUI_ANIMATION_DIRECTION_ALTERNATE（2，交替正向和反向播放，奇数次正向，偶数次反向）、ARKUI_ANIMATION_DIRECTION_ALTERNATE_REVERSE（3，      交替反向和正向播放，奇数次反向，偶数次正向）。option异常时返回-1。 |

### OH_ArkUI_AnimatorOption_GetCurve()

```c
ArkUI_CurveHandle OH_ArkUI_AnimatorOption_GetCurve(ArkUI_AnimatorOption* option)
```

**描述：**

获取animator动画插值曲线。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画参数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | 动画插值曲线。option异常时返回NULL。 |

### OH_ArkUI_AnimatorOption_GetBegin()

```c
float OH_ArkUI_AnimatorOption_GetBegin(ArkUI_AnimatorOption* option)
```

**描述：**

获取animator动画插值起点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画参数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| float | 动画插值起点。option异常时返回0.0。 |

### OH_ArkUI_AnimatorOption_GetEnd()

```c
float OH_ArkUI_AnimatorOption_GetEnd(ArkUI_AnimatorOption* option)
```

**描述：**

获取animator动画插值终点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画参数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| float | 动画插值终点。option异常时返回0.0。 |

### OH_ArkUI_AnimatorOption_GetExpectedFrameRateRange()

```c
ArkUI_ExpectedFrameRateRange* OH_ArkUI_AnimatorOption_GetExpectedFrameRateRange(ArkUI_AnimatorOption* option)
```

**描述：**

获取animator动画期望的帧率范围。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画对象参数。option为NULL时，返回NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ExpectedFrameRateRange*](capi-arkui-nativemodule-arkui-expectedframeraterange.md) | 期望的帧率范围对象指针。函数参数异常时返回NULL。 |

### OH_ArkUI_AnimatorOption_GetKeyframeTime()

```c
float OH_ArkUI_AnimatorOption_GetKeyframeTime(ArkUI_AnimatorOption* option, int32_t index)
```

**描述：**

获取animator动画关键帧时间，取值范围[0, 1]，为归一化时间比例。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画对象参数。 |
| int32_t index | 关键帧的索引值。取值范围：[0, keyframeSize-1]，其中keyframeSize为关键帧个数。 <br>index超出范围时，返回NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| float | 关键帧时间，取值范围[0, 1]，为归一化时间比例。 |

### OH_ArkUI_AnimatorOption_GetKeyframeValue()

```c
float OH_ArkUI_AnimatorOption_GetKeyframeValue(ArkUI_AnimatorOption* option, int32_t index)
```

**描述：**

获取animator动画关键帧数值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画对象参数。option为NULL时，返回0.0。 |
| int32_t index | 关键帧的索引值。取值范围：[0, keyframeSize-1]，其中keyframeSize为关键帧个数。 <br>index超出范围时，返回0.0。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| float | 关键帧数值。 |

### OH_ArkUI_AnimatorOption_GetKeyframeCurve()

```c
ArkUI_CurveHandle OH_ArkUI_AnimatorOption_GetKeyframeCurve(ArkUI_AnimatorOption* option, int32_t index)
```

**描述：**

获取animator动画关键帧动画插值曲线。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画对象参数。option为NULL时，返回空指针。 |
| int32_t index | 关键帧的索引值。取值范围：[0, keyframeSize-1]，其中keyframeSize为关键帧个数。 <br>index超出范围时，返回空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | 动画插值曲线。函数参数异常时返回NULL。 |

### OH_ArkUI_AnimatorEvent_GetUserData()

```c
void* OH_ArkUI_AnimatorEvent_GetUserData(ArkUI_AnimatorEvent* event)
```

**描述：**

获取动画事件对象中的用户自定义对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorEvent](capi-arkui-nativemodule-arkui-animatorevent.md)* event | 动画事件对象。event为NULL时，返回NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| void* | 用户自定义对象。 |

### OH_ArkUI_AnimatorOnFrameEvent_GetUserData()

```c
void* OH_ArkUI_AnimatorOnFrameEvent_GetUserData(ArkUI_AnimatorOnFrameEvent* event)
```

**描述：**

获取动画的帧事件中的用户自定义对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOnFrameEvent](capi-arkui-nativemodule-arkui-animatoronframeevent.md)* event | 动画事件对象。event为NULL时，返回NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| void* | 用户自定义对象。 |

### OH_ArkUI_AnimatorOnFrameEvent_GetValue()

```c
float OH_ArkUI_AnimatorOnFrameEvent_GetValue(ArkUI_AnimatorOnFrameEvent* event)
```

**描述：**

获取动画帧回调事件对象中的插值结果。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorOnFrameEvent](capi-arkui-nativemodule-arkui-animatoronframeevent.md)* event | 动画事件对象。event为NULL时，返回0.0。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| float | 动画插值结果。      <br>说明：      <br>在动画过程中，插值结果根据动画参数在插值起点[OH_ArkUI_AnimatorOption_SetBegin](capi-native-animate-h.md#oh_arkui_animatoroption_setbegin)和插值终点[OH_ArkUI_AnimatorOption_SetEnd](capi-native-animate-h.md#oh_arkui_animatoroption_setend)间变化。 |

### OH_ArkUI_AnimatorOption_RegisterOnFrameCallback()

```c
int32_t OH_ArkUI_AnimatorOption_RegisterOnFrameCallback(ArkUI_AnimatorOption* option, void* userData, void (*callback)(ArkUI_AnimatorOnFrameEvent* event))
```

**描述：**

设置animator动画接收到帧时回调。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_AnimatorOption\* option | animator动画对象参数。option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| void\* userData | 用户自定义参数。 |
| 回调函数。 | <br>- event：回调函数的入参，动画事件对象。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_AnimatorOption_RegisterOnFinishCallback()

```c
int32_t OH_ArkUI_AnimatorOption_RegisterOnFinishCallback(ArkUI_AnimatorOption* option, void* userData, void (*callback)(ArkUI_AnimatorEvent* event))
```

**描述：**

设置animator动画完成时回调。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_AnimatorOption\* option | animator动画对象参数。option为NULL时，返回[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| void\* userData | 用户自定义参数。 |
| 回调函数。 | <br>- event：回调函数的入参，动画事件对象。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_AnimatorOption_RegisterOnCancelCallback()

```c
int32_t OH_ArkUI_AnimatorOption_RegisterOnCancelCallback(ArkUI_AnimatorOption* option, void* userData, void (*callback)(ArkUI_AnimatorEvent* event))
```

**描述：**

设置animator动画被取消时回调。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_AnimatorOption\* option | animator动画对象参数。option为NULL时，返回 [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| void\* userData | 用户自定义参数。 |
| 回调函数。 | <br>- event：回调函数的入参，动画事件对象。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_AnimatorOption_RegisterOnRepeatCallback()

```c
int32_t OH_ArkUI_AnimatorOption_RegisterOnRepeatCallback(ArkUI_AnimatorOption* option, void* userData, void (*callback)(ArkUI_AnimatorEvent* event))
```

**描述：**

设置animator动画重复时回调。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_AnimatorOption\* option | animator动画对象参数。option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| void\* userData | 用户自定义参数。 |
| 回调函数。 | <br>- event：回调函数的入参，动画事件对象。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_Animator_ResetAnimatorOption()

```c
int32_t OH_ArkUI_Animator_ResetAnimatorOption(ArkUI_AnimatorHandle animatorHandle, ArkUI_AnimatorOption* option)
```

**描述：**

重置animator动画的配置参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | animator动画对象。 <br>animatorHandle为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option | animator动画参数。 <br>option为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_Animator_Play()

```c
int32_t OH_ArkUI_Animator_Play(ArkUI_AnimatorHandle animatorHandle)
```

**描述：**

启动animator动画。需要在主线程上调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | animator动画对象。animatorHandle为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_Animator_Finish()

```c
int32_t OH_ArkUI_Animator_Finish(ArkUI_AnimatorHandle animatorHandle)
```

**描述：**

结束animator动画，动画将跳到终点状态后停止。与[OH_ArkUI_Animator_Cancel](capi-native-animate-h.md#oh_arkui_animator_cancel)的区别：Cancel会立即中断动画并回到初始状态，Finish会让动画直接跳到终点状态后停止。 需要在主线程上调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | animator动画对象。animatorHandle为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_Animator_Pause()

```c
int32_t OH_ArkUI_Animator_Pause(ArkUI_AnimatorHandle animatorHandle)
```

**描述：**

暂停animator动画。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | animator动画对象。animatorHandle为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_Animator_Cancel()

```c
int32_t OH_ArkUI_Animator_Cancel(ArkUI_AnimatorHandle animatorHandle)
```

**描述：**

取消animator动画。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | animator动画对象。animatorHandle为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_Animator_Reverse()

```c
int32_t OH_ArkUI_Animator_Reverse(ArkUI_AnimatorHandle animatorHandle)
```

**描述：**

以相反的顺序播放animator动画。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | animator动画对象。animatorHandle为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_Curve_CreateCurveByType()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateCurveByType(ArkUI_AnimationCurve curve)
```

**描述：**

插值曲线的初始化函数，可以根据入参创建一个插值曲线对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AnimationCurve curve | 曲线类型。curve值异常时，返回NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | 插值曲线对象指针，用于动画属性值的插值计算。curve值异常时返回NULL。 |

### OH_ArkUI_Curve_CreateStepsCurve()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateStepsCurve(int32_t count, bool end)
```

**描述：**

构造阶梯曲线对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t count | 阶梯的数量，需要为正整数，取值范围：[1, +∞)。 <br>count值异常时，操作无效。 |
| bool end | 在每个间隔的起点或是终点发生阶跃变化。true：在终点发生阶跃变化。false：在起点发生阶跃变化。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | 阶梯曲线对象指针。如果参数异常返回NULL。 |

### OH_ArkUI_Curve_CreateCubicBezierCurve()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateCubicBezierCurve(float x1, float y1, float x2, float y2)
```

**描述：**

构造三阶贝塞尔曲线对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| float x1 | 确定贝塞尔曲线第一点横坐标，取值范围：[0, 1]。设置的值小于0时，按0处理；设置的值大于1时，按1处理。 |
| float y1 | 确定贝塞尔曲线第一点纵坐标。取值范围：(-∞, +∞)。 |
| float x2 | 确定贝塞尔曲线第二点横坐标，取值范围：[0, 1]。设置的值小于0时，按0处理；设置的值大于1时，按1处理。 |
| float y2 | 确定贝塞尔曲线第二点纵坐标。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | 三阶贝塞尔曲线对象指针。 |

### OH_ArkUI_Curve_CreateSpringCurve()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateSpringCurve(float velocity, float mass, float stiffness, float damping)
```

**描述：**

构造弹簧曲线对象，曲线形状由弹簧参数决定，动画时长受动画参数中的时长参数控制。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| float velocity | 初始速度。是由外部因素对弹性动效产生的影响参数，其目的是保证对象从之前的运动状态平滑地过渡到弹性动效。该速度是归一化速度，其值等于动画开始时的实际速度除以动画属性改变值。 |
| float mass | 质量。弹性系统的受力对象，会对弹性系统产生惯性影响。质量越大，震荡的幅度越大，恢复到平衡位置的速度越慢。取值范围：[0, +∞)。 <br>value小于等于0时，按1处理。 |
| float stiffness | 刚度。是物体抵抗施加的力而形变的程度。在弹性系统中，刚度越大，抵抗变形的能力越强，恢复到平衡位置的速度就越快。取值范围：[0, +∞)。 <br>value小于等于0时，按1处理。 |
| float damping | 阻尼。用于描述系统在受到扰动后震荡及衰减的情形。阻尼越大，弹性运动的震荡次数越少、震荡幅度越小。取值范围：[0, +∞)。 <br>value小于等于0时，按1处理。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | 插值器弹簧曲线的插值对象指针，用于基于弹簧物理模型进行插值计算，生成从0到1的动画曲线。如果参数异常返回NULL。 |

### OH_ArkUI_Curve_CreateSpringMotion()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateSpringMotion(float response, float dampingFraction, float overlapDuration)
```

**描述：**

构造弹性动画曲线对象。如果对同一对象的同一属性进行多个弹性动画，每个动画会替换掉前一个动画，并继承之前的速度。

> **说明：**
>
> 动画时间由曲线参数决定，不受{@link animation}、[animateTo](capi-arkui-nativemodule-arkui-nativeanimateapi-1.md#animateto)中的duration参数控制。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| float response | 弹簧自然振动周期，决定弹簧复位的速度，单位为s（秒）。取值范围：(0, +∞)。 <br>参数小于等于0时，按0.55处理。 |
| float dampingFraction | 阻尼系数。大于0小于1的值为欠阻尼，运动过程中会超出目标值；等于1为临界阻尼；大于1为过阻尼，运动过程中逐渐趋于目标值。取值范围：(0, +∞)。 <br>参数小于等于0时，按0.825处理。 |
| float overlapDuration | 弹性动画衔接时长，单位为s（秒）。发生动画继承时，如果前后两个弹性动画response不一致，response参数会在overlapDuration时间内平滑过渡。取值范围：[0, +∞) 。 <br>参数小于0时，按0处理。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | 弹性动画曲线的插值对象指针，使用响应式参数构造曲线，支持动画间的速度继承。如果参数异常返回NULL。 |

### OH_ArkUI_Curve_CreateResponsiveSpringMotion()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateResponsiveSpringMotion(float response, float dampingFraction, float overlapDuration)
```

**描述：**

构造弹性跟手动画曲线对象，是springMotion的一种特例，仅默认参数不同，可与springMotion混合使用。

> **说明：**
>
> 动画时间由曲线参数决定，不受{@link animation}、[animateTo](capi-arkui-nativemodule-arkui-nativeanimateapi-1.md#animateto)中的duration参数控制。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| float response | 弹簧自然振动周期，决定弹簧复位的速度，单位为s（秒）。取值范围：(0, +∞)。 <br>参数小于等于0时，按0.15处理。 |
| float dampingFraction | 阻尼系数。大于0小于1的值为欠阻尼，运动过程中会超出目标值；等于1为临界阻尼；大于1为过阻尼，运动过程中逐渐趋于目标值。取值范围：[0, +∞)。 <br>参数小于0时，按0.86处理。 |
| float overlapDuration | 弹性动画衔接时长，单位为s（秒）。发生动画继承时，如果前后两个弹性动画response不一致，response参数会在overlapDuration时间内平滑过渡。取值范围：[0, +∞) 。 <br>参数小于0时，按0.25处理。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | 响应式弹簧动画曲线的插值对象指针，是springMotion的一种特例，仅默认参数不同。如果参数异常返回NULL。 |

### OH_ArkUI_Curve_CreateInterpolatingSpring()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateInterpolatingSpring(float velocity, float mass, float stiffness, float damping)
```

**描述：**

构造插值器弹簧曲线对象，生成一条从0到1的动画曲线，实际动画值根据曲线进行插值计算。

> **说明：**
>
> 动画时间由曲线参数决定，不受{@link animation}、[animateTo](capi-arkui-nativemodule-arkui-nativeanimateapi-1.md#animateto)中的duration参数控制。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| float velocity | 初始速度。外部因素对弹性动效产生的影响参数，目的是保证对象从之前的运动状态平滑地过渡到弹性动效。该速度是归一化速度，其值等于动画开始时的实际速度除以动画属性改变值。取值范围：(-∞, +∞)。 |
| float mass | 质量。弹性系统的受力对象，会对弹性系统产生惯性影响。质量越大，震荡的幅度越大，恢复到平衡位置的速度越慢。取值范围：[0, +∞)。 <br>value小于等于0时，按1处理。 |
| float stiffness | 刚度。表示物体抵抗施加的力而形变的程度。刚度越大，抵抗变形的能力越强，恢复到平衡位置的速度越快。取值范围：[0, +∞)。 <br>value小于等于0时，按1处理。 |
| float damping | 阻尼。用于描述系统在受到扰动后震荡及衰减的情形。阻尼越大，弹性运动的震荡次数越少、震荡幅度越小。取值范围：[0, +∞)。 <br>value小于等于0时，按1处理。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | 曲线的插值对象指针。如果参数异常返回NULL。 |

### OH_ArkUI_Curve_CreateCustomCurve()

```c
ArkUI_CurveHandle OH_ArkUI_Curve_CreateCustomCurve(void* userData, float (*interpolate)(float fraction, void* userdata))
```

**描述：**

构造自定义曲线对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| oid\* userData | 用户自定义数据。 |
| float (\*interpolate)(float fraction | 用户自定义的插值回调函数。fraction为动画开始时的插值输入x值。取值范围：[0,1]。返回值为曲线的y值。取值范围：[0,1]。fraction等于0时， 返回值为0对应动画起点，返回不为0，动画在起点处有跳变效果。fraction等于1时，返回值为1对应动画终点，返回值不为1将导致动画的终值不是状态变量的值，出现 大于或者小于状态变量值，再跳变到状态变量值的效果。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) | 曲线的插值对象指针。如果参数异常返回NULL。 |

### OH_ArkUI_Curve_DisposeCurve()

```c
void OH_ArkUI_Curve_DisposeCurve(ArkUI_CurveHandle curveHandle)
```

**描述：**

销毁自定义曲线对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) curveHandle | 曲线的插值对象指针。 <br>curveHandle为NULL时，操作无效。 |

### OH_ArkUI_CreateOpacityTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateOpacityTransitionEffect(float opacity)
```

**描述：**

创建组件转场时的透明度效果对象。

> **说明：**
>
> 设置小于0的非法值按0处理，大于1的非法值按1处理。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| float opacity | 透明度，取值范围为[0, 1]。默认值为1。设置小于0的非法值按0处理，大于1的非法值按1处理，1表示不透明，0表示完全透明。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_TransitionEffect*](capi-arkui-nativemodule-arkui-transitioneffect.md) | 组件转场时的透明度效果对象。 |

### OH_ArkUI_CreateTranslationTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateTranslationTransitionEffect(ArkUI_TranslationOptions* translate)
```

**描述：**

创建组件转场时的平移效果对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_TranslationOptions* translate | 组件转场时的平移参数对象。 <br>translate为NULL时，返回NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_TransitionEffect*](capi-arkui-nativemodule-arkui-transitioneffect.md) | 组件转场时的平移效果对象。如果参数异常返回NULL。 |

### OH_ArkUI_CreateScaleTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateScaleTransitionEffect(ArkUI_ScaleOptions* scale)
```

**描述：**

创建组件转场时的缩放效果对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_ScaleOptions* scale | 组件转场时的缩放参数对象。scale为NULL时，返回NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_TransitionEffect*](capi-arkui-nativemodule-arkui-transitioneffect.md) | 组件转场时的缩放效果对象。如果参数异常返回NULL。 |

### OH_ArkUI_CreateRotationTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateRotationTransitionEffect(ArkUI_RotationOptions* rotate)
```

**描述：**

创建组件转场时的旋转效果对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_RotationOptions* rotate | 组件转场时的旋转参数对象。rotate为NULL时，返回NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_TransitionEffect*](capi-arkui-nativemodule-arkui-transitioneffect.md) | 组件转场时的旋转效果对象。如果参数异常返回NULL。 |

### OH_ArkUI_CreateMovementTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateMovementTransitionEffect(ArkUI_TransitionEdge edge)
```

**描述：**

创建组件平移效果对象，通过指定边缘方向（上、下、左、右）控制组件的滑入滑出方向，适用于仅需指定滑动方向的简单场景。与OH_ArkUI_CreateTranslationTransitionEffect不同： 后者支持自定义x/y/z方向的精确平移参数，适用于需要指定具体位移距离的场景。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_TransitionEdge edge | 组件平移的方向类型，决定组件出现和消失时的平移方向。edge值异常时，按[ARKUI_TRANSITION_EDGE_START](capi-native-type-h.md#arkui_transitionedge)处理。 <br>ARKUI_TRANSITION_EDGE_TOP（0）表示从上方滑入/滑出，ARKUI_TRANSITION_EDGE_BOTTOM（1）表示从下方滑入/滑出，ARKUI_TRANSITION_EDGE_START（ 2）表示从左侧滑入/滑出，ARKUI_TRANSITION_EDGE_END（3）表示从右侧滑入/滑出。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_TransitionEffect*](capi-arkui-nativemodule-arkui-transitioneffect.md) | 组件转场时的平移效果对象。如果参数异常返回NULL。 |

### OH_ArkUI_CreateAsymmetricTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateAsymmetricTransitionEffect(ArkUI_TransitionEffect* appear, ArkUI_TransitionEffect* disappear)
```

**描述：**

创建非对称的转场效果对象。

> **说明：**
>
> 如果不通过该函数构造[ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)，则表明该效果在组件出现和消失时均生效。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* appear | 组件出现时的转场效果。appear为NULL时，返回NULL。 |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* disappear | 组件消失时的转场效果。disappear为NULL时，返回NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_TransitionEffect*](capi-arkui-nativemodule-arkui-transitioneffect.md) | 非对称的转场效果对象。如果参数异常返回NULL。 |

### OH_ArkUI_CreateIdentityTransitionEffect()

```c
ArkUI_TransitionEffect* OH_ArkUI_CreateIdentityTransitionEffect(void)
```

**描述：**

创建无转场效果对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_TransitionEffect*](capi-arkui-nativemodule-arkui-transitioneffect.md) | 创建的无转场效果对象指针。调用者需要调用[OH_ArkUI_TransitionEffect_Dispose](capi-native-animate-h.md#oh_arkui_transitioneffect_dispose)释放该对象。 |

### OH_ArkUI_TransitionEffect_Dispose()

```c
void OH_ArkUI_TransitionEffect_Dispose(ArkUI_TransitionEffect* effect)
```

**描述：**

销毁转场效果对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* effect | 转场效果对象。 <br>effect为NULL时，操作无效。 |

### OH_ArkUI_TransitionEffect_Combine()

```c
int32_t OH_ArkUI_TransitionEffect_Combine(ArkUI_TransitionEffect* firstEffect, ArkUI_TransitionEffect* secondEffect)
```

**描述：**

设置转场效果链式组合，以形成包含多种转场效果的TransitionEffect。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* firstEffect | 链式组合的前一个转场效果，将与secondEffect组合形成包含多种转场效果的TransitionEffect。 <br>firstEffect为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* secondEffect | 需要组合的后一个转场效果，将与firstEffect链式组合形成包含多种转场效果的TransitionEffect。 <br>secondEffect为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TransitionEffect_SetAnimation()

```c
int32_t OH_ArkUI_TransitionEffect_SetAnimation(ArkUI_TransitionEffect* effect, ArkUI_AnimateOption* animation)
```

**描述：**

设置转场效果动画参数。

> **说明：**
>
> 如果通过[OH_ArkUI_TransitionEffect_Combine](capi-native-animate-h.md#oh_arkui_transitioneffect_combine)进行转场效果的组合，前一转场效果的动画参数也可用于后一转场效果。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md)* effect | 要设置动画参数的转场效果对象。 <br>effect为NULL时，返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* animation | 属性显示动画效果相关参数。 <br>animation为NULL时，设置动画参数为空。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PropertyAnimation_Create()

```c
OH_ArkUI_PropertyAnimationHandle OH_ArkUI_NativeModule_PropertyAnimation_Create(OH_ArkUI_AnimationPropertyType propertyType)
```

**描述：**

为指定的可动画属性创建属性动画。 <br> <b>propertyType</b>必须是有效的[OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype)，否则本接口返回<b>NULL</b>。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationPropertyType propertyType | [in] 表示要动画的属性类型。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle | 返回属性动画的句柄。调用者拥有返回的句柄，不再使用时需要调用[OH_ArkUI_NativeModule_PropertyAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_destroy)释放该句柄。 |

### OH_ArkUI_NativeModule_PropertyAnimation_Destroy()

```c
void OH_ArkUI_NativeModule_PropertyAnimation_Destroy(OH_ArkUI_PropertyAnimationHandle animation)
```

**描述：**

销毁属性动画。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] 表示由[OH_ArkUI_NativeModule_PropertyAnimation_Create](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_create)返回的属性动画句柄。传入<b>NULL</b>无效果。 该函数对非NULL句柄返回后，句柄即失效，不得再次使用或销毁。 |

### OH_ArkUI_NativeModule_PropertyAnimation_SetFromValue()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetFromValue(OH_ArkUI_PropertyAnimationHandle animation, const ArkUI_NumberValue *value, int32_t size)
```

**描述：**

设置属性动画的起始值。<br> 推荐设置起始值，若未设置则默认从当前属性值开始产生动画。但需注意：如果未设置起始值且对应属性从未被赋值，由于缺少有效的起始状态，属性动画将无法产生。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] 表示属性动画句柄。 |
| const ArkUI_NumberValue *value | [in] 表示起始值。元素的数量和类型取决于[OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype)。 例如，OH_ARKUI_ANIMATION_PROPERTY_OPACITY需要1个f32值，OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION需要2个f32值(x, y)。 |
| int32_t size | [in] 表示value数组中的元素个数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PropertyAnimation_GetFromValue()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetFromValue(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_NumberValue *value, int32_t size)
```

**描述：**

获取属性动画的起始值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] 表示属性动画句柄。 |
| ArkUI_NumberValue *value | [out] 表示用于接收[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)起始值数组的指针。  元素的数量和类型取决于[OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype)。 例如，OH_ARKUI_ANIMATION_PROPERTY_OPACITY需要1个f32值，OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION需要2个f32值(x, y)。 值将写入该指针指向的内存。  <br>该指针不能为**NULL**。如果**value**设置为**NULL**，则返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| int32_t size | [in] 表示输出数组的大小。必须等于[OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype)所需的元素个数， 否则返回错误码[ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 未设置起始值。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。          [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 数组大小与所需大小不一致。 |

### OH_ArkUI_NativeModule_PropertyAnimation_SetToValue()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetToValue(OH_ArkUI_PropertyAnimationHandle animation, const ArkUI_NumberValue *value, int32_t size)
```

**描述：**

设置属性动画的结束值。<br> 必须设置结束值，否则属性动画句柄无实际意义。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] 表示属性动画句柄。 |
| const ArkUI_NumberValue *value | [in] 表示结束值。元素的数量和类型取决于[OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype)。 例如，OH_ARKUI_ANIMATION_PROPERTY_OPACITY需要1个f32值，OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION需要2个f32值(x, y)。 |
| int32_t size | [in] 表示value数组中的元素个数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PropertyAnimation_GetToValue()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetToValue(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_NumberValue *value, int32_t size)
```

**描述：**

获取属性动画的结束值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] 表示属性动画句柄。 |
| ArkUI_NumberValue *value | [out] 表示用于接收[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)结束值数组的指针。  元素的数量和类型取决于[OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype)。 例如，OH_ARKUI_ANIMATION_PROPERTY_OPACITY需要1个f32值，OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION需要2个f32值(x, y)。 值将写入该指针指向的内存。  <br>该指针不能为**NULL**。如果**value**设置为**NULL**，则返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| int32_t size | [in] 表示输出数组的大小。必须等于[OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype)所需的元素个数； 否则返回错误码[ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 未设置结束值。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。          [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 数组大小与所需大小不一致。 |

### OH_ArkUI_NativeModule_PropertyAnimation_SetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetDuration(OH_ArkUI_PropertyAnimationHandle animation, int32_t duration)
```

**描述：**

设置属性动画的持续时间。<br> 实际生效的动画持续时间按以下优先级确定：如果通过本接口设置了子动画的持续时间，则使用该值； 否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration)在动画组上设置的持续时间；如果两者都未设置，则使用默认值**1000**毫秒。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] 表示属性动画句柄。 |
| int32_t duration | [in] 表示持续时间，单位为毫秒。该值必须大于0。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PropertyAnimation_GetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetDuration(OH_ArkUI_PropertyAnimationHandle animation, int32_t *duration)
```

**描述：**

获取属性动画的持续时间。 <br> 本接口仅返回在本动画上显式设置的持续时间；从动画组继承的值或默认值在运行时解析，不存储在本对象上。 如果本动画未设置持续时间，则返回[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 运行时实际生效的动画持续时间按以下优先级确定：如果通过[OH_ArkUI_NativeModule_PropertyAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setduration)设置了持续时间， 则使用该值；否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration)设置的动画组持续时间；如果两者都未设置，则使用默认值**1000**毫秒。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] 表示属性动画句柄。 |
| int32_t *duration | [out] 表示用于接收持续时间值的指针，单位为毫秒。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 未设置持续时间。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PropertyAnimation_SetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetDelay(OH_ArkUI_PropertyAnimationHandle animation, int32_t delay)
```

**描述：**

设置属性动画的延迟时间。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] 表示属性动画句柄。 |
| int32_t delay | [in] 表示延迟时间，单位为毫秒。默认值为<b>0</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PropertyAnimation_GetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetDelay(OH_ArkUI_PropertyAnimationHandle animation, int32_t *delay)
```

**描述：**

获取属性动画的延迟时间。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] 表示属性动画句柄。 |
| int32_t *delay | [out] 表示用于接收延迟时间值的指针，单位为毫秒。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PropertyAnimation_SetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetCurve(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_CurveHandle curve)
```

**描述：**

设置属性动画的动画曲线。 <br> 实际生效的动画曲线按以下优先级确定：如果通过本接口设置了曲线，则使用该值； 否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setcurve)在动画组上设置的曲线；如果两者都未设置，则使用[ARKUI_CURVE_LINEAR](capi-native-type-h.md#arkui_animationcurve)。 支持弹簧曲线（<b>springMotion</b>、<b>responsiveSpringMotion</b>和<b>interpolatingSpring</b>）。 设置弹簧曲线时，通过[OH_ArkUI_NativeModule_PropertyAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setduration)设置的持续时间不生效，动画持续时间由弹簧曲线决定。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] 表示属性动画句柄。 |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) curve | [in] 表示动画曲线。本接口不接管曲线句柄的所有权；调用者必须确保在使用该动画句柄期间，曲线保持有效。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PropertyAnimation_GetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetCurve(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_CurveHandle *outBorrowedCurve)
```

**描述：**

获取属性动画的动画曲线。 <br> 本接口仅返回在本动画上显式设置的曲线；从动画组继承的值或默认值在运行时解析，不存储在本对象上。 如果本动画未设置曲线，则返回[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 运行时实际生效的动画曲线按以下优先级确定：如果通过[OH_ArkUI_NativeModule_PropertyAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setcurve)设置了曲线，则使用该值； 否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setcurve)设置的动画组曲线；如果两者都未设置，则使用[ARKUI_CURVE_LINEAR](capi-native-type-h.md#arkui_animationcurve)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] 表示属性动画句柄。 |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) *outBorrowedCurve | [out] 表示用于接收动画曲线的指针；调用者不得销毁该句柄。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 未设置曲线。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PropertyAnimation_SetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetTempo(OH_ArkUI_PropertyAnimationHandle animation, float tempo)
```

**描述：**

设置属性动画的播放速率。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] 表示属性动画句柄。 |
| float tempo | [in] 表示动画播放速率。取值范围：(0, +∞)。默认值为<b>1</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PropertyAnimation_GetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetTempo(OH_ArkUI_PropertyAnimationHandle animation, float *tempo)
```

**描述：**

获取属性动画的播放速率。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] 表示属性动画句柄。 |
| float *tempo | [out] 表示用于接收动画播放速率的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PropertyAnimation_SetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetAutoReverse(OH_ArkUI_PropertyAnimationHandle animation, bool autoReverse)
```

**描述：**

设置属性动画是否自动反转。<br> 启用自动反转后，动画在每轮播放中交替正向播放和反向播放。默认值为<b>false</b>。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] 表示属性动画句柄。 |
| bool autoReverse | [in] 表示是否启用自动反转。默认值为<b>false</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PropertyAnimation_GetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetAutoReverse(OH_ArkUI_PropertyAnimationHandle animation, bool *autoReverse)
```

**描述：**

获取属性动画是否启用自动反转。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] 表示属性动画句柄。 |
| bool *autoReverse | [out] 表示用于接收该值的指针。如果启用自动反转则为<b>true</b>；否则为<b>false</b>。默认值为<b>false</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PropertyAnimation_SetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetIterations(OH_ArkUI_PropertyAnimationHandle animation, int32_t iterations)
```

**描述：**

设置属性动画的播放次数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] 表示属性动画句柄。 |
| int32_t iterations | [in] 表示播放次数。该值必须为-1或大于等于1；值为0时返回[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。值<b>-1</b>表示无限次播放。 默认值为<b>1</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PropertyAnimation_GetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetIterations(OH_ArkUI_PropertyAnimationHandle animation, int32_t *iterations)
```

**描述：**

获取属性动画的播放次数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] 表示属性动画句柄。 |
| int32_t *iterations | [out] 表示用于接收播放次数的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_RenderNodeHandle targetNode)
```

**描述：**

设置属性动画的目标渲染节点。<br> 目标节点是被该属性动画驱动的渲染节点。 如果为<b>NULL</b>（默认值），则动画继承通过[OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode)设置的动画组默认目标。 非NULL目标必须属于动画组注册的同一UIContext，该检查在通过[OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup)注册动画组时执行。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] 表示属性动画句柄。 |
| ArkUI_RenderNodeHandle targetNode | [in] 表示要动画的渲染节点。<b>NULL</b>表示继承动画组的默认目标。默认值为<b>NULL</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PropertyAnimation_GetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PropertyAnimation_GetTargetNode(OH_ArkUI_PropertyAnimationHandle animation, ArkUI_RenderNodeHandle *outBorrowedTargetNode)
```

**描述：**

获取属性动画的目标渲染节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PropertyAnimationHandle animation | [in] 表示属性动画句柄。 |
| ArkUI_RenderNodeHandle *outBorrowedTargetNode | [out] 表示用于接收目标渲染节点的指针；调用者不得销毁该句柄。<b>NULL</b>表示继承动画组的默认目标。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_Create()

```c
OH_ArkUI_KeyframeAnimationHandle OH_ArkUI_NativeModule_KeyframeAnimation_Create(OH_ArkUI_AnimationPropertyType propertyType, int32_t size)
```

**描述：**

为指定的可动画属性创建关键帧动画。 <br> 每个关键帧的关键时间默认按索引在[0, 1]区间均匀分布（例如，当有3个关键帧时，第一帧为<b>0.0</b>，第二帧为<b>0.5</b>，第三帧为<b>1.0</b>）。 使用[OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTimes](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setkeytimes)或 [OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTime](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setkeytime)自定义关键时间点。 <br> <b>propertyType</b>必须是有效的[OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype)，且<b>size</b>必须大于等于2；否则，本接口返回<b>NULL</b>。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationPropertyType propertyType | [in] 表示要动画的属性类型。 |
| int32_t size | [in] 表示关键帧数量。该值必须大于等于2。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle | 返回关键帧动画的句柄。调用者拥有返回的句柄，不再使用时需要调用[OH_ArkUI_NativeModule_KeyframeAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_destroy)释放该句柄。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_Destroy()

```c
void OH_ArkUI_NativeModule_KeyframeAnimation_Destroy(OH_ArkUI_KeyframeAnimationHandle animation)
```

**描述：**

销毁关键帧动画。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示由[OH_ArkUI_NativeModule_KeyframeAnimation_Create](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_create)返回的关键帧动画句柄。  传入<b>NULL</b>无效果。该函数对非NULL句柄返回后，句柄即失效，不得再次使用或销毁。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTimes()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTimes(OH_ArkUI_KeyframeAnimationHandle animation, const float *keyTimes, int32_t size)
```

**描述：**

设置关键帧的关键时间点。 <br> 如果不调用本接口，每个关键帧的关键时间默认按索引在[0, 1]区间均匀分布（例如，当有3个关键帧时，第一帧为<b>0.0</b>，第二帧为<b>0.5</b>，第三帧为<b>1.0</b>）。 <br> <b>keyTimes</b>中的元素必须非递减， 且<b>size</b>必须等于关键帧动画的关键帧数量（即通过[OH_ArkUI_NativeModule_KeyframeAnimation_Create](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_create)创建动画时指定的<b>size</b>值）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| const float *keyTimes | [in] 表示关键时间点数组。每个元素的取值范围：[0, 1]。 |
| int32_t size | [in] 表示关键时间点的数量。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_GetKeyTime()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetKeyTime(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, float *keyTime)
```

**描述：**

获取指定索引处关键帧的关键时间点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| int32_t index | [in] 表示关键帧索引。 |
| float *keyTime | [out] 表示用于接收关键时间点的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTime()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTime(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, float keyTime)
```

**描述：**

设置指定索引处关键帧的关键时间点。 <br> 如果不调用本接口设置某个关键帧，其关键时间默认按索引在[0, 1]区间均匀分布（例如，当有3个关键帧时，第一帧为<b>0.0</b>，第二帧为<b>0.5</b>，第三帧为<b>1.0</b>）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| int32_t index | [in] 表示关键帧索引。 |
| float keyTime | [in] 表示关键时间点。取值范围：[0, 1]。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetValue()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetValue(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, const ArkUI_NumberValue *value, int32_t size)
```

**描述：**

设置指定索引处关键帧的值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| int32_t index | [in] 表示关键帧索引。 |
| const ArkUI_NumberValue *value | [in] 表示[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)数组。  元素的数量和类型取决于[OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype)。 例如，OH_ARKUI_ANIMATION_PROPERTY_OPACITY需要1个f32值，OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION需要2个f32值(x, y)。 |
| int32_t size | [in] 表示value数组中的元素个数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetValues()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetValues(OH_ArkUI_KeyframeAnimationHandle animation, const ArkUI_NumberValue *values, int32_t size)
```

**描述：**

一次性设置所有关键帧的值。 <br> 值以扁平数组形式提供。每个关键帧的元素数量取决于[OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype)。 例如，OH_ARKUI_ANIMATION_PROPERTY_OPACITY每个关键帧需要1个值，OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION每个关键帧需要2个值。 元素总数必须等于关键帧数量乘以每个关键帧的值数量。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| const ArkUI_NumberValue *values | [in] 表示所有关键帧的[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)扁平数组。 |
| int32_t size | [in] 表示values数组中的元素总数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_GetValue()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetValue(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, ArkUI_NumberValue *value, int32_t size)
```

**描述：**

获取指定索引处关键帧的值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| int32_t index | [in] 表示关键帧索引。 |
| ArkUI_NumberValue *value | [out] 表示用于接收[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)值数组的指针。  元素的数量和类型取决于[OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype)。 例如，OH_ARKUI_ANIMATION_PROPERTY_OPACITY需要1个f32值，OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION需要2个f32值(x, y)。 值将写入该指针指向的内存。  <br>该指针不能为**NULL**。如果**value**设置为**NULL**，则返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |
| int32_t size | [in] 表示输出数组的大小。必须等于[OH_ArkUI_AnimationPropertyType](capi-native-type-visual-h.md#oh_arkui_animationpropertytype)所需的元素个数； 否则返回错误码[ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 关键帧的值未设置。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。          [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 数组大小与所需大小不一致。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetCurves()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetCurves(OH_ArkUI_KeyframeAnimationHandle animation, const ArkUI_CurveHandle *value, int32_t size)
```

**描述：**

设置关键帧的动画曲线。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| [const ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) *value | [in] 表示曲线句柄数组。本接口不接管曲线句柄的所有权；调用者必须确保在使用该动画句柄期间，所有曲线保持有效。 不支持<b>springMotion</b>、<b>responsiveSpringMotion</b>和<b>interpolatingSpring</b>曲线，因为这些曲线没有有效的持续时间设置。 |
| int32_t size | [in] 表示曲线数量。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, ArkUI_CurveHandle curve)
```

**描述：**

设置指定索引处关键帧的动画曲线。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| int32_t index | [in] 表示关键帧索引。 |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) curve | [in] 表示动画曲线。本接口不接管曲线句柄的所有权；调用者必须确保在使用该动画句柄期间，曲线保持有效。 不支持<b>springMotion</b>、<b>responsiveSpringMotion</b>和<b>interpolatingSpring</b>曲线，因为这些曲线没有有效的持续时间设置。 实际生效的动画曲线按以下优先级确定：如果通过本接口或[OH_ArkUI_NativeModule_KeyframeAnimation_SetCurves](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setcurves)为关键帧设置了曲线，则使用该值； 否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setcurve)在动画组上设置的曲线；如果两者都未设置，则使用[ARKUI_CURVE_LINEAR](capi-native-type-h.md#arkui_animationcurve)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_GetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetCurve(OH_ArkUI_KeyframeAnimationHandle animation, int32_t index, ArkUI_CurveHandle *outBorrowedCurve)
```

**描述：**

获取指定索引处关键帧的动画曲线。 <br> 本接口仅返回为关键帧显式设置的曲线；从动画组继承的值或默认值在运行时解析，不存储在本对象上。 如果关键帧未设置曲线，则返回[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 运行时实际生效的动画曲线按以下优先级确定：如果通过[OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setcurve)或 [OH_ArkUI_NativeModule_KeyframeAnimation_SetCurves](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setcurves)为关键帧设置了曲线，则使用该值； 否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setcurve)设置的动画组曲线；如果两者都未设置，则使用[ARKUI_CURVE_LINEAR](capi-native-type-h.md#arkui_animationcurve)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| int32_t index | [in] 表示关键帧索引。 |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) *outBorrowedCurve | [out] 表示用于接收动画曲线的指针；调用者不得销毁该句柄。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 未设置曲线。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration(OH_ArkUI_KeyframeAnimationHandle animation, int32_t duration)
```

**描述：**

设置关键帧动画的持续时间。 <br> 实际生效的动画持续时间按以下优先级确定：如果通过本接口设置了持续时间，则使用该值； 否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration)在动画组上设置的持续时间；如果两者都未设置，则使用默认值**1000**毫秒。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| int32_t duration | [in] 表示持续时间，单位为毫秒。该值必须大于0。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_GetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetDuration(OH_ArkUI_KeyframeAnimationHandle animation, int32_t *duration)
```

**描述：**

获取关键帧动画的持续时间。 <br> 本接口仅返回在本动画上显式设置的持续时间；从动画组继承的值或默认值在运行时解析，不存储在本对象上。 如果本动画未设置持续时间，则返回[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 运行时实际生效的动画持续时间按以下优先级确定：如果通过[OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setduration)设置了持续时间，则使用该值； 否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration)设置的动画组持续时间；如果两者都未设置，则使用默认值**1000**毫秒。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| int32_t *duration | [out] 表示用于接收持续时间值的指针，单位为毫秒。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 未设置持续时间。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetDelay(OH_ArkUI_KeyframeAnimationHandle animation, int32_t delay)
```

**描述：**

设置关键帧动画的延迟时间。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| int32_t delay | [in] 表示延迟时间，单位为毫秒。默认值为<b>0</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_GetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetDelay(OH_ArkUI_KeyframeAnimationHandle animation, int32_t *delay)
```

**描述：**

获取关键帧动画的延迟时间。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| int32_t *delay | [out] 表示用于接收延迟时间值的指针，单位为毫秒。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetTempo(OH_ArkUI_KeyframeAnimationHandle animation, float tempo)
```

**描述：**

设置关键帧动画的播放速率。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| float tempo | [in] 表示动画播放速率。取值范围：(0, +∞)。默认值为<b>1</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_GetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetTempo(OH_ArkUI_KeyframeAnimationHandle animation, float *tempo)
```

**描述：**

获取关键帧动画的播放速率。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| float *tempo | [out] 表示用于接收动画播放速率的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetAutoReverse(OH_ArkUI_KeyframeAnimationHandle animation, bool autoReverse)
```

**描述：**

设置关键帧动画是否自动反转。 <br> 启用自动反转后，动画在每轮播放中交替正向播放和反向播放。默认值为<b>false</b>。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| bool autoReverse | [in] 表示是否启用自动反转。默认值为<b>false</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_GetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetAutoReverse(OH_ArkUI_KeyframeAnimationHandle animation, bool *autoReverse)
```

**描述：**

获取关键帧动画是否启用自动反转。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| bool *autoReverse | [out] 表示用于接收该值的指针。如果启用自动反转则为<b>true</b>；否则为<b>false</b>。默认值为<b>false</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetIterations(OH_ArkUI_KeyframeAnimationHandle animation, int32_t iterations)
```

**描述：**

设置关键帧动画的播放次数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| int32_t iterations | [in] 表示播放次数。该值必须为-1或大于等于1；值为0时返回[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。值<b>-1</b>表示无限次播放。 默认值为<b>1</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_GetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetIterations(OH_ArkUI_KeyframeAnimationHandle animation, int32_t *iterations)
```

**描述：**

获取关键帧动画的播放次数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| int32_t *iterations | [out] 表示用于接收播放次数的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode(OH_ArkUI_KeyframeAnimationHandle animation, ArkUI_RenderNodeHandle targetNode)
```

**描述：**

设置关键帧动画的目标渲染节点。 <br> 目标节点是被该关键帧动画驱动的渲染节点。如果为<b>NULL</b>（默认值），则动画继承通过[OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode)设置的动画组默认目标。 非NULL目标必须属于动画组注册的同一UIContext，该检查在通过[OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup)注册动画组时执行。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| ArkUI_RenderNodeHandle targetNode | [in] 表示要动画的渲染节点。<b>NULL</b>表示继承动画组的默认目标。默认值为<b>NULL</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_KeyframeAnimation_GetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_KeyframeAnimation_GetTargetNode(OH_ArkUI_KeyframeAnimationHandle animation, ArkUI_RenderNodeHandle *outBorrowedTargetNode)
```

**描述：**

获取关键帧动画的目标渲染节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示关键帧动画句柄。 |
| ArkUI_RenderNodeHandle *outBorrowedTargetNode | [out] 表示用于接收目标渲染节点的指针；调用者不得销毁该句柄。<b>NULL</b>表示继承动画组的默认目标。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PathAnimation_Create()

```c
OH_ArkUI_PathAnimationHandle OH_ArkUI_NativeModule_PathAnimation_Create(const char *path)
```

**描述：**

创建路径动画，使组件沿几何路径移动。 <br> 路径动画作用于OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION属性。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *path | [in] 表示SVG路径语法的路径字符串。不支持<b>"start"</b>和<b>"end"</b>关键字作为位置值。 如果<b>path</b>为<b>NULL</b>、空字符串或包含不支持的值，则返回<b>NULL</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_ArkUI_PathAnimationHandle | 返回路径动画的句柄。输入无效时返回<b>NULL</b>。调用者拥有返回的句柄，不再使用时需要调用[OH_ArkUI_NativeModule_PathAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_destroy)释放该句柄。 |

### OH_ArkUI_NativeModule_PathAnimation_Destroy()

```c
void OH_ArkUI_NativeModule_PathAnimation_Destroy(OH_ArkUI_PathAnimationHandle animation)
```

**描述：**

销毁路径动画。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] 表示由[OH_ArkUI_NativeModule_PathAnimation_Create](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_create)返回的路径动画句柄。传入<b>NULL</b>无效果。 该函数对非NULL句柄返回后，句柄即失效，不得再次使用或销毁。 |

### OH_ArkUI_NativeModule_PathAnimation_SetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetDuration(OH_ArkUI_PathAnimationHandle animation, int32_t duration)
```

**描述：**

设置路径动画的持续时间。 <br> 实际生效的动画持续时间按以下优先级确定：如果通过本接口设置了持续时间，则使用该值； 否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration)在动画组上设置的持续时间；如果两者都未设置，则使用默认值**1000**毫秒。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] 表示路径动画句柄。 |
| int32_t duration | [in] 表示持续时间，单位为毫秒。该值必须大于0。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PathAnimation_GetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetDuration(OH_ArkUI_PathAnimationHandle animation, int32_t *duration)
```

**描述：**

获取路径动画的持续时间。 <br> 本接口仅返回在本动画上显式设置的持续时间；从动画组继承的值或默认值在运行时解析，不存储在本对象上。 如果本动画未设置持续时间，则返回[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 运行时实际生效的动画持续时间按以下优先级确定：如果通过[OH_ArkUI_NativeModule_PathAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_setduration)设置了持续时间，则使用该值； 否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setduration)设置的动画组持续时间；如果两者都未设置，则使用默认值**1000**毫秒。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] 表示路径动画句柄。 |
| int32_t *duration | [out] 表示用于接收持续时间值的指针，单位为毫秒。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 未设置持续时间。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PathAnimation_SetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetDelay(OH_ArkUI_PathAnimationHandle animation, int32_t delay)
```

**描述：**

设置路径动画的延迟时间。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] 表示路径动画句柄。 |
| int32_t delay | [in] 表示延迟时间，单位为毫秒。默认值为<b>0</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PathAnimation_GetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetDelay(OH_ArkUI_PathAnimationHandle animation, int32_t *delay)
```

**描述：**

获取路径动画的延迟时间。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] 表示路径动画句柄。 |
| int32_t *delay | [out] 表示用于接收延迟时间值的指针，单位为毫秒。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PathAnimation_SetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetCurve(OH_ArkUI_PathAnimationHandle animation, ArkUI_CurveHandle curve)
```

**描述：**

设置路径动画的动画曲线。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] 表示路径动画句柄。 |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) curve | [in] 表示控制沿路径运动速率的动画曲线。  本接口不接管曲线句柄的所有权；调用者必须确保在使用该动画句柄期间，曲线保持有效。 不支持<b>springMotion</b>、<b>responsiveSpringMotion</b>和<b>interpolatingSpring</b>曲线，因为这些曲线没有有效的持续时间设置。 实际生效的动画曲线按以下优先级确定：如果通过本接口设置了曲线，则使用该值；否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setcurve)在动画组上设置的曲线； 如果两者都未设置，则使用[ARKUI_CURVE_LINEAR](capi-native-type-h.md#arkui_animationcurve)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PathAnimation_GetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetCurve(OH_ArkUI_PathAnimationHandle animation, ArkUI_CurveHandle *outBorrowedCurve)
```

**描述：**

获取路径动画的动画曲线。 <br> 本接口仅返回在本动画上显式设置的曲线；从动画组继承的值或默认值在运行时解析，不存储在本对象上。 如果本动画未设置曲线，则返回[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 运行时实际生效的动画曲线按以下优先级确定：如果通过[OH_ArkUI_NativeModule_PathAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_setcurve)设置了曲线，则使用该值； 否则，使用通过[OH_ArkUI_NativeModule_AnimationGroup_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_setcurve)设置的动画组曲线；如果两者都未设置，则使用[ARKUI_CURVE_LINEAR](capi-native-type-h.md#arkui_animationcurve)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] 表示路径动画句柄。 |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) *outBorrowedCurve | [out] 表示用于接收动画曲线的指针；调用者不得销毁该句柄。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 未设置曲线。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PathAnimation_SetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetTempo(OH_ArkUI_PathAnimationHandle animation, float tempo)
```

**描述：**

设置路径动画的播放速率。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] 表示路径动画句柄。 |
| float tempo | [in] 表示动画播放速率。取值范围：(0, +∞)。默认值为<b>1</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PathAnimation_GetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetTempo(OH_ArkUI_PathAnimationHandle animation, float *tempo)
```

**描述：**

获取路径动画的播放速率。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] 表示路径动画句柄。 |
| float *tempo | [out] 表示用于接收动画播放速率的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PathAnimation_SetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetAutoReverse(OH_ArkUI_PathAnimationHandle animation, bool autoReverse)
```

**描述：**

设置路径动画是否自动反转。 <br> 启用自动反转后，动画在每轮播放中交替正向播放和反向播放。默认值为<b>false</b>。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] 表示路径动画句柄。 |
| bool autoReverse | [in] 表示是否启用自动反转。默认值为<b>false</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PathAnimation_GetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetAutoReverse(OH_ArkUI_PathAnimationHandle animation, bool *autoReverse)
```

**描述：**

获取路径动画是否启用自动反转。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] 表示路径动画句柄。 |
| bool *autoReverse | [out] 表示用于接收该值的指针。如果启用自动反转则为<b>true</b>；否则为<b>false</b>。默认值为<b>false</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PathAnimation_SetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetIterations(OH_ArkUI_PathAnimationHandle animation, int32_t iterations)
```

**描述：**

设置路径动画的播放次数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] 表示路径动画句柄。 |
| int32_t iterations | [in] 表示播放次数。该值必须为-1或大于等于1；值为0时返回[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。值<b>-1</b>表示无限次播放。 默认值为<b>1</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PathAnimation_GetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetIterations(OH_ArkUI_PathAnimationHandle animation, int32_t *iterations)
```

**描述：**

获取路径动画的播放次数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] 表示路径动画句柄。 |
| int32_t *iterations | [out] 表示用于接收播放次数的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PathAnimation_SetAutoRotation()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetAutoRotation(OH_ArkUI_PathAnimationHandle animation, bool autoRotation)
```

**描述：**

设置路径动画过程中组件是否沿路径切线方向自动旋转。 <br> 启用自动旋转后，组件将旋转使其朝向方向与当前位置的路径切线对齐。默认值为<b>false</b>。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] 表示路径动画句柄。 |
| bool autoRotation | [in] 表示是否启用自动旋转。默认值为<b>false</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PathAnimation_GetAutoRotation()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetAutoRotation(OH_ArkUI_PathAnimationHandle animation, bool *autoRotation)
```

**描述：**

获取路径动画是否启用自动旋转。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] 表示路径动画句柄。 |
| bool *autoRotation | [out] 表示用于接收该值的指针。如果启用自动旋转则为<b>true</b>；否则为<b>false</b>。默认值为<b>false</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PathAnimation_SetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_SetTargetNode(OH_ArkUI_PathAnimationHandle animation, ArkUI_RenderNodeHandle targetNode)
```

**描述：**

设置路径动画的目标渲染节点。 <br> 目标节点是被该路径动画驱动的渲染节点。 如果为<b>NULL</b>（默认值），则动画继承通过[OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode)设置的动画组默认目标。 非NULL目标必须属于动画组注册的同一UIContext，该检查在通过[OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup)注册动画组时执行。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] 表示路径动画句柄。 |
| ArkUI_RenderNodeHandle targetNode | [in] 表示要动画的渲染节点。<b>NULL</b>表示继承动画组的默认目标。默认值为<b>NULL</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_PathAnimation_GetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PathAnimation_GetTargetNode(OH_ArkUI_PathAnimationHandle animation, ArkUI_RenderNodeHandle *outBorrowedTargetNode)
```

**描述：**

获取路径动画的目标渲染节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_PathAnimationHandle animation | [in] 表示路径动画句柄。 |
| ArkUI_RenderNodeHandle *outBorrowedTargetNode | [out] 表示用于接收目标渲染节点的指针；调用者不得销毁该句柄。<b>NULL</b>表示继承动画组的默认目标。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_AnimationGroup_Create()

```c
OH_ArkUI_AnimationGroupHandle OH_ArkUI_NativeModule_AnimationGroup_Create(void)
```

**描述：**

创建动画组。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle | 返回动画组的句柄。调用者拥有返回的句柄，不再使用时需要调用[OH_ArkUI_NativeModule_AnimationGroup_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_destroy)释放该句柄。 |

### OH_ArkUI_NativeModule_AnimationGroup_Destroy()

```c
void OH_ArkUI_NativeModule_AnimationGroup_Destroy(OH_ArkUI_AnimationGroupHandle group)
```

**描述：**

销毁动画组的前端句柄。<br> 本接口仅释放前端句柄。 通过[OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup)注册的动画组的后端（运行时）对象将被单独释放——在finish回调触发时自动释放， 或通过[OH_ArkUI_NativeModule_RemoveAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_removeanimationgroup)释放。<br> 添加到动画组的子动画不会被自动销毁。 需要分别调用[OH_ArkUI_NativeModule_PropertyAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_destroy)、 [OH_ArkUI_NativeModule_KeyframeAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_destroy)或[OH_ArkUI_NativeModule_PathAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_destroy)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示由[OH_ArkUI_NativeModule_AnimationGroup_Create](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_create)返回的动画组句柄。  传入<b>NULL</b>无效果。该函数对非NULL句柄返回后，句柄即失效，不得再次使用或销毁。 |

### OH_ArkUI_NativeModule_AnimationGroup_SetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetDuration(OH_ArkUI_AnimationGroupHandle group, int32_t duration)
```

**描述：**

设置动画组的持续时间。<br> 动画组的持续时间作为未通过[OH_ArkUI_NativeModule_PropertyAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setduration)、 [OH_ArkUI_NativeModule_KeyframeAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setduration)或[OH_ArkUI_NativeModule_PathAnimation_SetDuration](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_setduration) 设置自身持续时间的子动画的默认持续时间。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| int32_t duration | [in] 表示持续时间，单位为毫秒。该值必须大于0。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_AnimationGroup_GetDuration()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetDuration(OH_ArkUI_AnimationGroupHandle group, int32_t *duration)
```

**描述：**

获取动画组的持续时间。 <br> 本接口仅返回在本动画组上显式设置的持续时间，不受子动画的持续时间影响。 如果本动画组未设置持续时间，则返回[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。运行时，未设置的动画组持续时间默认为**1000**毫秒。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| int32_t *duration | [out] 表示用于接收持续时间值的指针，单位为毫秒。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 未设置持续时间。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_AnimationGroup_SetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetDelay(OH_ArkUI_AnimationGroupHandle group, int32_t delay)
```

**描述：**

设置动画组的延迟时间。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| int32_t delay | [in] 表示延迟时间，单位为毫秒。默认值为<b>0</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_AnimationGroup_GetDelay()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetDelay(OH_ArkUI_AnimationGroupHandle group, int32_t *delay)
```

**描述：**

获取动画组的延迟时间。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| int32_t *delay | [out] 表示用于接收延迟时间值的指针，单位为毫秒。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_AnimationGroup_SetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetCurve(OH_ArkUI_AnimationGroupHandle group, ArkUI_CurveHandle curve)
```

**描述：**

设置动画组的动画曲线。 <br> 动画组的曲线作为未通过[OH_ArkUI_NativeModule_PropertyAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setcurve)、 [OH_ArkUI_NativeModule_KeyframeAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setcurve)或[OH_ArkUI_NativeModule_PathAnimation_SetCurve](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_setcurve) 设置自身曲线的子动画的默认曲线。 不支持<b>springMotion</b>、<b>responsiveSpringMotion</b>和<b>interpolatingSpring</b>曲线，因为这些曲线没有有效的持续时间设置。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) curve | [in] 表示动画曲线。本接口不接管曲线句柄的所有权；调用者必须确保在使用该动画句柄期间，曲线保持有效。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_AnimationGroup_GetCurve()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetCurve(OH_ArkUI_AnimationGroupHandle group, ArkUI_CurveHandle *outBorrowedCurve)
```

**描述：**

获取动画组的动画曲线。<br> 本接口仅返回在本动画组上显式设置的曲线，不受子动画的曲线影响。 如果本动画组未设置曲线，则返回[ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 运行时，未设置的动画组曲线默认为[ARKUI_CURVE_LINEAR](capi-native-type-h.md#arkui_animationcurve)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| [ArkUI_CurveHandle](capi-arkui-nativemodule-arkui-curve8h.md) *outBorrowedCurve | [out] 表示用于接收动画曲线的指针；调用者不得销毁该句柄。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 未设置曲线。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_AnimationGroup_SetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetTempo(OH_ArkUI_AnimationGroupHandle group, float tempo)
```

**描述：**

设置动画组的播放速率。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| float tempo | [in] 表示动画播放速率。取值范围：(0, +∞)。默认值为<b>1</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_AnimationGroup_GetTempo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetTempo(OH_ArkUI_AnimationGroupHandle group, float *tempo)
```

**描述：**

获取动画组的播放速率。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| float *tempo | [out] 表示用于接收动画播放速率的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_AnimationGroup_SetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetAutoReverse(OH_ArkUI_AnimationGroupHandle group, bool autoReverse)
```

**描述：**

设置动画组是否自动反转。<br> 启用自动反转后，动画组在每轮播放中交替正向播放和反向播放。默认值为<b>false</b>。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| bool autoReverse | [in] 表示是否启用自动反转。默认值为<b>false</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_AnimationGroup_GetAutoReverse()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetAutoReverse(OH_ArkUI_AnimationGroupHandle group, bool *autoReverse)
```

**描述：**

获取动画组是否启用自动反转。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| bool *autoReverse | [out] 表示用于接收该值的指针。如果启用自动反转则为<b>true</b>；否则为<b>false</b>。默认值为<b>false</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_AnimationGroup_SetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetIterations(OH_ArkUI_AnimationGroupHandle group, int32_t iterations)
```

**描述：**

设置动画组的播放次数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| int32_t iterations | [in] 表示播放次数。该值必须为-1或大于等于1；值为0时返回[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。值<b>-1</b>表示无限次播放。 默认值为<b>1</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_AnimationGroup_GetIterations()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetIterations(OH_ArkUI_AnimationGroupHandle group, int32_t *iterations)
```

**描述：**

获取动画组的播放次数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| int32_t *iterations | [out] 表示用于接收播放次数的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_AnimationGroup_SetExpectedFrameRateRange()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetExpectedFrameRateRange(OH_ArkUI_AnimationGroupHandle group, const ArkUI_ExpectedFrameRateRange *frameRate)
```

**描述：**

设置动画组的期望帧率范围。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| [const ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md) *frameRate | [in] 表示期望帧率范围。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_AnimationGroup_GetExpectedFrameRateRange()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetExpectedFrameRateRange(OH_ArkUI_AnimationGroupHandle group, ArkUI_ExpectedFrameRateRange *frameRate)
```

**描述：**

获取动画组的期望帧率范围。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md) *frameRate | [out] 表示用于接收期望帧率范围的指针。  [ArkUI_ExpectedFrameRateRange](capi-arkui-nativemodule-arkui-expectedframeraterange.md)对象的值将写入该指针指向的内存。 <br>该指针不能为**NULL**。如果**frameRate**设置为**NULL**，则返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_AnimationGroup_RegisterOnFinishCallback()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_RegisterOnFinishCallback(OH_ArkUI_AnimationGroupHandle group, void *userData, void (*callback)(void *userData))
```

**描述：**

注册动画组播放完成时的回调函数。 <br> 动画组只有一个完成回调。注册另一个回调会替换之前的回调和userData对。再次注册相同的回调和userData对会成功，但不会创建额外的注册。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| H_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| void \*userData | [in] 表示调用者拥有的自定义数据，原样传递给回调。可以为NULL，必须保持有效直到回调返回，本接口不负责释放该数据。 |
| void (\*callback)(void \*userData) | [in] 表示完成回调函数。不能为NULL，在UI主线程上串行调用一次。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode(OH_ArkUI_AnimationGroupHandle group, ArkUI_RenderNodeHandle targetNode)
```

**描述：**

设置动画组的默认目标渲染节点。 <br> 默认目标是被未通过[OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_settargetnode)、 [OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_settargetnode)或 [OH_ArkUI_NativeModule_PathAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_settargetnode)设置自身目标的子动画驱动的渲染节点。 在通过[OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup)注册动画组时，每个子动画必须解析为非NULL目标（自身的目标或动画组默认目标）； 任何解析后的目标必须属于动画组注册的同一UIContext。默认值为<b>NULL</b>。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| ArkUI_RenderNodeHandle targetNode | [in] 表示默认的要动画的渲染节点。<b>NULL</b>表示没有动画组级别的默认值。默认值为<b>NULL</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_AnimationGroup_GetTargetNode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_GetTargetNode(OH_ArkUI_AnimationGroupHandle group, ArkUI_RenderNodeHandle *outBorrowedTargetNode)
```

**描述：**

获取动画组的默认目标渲染节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| ArkUI_RenderNodeHandle *outBorrowedTargetNode | [out] 表示用于接收默认目标节点的指针；调用者不得销毁该句柄。<b>NULL</b>表示未设置动画组级别的默认值。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_AnimationGroup_AddPropertyAnimation()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_AddPropertyAnimation(OH_ArkUI_AnimationGroupHandle group, OH_ArkUI_PropertyAnimationHandle animation)
```

**描述：**

将属性动画添加到动画组中。<br> 动画的目标节点由[OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_settargetnode)确定； 如果未设置，则动画继承通过[OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode)设置的动画组默认目标。 在注册动画组时，每个子动画必须解析为非NULL目标。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| OH_ArkUI_PropertyAnimationHandle animation | [in] 表示要添加的属性动画。本接口不接管该动画句柄的所有权；调用者必须确保在使用动画组句柄期间，该动画保持有效。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。<br>        [ARKUI_ERROR_CODE_SUB_ANIMATION_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) {@link OH_ArkUI_PropertyAnimationHandle}参数无效。 |

### OH_ArkUI_NativeModule_AnimationGroup_AddKeyframeAnimation()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_AddKeyframeAnimation(OH_ArkUI_AnimationGroupHandle group, OH_ArkUI_KeyframeAnimationHandle animation)
```

**描述：**

将关键帧动画添加到动画组中。 <br> 动画的目标节点由[OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_settargetnode)确定； 如果未设置，则动画继承通过[OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode)设置的动画组默认目标。 在注册动画组时，每个子动画必须解析为非NULL目标。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| OH_ArkUI_KeyframeAnimationHandle animation | [in] 表示要添加的关键帧动画。本接口不接管该动画句柄的所有权；调用者必须确保在使用动画组句柄期间，该动画保持有效。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。<br>        [ARKUI_ERROR_CODE_SUB_ANIMATION_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) {@link OH_ArkUI_KeyframeAnimationHandle}参数无效。 |

### OH_ArkUI_NativeModule_AnimationGroup_AddPathAnimation()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AnimationGroup_AddPathAnimation(OH_ArkUI_AnimationGroupHandle group, OH_ArkUI_PathAnimationHandle animation)
```

**描述：**

将路径动画添加到动画组中。 <br> 动画的目标节点由[OH_ArkUI_NativeModule_PathAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_settargetnode)确定； 如果未设置，则动画继承通过[OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode)设置的动画组默认目标。 在注册动画组时，每个子动画必须解析为非NULL目标。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| OH_ArkUI_PathAnimationHandle animation | [in] 表示要添加的路径动画。本接口不接管该动画句柄的所有权；调用者必须确保在使用动画组句柄期间，该动画保持有效。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。<br>        [ARKUI_ERROR_CODE_SUB_ANIMATION_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) {@link OH_ArkUI_PathAnimationHandle}参数无效。 |

### OH_ArkUI_NativeModule_AddAnimationGroup()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_AddAnimationGroup(ArkUI_ContextHandle context, OH_ArkUI_AnimationGroupHandle group, const char *key)
```

**描述：**

在UIContext上以指定key注册动画组并开始播放。 <br> UIContext通过<b>key</b>拥有动画组：注册后，UIContext持有动画组的后端（运行时）对象，调用者可以在注册后销毁前端动画组句柄（及子动画句柄）， 因为后端通过(UIContext, key)独立运行。 key按UIContext（实例）划分作用域：不同UIContext中的相同key不会冲突。 在一个UIContext内，如果已用相同key注册了动画组，系统会先移除前一个动画组（释放其后端对象）再注册新动画组。 动画组随后通过相同的(UIContext, key)对进行标识和管理。 <br> 通过[OH_ArkUI_NativeModule_AnimationGroup_AddPropertyAnimation](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_addpropertyanimation)、 [OH_ArkUI_NativeModule_AnimationGroup_AddKeyframeAnimation](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_addkeyframeanimation)或 [OH_ArkUI_NativeModule_AnimationGroup_AddPathAnimation](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_addpathanimation)添加的每个子动画， 驱动由其自身<b>SetTargetNode</b>接口设置的目标节点；如果该目标未设置（或为<b>NULL</b>）， 则继承通过[OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode)设置的动画组默认目标。 注册时，每个子动画必须解析为非NULL目标节点（自身的或动画组默认的），且每个解析后的目标节点必须属于与<b>context</b>相同的UIContext； 否则返回错误码[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。 <br> 播放控制和生命周期接口（[OH_ArkUI_NativeModule_RemoveAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_removeanimationgroup)、 [OH_ArkUI_NativeModule_GetAnimationGroupState](capi-native-animate-h.md#oh_arkui_nativemodule_getanimationgroupstate)、 [OH_ArkUI_NativeModule_HasAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_hasanimationgroup)、 [OH_ArkUI_NativeModule_PauseAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_pauseanimationgroup)、 [OH_ArkUI_NativeModule_ResumeAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_resumeanimationgroup)、 [OH_ArkUI_NativeModule_FinishAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_finishanimationgroup)）均以(UIContext, key)对为键。 <br> finish回调（见[OH_ArkUI_NativeModule_AnimationGroup_RegisterOnFinishCallback](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_registeronfinishcallback)）仅触发一次， 由停止动画的事件触发——自然结束、[OH_ArkUI_NativeModule_FinishAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_finishanimationgroup)或目标节点销毁。 如果[OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup)返回错误，动画创建失败，finish回调不会被触发。 回调返回后，系统自动从UIContext移除动画组并释放动画组及其子动画的后端（运行时）对象； 前端句柄（动画组及其子动画）仍需由调用者通过[OH_ArkUI_NativeModule_AnimationGroup_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_destroy)、 [OH_ArkUI_NativeModule_PropertyAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_destroy)、 [OH_ArkUI_NativeModule_KeyframeAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_destroy)或[OH_ArkUI_NativeModule_PathAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_destroy)销毁。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_ContextHandle context | [in] 表示注册并播放动画组的[ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md)（UIContext）。 |
| OH_ArkUI_AnimationGroupHandle group | [in] 表示动画组句柄。 |
| const char *key | [in] 表示用于在UIContext上标识动画组的key。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常，或解析后的目标节点不属于与<b>context</b>相同的UIContext。          [ARKUI_ERROR_CODE_SUB_ANIMATION_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 子动画无可解析的目标节点或子动画参数非法。          [ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 检测到同线程重入调用。 |

### OH_ArkUI_NativeModule_RemoveAnimationGroup()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_RemoveAnimationGroup(ArkUI_ContextHandle context, const char *key)
```

**描述：**

从UIContext中移除指定key标识的动画组。 <br> 停止动画组（如果仍在运行）并释放动画组及其子动画的后端（运行时）对象。被动画的目标节点将恢复到动画开始时的状态。 前端句柄（动画组及其子动画）不会被本调用释放，需要由调用者通过[OH_ArkUI_NativeModule_AnimationGroup_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_destroy)、 [OH_ArkUI_NativeModule_PropertyAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_destroy)、 [OH_ArkUI_NativeModule_KeyframeAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_destroy)或[OH_ArkUI_NativeModule_PathAnimation_Destroy](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_destroy)销毁。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_ContextHandle context | [in] 表示注册动画组的UIContext。 |
| const char *key | [in] 表示要移除的动画组的key。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。          [ARKUI_ERROR_CODE_ANIMATION_GROUP_NOT_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 在UIContext上未找到<b>key</b>标识的动画组。          [ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 检测到同线程重入调用。 |

### OH_ArkUI_NativeModule_GetAnimationGroupState()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_GetAnimationGroupState(ArkUI_ContextHandle context, const char *key, OH_ArkUI_AnimationGroupState *state)
```

**描述：**

获取UIContext上指定key标识的动画组的播放状态。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_ContextHandle context | [in] 表示UIContext。 |
| const char *key | [in] 表示动画组的key。 |
| OH_ArkUI_AnimationGroupState *state | [out] 表示用于接收状态值的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。          [ARKUI_ERROR_CODE_ANIMATION_GROUP_NOT_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 在UIContext上未找到<b>key</b>标识的动画组。          [ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 检测到同线程重入调用。 |

### OH_ArkUI_NativeModule_HasAnimationGroup()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_HasAnimationGroup(ArkUI_ContextHandle context, const char *key, bool *exists)
```

**描述：**

检查UIContext上是否存在指定key的动画组。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_ContextHandle context | [in] 表示UIContext。 |
| const char *key | [in] 表示动画组的key。 |
| bool *exists | [in] 表示用于接收该值的指针。如果动画组存在则为<b>true</b>；否则为<b>false</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。          [ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 检测到同线程重入调用。 |

### OH_ArkUI_NativeModule_PauseAnimationGroup()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_PauseAnimationGroup(ArkUI_ContextHandle context, const char *key)
```

**描述：**

暂停UIContext上指定key标识的动画组。 <br> 调用此接口时动画组必须处于RUNNING状态；否则返回[ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_ContextHandle context | [in] 表示UIContext。 |
| const char *key | [in] 表示动画组的key。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。          [ARKUI_ERROR_CODE_ANIMATION_GROUP_NOT_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 在UIContext上未找到<b>key</b>标识的动画组。          [ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 动画组不处于RUNNING状态。          [ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 检测到同线程重入调用。 |

### OH_ArkUI_NativeModule_ResumeAnimationGroup()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ResumeAnimationGroup(ArkUI_ContextHandle context, const char *key)
```

**描述：**

恢复UIContext上指定key标识的动画组。<br> 调用此接口时动画组必须处于PAUSED状态；否则返回[ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_ContextHandle context | [in] 表示UIContext。 |
| const char *key | [in] 表示动画组的key。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。          [ARKUI_ERROR_CODE_ANIMATION_GROUP_NOT_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 在UIContext上未找到<b>key</b>标识的动画组。          [ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 动画组不处于PAUSED状态。          [ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 检测到同线程重入调用。 |

### OH_ArkUI_NativeModule_FinishAnimationGroup()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_FinishAnimationGroup(ArkUI_ContextHandle context, const char *key, OH_ArkUI_AnimationFinishMode mode)
```

**描述：**

结束UIContext上指定key标识的动画组。 <br> 根据指定的结束模式结束动画组：跳转到结束状态、跳转到起始状态或保持当前值。 动画组必须处于RUNNING或PAUSED状态；否则返回[ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_ContextHandle context | [in] 表示UIContext。 |
| const char *key | [in] 表示动画组的key。 |
| OH_ArkUI_AnimationFinishMode mode | [in] 表示结束模式。该值为[OH_ArkUI_AnimationFinishMode](capi-native-type-visual-h.md#oh_arkui_animationfinishmode)的枚举值。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常，例如<b>context</b>或<b>key</b>无效，              或<b>mode</b>不是[OH_ArkUI_AnimationFinishMode](capi-native-type-visual-h.md#oh_arkui_animationfinishmode)的有效值。          [ARKUI_ERROR_CODE_ANIMATION_GROUP_NOT_FOUND](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 在UIContext上未找到<b>key</b>标识的动画组。          [ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 动画组不处于RUNNING或PAUSED状态。          [ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 检测到同线程重入调用。 |


