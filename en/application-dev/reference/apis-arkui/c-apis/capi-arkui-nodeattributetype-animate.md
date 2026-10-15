# Animate

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_OPACITY_TRANSITION

```c
NODE_OPACITY_TRANSITION
```

**Description**

Transition opacity attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: opacity value at the end of the transition (that is, the end point). The transition changes from the current opacity to this value. .value[1].i32: animation duration, in ms. The value must be greater than 0. .value[2].i32: animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). .value[3]?.i32: animation delay duration, in ms. The default value is **0** (no delay) when this parameter is not passed. Pass this parameter when the animation needs to wait for a period of time before starting. .value[4]?.i32: number of times the animation is played. The default value is **1** (play once) when this parameter is not passed. Pass this parameter when the animation needs to be played repeatedly. .value[5]?.i32: animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). The default value is **ARKUI_ANIMATION_PLAY_MODE_NORMAL**. Pass this parameter when a special play mode such as reverse playback or loop playback is required. .value[6]?.f32: animation playback speed. The default value is **1.0** (normal speed) when this parameter is not passed. Pass this parameter when the animation needs to be played faster or slower. A value greater than **1.0** indicates acceleration, and a value less than **1.0** indicates deceleration. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: opacity values of the start and end points. The value range is [0, 1]. Values beyond the range are automatically corrected to the boundary values. .value[1].i32: animation duration, in ms. .value[2].i32: animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). .value[3].i32: animation delay duration, in ms. .value[4].i32: number of times the animation is played. .value[5].i32: animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). .value[6].f32: animation playback speed.

**Since**: 12

### NODE_ROTATE_TRANSITION

```c
NODE_ROTATE_TRANSITION
```

**Description**

Transition rotation attribute, which takes effect only when a component is inserted or deleted. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: X-component of the rotation vector. .value[1].f32: Y-component of the rotation vector. .value[2].f32: Z-component of the rotation vector. .value[3].f32: angle, in degrees (°). .value[4].f32: line of sight, that is, the distance from the viewpoint to the z=0 plane. Value range: [0, +∞). A negative value is treated as **0**. Unit: vp. Default value: **0.0**. .value[5].i32: animation duration, in ms. .value[6].i32: animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). .value[7]?.i32: animation delay duration, in ms. If not passed, the default value is **0** (no delay). Pass this parameter when the animation needs to wait for a period of time before starting. .value[8]?.i32: number of times the animation is played. .value[9]?.i32: animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). Default value: **ARKUI_ANIMATION_PLAY_MODE_NORMAL**. .value[10]?.f32: animation playback speed. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: X-component of the rotation vector. .value[1].f32: Y-component of the rotation vector. .value[2].f32: Z-component of the rotation vector. .value[3].f32: angle, in degrees (°). .value[4].f32: line of sight, in vp. .value[5].i32: animation duration, in ms. .value[6].i32: animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). .value[7].i32: animation delay duration, in ms. .value[8].i32: number of times the animation is played. .value[9].i32: animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). .value[10].f32: animation playback speed.

**Since**: 12

### NODE_SCALE_TRANSITION

```c
NODE_SCALE_TRANSITION
```

**Description**

Transition scaling attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: scale factor along the x-axis. Default value: **1.0**. .value[1].f32: scale factor along the y-axis. Default value: **1.0**. .value[2].f32: scale factor along the z-axis. Default value: **1.0**. .value[3].i32: animation duration, in ms. .value[4].i32: animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). .value[5]?.i32: animation delay duration, in ms. If not passed, the default value is **0** (no delay). Pass this parameter when the animation needs to wait for a period of time before starting. .value[6]?.i32: number of times the animation is played. .value[7]?.i32: animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). The default value is **ARKUI_ANIMATION_PLAY_MODE_NORMAL**. .value[8]?.f32: animation playback speed. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: scale factor along the x-axis. .value[1].f32: scale factor along the y-axis. .value[2].f32: scale factor along the z-axis. .value[3].i32: animation duration, in ms. .value[4].i32: animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). .value[5].i32: animation delay duration, in ms. .value[6].i32: number of times the animation is played. .value[7].i32: animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). .value[8].f32: animation playback speed.

**Since**: 12

### NODE_TRANSLATE_TRANSITION

```c
NODE_TRANSLATE_TRANSITION
```

**Description**

Transition translation attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: translation distance along the x-axis, in vp. The default value is **0.0**. .value[1].f32: translation distance along the y-axis, in vp. The default value is **0.0**. .value[2].f32: translation distance along the z-axis, in vp. The default value is **0.0**. .value[3].i32: animation duration, in ms. .value[4].i32: animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). .value[5]?.i32: animation delay duration, in ms. If not passed, the default value is **0** (no delay). Pass this parameter when the animation needs to wait for a period of time before starting. .value[6]?.i32: number of times the animation is played. .value[7]?.i32: animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). The default value is **ARKUI_ANIMATION_PLAY_MODE_NORMAL**. .value[8]?.f32: animation playback speed. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: translation distance along the x-axis, in vp. .value[1].f32: translation distance along the y-axis, in vp. .value[2].f32: translation distance along the z-axis, in vp. .value[3].i32: animation duration, in ms. .value[4].i32: animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). .value[5].i32: animation delay duration, in ms. .value[6].i32: number of times the animation is played. .value[7].i32: animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). .value[8].f32: animation playback speed.

**Since**: 12

### NODE_MOVE_TRANSITION

```c
NODE_MOVE_TRANSITION
```

**Description**

Slide-in and slide-out of the component from the screen edge during transition. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].i32: edge from which the component slides in and out during transition. The parameter type is [ArkUI_TransitionEdge](capi-native-type-visual-h.md#arkui_transitionedge). Different enumerated values determine from which edge of the screen the component slides in and out. .value[1].i32: animation duration, in ms. .value[2].i32: animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). .value[3]?.i32: animation delay duration, in ms. The default value is **0** (no delay) when this parameter is not passed. Pass this parameter when the animation needs to wait for a period of time before starting. .value[4]?.i32: number of times the animation is played. .value[5]?.i32: animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). The default value is **ARKUI_ANIMATION_PLAY_MODE_NORMAL**. .value[6]?.f32: animation playback speed. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].i32: transition edge. The parameter type is [ArkUI_TransitionEdge](capi-native-type-visual-h.md#arkui_transitionedge). .value[1].i32: animation duration, in ms. .value[2].i32: animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). .value[3].i32: animation delay duration, in ms. .value[4].i32: number of times the animation is played. .value[5].i32: animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). .value[6].f32: animation playback speed.

**Since**: 12

### NODE_GEOMETRY_TRANSITION

```c
NODE_GEOMETRY_TRANSITION
```

**Description**

Implicit shared element transition within a component (the transition is automatically triggered when the component is inserted or deleted). This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0]?.i32: two components bound to the shared element. The value is **1** or **0**. By default, the out component does not continue to participate in the shared element animation when not yet deleted, which means that it stays in its original position. .string: ID used to set up a binding relationship. If this attribute is set to an empty string **""**, the binding relationship is cleared. The value can be dynamically changed to refresh the binding relationship. One ID can be bound to only two components, which function as in and out components. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].i32: two components bound to the shared element. The value is **1** or **0**. By default, the out component does not continue to participate in the shared element animation when not yet deleted, which means that it stays in its original position. .string: ID used to set up a binding relationship. If this attribute is set to an empty string **""**, the binding relationship is cleared. The value can be dynamically changed to refresh the binding relationship. One ID can be bound to only two components, which function as in and out components.

**Since**: 12

### NODE_TRANSITION

```c
NODE_TRANSITION = 94
```

**Description**

Transition effect when the component is inserted or deleted. This attribute can be set and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .object: transition effect when the component is inserted or deleted. The parameter type is [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md). Different **TransitionEffect** values determine the animation effect type when a component appears and disappears. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .object: transition effect when the component is inserted or deleted. The parameter type is [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md).

**Since**: 12

### NODE_MOTION_PATH

```c
NODE_MOTION_PATH = 111
```

**Description**

Motion path of the component. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .object indicates a pointer to the ArkUI_MotionPathOptions. The parameter type is [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md). Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .object indicates a pointer to the ArkUI_MotionPathOptions. The parameter type is [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md).

**Since**: 23


