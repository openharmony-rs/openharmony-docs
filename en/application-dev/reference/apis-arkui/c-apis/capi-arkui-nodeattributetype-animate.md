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

Defines the transition opacity attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].f32: opacity values of the start and end points.<br>.value[1].i32: animation duration, in milliseconds.<br>.value[2].i32: animation curve type. The value is an enum of {@link ArkUI_AnimationCurve}.<br>.value[3]?.i32: animation delay duration, in milliseconds.<br>.value[4]?.i32: number of times that the animation is played.<br>.value[5]?.i32: animation playback mode. The value is an enum of {@link ArkUI_AnimationPlayMode}.<br>.value[6]?.f32: animation playback speed.<br><br>Format of the return value {@link ArkUI_AttributeItem}:<br>.value[0].f32: opacity values of the start and end points.<br>.value[1].i32: animation duration, in milliseconds.<br>.value[2].i32: animation curve type. The value is an enum of {@link ArkUI_AnimationCurve}.<br>.value[3].i32: animation delay duration, in milliseconds. <br>.value[4].i32: number of times that the animation is played. <br>.value[5].i32: animation playback mode. The value is an enum of {@link ArkUI_AnimationPlayMode}. .value[6].f32: animation playback speed.

**Since**: 12

### NODE_ROTATE_TRANSITION

```c
NODE_ROTATE_TRANSITION
```

**Description**

Defines the transition rotation attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].f32: X-component of the rotation vector. <br>.value[1].f32: Y-component of the rotation vector. <br>.value[2].f32: Z-component of the rotation vector <br>.value[3].f32: angle. <br>.value[4].f32: line of sight. The default value is <b>0.0f</b>. <br>.value[5].i32: animation duration, in milliseconds. <br>.value[6].i32: animation curve type. The value is an enum of {@link ArkUI_AnimationCurve}. <br>.value[7]?.i32: animation delay duration, in milliseconds. <br>.value[8]?.i32: number of times that the animation is played. <br>.value[9]?.i32: animation playback mode. The value is an enum of {@link ArkUI_AnimationPlayMode}. <br>.value[10]?.f32: animation playback speed. <br><br>Format of the return value {@link ArkUI_AttributeItem}:<br>.value[0].f32: X-component of the rotation vector. <br>.value[1].f32: Y-component of the rotation vector. <br>.value[2].f32: Z-component of the rotation vector <br>.value[3].f32: angle. <br>.value[4].f32: line of sight. <br>.value[5].i32: animation duration, in milliseconds. <br>.value[6].i32: animation curve type. The value is an enum of {@link ArkUI_AnimationCurve}. <br>.value[7].i32: animation delay duration, in milliseconds. <br>.value[8].i32: number of times that the animation is played. <br>.value[9].i32: animation playback mode. The value is an enum of {@link ArkUI_AnimationPlayMode}. .value[10].f32: animation playback speed.

**Since**: 12

### NODE_SCALE_TRANSITION

```c
NODE_SCALE_TRANSITION
```

**Description**

Defines the transition scaling attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].f32: scale factor along the x-axis. <br>.value[1].f32: scale factor along the y-axis. <br>.value[2].f32: scale factor along the z-axis. <br>.value[3].i32: animation duration, in milliseconds. <br>.value[4].i32: animation curve type. The value is an enum of {@link ArkUI_AnimationCurve}. <br>.value[5]?.i32: animation delay duration, in milliseconds. <br>.value[6]?.i32: number of times that the animation is played. <br>.value[7]?.i32: animation playback mode. The value is an enum of {@link ArkUI_AnimationPlayMode}. <br>.value[8]?.f32: animation playback speed. <br><br>Format of the return value {@link ArkUI_AttributeItem}:<br>.value[0].f32: scale factor along the x-axis. <br>.value[1].f32: scale factor along the y-axis. <br>.value[2].f32: scale factor along the z-axis. <br>.value[3].i32: animation duration, in milliseconds. <br>.value[4].i32: animation curve type. The value is an enum of {@link ArkUI_AnimationCurve}. <br>.value[5].i32: animation delay duration, in milliseconds. <br>.value[6].i32: number of times that the animation is played. <br>.value[7].i32: animation playback mode. The value is an enum of {@link ArkUI_AnimationPlayMode}. .value[8].f32: animation playback speed.

**Since**: 12

### NODE_TRANSLATE_TRANSITION

```c
NODE_TRANSLATE_TRANSITION
```

**Description**

Defines the transition translation attribute. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>value[0].f32: translation distance along the x-axis, in vp.<br>value[1].f32: translation distance along the y-axis, in vp.<br>value[2].f32: translation distance along the z-axis, in vp.<br>value[3].i32: animation duration, in milliseconds. <br>value[4].i32: animation curve type. The value is an enum of {@link ArkUI_AnimationCurve}. <br>value[5]?.i32: animation delay duration, in milliseconds. <br>value[6]?.i32: number of times that the animation is played. <br>value[7]?.i32: animation playback mode. The value is an enum of {@link ArkUI_AnimationPlayMode}. <br>value[8]?.f32: animation playback speed. <br><br>Format of the return value {@link ArkUI_AttributeItem}:<br>value[0].f32: translation distance along the x-axis, in vp.<br>value[1].f32: translation distance along the y-axis, in vp.<br>value[2].f32: translation distance along the z-axis, in vp.<br>value[3].i32: animation duration, in milliseconds. <br>value[4].i32: animation curve type. The value is an enum of {@link ArkUI_AnimationCurve}. <br>value[5].i32: animation delay duration, in milliseconds. <br>value[6].i32: number of times that the animation is played. <br>value[7].i32: animation playback mode. The value is an enum of {@link ArkUI_AnimationPlayMode}. value[8].f32: animation playback speed.

**Since**: 12

### NODE_MOVE_TRANSITION

```c
NODE_MOVE_TRANSITION
```

**Description**

Defines the slide-in and slide-out of the component from the screen edge during transition. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].i32: The parameter type is {@link ArkUI_TransitionEdge}. <br>.value[1].i32: animation duration, in milliseconds.<br>.value[2].i32: animation curve type. The value is an enum of {@link ArkUI_AnimationCurve}.<br>.value[3]?.i32: animation delay duration, in milliseconds.<br>.value[4]?.i32: number of times that the animation is played.<br>.value[5]?.i32: animation playback mode. The value is an enum of {@link ArkUI_AnimationPlayMode}.<br>.value[6]?.f32: animation playback speed.<br><br>Format of the return value {@link ArkUI_AttributeItem}:<br>.value[0].i32: The parameter type is {@link ArkUI_TransitionEdge}. <br>.value[1].i32: animation duration, in milliseconds.<br>.value[2].i32: animation curve type. The value is an enum of {@link ArkUI_AnimationCurve}.<br>.value[3].i32: animation delay duration, in milliseconds. <br>.value[4].i32: number of times that the animation is played. <br>.value[5].i32: animation playback mode. The value is an enum of {@link ArkUI_AnimationPlayMode}. .value[6].f32: animation playback speed.

**Since**: 12

### NODE_GEOMETRY_TRANSITION

```c
NODE_GEOMETRY_TRANSITION
```

**Description**

The implicit shared element transition within the component supports attribute setting, attribute reset, and attribute acquisition interfaces.<br> Attribute setting method parameter {@link ArkUI_AttributeItem} format: <br>.value[0]?.i32: The parameter type is 1 or 0. 2 components that share element bindings,<br>Whether to continue to participate in the shared element animation when the appearance element is not deleted,<br>the default is false, and the original position will remain unchanged if not involved. <br>.string is used to set the binding relationship. Set the id to "" to<br>clear the binding relationship to avoid participating in sharing behavior. <br>The id can be changed and the binding relationship re-established.<br>The same ID can only be bound to two components and they are in/out roles of different types.<br>Multiple components cannot be bound to the same id. <br><br>Attribute acquisition method return value {@link ArkUI_AttributeItem} format: .value[0].i32: The parameter type is 1 or 0. 2 components that share element bindings, Whether to continue to participate in the shared element animation when the appearance element is not deleted, the default is not false, if not involved, the original position will remain unchanged. .string is used to set the binding relationship. Set the id to "" to clear the binding relationship to avoid participating in sharing behavior. The id can be changed and the binding relationship re-established. The same ID can only be bound to two components and they are in/out roles of different types. Multiple components cannot be bound to the same id.

**Since**: 12

### NODE_TRANSITION

```c
NODE_TRANSITION = 94
```

**Description**

Sets the transition effect when the component is inserted or deleted. This attribute can be set, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.object: transition effect. The parameter type is {@link ArkUI_TransitionEffect}. <br><br>Format of the return value {@link ArkUI_AttributeItem}:<br>.object: transition effect. The parameter type is {@link ArkUI_TransitionEffect}.

**Since**: 12

### NODE_MOTION_PATH

```c
NODE_MOTION_PATH = 111
```

**Description**

Defines the motion path attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute: <br>.object indicates a pointer to the ArkUI_MotionPathOptions. The parameter type is<br>{@link ArkUI_MotionPathOptions}. <br><br>Format of the return value {@link ArkUI_AttributeItem}: <br>.object indicates a pointer to the ArkUI_MotionPathOptions. The parameter type is<br>{@link ArkUI_MotionPathOptions}.

**Since**: 23


