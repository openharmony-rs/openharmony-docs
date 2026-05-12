# ArkUI_NodeAttributeType (Animation and Visual Effect Attributes)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the animation and visual effect attribute types that can be set by ArkUI on the native side, including image transformation, gradient, shadow, blur, and transition.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)


## NODE_TRANSLATE

```c
NODE_TRANSLATE = 8
```

Translate attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Distance to translate along the x-axis, in vp. The default value is **0**.|
| .value[1].f32 | Distance to translate along the y-axis, in vp. The default value is **0**.|
| .value[2].f32 | Distance to translate along the z-axis, in vp. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Distance to translate along the x-axis, in vp.|
| .value[1].f32 | Distance to translate along the y-axis, in vp.|
| .value[2].f32 | Distance to translate along the z-axis, in vp.|

## NODE_SCALE

```c
NODE_SCALE = 9
```

Scale attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Scale factor along the x-axis. The default value is **1**.|
| .value[1].f32 | Scale factor along the y-axis. The default value is **1**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Scale factor along the x-axis.|
| .value[1].f32 | Scale factor along the y-axis.|

## NODE_ROTATE

```c
NODE_ROTATE = 10
```

Rotate attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | X-coordinate of the rotation axis vector. The default value is **0**.|
| .value[1].f32 | Y-coordinate of the rotation axis vector. The default value is **0**.|
| .value[2].f32 | Z-coordinate of the rotation axis vector. The default value is **0**.|
| .value[3].f32 | Rotation angle. The default value is **0**.|
| .value[4].f32 | Line of sight, that is, the distance from the viewpoint to the z=0 plane, in vp. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | X-coordinate of the rotation axis vector.|
| .value[1].f32 | Y-coordinate of the rotation axis vector.|
| .value[2].f32 | Z-coordinate of the rotation axis vector.|
| .value[3].f32 | Rotation angle.|
| .value[4].f32 | Line of sight, that is, the distance from the viewpoint to the z=0 plane, in vp.|

## NODE_BRIGHTNESS

```c
NODE_BRIGHTNESS = 11
```

Brightness attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Brightness value. The default value is **1.0**, and the recommended value range is [0, 2.0].|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Brightness value.|

## NODE_SATURATION

```c
NODE_SATURATION = 12
```

Saturation attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Saturation value. The default value is **1.0**, and the recommended value range is [0, 50.0).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Saturation value.|

## NODE_BLUR

```c
NODE_BLUR = 13
```

Blur attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Blur radius. A larger value indicates a higher blur degree. If the value is 0, the content is not blurred. If the value is less than 0, it is treated as 0 and no error code is returned. The unit is vp. The default value is **0.0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Blur radius. A larger value indicates a higher blur degree. If the value is 0, the content is not blurred. The unit is vp.|

## NODE_LINEAR_GRADIENT

```c
NODE_LINEAR_GRADIENT = 14
```

Gradient attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Start angle of the linear gradient. When [ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection) is set to **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM**, the **angle** attribute takes effect. Otherwise, the **direction** attribute is used as the main layout mode. A positive value indicates a clockwise rotation from the origin, (0, 0). The default value is **180**.|
| .value[1].i32 | Direction of the linear gradient. When the **direction** attribute is set to a value other than **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM**, the **angle** attribute does not take effect. The parameter type is [ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection).|
| .value[2].i32 | Whether the colors are repeated. The default value is **false**.|
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.|
| colors | Colors of the color stops.|
| stops | Stop positions of the color stops.|
| size | Number of colors.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Start angle of the linear gradient. The set value is used only when **direction** is set to **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM**. In other cases, the default value is used.|
| .value[1].i32 | Direction of the linear gradient.|
| .value[2].i32 | Whether the colors are repeated.|
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.|
| colors | Colors of the color stops.|
| stops | Stop positions of the color stops.|
| size | Number of colors.|

## NODE_OPACITY

```c
NODE_OPACITY = 16
```

Opacity attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Opacity value. The default value is **1**. The value ranges from 0 to 1.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Opacity value. The value ranges from 0 to 1.|

## NODE_Z_INDEX

```c
NODE_Z_INDEX = 21
```

Z-index attribute for the stack sequence. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Z-index value.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Z-index value.|

## NODE_VISIBILITY

```c
NODE_VISIBILITY = 22
```

Visibility attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to show or hide the component. The parameter type is [ArkUI_Visibility](capi-native-type-h.md#arkui_visibility). The default value is **ARKUI_VISIBILITY_VISIBLE**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the component is shown or hidden. The parameter type is [ArkUI_Visibility](capi-native-type-h.md#arkui_visibility). The default value is **ARKUI_VISIBILITY_VISIBLE**.|

## NODE_CLIP

```c
NODE_CLIP = 23
```

Clip attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to clip the area of child components that extends beyond the bounds of the parent component. The value **0** indicates not to clip, and the value **1** indicates to clip. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the area of child components that extends beyond the bounds of the parent component is clipped. The value **0** indicates no clipping, and the value **1** indicates clipping.|

## NODE_CLIP_SHAPE

```c
NODE_CLIP_SHAPE = 24
```

Clipping shape on the component. This attribute can be set and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters:**

1. Rectangle<br>

| Name| Description|
| -- | -- |
| .value[0].i32 | Shape type. The parameter type is **ArkUI_ClipType**. The value is **ARKUI_CLIP_TYPE_RECTANGLE**.|
| .value[1].f32 | Width of the rectangle, in vp.|
| .value[2].f32 | Height of the rectangle, in vp.|
| .value[3].f32 | Width of the rounded corner of the rectangle, in vp.|
| .value[4].f32 | Height of the rounded corner of the rectangle, in vp.|
| .value[5]?.f32 | Radius of the upper left corner of the rectangle, in vp.|
| .value[6]?.f32 | Radius of the lower left corner of the rectangle, in vp.|
| .value[7]?.f32 | Radius of the upper right corner of the rectangle, in vp.|
| .value[8]?.f32 | Radius of the lower right corner of the rectangle, in vp.|
| .object | Coordinate offset of the rectangle. The parameter type is **ArkUI_RenderNodeClipOption**. It takes effect only when the **.object** parameter is passed.|

2. Circle<br>

| Name| Description|
| -- | -- |
| .value[0].i32 | Shape type. The parameter type is **ArkUI_ClipType**. The value is **ARKUI_CLIP_TYPE_CIRCLE**.|
| .value[1].f32 | Width of the circle, in vp.|
| .value[2].f32 | Height of the circle, in vp.|
| .object | Coordinate offset of the circle. The parameter type is **ArkUI_RenderNodeClipOption**. It takes effect only when the **.object** parameter is passed.|

3. Ellipse<br>

| Name| Description|
| -- | -- |
| .value[0].i32 | Shape type. The parameter type is **ArkUI_ClipType**. The value is **ARKUI_CLIP_TYPE_ELLIPSE**.|
| .value[1].f32 | Width of the ellipse, in vp.|
| .value[2].f32 | Height of the ellipse, in vp.|
| .object | Coordinate offset of the ellipse. The parameter type is **ArkUI_RenderNodeClipOption**. It takes effect only when the **.object** parameter is passed.|

4. Path<br>

| Name| Description|
| -- | -- |
| .value[0].i32 | Shape type. The parameter type is **ArkUI_ClipType**. The value is **ARKUI_CLIP_TYPE_PATH**.|
| .value[1].f32 | Width of the path, in vp.|
| .value[2].f32 | Height of the path, in vp.|
| .string | Command string for drawing the path.|
| .object | Command for drawing the path. The parameter type is **ArkUI_RenderNodeClipOption**. It takes effect only when the **.object** parameter is passed.|

**Returns**

1. Rectangle<br>

| Type| Description|
| -- | -- |
| .value[0].i32 | Shape type. The parameter type is **ArkUI_ClipType**. The value is **ARKUI_CLIP_TYPE_RECTANGLE**.|
| .value[1].f32 | Width of the rectangle, in vp.|
| .value[2].f32 | Height of the rectangle, in vp.|
| .value[3].f32 | Width of the rounded corner of the rectangle, in vp.|
| .value[4].f32 | Height of the rounded corner of the rectangle, in vp.|
| .value[5]?.f32 | Radius of the upper left corner of the rectangle, in vp.|
| .value[6]?.f32 | Radius of the lower left corner of the rectangle, in vp.|
| .value[7]?.f32 | Radius of the upper right corner of the rectangle, in vp.|
| .value[8]?.f32 | Radius of the lower right corner of the rectangle, in vp.|
| .value[9]?.f32 | Horizontal coordinate offset of the rectangle, in vp.|
| .value[10]?.f32 | Vertical coordinate offset of the rectangle, in vp.|

2. Circle<br>

| Type| Description|
| -- | -- |
| .value[0].i32 | Shape type. The parameter type is **ArkUI_ClipType**. The value is **ARKUI_CLIP_TYPE_CIRCLE**.|
| .value[1].f32 | Width of the circle, in vp.|
| .value[2].f32 | Height of the circle, in vp.|
| .value[3]?.f32 | Horizontal coordinate offset of the circle, in vp.|
| .value[4]?.f32 | Vertical coordinate offset of the circle, in vp.|

3. Ellipse<br>

| Type| Description|
| -- | -- |
| .value[0].i32 | Shape type. The parameter type is **ArkUI_ClipType**. The value is **ARKUI_CLIP_TYPE_ELLIPSE**.|
| .value[1].f32 | Width of the ellipse, in vp.|
| .value[2].f32 | Height of the ellipse, in vp.|
| .value[3]?.f32 | Horizontal coordinate offset of the ellipse, in vp.|
| .value[4]?.f32 | Vertical coordinate offset of the ellipse, in vp.|

4. Path<br>

| Type| Description|
| -- | -- |
| .value[0].i32 | Shape type. The parameter type is **ArkUI_ClipType**. The value is **ARKUI_CLIP_TYPE_PATH**.|
| .value[1].f32 | Width of the path, in vp.|
| .value[2].f32 | Height of the path, in vp.|
| .string | Command string for drawing the path.|


## NODE_TRANSFORM

```c
NODE_TRANSFORM = 25
```

Transform attribute, which can be used to translate, rotate, and scale images. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0...15].f32 | 16 floating-point numbers. The value of **size** in [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) cannot be **0**.|
| .object | Pointer to [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md). The value of **size** in [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0...15].f32 | 16 floating-point numbers.|

## NODE_SHADOW

```c
NODE_SHADOW = 28
```

Shadow attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Shadow effect of the current component. The parameter type is [ArkUI_ShadowStyle](capi-native-type-h.md#arkui_shadowstyle).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Shadow effect of the current component. The parameter type is [ArkUI_ShadowStyle](capi-native-type-h.md#arkui_shadowstyle).|

## NODE_CUSTOM_SHADOW

```c
NODE_CUSTOM_SHADOW = 29
```

Custom shadow effect. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0]?.f32 | Blur radius of the shadow, in px.|
| .value[1]?.i32 | Whether to enable the the coloring strategy. The value **1** means to enable the coloring strategy, and **0** means the opposite. The default value is **0**.|
| .value[2]?.f32 | Offset of the shadow along the x-axis, in px.|
| .value[3]?.f32 | Offset of the shadow along the y-axis, in px.|
| .value[4]?.i32 | Shadow type. The parameter type is [ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype). The default value is **ARKUI_SHADOW_TYPE_COLOR**.|
| .value[5]?.u32 | Shadow color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|
| .value[6]?.u32 | Whether to fill the shadow. The value **1** means to fill the shadow, and **0** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Blur radius of the shadow, in px.|
| .value[1].i32 | Whether the coloring strategy is enabled.|
| .value[2].f32 | Offset of the shadow along the x-axis, in px.|
| .value[3].f32 | Offset of the shadow along the y-axis, in px.|
| .value[4].i32 | Shadow type. The parameter type is [ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype). The default value is **ARKUI_SHADOW_TYPE_COLOR**.|
| .value[5].u32 | Shadow color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|
| .value[6].u32 | Whether the shadow is filled. The value **1** means that the shadow is filled, and **0** means the opposite.|

## NODE_BACKGROUND_BLUR_STYLE

```c
NODE_BACKGROUND_BLUR_STYLE = 32
```

Background blur attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Blur type. The value is an enumerated value of [ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle).|
| .value[1]?.i32 | Color mode. The value is an enumerated value of [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode).|
| .value[2]?.i32 | Adaptive color mode. The value is an enumerated value of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor).|
| .value[3]?.f32 | Blur degree. The value range is [0.0, 1.0].|
| .value[4]?.f32 | Start boundary of grayscale blur.|
| .value[5]?.f32 | End boundary of grayscale blur.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Blur type. The value is an enumerated value of [ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle).|
| .value[1].i32 | Color mode. The value is an enumerated value of [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode).|
| .value[2].i32 | Adaptive color mode. The value is an enumerated value of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor).|
| .value[3].f32 | Blur degree. The value range is [0.0, 1.0].|
| .value[4].f32 | Start boundary of grayscale blur.|
| .value[5].f32 | End boundary of grayscale blur.|

## NODE_TRANSFORM_CENTER

```c
NODE_TRANSFORM_CENTER = 33
```

Transform center attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>
Note: If the coordinate is expressed in a number that represents a percentage, the attribute obtaining API returns the calculated value in vp.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0]?.f32 | X-coordinate of the center point, in vp.|
| .value[1]?.f32 | Y-coordinate of the center point, in vp.|
| .value[2]?.f32 | Z-coordinate of the center point, in vp.|
| .value[3]?.f32 | X-coordinate of the center point, expressed in a number that represents a percentage. For example, 0.2 indicates 20%. This attribute overwrites value[0].f32. The default value is **0.5f**.|
| .value[4]?.f32 | Y-coordinate of the center point, expressed in a number that represents a percentage. For example, 0.2 indicates 20%. This attribute overwrites value[1].f32. The default value is **0.5f**.|
| .value[5]?.f32 | Z-coordinate of the center point, expressed in a number that represents a percentage. For example, 0.2 indicates 20%. This attribute overwrites value[2].f32. The default value is **0.0f**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | X-coordinate of the center point, in vp.|
| .value[1].f32 | Y-coordinate of the center point, in vp.|
| .value[2].f32 | Z-coordinate of the center point, in vp.|

## NODE_MOTION_PATH

```c
NODE_MOTION_PATH = 111
```

Motion path of the component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 23


**Parameters**

| Name| Description|
| -- | -- |
| .object | Pointer to the motion path configuration item of the path animation. The parameter type is [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Pointer to the motion path configuration item of the path animation. The parameter type is [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md).|

## NODE_OPACITY_TRANSITION

```c
NODE_OPACITY_TRANSITION = 34
```

Transition opacity attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Opacity values of the start and end points.|
| .value[1].i32 | Animation duration, in ms.|
| .value[2].i32 | Animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).|
| .value[3]?.i32 | Animation delay duration, in ms.|
| .value[4]?.i32 | Number of times the animation is played.|
| .value[5]?.i32 | Animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).|
| .value[6]?.f32 | Animation playback speed.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Opacity values of the start and end points.|
| .value[1].i32 | Animation duration, in ms.|
| .value[2].i32 | Animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).|
| .value[3].i32 | Animation delay duration, in ms.|
| .value[4].i32 | Number of times the animation is played.|
| .value[5].i32 | Animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).|
| .value[6].f32 | Animation playback speed.|

## NODE_ROTATE_TRANSITION

```c
NODE_ROTATE_TRANSITION = 35
```

Transition rotation attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | X-component of the rotation vector.|
| .value[1].f32 | Y-component of the rotation vector.|
| .value[2].f32 | Z-component of the rotation vector.|
| .value[3].f32 | Angle.|
| .value[4].f32 | Line of sight. The default value is **0.0f**.|
| .value[5].i32 | Animation duration, in ms.|
| .value[6].i32 | Animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).|
| .value[7]?.i32 | Animation delay duration, in ms.|
| .value[8]?.i32 | Number of times the animation is played.|
| .value[9]?.i32 | Animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).|
| .value[10]?.f32 | Animation playback speed.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | X-component of the rotation vector.|
| .value[1].f32 | Y-component of the rotation vector.|
| .value[2].f32 | Z-component of the rotation vector.|
| .value[3].f32 | Angle.|
| .value[4].f32 | Line of sight.|
| .value[5].i32 | Animation duration, in ms.|
| .value[6].i32 | Animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).|
| .value[7].i32 | Animation delay duration, in ms.|
| .value[8].i32 | Number of times the animation is played.|
| .value[9].i32 | Animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).|
| .value[10].f32 | Animation playback speed.|

## NODE_SCALE_TRANSITION

```c
NODE_SCALE_TRANSITION = 36
```

Transition scaling attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Scale factor along the x-axis.|
| .value[1].f32 | Scale factor along the y-axis.|
| .value[2].f32 | Scale factor along the z-axis.|
| .value[3].i32 | Animation duration, in ms.|
| .value[4].i32 | Animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).|
| .value[5]?.i32 | Animation delay duration, in ms.|
| .value[6]?.i32 | Number of times the animation is played.|
| .value[7]?.i32 | Animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).|
| .value[8]?.f32 | Animation playback speed.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Scale factor along the x-axis.|
| .value[1].f32 | Scale factor along the y-axis.|
| .value[2].f32 | Scale factor along the z-axis.|
| .value[3].i32 | Animation duration, in ms.|
| .value[4].i32 | Animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).|
| .value[5].i32 | Animation delay duration, in ms.|
| .value[6].i32 | Number of times the animation is played.|
| .value[7].i32 | Animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).|
| .value[8].f32 | Animation playback speed.|

## NODE_TRANSLATE_TRANSITION

```c
NODE_TRANSLATE_TRANSITION = 37
```

Transition translation attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Translation distance along the x-axis, in vp. The default value is **0.0**.|
| .value[1].f32 | Translation distance along the y-axis, in vp. The default value is **0.0**.|
| .value[2].f32 | Translation distance along the z-axis, in vp. The default value is **0.0**.|
| .value[3].i32 | Animation duration, in ms.|
| .value[4].i32 | Animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).|
| .value[5]?.i32 | Animation delay duration, in ms.|
| .value[6]?.i32 | Number of times the animation is played.|
| .value[7]?.i32 | Animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).|
| .value[8]?.f32 | Animation playback speed.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Translation distance along the x-axis, in vp.|
| .value[1].f32 | Translation distance along the y-axis, in vp.|
| .value[2].f32 | Translation distance along the z-axis, in vp.|
| .value[3].i32 | Animation duration, in ms.|
| .value[4].i32 | Animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).|
| .value[5].i32 | Animation delay duration, in ms.|
| .value[6].i32 | Number of times the animation is played.|
| .value[7].i32 | Animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).|
| .value[8].f32 | Animation playback speed.|

## NODE_MOVE_TRANSITION

```c
NODE_MOVE_TRANSITION = 38
```

Slide-in and slide-out of the component from the screen edge during transition. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Transition edge. The parameter type is [ArkUI_TransitionEdge](capi-native-type-h.md#arkui_transitionedge).|
| .value[1].i32 | Animation duration, in ms.|
| .value[2].i32 | Animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).|
| .value[3]?.i32 | Animation delay duration, in ms.|
| .value[4]?.i32 | Number of times the animation is played.|
| .value[5]?.i32 | Animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).|
| .value[6]?.f32 | Animation playback speed.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Transition edge. The parameter type is [ArkUI_TransitionEdge](capi-native-type-h.md#arkui_transitionedge).|
| .value[1].i32 | Animation duration, in ms.|
| .value[2].i32 | Animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).|
| .value[3].i32 | Animation delay duration, in ms.|
| .value[4].i32 | Number of times the animation is played.|
| .value[5].i32 | Animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).|
| .value[6].f32 | Animation playback speed.|

## NODE_SWEEP_GRADIENT

```c
NODE_SWEEP_GRADIENT = 43
```

Sweep gradient effect. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0]?.f32 | X-coordinate of the sweep gradient center relative to the upper left corner of the component.|
| .value[1]?.f32 | Y-coordinate of the sweep gradient center relative to the upper left corner of the component.|
| .value[2]?.f32 | Start point of the sweep gradient. The default value is **0**.|
| .value[3]?.f32 | End point of the sweep gradient. The default value is **0**.|
| .value[4]?.f32 | Rotation angle of the sweep gradient. The default value is **0**.|
| .value[5]?.i32 | Whether the colors are repeated. The value **0** means that the colors are not repeated, and **1** means the opposite.|
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.|
| colors | Colors of the color stops.|
| stops | Stop positions of the color stops.|
| size | Number of colors.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | X-coordinate of the sweep gradient center relative to the upper left corner of the component.|
| .value[1].f32 | Y-coordinate of the sweep gradient center relative to the upper left corner of the component.|
| .value[2].f32 | Start point of the sweep gradient. The default value is **0**.|
| .value[3].f32 | End point of the sweep gradient. The default value is **0**.|
| .value[4].f32 | Rotation angle of the sweep gradient. The default value is **0**.|
| .value[5].i32 | Whether the colors are repeated. The value **0** means that the colors are not repeated, and **1** means the opposite.|
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.|
| colors | Colors of the color stops.|
| stops | Stop positions of the color stops.|
| size | Number of colors.|

## NODE_RADIAL_GRADIENT

```c
NODE_RADIAL_GRADIENT = 44
```

Radial gradient effect. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0]?.f32 | X-coordinate of the radial gradient center relative to the upper left corner of the component.|
| .value[1]?.f32 | Y-coordinate of the radial gradient center relative to the upper left corner of the component.|
| .value[2]?.f32 | Radius of the radial gradient. The default value is **0**.|
| .value[3]?.i32 | Whether the colors are repeated. The value **0** means that the colors are not repeated, and **1** means the opposite.|
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.|
| colors | Colors of the color stops.|
| stops | Stop positions of the color stops.|
| size | Number of colors.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | X-coordinate of the radial gradient center relative to the upper left corner of the component.|
| .value[1].f32 | Y-coordinate of the radial gradient center relative to the upper left corner of the component.|
| .value[2].f32 | Radius of the radial gradient. The default value is **0**.|
| .value[3].i32 | Whether the colors are repeated. The value **0** means that the colors are not repeated, and **1** means the opposite.|
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.|
| colors | Colors of the color stops.|
| stops | Stop positions of the color stops.|
| size | Number of colors.|

## NODE_MASK

```c
NODE_MASK = 45
```

Adds a mask of the specified shape to the component. This attribute can be set and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| 1. Rectangle| .value[0].u32: fill color, in 0xARGB format.<br>.value[1].u32: stroke color, in 0xARGB format.<br>.value[2].f32: stroke width, in vp.<br>.value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-h.md#arkui_masktype). The value is **ARKUI_MASK_TYPE_RECTANGLE**.<br>.value[4].f32: width of the rectangle, in vp.<br>.value[5].f32: height of the rectangle, in vp.<br>.value[6].f32: width of the rounded corner of the rectangle, in vp.<br>.value[7].f32: height of the rounded corner of the rectangle, in vp.<br>.value[8]?.f32: radius of the upper left corner of the rectangle, in vp.<br>.value[9]?.f32: radius of the lower left corner of the rectangle, in vp.<br>.value[10]?.f32: radius of the upper right corner of the rectangle, in vp.<br>.value[11]?.f32: radius of the lower right corner of the rectangle, in vp.|
| 2. Circle| .value[0].u32: fill color, in 0xARGB format.<br>.value[1].u32: stroke color, in 0xARGB format.<br>.value[2].f32: stroke width, in vp.<br>.value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-h.md#arkui_masktype). The value is **ARKUI_MASK_TYPE_CIRCLE**.<br>.value[4].f32: width of the circle, in vp.<br>.value[5].f32: height of the circle, in vp.|
| 3. Ellipse| .value[0].u32: fill color, in 0xARGB format.<br>.value[1].u32: stroke color, in 0xARGB format.<br>.value[2].f32: stroke width, in vp.<br>.value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-h.md#arkui_masktype). The value is **ARKUI_MASK_TYPE_ELLIPSE**.<br>.value[4].f32: width of the ellipse, in vp.<br>.value[5].f32: height of the ellipse, in vp.|
| 4. Path| .value[0].u32: fill color, in 0xARGB format.<br>.value[1].u32: stroke color, in 0xARGB format.<br>.value[2].f32: stroke width, in vp.<br>.value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-h.md#arkui_masktype). The value is **ARKUI_MASK_TYPE_PATH**.<br>.value[4].f32: width of the path, in vp.<br>.value[5].f32: height of the path, in vp.<br>.string: command string for drawing the path.|
| 5. Progress| .value[0].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-h.md#arkui_masktype). The value is **ARKUI_MASK_TYPE_PROGRESS**.<br>.value[1].f32: current value of the progress indicator.<br>.value[2].f32: maximum value of the progress indicator.<br>.value[3].u32: color of the progress indicator.|

**Returns**

| Type| Description|
| -- | -- |
| 1. Rectangle| .value[0].u32: fill color, in 0xARGB format.<br>.value[1].u32: stroke color, in 0xARGB format.<br>.value[2].f32: stroke width, in vp.<br>.value[3].i32: mask type.<br>.value[4].f32: width of the rectangle, in vp.<br>.value[5].f32: height of the rectangle, in vp.<br>.value[6].f32: width of the rounded corner of the rectangle, in vp.<br>.value[7].f32: height of the rounded corner of the rectangle, in vp.<br>.value[8]?.f32: radius of the upper left corner of the rectangle, in vp.<br>.value[9]?.f32: radius of the lower left corner of the rectangle, in vp.<br>.value[10]?.f32: radius of the upper right corner of the rectangle, in vp.<br>.value[11]?.f32: radius of the lower right corner of the rectangle, in vp.|
| 2. Circle| .value[0].u32: fill color, in 0xARGB format.<br>.value[1].u32: stroke color, in 0xARGB format.<br>.value[2].f32: stroke width, in vp.<br>.value[3].i32: mask type.<br>.value[4].f32: width of the circle, in vp.<br>.value[5].f32: height of the circle, in vp.|
| 3. Ellipse| .value[0].u32: fill color, in 0xARGB format.<br>.value[1].u32: stroke color, in 0xARGB format.<br>.value[2].f32: stroke width, in vp.<br>.value[3].i32: mask type.<br>.value[4].f32: width of the ellipse, in vp.<br>.value[5].f32: height of the ellipse, in vp.|
| 4. Path| .value[0].u32: fill color, in 0xARGB format.<br>.value[1].u32: stroke color, in 0xARGB format.<br>.value[2].f32: stroke width, in vp.<br>.value[3].i32: mask type.<br>.value[4].f32: width of the path, in vp.<br>.value[5].f32: height of the path, in vp.<br>.string: command string for drawing the path.|
| 5. Progress| .value[0].i32: mask type.<br>.value[1].f32: current value of the progress indicator.<br>.value[2].f32: maximum value of the progress indicator.<br>.value[3].u32: color of the progress indicator.|

## NODE_BLEND_MODE

```c
NODE_BLEND_MODE = 46
```

Blends the component's background with the content of the component's child node. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Blend mode of the current component. The parameter type is [ArkUI_BlendMode](capi-native-type-h.md#arkui_blendmode). The default value is **ARKUI_BLEND_MODE_NONE**.|
| .value[1]?.i32 | How the specified blend mode is applied. The parameter type is [ArkUI_BlendApplyType](capi-native-type-h.md#arkui_blendapplytype). The default value is **BLEND_APPLY_TYPE_FAST**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Blend mode of the current component. The parameter type is [ArkUI_BlendMode](capi-native-type-h.md#arkui_blendmode). The default value is **ARKUI_BLEND_MODE_NONE**.|
| .value[1].i32 | How the specified blend mode is applied. The parameter type is [ArkUI_BlendApplyType](capi-native-type-h.md#arkui_blendapplytype). The default value is **BLEND_APPLY_TYPE_FAST**.|

## NODE_GRAY_SCALE

```c
NODE_GRAY_SCALE = 49
```

Grayscale effect. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Grayscale conversion ratio. The value ranges from 0 to 1. The default value is **0**. For example, **0.5** indicates a 50% grayscale conversion ratio.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Grayscale conversion ratio. The value ranges from 0 to 1.|

## NODE_INVERT

```c
NODE_INVERT = 50
```

Image inversion ratio. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Image inversion ratio. The value ranges from 0 to 1. The default value is **0**. For example, **0.5** indicates a 50% image inversion ratio.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Image inversion ratio. The value ranges from 0 to 1.|

## NODE_SEPIA

```c
NODE_SEPIA = 51
```

Sepia conversion ratio. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Sepia conversion ratio. The value ranges from 0 to 1. The default value is **0**. For example, **0.5** indicates a 50% sepia conversion ratio.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Sepia conversion ratio. The value ranges from 0 to 1.|

## NODE_CONTRAST

```c
NODE_CONTRAST = 52
```

Contrast attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Contrast. If the value is 1, the source image is displayed. A larger value indicates a higher contrast. The default value is **1**. The value range is [0, 10).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Contrast. The value range is [0, 10).|

## NODE_FOREGROUND_COLOR

```c
NODE_FOREGROUND_COLOR = 53
```

Foreground color attribute, which can be set and obtained as required through APIs. However, the reset API has no effect on this attribute.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Color, in 0xARGB format. For example, **0xFFFF0000** indicates red. The default value is **0xFF000000**.|
| .value[0].i32 | Color enum **ArkUI_ColoringStrategy**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Color, in 0xARGB format.|

## NODE_OUTLINE_WIDTH

```c
NODE_OUTLINE_WIDTH = 70
```

Outline width of an element, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Width of the left outline, in vp.|
| .value[1].f32 | Width of the top outline, in vp.|
| .value[2].f32 | Width of the right outline, in vp.|
| .value[3].f32 | Width of the bottom outline, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Width of the left outline, in vp.|
| .value[1].f32 | Width of the top outline, in vp.|
| .value[2].f32 | Width of the right outline, in vp.|
| .value[3].f32 | Width of the bottom outline, in vp.|

## NODE_GEOMETRY_TRANSITION

```c
NODE_GEOMETRY_TRANSITION = 75
```

Implicit shared element transition. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0]?.i32 | Two components bound to the shared element. The value is **1** or **0**. By default, the out component does not continue to participate in the shared element animation when not yet deleted, which means that it stays in its original position.|
| .string | ID used to set up a binding relationship. If this attribute is set to an empty string **""**, the binding relationship is cleared. The value can be dynamically changed to refresh the binding relationship. One ID can be bound to only two components, which function as in and out components.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Two components bound to the shared element. The value is **1** or **0**. The default value is **false**. By default, the out component does not continue to participate in the shared element animation when not yet deleted, which means that it stays in its original position.|
| .string | ID used to set up a binding relationship. If this attribute is set to an empty string **""**, the binding relationship is cleared. The value can be dynamically changed to refresh the binding relationship. One ID can be bound to only two components, which function as in and out components.|

## NODE_RENDER_FIT

```c
NODE_RENDER_FIT = 77
```

How the final state of the component's content is rendered during its width and height animation process. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | How the final state of the component's content is rendered. The value is an enumerated value of [ArkUI_RenderFit](capi-native-type-h.md#arkui_renderfit).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | How the final state of the component's content is rendered. The value is an enumerated value of [ArkUI_RenderFit](capi-native-type-h.md#arkui_renderfit).|

## NODE_OUTLINE_COLOR

```c
NODE_OUTLINE_COLOR = 78
```

Outline color attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Color of the four outlines, in 0xARGB format, for example, **0xFFFF11FF**.|
| .value[0].u32 | Color of the top outline, in 0xARGB format, for example, **0xFFFF11FF**.|
| .value[1].u32 | Color of the right outline, in 0xARGB format, for example, **0xFFFF11FF**.|
| .value[2].u32 | Color of the bottom outline, in 0xARGB format, for example, **0xFFFF11FF**.|
| .value[3].u32 | Color of the left outline, in 0xARGB format, for example, **0xFFFF11FF**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Color of the top outline, in 0xARGB format, for example, **0xFFFF11FF**.|
| .value[1].u32 | Color of the right outline, in 0xARGB format, for example, **0xFFFF11FF**.|
| .value[2].u32 | Color of the bottom outline, in 0xARGB format, for example, **0xFFFF11FF**.|
| .value[3].u32 | Color of the left outline, in 0xARGB format, for example, **0xFFFF11FF**.|

## NODE_COLOR_BLEND

```c
NODE_COLOR_BLEND = 81
```

Applies a color blend effect to the component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Color to blend with the component, in 0xARGB format. The default value is **0x00000000**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Color to blend with the component, in 0xARGB format, for example, **0xFFFF11FF**.|

## NODE_FOREGROUND_BLUR_STYLE

```c
NODE_FOREGROUND_BLUR_STYLE = 82
```

Applies a foreground blur style to the component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Foreground blur style. The value is an enumerated value of [ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle).|
| .value[1]?.i32 | Color mode used for the foreground blur. The value is an enumerated value of [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode).|
| .value[2]?.i32 | Adaptive color mode used for the foreground blur. The value is an enumerated value of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor).|
| .value[3]?.f32 | Blur degree. The value range is [0.0, 1.0].|
| .value[4]?.i32 | Brightness of black in the grayscale blur. The value range is [0, 127].|
| .value[5]?.i32 | Degree of darkening the white color in the grayscale blur. The value range is [0, 127].|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Foreground blur style. The value is an enumerated value of [ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle).|
| .value[1].i32 | Color mode used for the foreground blur. The value is an enumerated value of [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode).|
| .value[2].i32 | Adaptive color mode used for the foreground blur. The value is an enumerated value of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor).|
| .value[3].f32 | Blur degree. The value range is [0.0, 1.0].|
| .value[4].i32 | Brightness of black in the grayscale blur. The value range is [0, 127].|
| .value[5].i32 | Degree of darkening the white color in the grayscale blur. The value range is [0, 127].|

## NODE_TRANSITION

```c
NODE_TRANSITION = 94
```

Transition effect when the component is inserted or deleted. This attribute can be set and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .object | Transition effect. The parameter type is [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Transition effect. The parameter type is [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md).|

## NODE_BACKDROP_BLUR

```c
NODE_BACKDROP_BLUR = 99
```

Background blur effect. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Background blur radius. The value range is [0,+∞). The unit is px. The default value is **0.0**.|
| .value[1]?.f32 | Brightness of black in the grayscale blur. The value range is [0, 127].|
| .value[2]?.f32 | Degree of darkening the white color in the grayscale blur. The value range is [0, 127].|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Background blur radius. The value range is [0,+∞). The unit is px.|
| .value[1].f32 | Brightness of black in the grayscale blur. The value range is [0, 127].|
| .value[2].f32 | Degree of darkening the white color in the grayscale blur. The value range is [0, 127].|

## NODE_BACKGROUND_IMAGE_RESIZABLE_WITH_SLICE

```c
NODE_BACKGROUND_IMAGE_RESIZABLE_WITH_SLICE = 100
```

Resizable attribute of a background image when it is stretched. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Pixel value of the image that remains unchanged when the left side of the image is stretched, in vp.|
| .value[1].f32 | Pixel value of the image that remains unchanged when the top side of the image is stretched, in vp.|
| .value[2].f32 | Pixel value of the image that remains unchanged when the right side of the image is stretched, in vp.|
| .value[3].f32 | Pixel value of the image that remains unchanged when the bottom side of the image is stretched, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Pixel value of the image that remains unchanged when the left side of the image is stretched, in vp.|
| .value[1].f32 | Pixel value of the image that remains unchanged when the top side of the image is stretched, in vp.|
| .value[2].f32 | Pixel value of the image that remains unchanged when the right side of the image is stretched, in vp.|
| .value[3].f32 | Pixel value of the image that remains unchanged when the bottom side of the image is stretched, in vp.|

## NODE_TRANSLATE_WITH_PERCENT

```c
NODE_TRANSLATE_WITH_PERCENT = 103
```

Component translation, with support for percentage-based translation parameters. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Translation distance along the x-axis. The default unit is percentage. The default unit is percentage, unless **value[3]** exists and is **0** (then the unit is vp). The default value is **0**.|
| .value[1].f32 | Translation distance along the y-axis. The default unit is percentage. The default unit is percentage, unless **value[4]** exists and is **0** (then the unit is vp). The default value is **0**.|
| .value[2].f32 | Translation distance along the z-axis, in vp. The default value is **0**.|
| .value[3]?.i32 | Whether the x-axis translation distance is in percentage format. The value is **0** or **1**. The value **1** means percentage format (for example, value[0].f32=0.1 and value[3].i32=1 translates 10% along the x-axis). The default value is **1**.|
| .value[4]?.i32 | Whether the y-axis translation distance is in percentage format. The value is **0** or **1**. The value **1** means percentage format (for example, value[1].f32=0.1 and value[4].i32=1 translates 10% along the y-axis). The default value is **1**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Translation distance along the x-axis. The unit depends on **value[3]**.|
| .value[1].f32 | Translation distance along the y-axis. The unit depends on **value[4]**.|
| .value[2].f32 | Translation distance along the z-axis, in vp.|
| .value[3].i32 | Whether the unit of the translation distance along the x-axis is percentage. When **value[3].i32** is 0, the unit is vp. When **value[3].i32** is 1, the unit is percentage.|
| .value[4].i32 | Whether the unit of the translation distance along the y-axis is percentage. When **value[4].i32** is 0, the unit is vp. When **value[4].i32** is 1, the unit is percentage.|

## NODE_ROTATE_ANGLE

```c
NODE_ROTATE_ANGLE = 104
```

Component rotation with multi-axis angle control. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Rotation angle along the x-axis. The default value is **0**.|
| .value[1].f32 | Rotation angle along the y-axis. The default value is **0**.|
| .value[2].f32 | Rotation angle along the z-axis. The default value is **0**.|
| .value[3].f32 | Line of sight, that is, the distance from the viewpoint to the z=0 plane, in px. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Rotation angle along the x-axis. The default value is **0**.|
| .value[1].f32 | Rotation angle along the y-axis. The default value is **0**.|
| .value[2].f32 | Rotation angle along the z-axis. The default value is **0**.|
| .value[3].f32 | Line of sight, that is, the distance from the viewpoint to the z=0 plane, in px. The default value is **0**.|

## NODE_PIXEL_ROUND

```c
NODE_PIXEL_ROUND = 109
```

Pixel rounding policy of the component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| .object | Pixel rounding policy of the component. The parameter type is [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Pixel rounding policy of the component. The parameter type is [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md).|
