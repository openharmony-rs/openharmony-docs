# Animate

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_OPACITY_TRANSITION

```c
NODE_OPACITY_TRANSITION
```

**Description**

Defines the transition opacity attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: opacity values of the start and end points. .value[1].i32: animation duration, in milliseconds. .value[2].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). .value[3]?.i32: animation delay duration, in milliseconds. .value[4]?.i32: number of times that the animation is played. .value[5]?.i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). .value[6]?.f32: animation playback speed. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: opacity values of the start and end points. .value[1].i32: animation duration, in milliseconds. .value[2].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). .value[3].i32: animation delay duration, in milliseconds. .value[4].i32: number of times that the animation is played. .value[5].i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). .value[6].f32: animation playback speed.

**Since**: 12

### NODE_ROTATE_TRANSITION

```c
NODE_ROTATE_TRANSITION
```

**Description**

Defines the transition rotation attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: X-component of the rotation vector. .value[1].f32: Y-component of the rotation vector. .value[2].f32: Z-component of the rotation vector .value[3].f32: angle. .value[4].f32: line of sight. The default value is <b>0.0f</b>. .value[5].i32: animation duration, in milliseconds. .value[6].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). .value[7]?.i32: animation delay duration, in milliseconds. .value[8]?.i32: number of times that the animation is played. .value[9]?.i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). .value[10]?.f32: animation playback speed. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: X-component of the rotation vector. .value[1].f32: Y-component of the rotation vector. .value[2].f32: Z-component of the rotation vector .value[3].f32: angle. .value[4].f32: line of sight. .value[5].i32: animation duration, in milliseconds. .value[6].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). .value[7].i32: animation delay duration, in milliseconds. .value[8].i32: number of times that the animation is played. .value[9].i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). .value[10].f32: animation playback speed.

**Since**: 12

### NODE_SCALE_TRANSITION

```c
NODE_SCALE_TRANSITION
```

**Description**

Defines the transition scaling attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: scale factor along the x-axis. .value[1].f32: scale factor along the y-axis. .value[2].f32: scale factor along the z-axis. .value[3].i32: animation duration, in milliseconds. .value[4].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). .value[5]?.i32: animation delay duration, in milliseconds. .value[6]?.i32: number of times that the animation is played. .value[7]?.i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). .value[8]?.f32: animation playback speed. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: scale factor along the x-axis. .value[1].f32: scale factor along the y-axis. .value[2].f32: scale factor along the z-axis. .value[3].i32: animation duration, in milliseconds. .value[4].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). .value[5].i32: animation delay duration, in milliseconds. .value[6].i32: number of times that the animation is played. .value[7].i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). .value[8].f32: animation playback speed.

**Since**: 12

### NODE_TRANSLATE_TRANSITION

```c
NODE_TRANSLATE_TRANSITION
```

**Description**

Defines the transition translation attribute. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: value[0].f32: translation distance along the x-axis, in vp. value[1].f32: translation distance along the y-axis, in vp. value[2].f32: translation distance along the z-axis, in vp. value[3].i32: animation duration, in milliseconds. value[4].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). value[5]?.i32: animation delay duration, in milliseconds. value[6]?.i32: number of times that the animation is played. value[7]?.i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). value[8]?.f32: animation playback speed. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): value[0].f32: translation distance along the x-axis, in vp. value[1].f32: translation distance along the y-axis, in vp. value[2].f32: translation distance along the z-axis, in vp. value[3].i32: animation duration, in milliseconds. value[4].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). value[5].i32: animation delay duration, in milliseconds. value[6].i32: number of times that the animation is played. value[7].i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). value[8].f32: animation playback speed.

**Since**: 12

### NODE_MOVE_TRANSITION

```c
NODE_MOVE_TRANSITION
```

**Description**

Defines the slide-in and slide-out of the component from the screen edge during transition. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].i32: The parameter type is [ArkUI_TransitionEdge](capi-native-type-visual-h.md#arkui_transitionedge). .value[1].i32: animation duration, in milliseconds. .value[2].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). .value[3]?.i32: animation delay duration, in milliseconds. .value[4]?.i32: number of times that the animation is played. .value[5]?.i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). .value[6]?.f32: animation playback speed. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].i32: The parameter type is [ArkUI_TransitionEdge](capi-native-type-visual-h.md#arkui_transitionedge). .value[1].i32: animation duration, in milliseconds. .value[2].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). .value[3].i32: animation delay duration, in milliseconds. .value[4].i32: number of times that the animation is played. .value[5].i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). .value[6].f32: animation playback speed.

**Since**: 12

### NODE_GEOMETRY_TRANSITION

```c
NODE_GEOMETRY_TRANSITION
```

**Description**

The implicit shared element transition within the component supports attribute setting, attribute reset, and attribute acquisition interfaces.<br> Attribute setting method parameter [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format: .value[0]?.i32: The parameter type is 1 or 0. 2 components that share element bindings, Whether to continue to participate in the shared element animation when the appearance element is not deleted, the default is false, and the original position will remain unchanged if not involved. .string is used to set the binding relationship. Set the id to "" to clear the binding relationship to avoid participating in sharing behavior. The id can be changed and the binding relationship re-established. The same ID can only be bound to two components and they are in/out roles of different types. Multiple components cannot be bound to the same id. <br> Attribute acquisition method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format: .value[0].i32: The parameter type is 1 or 0. 2 components that share element bindings, Whether to continue to participate in the shared element animation when the appearance element is not deleted, the default is not false, if not involved, the original position will remain unchanged. .string is used to set the binding relationship. Set the id to "" to clear the binding relationship to avoid participating in sharing behavior. The id can be changed and the binding relationship re-established. The same ID can only be bound to two components and they are in/out roles of different types. Multiple components cannot be bound to the same id.

**Since**: 12

### NODE_TRANSITION

```c
NODE_TRANSITION = 94
```

**Description**

Sets the transition effect when the component is inserted or deleted. This attribute can be set, and obtained as required through APIs.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .object: transition effect. The parameter type is [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md). Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .object: transition effect. The parameter type is [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md).

**Since**: 12

### NODE_MOTION_PATH

```c
NODE_MOTION_PATH = 111
```

**Description**

Defines the motion path attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .object indicates a pointer to the ArkUI_MotionPathOptions. The parameter type is [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md). Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .object indicates a pointer to the ArkUI_MotionPathOptions. The parameter type is [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md).

**Since**: 23


