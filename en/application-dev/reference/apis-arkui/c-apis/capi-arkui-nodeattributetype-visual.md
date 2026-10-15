# Visual

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_TRANSLATE

```c
NODE_TRANSLATE
```

**Description**

Translate attribute, which can be set, reset, and obtained as required through APIs. This attribute is mutually exclusive with **NODE_TRANSLATE_WITH_PERCENT**. A component can use only one translation attribute. If **NODE_TRANSLATE** and **NODE_TRANSLATE_WITH_PERCENT** are set simultaneously, the value set by the latter overrides the former. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: distance to translate along the x-axis, in vp. The default value is **0**. .value[1].f32: distance to translate along the y-axis, in vp. The default value is **0**. .value[2].f32: distance to translate along the z-axis, in vp. The default value is **0**. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: distance to translate along the x-axis, in vp. .value[1].f32: distance to translate along the y-axis, in vp. .value[2].f32: distance to translate along the z-axis, in vp.

**Since**: 12

### NODE_SCALE

```c
NODE_SCALE
```

**Description**

Scale attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: scale factor along the x-axis. The default value is **1**. When the value is **0**, the component is invisible. When the value is negative, the component is flipped along the x-axis. .value[1].f32: scale factor along the y-axis. The default value is **1**. When the value is **0**, the component is invisible. When the value is negative, the component is flipped along the y-axis. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: scale factor along the x-axis. .value[1].f32: scale factor along the y-axis.

**Since**: 12

### NODE_ROTATE

```c
NODE_ROTATE
```

**Description**

Rotate attribute, which can be set, reset, and obtained as required through APIs. This attribute is mutually exclusive with **NODE_ROTATE_ANGLE**. A component can use only one rotation attribute. If **NODE_ROTATE** and **NODE_ROTATE_ANGLE** are set simultaneously, the value set by the latter overrides the former. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: X-coordinate of the rotation axis vector. The default value is **0**. .value[1].f32: Y-coordinate of the rotation axis vector. The default value is **0**. .value[2].f32: Z-coordinate of the rotation axis vector. The default value is **0**. .value[3].f32: rotation angle, in degrees (°). The default value is **0**. .value[4].f32: line of sight, that is, the distance from the viewpoint to the z=0 plane, in vp. The default value is **0**. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: X-coordinate of the rotation axis vector. .value[1].f32: Y-coordinate of the rotation axis vector. .value[2].f32: Z-coordinate of the rotation axis vector. .value[3].f32: rotation angle, in degrees (°). .value[4].f32: line of sight, that is, the distance from the viewpoint to the z=0 plane, in vp.

**Since**: 12

### NODE_BRIGHTNESS

```c
NODE_BRIGHTNESS
```

**Description**

Brightness attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: brightness value. The default value is **1.0**, and the recommended value range is [0, 2.0]. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: brightness value. **1.0** indicates the original brightness. Recommended value range: [0, 2.0].

**Since**: 12

### NODE_SATURATION

```c
NODE_SATURATION
```

**Description**

Saturation attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: saturation value. Default value: **1.0**. Recommended value range: [0, 50.0). If a negative value is passed, the value **0** is used. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: saturation value. **1.0** indicates the original saturation. Recommended value range: [0, 50.0).

**Since**: 12

### NODE_BLUR

```c
NODE_BLUR
```

**Description**

Blur attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: blur radius. Value range: [0, +∞). A larger value indicates a higher blur degree. If the value is **0**, the content is not blurred. If the value is less than 0, it is treated as 0 and no error code is returned. The unit is vp. The default value is **0.0**. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: blur radius. A larger value indicates a higher blur degree. If the value is 0, the content is not blurred. The unit is vp.

**Since**: 12

### NODE_LINEAR_GRADIENT

```c
NODE_LINEAR_GRADIENT
```

**Description**

Linear gradient attribute, which can be set, reset, and obtained as required through APIs. This attribute is mutually exclusive with **NODE_SWEEP_GRADIENT** and **NODE_RADIAL_GRADIENT**. A component can set only one gradient type. If multiple gradient attributes are set simultaneously, the gradient type set later overrides the previously set gradient effect. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: start angle of the linear gradient, in degrees (°). The angle increases clockwise from the 0 o'clock direction. The default value is **180**. When [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection) is set to **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM**, the **angle** attribute takes effect; otherwise, the **direction** attribute is used as the main layout mode. .value[1].i32: direction of the linear gradient. The parameter type is [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection). When it is set to a value other than **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM**, the **angle** attribute does not take effect. .value[2].i32: whether the colors are repeated. The value **0** means that the colors are not repeated, and **1** means the opposite. The default value is **0**. .object: the parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: start angle of the linear gradient, in degrees (°). The set value is used only when **direction** is set to **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM**. In other cases, the default value is used. .value[1].i32: direction of the linear gradient. The parameter type is [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection). .value[2].i32: whether the colors are repeated. The value **0** means that the colors are not repeated, and **1** means the opposite. .object: the parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.

**Since**: 12

### NODE_OPACITY

```c
NODE_OPACITY
```

**Description**

Opacity attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: opacity value. Default value: **1**. Value range: [0, 1]. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: opacity value. The value ranges from 0 to 1.

**Since**: 12

### NODE_CLIP

```c
NODE_CLIP
```

**Description**

Clip attribute, which controls whether to clip the area of child components that extends beyond the current component range. This attribute can be set, reset, and obtained as required through APIs. This attribute is mutually exclusive with **NODE_CLIP_SHAPE**. A component can use only one clipping attribute. **NODE_CLIP** provides simple boolean clipping, and **NODE_CLIP_SHAPE** provides clipping with a specified shape. When both are set, the latter overrides the former. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].i32: whether to clip the area of child components that extends beyond the bounds of the parent component. The value **0** indicates not to clip, and the value **1** indicates to clip. The default value is **0**. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].i32: whether the area of child components that extends beyond the bounds of the parent component is clipped. The value **0** indicates no clipping, and the value **1** indicates clipping.

**Since**: 12

### NODE_CLIP_SHAPE

```c
NODE_CLIP_SHAPE
```

**Description**

Clipping shape on the component. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute, which supports four types of shapes: 1. Rectangle: .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-visual-h.md#arkui_cliptype). The value is <b>ARKUI_CLIP_TYPE_RECTANGLE</b> for the rectangle shape. .value[1].f32: width of the rectangle. .value[2].f32: height of rectangle. .value[3].f32: width of the rounded corner of the rectangle. .value[4].f32: height of the rounded corner of the rectangle. .value[5]?.f32: radius of the top left corner of the rectangular shape. .value[6]?.f32: radius of the bottom left corner of the rectangular shape. .value[7]?.f32: radius of the top right corner of the rectangular shape. .value[8]?.f32: radius of the bottom right corner of the rectangular shape. ?.object: clipOption of the rectangle. The parameter type is [ArkUI_RenderNodeClipOption](capi-arkui-rendernodeutils-arkui-rendernodeclipoption.md) type. It takes effect when only the .object parameter is passed, ArkUI_RenderNodeClipOption type is rectangle, and .size must be equal to 1. 2. Circle: .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-visual-h.md#arkui_cliptype). The value is <b>ARKUI_CLIP_TYPE_CIRCLE</b> for the circle shape. .value[1].f32: width of the circle. .value[2].f32: height of the circle. ?.object: clipOption of the circle. The parameter type is [ArkUI_RenderNodeClipOption](capi-arkui-rendernodeutils-arkui-rendernodeclipoption.md) type. It takes effect when only the .object parameter is passed, ArkUI_RenderNodeClipOption type is circle, and .size must be equal to 1. 3.Ellipse: .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-visual-h.md#arkui_cliptype). The value is <b>ARKUI_CLIP_TYPE_ELLIPSE</b> for the ellipse shape. .value[1].f32: width of the ellipse. .value[2].f32: height of the ellipse. ?.object: clipOption of the ellipse. The parameter type is [ArkUI_RenderNodeClipOption](capi-arkui-rendernodeutils-arkui-rendernodeclipoption.md) type. It takes effect when only the .object parameter is passed, ArkUI_RenderNodeClipOption type is ellipse, and .size must be equal to 1. 4. Path: .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-visual-h.md#arkui_cliptype). The value is <b>ARKUI_CLIP_TYPE_PATH</b> for the path shape. .value[1].f32: width of the path. .value[2].f32: height of the path. .string: command for drawing the path. ?.object: clipOption of the path. The parameter type is [ArkUI_RenderNodeClipOption](capi-arkui-rendernodeutils-arkui-rendernodeclipoption.md) type. It takes effect when only the .object parameter is passed, ArkUI_RenderNodeClipOption type is path, and .size must be equal to 1. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md), which supports four types of shapes: 1. Rectangle: .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-visual-h.md#arkui_cliptype). The value is <b>ARKUI_CLIP_TYPE_RECTANGLE</b> for the rectangle shape. .value[1].f32: width of the rectangle. .value[2].f32: height of rectangle. .value[3].f32: width of the rounded corner of the rectangle. .value[4].f32: height of the rounded corner of the rectangle. .value[5].f32: radius of the top left corner of the rectangular shape; .value[6].f32: radius of the bottom left corner of the rectangular shape; .value[7].f32: radius of the top right corner of the rectangular shape; .value[8].f32: radius of the bottom right corner of the rectangular shape; .value[9]?.f32: horizontal coordinate offset of the rectangle. .value[10]?.f32: vertical coordinate offset of the rectangle. 2. Circle: .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-visual-h.md#arkui_cliptype). The value is <b>ARKUI_CLIP_TYPE_CIRCLE</b> for the circle shape. .value[1].f32: width of the circle. .value[2].f32: height of the circle. .value[3]?.f32: horizontal coordinate offset of the circle. .value[4]?.f32: vertical coordinate offset of the circle. 3.Ellipse: .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-visual-h.md#arkui_cliptype). The value is <b>ARKUI_CLIP_TYPE_ELLIPSE</b> for the ellipse shape. .value[1].f32: width of the ellipse. .value[2].f32: height of the ellipse. .value[3]?.f32: horizontal coordinate offset of the ellipse. .value[4]?.f32: vertical coordinate offset of the ellipse. 4. Path: .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-visual-h.md#arkui_cliptype). The value is <b>ARKUI_CLIP_TYPE_PATH</b> for the path shape. .value[1].f32: width of the path. .value[2].f32: height of the path. .string: command for drawing the path.

**Since**: 12

### NODE_TRANSFORM

```c
NODE_TRANSFORM
```

**Description**

Transform attribute, which can be used to translate, rotate, and scale images. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0...15].f32: 16 floating-point numbers of a 4 x 4 transformation matrix, used to perform matrix transformations such as translation, rotation, and scaling on images, arranged in row-major order. In this case, the value of **size** in [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) should not be **0**. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0...15].f32: 16 floating-point numbers of the 4 x 4 transformation matrix.

**Since**: 12

### NODE_SHADOW

```c
NODE_SHADOW
```

**Description**

Shadow attribute, which can be set, reset, and obtained as required through APIs. This attribute is mutually exclusive with **NODE_CUSTOM_SHADOW**. A component can use only one shadow attribute. When both are set, the latter overrides the former. To use a predefined shadow style, use **NODE_SHADOW**. To customize shadow parameters, use **NODE_CUSTOM_SHADOW**. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].i32: shadow effect of the current component. The parameter type is [ArkUI_ShadowStyle](capi-native-type-visual-h.md#arkui_shadowstyle). Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].i32: shadow effect of the current component. The parameter type is [ArkUI_ShadowStyle](capi-native-type-visual-h.md#arkui_shadowstyle).

**Since**: 12

### NODE_CUSTOM_SHADOW

```c
NODE_CUSTOM_SHADOW
```

**Description**

Custom shadow effect. It is mutually exclusive with **NODE_SHADOW**. A component can use only one shadow attribute. When both are set, the latter overrides the former. To use a predefined shadow style, use **NODE_SHADOW**. To customize shadow parameters, use **NODE_CUSTOM_SHADOW**. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0]?.f32: blur radius of the shadow. Value range: [0, +∞). Passing a negative value returns a parameter verification failure. Unit: px. Default value: **0.0**. .value[1]?.i32: whether to enable the coloring strategy. The value **1** means to enable the coloring strategy (the color is automatically picked from around the component to adapt to the background), and **0** means the opposite (a fixed color is used). The default value is **0**. Pass **1** when the shadow color needs to automatically adapt to the surrounding background. .value[2]?.f32: offset of the shadow along the x-axis, in px. Default value: **0.0**. .value[3]?.f32: offset of the shadow along the y-axis, in px. Default value: **0.0**. .value[4]?.i32: shadow type. The parameter type is [ArkUI_ShadowType](capi-native-type-visual-h.md#arkui_shadowtype). The default value is **ARKUI_SHADOW_TYPE_COLOR**. .value[5]?.u32: it specifies the shadow color when the coloring strategy is disabled (**.value[1]** is set to **0**), in 0xARGB format. For example, **0xFFFF0000** indicates red. If not passed, the default value is **0xFF000000** (black). It specifies the coloring strategy when the coloring strategy is enabled (**.value[1]** is set to **1**), and the parameter type is [ArkUI_ColorStrategy](capi-native-type-visual-h.md#arkui_colorstrategy). .value[6]?.u32: whether to fill the shadow. The value **1** means to fill the shadow, and **0** means the opposite. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: blur radius of the shadow, in px. .value[1].i32: whether the coloring strategy is enabled. The value 1 indicates the coloring strategy is enabled, and **0** indicates the opposite. .value[2].f32: offset of the shadow along the x-axis, in px. .value[3].f32: offset of the shadow along the y-axis, in px. .value[4].i32: shadow type. The parameter type is [ArkUI_ShadowType](capi-native-type-visual-h.md#arkui_shadowtype), and the default value is **ARKUI_SHADOW_TYPE_COLOR**. The enumerated values include: **ARKUI_SHADOW_TYPE_COLOR** (color shadow) and **ARKUI_SHADOW_TYPE_BLUR** (blur shadow). .value[5].u32: shadow color, in 0xARGB format. For example, **0xFFFF0000** indicates red. .value[6].u32: whether the shadow is filled. The value **1** means that the shadow is filled, and **0**<br>means the opposite.

**Since**: 12

### NODE_TRANSFORM_CENTER

```c
NODE_TRANSFORM_CENTER
```

**Description**

Center point attribute for image transformation and transition, which affects the center point behavior of transformation and transition attributes such as rotation (**NODE_ROTATE** / **NODE_ROTATE_ANGLE** / **NODE_ROTATE_TRANSITION**), scaling (**NODE_SCALE** / **NODE_SCALE_TRANSITION**), and translation (**NODE_TRANSLATE** / **NODE_TRANSLATE_TRANSITION**). This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows. Note: If the coordinate is expressed in a number that represents a percentage, the attribute obtaining API returns the calculated value in vp.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0]?.f32: X-coordinate of the center point, in vp. Default value: **0.0**. .value[1]?.f32: Y-coordinate of the center point, in vp. Default value: **0.0**. .value[2]?.f32: Z-coordinate of the center point, in vp. Default value: **0.0**. .value[3]?.f32: X-coordinate of the center point, expressed in a number that represents a percentage. The value range is [0, 1]. For example, **0.2** indicates 20%. This attribute overwrites **value[0].f32**. The default value is **0.5f**. The error code ARKUI_ERROR_CODE_PARAM_INVALID is returned when the value is out of range. .value[4]?.f32: Y-coordinate of the center point, expressed in a number that represents a percentage. The value range is [0, 1]. For example, **0.2** indicates 20%. This attribute overwrites **value[1].f32**. The default value is **0.5f**. The error code ARKUI_ERROR_CODE_PARAM_INVALID is returned when the value is out of range. .value[5]?.f32: Z-coordinate of the center point, expressed in a number that represents a percentage. The value range is [0, 1]. For example, **0.2** indicates 20%. This attribute overwrites **value[2].f32**. The default value is **0.0f**. The error code ARKUI_ERROR_CODE_PARAM_INVALID is returned when the value is out of range. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: X-coordinate of the center point, in vp. .value[1].f32: Y-coordinate of the center point, in vp. .value[2].f32: Z-coordinate of the center point, in vp.

**Since**: 12

### NODE_SWEEP_GRADIENT

```c
NODE_SWEEP_GRADIENT
```

**Description**

Sweep gradient effect. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0]?.f32: X-coordinate of the sweep gradient center relative to the upper left corner of the component, in vp. Default value: 50% of the component width. .value[1]?.f32: Y-coordinate of the sweep gradient center relative to the upper left corner of the component, in vp. If not passed, the default value is the vertical center position of the component. Pass this parameter when the gradient center needs to be offset to a specific position. .value[2]?.f32: start point of the sweep gradient, in degrees (°). Default value: **0**. .value[3]?.f32: end point of the sweep gradient, in degrees (°). Default value: **0**. .value[4]?.f32: rotation angle of the sweep gradient, in degrees (°). Default value: **0**. .value[5]?.i32: whether the colors are repeated. The value **0** means that the colors are not repeated, and **1** means the opposite. If not passed, the default value is **0** (no repeat). Pass **1** when the colors need to be filled cyclically and repeatedly. .object: the parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: X-coordinate of the sweep gradient center relative to the upper left corner of the component. .value[1].f32: Y-coordinate of the sweep gradient center relative to the upper left corner of the component. .value[2].f32: start point of the sweep gradient, in degrees (°). Default value: **0**. .value[3].f32: end point of the sweep gradient, in degrees (°). Default value: **0**. .value[4].f32: rotation angle of the sweep gradient, in degrees (°). Default value: **0**. .value[5].i32: whether the colors are repeated. The value **0** means that the colors are not repeated, and **1** means the opposite. .object: the parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.

**Since**: 12

### NODE_RADIAL_GRADIENT

```c
NODE_RADIAL_GRADIENT
```

**Description**

Radial gradient effect. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0]?.f32: X-coordinate of the radial gradient center relative to the upper left corner of the current component. .value[1]?.f32: Y-coordinate of the radial gradient center relative to the upper left corner of the current component. .value[2]?.f32: radius of the radial gradient. The value range is [0, +∞), and the default value is **0**. .value[3]?.i32: whether the colors are repeated. The value **0** means that the colors are not repeated, and **1** means the opposite. If this parameter is not passed, the default value is **0** (no repeat). .object: the parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: X-coordinate of the radial gradient center relative to the upper left corner of the component. .value[1].f32: Y-coordinate of the radial gradient center relative to the upper left corner of the component. .value[2].f32: radius of the radial gradient. The default value is **0**. .value[3].i32: whether the colors are repeated. The value **false (0)** means that the colors are not repeated, and **true (1)** means the opposite. .object: the parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.

**Since**: 12

### NODE_MASK

```c
NODE_MASK
```

**Description**

Adds a mask of the specified shape to the component. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute, which supports five types of shapes: 1. Rectangle: .value[0].u32 fill color, in 0xARGB format. .value[1].u32: stroke color, in 0xARGB format. .value[2].f32: stroke width, in vp. .value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-visual-h.md#arkui_masktype). The value is <b>ARKUI_MASK_TYPE_RECTANGLE</b> for the rectangle shape. .value[4].f32: width of the rectangle. .value[5].f32: height of the rectangle. .value[6].f32: width of the rounded corner of the rectangle. .value[7].f32: height of the rounded corner of the rectangle. .value[8]?.f32: radius of the top left corner of the rectangular shape. .value[9]?.f32: radius of the bottom left corner of the rectangular shape. .value[10]?.f32: radius of the top right corner of the rectangular shape. .value[11]?.f32: radius of the bottom right corner of the rectangular shape. 2. Circle: .value[0].u32 fill color, in 0xARGB format. .value[1].u32: stroke color, in 0xARGB format. .value[2].f32: stroke width, in vp. .value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-visual-h.md#arkui_masktype). The value is <b>ARKUI_MASK_TYPE_CIRCLE</b> for the circle shape. .value[4].f32: width of the circle. .value[5].f32: height of the circle. 3. Ellipse: .value[0].u32 fill color, in 0xARGB format. .value[1].u32: stroke color, in 0xARGB format. .value[2].f32: stroke width, in vp. .value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-visual-h.md#arkui_masktype). The value is <b>ARKUI_MASK_TYPE_ELLIPSE</b> for the ellipse shape. .value[4].f32: width of the ellipse. .value[5].f32: height of the ellipse. 4. Path: .value[0].u32 fill color, in 0xARGB format. .value[1].u32: stroke color, in 0xARGB format. .value[2].f32: stroke width, in vp. .value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-visual-h.md#arkui_masktype). The value is <b>ARKUI_MASK_TYPE_PATH</b> for the path shape. .value[4].f32: width of the path. .value[5].f32: height of the path. .string: command for drawing the path. 5. Progress: .value[0].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-visual-h.md#arkui_masktype). The value is <b>ARKUI_MASK_TYPE_PROGRESS</b> for the progress shape. .value[1].f32: current value of the progress indicator. .value[2].f32: maximum value of the progress indicator. .value[3].u32: color of the progress indicator, in 0xARGB format. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md), which supports five types of shapes: 1. Rectangle: .value[0].u32 fill color, in 0xARGB format. .value[1].u32: stroke color, in 0xARGB format. .value[2].f32: stroke width, in vp. .value[3].i32: mask type. .value[4].f32: width of the rectangle. .value[5].f32: height of the rectangle. .value[6].f32: width of the rounded corner of the rectangle. .value[7].f32: height of the rounded corner of the rectangle. .value[8].f32: radius of the top left corner of the rectangular shape. .value[9].f32: radius of the bottom left corner of the rectangular shape. .value[10].f32: radius of the top right corner of the rectangular shape. .value[11].f32: radius of the bottom right corner of the rectangular shape. 2. Circle: .value[0].u32 fill color, in 0xARGB format. .value[1].u32: stroke color, in 0xARGB format. .value[2].f32: stroke width, in vp. .value[3].i32: mask type. .value[4].f32: width of the circle. .value[5].f32: height of the circle. 3. Ellipse: .value[0].u32 fill color, in 0xARGB format. .value[1].u32: stroke color, in 0xARGB format. .value[2].f32: stroke width, in vp. .value[3].i32: mask type. .value[4].f32: width of the ellipse. .value[5].f32: height of the ellipse. 4. Path: .value[0].u32 fill color, in 0xARGB format. .value[1].u32: stroke color, in 0xARGB format. .value[2].f32: stroke width, in vp. .value[3].i32: mask type. .value[4].f32: width of the path. .value[5].f32: height of the path. .string: command for drawing the path. 5. Progress: .value[0].i32: mask type. .value[1].f32: current value of the progress indicator. .value[2].f32: maximum value of the progress indicator. .value[3].u32: color of the progress indicator.

**Since**: 12

### NODE_BLEND_MODE

```c
NODE_BLEND_MODE
```

**Description**

Blends the component's background with the content of the component's child node. It is used for visual composition scenarios such as overlay transparency effects and color blending. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].i32: blend mode of the current component. The parameter type is [ArkUI_BlendMode](capi-native-type-visual-h.md#arkui_blendmode). The default value is **ARKUI_BLEND_MODE_NONE**. .value[1]?.i32: how the specified blend mode is applied. The parameter type is [ArkUI_BlendApplyType](capi-native-type-visual-h.md#arkui_blendapplytype). The default value is **BLEND_APPLY_TYPE_FAST**. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].i32: blend mode of the current component. The parameter type is [ArkUI_BlendMode](capi-native-type-visual-h.md#arkui_blendmode). The default value is **ARKUI_BLEND_MODE_NONE**. .value[1].i32: how the specified blend mode is applied. The parameter type is [ArkUI_BlendApplyType](capi-native-type-visual-h.md#arkui_blendapplytype). The default value is **BLEND_APPLY_TYPE_FAST**. The enumerated values include: **BLEND_APPLY_TYPE_FAST** (fast implementation, non-offscreen) and **BLEND_APPLY_TYPE_OFFSCREEN**<br>(offscreen implementation).

**Since**: 12

### NODE_GRAY_SCALE

```c
NODE_GRAY_SCALE
```

**Description**

Grayscale effect. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: grayscale conversion ratio. The value ranges from 0 to 1. The default value is **0**. For example, **0.5** indicates a 50% grayscale conversion ratio. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: grayscale conversion ratio. The value ranges from 0 to 1.

**Since**: 12

### NODE_INVERT

```c
NODE_INVERT
```

**Description**

Image inversion ratio. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: image inversion ratio. The value ranges from 0 to 1. The default value is **0**. For example, **0.5** indicates a 50% image inversion ratio. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: image inversion ratio. The value ranges from 0 to 1.

**Since**: 12

### NODE_SEPIA

```c
NODE_SEPIA
```

**Description**

Sepia conversion ratio. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: sepia conversion ratio. The value ranges from 0 to 1. The default value is **0**. For example, **0.5** indicates a 50% sepia conversion ratio. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: sepia conversion ratio. The value ranges from 0 to 1.

**Since**: 12

### NODE_CONTRAST

```c
NODE_CONTRAST
```

**Description**

Contrast attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: contrast. If the value is **1**, the source image is displayed. A larger value indicates a higher contrast. The default value is **1**. The value range is [0, 10). If the value is out of range, the error code ARKUI_ERROR_CODE_PARAM_INVALID is returned. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: contrast. The value range is [0, 10).

**Since**: 12

### NODE_FOREGROUND_COLOR

```c
NODE_FOREGROUND_COLOR
```

**Description**

Foreground color attribute, which can be set and obtained as required through APIs. The reset API has no effect on this attribute, because the foreground color is an attribute type that cannot automatically restore its default value, and the reset operation does not change the foreground color that has been set. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].u32: color, in 0xAARRGGBB format. For example, **0xFFFF0000** indicates red. The default value is **0xFF000000**. .value[0].i32: coloring strategy. The value is an enumerated value of [ArkUI_ColorStrategy](capi-native-type-visual-h.md#arkui_colorstrategy). Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].u32: color, in 0xARGB format.

**Since**: 12

### NODE_OUTLINE_WIDTH

```c
NODE_OUTLINE_WIDTH
```

**Description**

Outline width of an element, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: width of the left outline, in vp. .value[1].f32: width of the top outline, in vp. .value[2].f32: width of the right outline, in vp. .value[3].f32: width of the bottom outline, in vp. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: width of the left outline, in vp. .value[1].f32: width of the top outline, in vp. .value[2].f32: width of the right outline, in vp. .value[3].f32: width of the bottom outline, in vp.

**Since**: 12

### NODE_RENDER_FIT

```c
NODE_RENDER_FIT
```

**Description**

How the final state of the component's content is rendered during its width and height animation process. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].i32: how the final state of the component's content is rendered. The value is an enumerated value of [ArkUI_RenderFit](capi-native-type-visual-h.md#arkui_renderfit). Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].i32: how the final state of the component's content is rendered. The value is an enumerated value of [ArkUI_RenderFit](capi-native-type-visual-h.md#arkui_renderfit).

**Since**: 12

### NODE_OUTLINE_COLOR

```c
NODE_OUTLINE_COLOR
```

**Description**

Outline color attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].u32: color of the four outlines, in 0xARGB format, for example, **0xFFFF11FF**. This parameter takes effect only when **.value[0]** is passed. .value[0].u32: color of the top outline, in 0xARGB format, for example, **0xFFFF11FF**. This parameter takes effect when the four values from **.value[0]** to **.value[3]** are passed. .value[1].u32: color of the right outline, in 0xARGB format, for example, **0xFFFF11FF**. .value[2].u32: color of the bottom outline, in 0xARGB format, for example, **0xFFFF11FF**. .value[3].u32: color of the left outline, in 0xARGB format, for example, **0xFFFF11FF**. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].u32: color of the top outline, in 0xARGB format, for example, **0xFFFF11FF**. .value[1].u32: color of the right outline, in 0xARGB format, for example, **0xFFFF11FF**. .value[2].u32: color of the bottom outline, in 0xARGB format, for example, **0xFFFF11FF**. .value[3].u32: color of the left outline, in 0xARGB format, for example, **0xFFFF11FF**.

**Since**: 12

### NODE_RENDER_GROUP

```c
NODE_RENDER_GROUP
```

**Description**

Whether the component and its child components are rendered off the screen and then drawn together with its parent. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].i32: whether the component and its child components are rendered off the screen and then drawn together with its parent. The value **1** means that the component and its child components are rendered off the screen and then drawn together with its parent, and **0** means the opposite. The default value is **0**. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].i32: whether the component and its child components are rendered off the screen and then drawn together with its parent. The value **1** means that the component and its child components are rendered off the screen and then drawn together with its parent, and **0** means the opposite.

**Since**: 12

### NODE_COLOR_BLEND

```c
NODE_COLOR_BLEND
```

**Description**

Applies a color blend effect to the component. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].u32: color to blend with the component, in 0xARGB format. The default value is **0x00000000**. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].u32: color to blend with the component, in 0xARGB format, for example, **0xFFFF11FF**.

**Since**: 12

### NODE_FOREGROUND_BLUR_STYLE

```c
NODE_FOREGROUND_BLUR_STYLE
```

**Description**

Applies a foreground blur style to the component. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].i32: foreground blur style. The value is an enumerated value of [ArkUI_BlurStyle](capi-native-type-visual-h.md#arkui_blurstyle). .value[1]?.i32: color mode used for the foreground blur. The value is an enumerated value of [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode). If not passed, the default value is **ARKUI_COLOR_MODE_SYSTEM**. .value[2]?.i32: adaptive color mode used for the foreground blur. The value is an enumerated value of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor). .value[3]?.f32: blur degree. The value range is [0.0, 1.0]. .value[4]?.f32: brightness of black in the grayscale blur. The value range is [0,127]. If not passed, the default value is **0**. .value[5]?.f32: degree of darkening the white color in the grayscale blur. The value range is [0,127]. If not passed, the default value is **0**. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].i32: foreground blur style. The value is an enumerated value of [ArkUI_BlurStyle](capi-native-type-visual-h.md#arkui_blurstyle). .value[1].i32: color mode used for the foreground blur. The value is an enumerated value of [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode). .value[2].i32: adaptive color mode used for the foreground blur. The value is an enumerated value of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor). .value[3].f32: blur degree. The value range is [0.0, 1.0]. .value[4].f32: brightness of black in the grayscale blur. The value range is [0,127]. .value[5].f32: degree of darkening the white color in the grayscale blur. The value range is [0,127].

**Since**: 12

### NODE_BACKDROP_BLUR

```c
NODE_BACKDROP_BLUR = 99
```

**Description**

Background blur effect. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: background blur radius. The value range is [0, +∞). If the value is out of range, the error code ARKUI_ERROR_CODE_PARAM_INVALID is returned. Unit: px. Default value: **0.0**. .value[1]?.f32: brightness of black in the grayscale blur. The value range is [0, 127]. If this parameter is not passed, the default value is **0**. Pass this parameter when the degree to which black areas are brightened in the blur effect needs to be finely adjusted. .value[2]?.f32: degree of darkening the white color in the grayscale blur. The value range is [0, 127]. If this parameter is not passed, the default value is **0**. Pass this parameter when the degree to which white areas are darkened in the blur effect needs to be finely adjusted. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: background blur radius. The value range is [0, +∞). Unit: px. .value[1].f32: brightness of black in the grayscale blur. The value range is [0, 127]. .value[2].f32: degree of darkening the white color in the grayscale blur. The value range is [0, 127].

**Since**: 15

### NODE_TRANSLATE_WITH_PERCENT

```c
NODE_TRANSLATE_WITH_PERCENT = 103
```

**Description**

Component translation, with support for percentage-based translation parameters. This attribute is mutually exclusive with **NODE_TRANSLATE**. A component can use only one translation attribute. When both are set, the latter overrides the former. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: distance to translate along the x-axis. The default unit is percentage. The unit is vp only if value[3] exists and value[3] is 0. The default value of value[0] is <b>0</b>. .value[1].f32: distance to translate along the y-axis. The default unit is percentage. The unit is vp only if value[4] exists and value[4] is 0. The default value of value[1] is <b>0</b>. .value[2].f32: distance to translate along the z-axis, in vp. The default value is <b>0</b>. .value[3]?.i32: Whether the translation distance along the x-axis is specified as a percentage. The value can be 0 or 1. When the value is 1, it is specified as a percentage. For example, value[0].f32=0.1 and value[3].i32=1 indicates a 10% shift in the x direction. The default value is <b>1</b>. .value[4]?.i32: Whether the translation distance along the y-axis is specified as a percentage. The value can be 0 or 1. When the value is 1, it is specified as a percentage. For example, value[1].f32=0.1 and value[4].i32=1 indicates a 10% shift in the y direction. The default value is <b>1</b>. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: distance to translate along the x-axis. The unit depends on value[3]. .value[1].f32: distance to translate along the y-axis. The unit depends on value[4]. .value[2].f32: distance to translate along the z-axis. The unit is vp. .value[3].i32: Whether the unit of the X-axis translation distance is in percentage. When value[3].i32 is 0, the unit of the X-axis translation distance is vp; when value[3].i32 is 1, the unit of the X-axis translation distance is percentage; .value[4].i32: Whether the unit of the Y-axis translation distance is in percentage. When value[4].i32 is 0, the unit of the Y-axis translation distance is vp; when value[4].i32 is 1, the unit of the Y-axis translation distance is percentage;

**Since**: 20

### NODE_ROTATE_ANGLE

```c
NODE_ROTATE_ANGLE = 104
```

**Description**

Component rotation with multi-axis angle control. This attribute can be reset and obtained as required through APIs. It is mutually exclusive with **NODE_ROTATE**. A component can use only one rotation attribute. When both are set, the latter overrides the former.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].f32: x-axis rotation angle. The default value is <b>0</b>. .value[1].f32: y-axis rotation angle. The default value is <b>0</b>. .value[2].f32: z-axis rotation angle. The default value is <b>0</b>. .value[3].f32: perspective distance from the viewpoint to the z=0 plane, in px. The default value is <b>0</b>. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].f32: x-axis rotation angle. The default value is <b>0</b>. .value[1].f32: y-axis rotation angle. The default value is <b>0</b>. .value[2].f32: z-axis rotation angle. The default value is <b>0</b>. .value[3].f32: perspective distance from the viewpoint to the z=0 plane, in px. The default value is <b>0</b>.

**Since**: 20

### NODE_SYSTEM_MATERIAL

```c
NODE_SYSTEM_MATERIAL = 127
```

**Description**

System material attribute, which can be set, reset, and obtained as required through APIs. Only devices that support systemMaterial can use this attribute. Otherwise, when setting this attribute, the error code ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED will be returned. Whether a device supports materials can be determined by calling [OH_ArkUI_NativeModule_GetSystemMaterialSupported](capi-native-material-h.md#oh_arkui_nativemodule_getsystemmaterialsupported). The material effect behaves differently on devices with different level of computing powers. The level is defined by [ArkUI_MaterialLevel](capi-native-material-h.md#arkui_materiallevel), which can be obtained by [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](capi-native-material-h.md#oh_arkui_nativemodule_getglobalmateriallevel). On devices with the computing power level of ARKUI_MATERIAL_LEVEL_SMOOTH, it affects attributes such as the backgroundColor, borderWidth, borderColor, shadow. On devices with the computing power levels of ARKUI_MATERIAL_LEVEL_EXQUISITE or ARKUI_MATERIAL_LEVEL_GENTLE, it affects shadow attribute and adds a filter effect at the system material layer, which can produce an effect similar to glass.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .object: system material object. The parameter type is [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerialhandle.md). Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .object: system material object. The parameter type is [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerialhandle.md). The ArkUI_ImmersiveMaterialHandle object of the return value is a pointer to static member, so do not release the return object by calling [OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy](capi-native-material-h.md#oh_arkui_nativemodule_immersivematerial_destroy).

**Since**: 26.0.0

### NODE_TRANSFORM_3D

```c
NODE_TRANSFORM_3D = 128
```

**Description**

Defines the 3D transform attribute, which sets the 3D transformation matrix of the component. When 3D transformation with the perspective effect is involved, the display effect of [NODE_TRANSFORM](capi-native-node-h.md#arkui_nodeattributetype) may be incorrect. In this case, this attribute is recommended. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0...15].f32: 16 floating-point numbers, indicating a 4x4 transformation matrix. The array length must be <b>16</b>.</li> <li>.object: pointer to an [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md) object, indicating a 4x4 transformation matrix. Either .value or .object is used to set the matrix. If both are set at the same time, .value takes priority.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0...15].f32: 16 floating-point numbers, indicating the current 3D transformation matrix.</li> </ul>

**Since**: 26.0.1

### NODE_LINEAR_GRADIENT_BLUR

```c
NODE_LINEAR_GRADIENT_BLUR = 129
```

**Description**

Defines the linear gradient blur attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: linear gradient blur options object. The parameter type is [OH_ArkUI_LinearGradientBlurOptions](capi-arkui-nativemodule-oh-arkui-lineargradientbluroptions.md)*.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: linear gradient blur options object. The type is [OH_ArkUI_LinearGradientBlurOptions](capi-arkui-nativemodule-oh-arkui-lineargradientbluroptions.md)*. The object is an internal static object; do not release it by calling [OH_ArkUI_NativeModule_LinearGradientBlurOptions_Destroy](capi-native-type-visual-h.md#oh_arkui_nativemodule_lineargradientbluroptions_destroy). When the attribute is not set or has been reset, the returned object contains default values (blurRadius = 0, fractionStops = {0.0, 0.0, 0.0, 1.0}, direction = [OH_ARKUI_LINEAR_GRADIENT_BLUR_DIRECTION_BOTTOM](capi-native-type-visual-h.md#oh_arkui_lineargradientblurdirection)).</li> </ul>

**Since**: 26.2.0


