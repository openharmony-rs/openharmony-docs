# ArkUI_NodeAttributeType (Animation and Visual Effect Attributes)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e10e7def4863f4f964c4d0cb425b7650081cb83e translatedAt=2026-08-25T02:24:25.838Z pushedAt=2026-08-26T02:58:36.313Z -->

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
This attribute is mutually exclusive with **NODE_TRANSLATE_WITH_PERCENT**. A component can use only one translation attribute. If **NODE_TRANSLATE** and **NODE_TRANSLATE_WITH_PERCENT** are set simultaneously, the value set by the latter overrides the former.<br>
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
| .value[0].f32 | Scale factor along the x-axis. The default value is **1**. When the value is **0**, the component is invisible. When the value is negative, the component is flipped along the x-axis. |
| .value[1].f32 | Scale factor along the y-axis. The default value is **1**. When the value is **0**, the component is invisible. When the value is negative, the component is flipped along the y-axis. |

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
This attribute is mutually exclusive with **NODE_ROTATE_ANGLE**. A component can use only one rotation attribute. If **NODE_ROTATE** and **NODE_ROTATE_ANGLE** are set simultaneously, the value set by the latter overrides the former.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | X-coordinate of the rotation axis vector. The default value is **0**.|
| .value[1].f32 | Y-coordinate of the rotation axis vector. The default value is **0**.|
| .value[2].f32 | Z-coordinate of the rotation axis vector. The default value is **0**.|
| .value[3].f32 | Rotation angle, in degrees (°). The default value is **0**. |
| .value[4].f32 | Line of sight, that is, the distance from the viewpoint to the z=0 plane, in vp. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | X-coordinate of the rotation axis vector.|
| .value[1].f32 | Y-coordinate of the rotation axis vector.|
| .value[2].f32 | Z-coordinate of the rotation axis vector.|
| .value[3].f32 | Rotation angle, in degrees (°). |
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
| .value[0].f32 | Brightness value. **1.0** indicates the original brightness. Recommended value range: [0, 2.0]. |

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
| .value[0].f32 | Saturation value. Default value: **1.0**. Recommended value range: [0, 50.0). If a negative value is passed, the value **0** is used. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Saturation value. **1.0** indicates the original saturation. Recommended value range: [0, 50.0). |

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
| .value[0].f32 | Blur radius. Value range: [0, +∞). A larger value indicates a higher blur degree. If the value is **0**, the content is not blurred. If the value is less than 0, it is treated as 0 and no error code is returned. The unit is vp. The default value is **0.0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Blur radius. A larger value indicates a higher blur degree. If the value is 0, the content is not blurred. The unit is vp.|

## NODE_LINEAR_GRADIENT

```c
NODE_LINEAR_GRADIENT = 14
```

Linear gradient attribute, which can be set, reset, and obtained as required through APIs.<br>
This attribute is mutually exclusive with **NODE_SWEEP_GRADIENT** and **NODE_RADIAL_GRADIENT**. A component can set only one gradient type. If multiple gradient attributes are set simultaneously, the gradient type set later overrides the previously set gradient effect.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Start angle of the linear gradient, in degrees (°). The angle increases clockwise from the 0 o'clock direction. The default value is **180**. When [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection) is set to **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM**, the **angle** attribute takes effect; otherwise, the **direction** attribute is used as the main layout mode. |
| .value[1].i32 | Direction of the linear gradient. The parameter type is [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection). When it is set to a value other than **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM**, the **angle** attribute does not take effect. The enumerated values include: **ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT** (from left to right), **ARKUI_LINEAR_GRADIENT_DIRECTION_TOP** (from top to bottom), **ARKUI_LINEAR_GRADIENT_DIRECTION_RIGHT** (from right to left), **ARKUI_LINEAR_GRADIENT_DIRECTION_BOTTOM** (from bottom to top), **ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_TOP** (from upper left to lower right), **ARKUI_LINEAR_GRADIENT_DIRECTION_RIGHT_TOP** (from upper right to lower left), **ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_BOTTOM** (from lower left to upper right), **ARKUI_LINEAR_GRADIENT_DIRECTION_RIGHT_BOTTOM** (from lower right to upper left), and **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM** (custom direction). |
| .value[2].i32 | Whether the colors are repeated. The value **0** means that the colors are not repeated, and **1** means the opposite. The default value is **0**. |
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. |
| colors | Colors of the color stops.|
| stops | Stop positions of the color stops.|
| size | Number of colors.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Start angle of the linear gradient, in degrees (°). The set value is used only when **direction** is set to **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM**. In other cases, the default value is used. |
| .value[1].i32 | Direction of the linear gradient. The parameter type is [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection). |
| .value[2].i32 | Whether the colors are repeated. The value **0** means that the colors are not repeated, and **1** means the opposite. |
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. |
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
| .value[0].f32 | Opacity value. Default value: **1**. Value range: [0, 1]. |

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
| .value[0].i32 | Z-index value. A larger value indicates a higher component level. Default value: **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Z-index value. The default value is **0**. |

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
| .value[0].i32 | Whether to show or hide the component. The parameter type is [ArkUI_Visibility](capi-common-attributes-h.md#arkui_visibility). The default value is **ARKUI_VISIBILITY_VISIBLE**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the component is shown or hidden. The parameter type is [ArkUI_Visibility](capi-common-attributes-h.md#arkui_visibility). Default value: **ARKUI_VISIBILITY_VISIBLE**. The meaning of each enumerated value and its corresponding number are as follows: **ARKUI_VISIBILITY_VISIBLE(0)** indicates visible, **ARKUI_VISIBILITY_HIDDEN(1)** indicates hidden but occupying space, and **ARKUI_VISIBILITY_NONE(2)** indicates hidden and not occupying space. |

## NODE_CLIP

```c
NODE_CLIP = 23
```

Clip attribute, which controls whether to clip the area of child components that extends beyond the current component range. This attribute can be set, reset, and obtained as required through APIs.<br>
This attribute is mutually exclusive with **NODE_CLIP_SHAPE**. A component can use only one clipping attribute. **NODE_CLIP** provides simple boolean clipping, and **NODE_CLIP_SHAPE** provides clipping with a specified shape. When both are set, the latter overrides the former.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to clip the area of child components that extends beyond the bounds of the parent component. The value **0** indicates not to clip, and the value **1** indicates to clip. The default value is **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the area of child components that extends beyond the bounds of the parent component is clipped. The value **0** indicates no clipping, and the value **1** indicates clipping. |

## NODE_CLIP_SHAPE

```c
NODE_CLIP_SHAPE = 24
```

Clipping shape on the component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

1. Rectangle<br>

| Name| Description|
| -- | -- |
| .value[0].i32 | Clip type. The parameter type is [ArkUI_ClipType](capi-native-type-visual-h.md#arkui_cliptype). For the rectangle type, set this to **ARKUI_CLIP_TYPE_RECTANGLE**. |
| .value[1].f32 | Width of the rectangle, in vp.|
| .value[2].f32 | Height of the rectangle, in vp.|
| .value[3].f32 | Width of the rounded corner of the rectangle, in vp.|
| .value[4].f32 | Height of the rounded corner of the rectangle, in vp.|
| .value[5]?.f32 | Radius of the upper left rounded corner of the rectangle, in vp. Default value: **0**. |
| .value[6]?.f32 | Radius of the lower left rounded corner of the rectangle, in vp. Default value: **0**. |
| .value[7]?.f32 | Radius of the upper right rounded corner of the rectangle, in vp. Default value: **0**. |
| .value[8]?.f32 | Radius of the lower right rounded corner of the rectangle, in vp. Default value: **0**. |
| .object | Coordinate offset of the rectangle. The parameter type is [ArkUI_RenderNodeClipOption](capi-arkui-nativemodule-arkui-rendernodeclipoption.md). It takes effect only when the **.object** parameter is passed. |

2. Circle<br>

| Name| Description|
| -- | -- |
| .value[0].i32 | Clip type. The parameter type is **ArkUI_ClipType**. For the circle type, set this parameter to **ARKUI_CLIP_TYPE_CIRCLE**. |
| .value[1].f32 | Width of the circle, in vp.|
| .value[2].f32 | Height of the circle, in vp.|
| .object | Coordinate offset of the circle. The parameter type is [ArkUI_RenderNodeClipOption](capi-arkui-nativemodule-arkui-rendernodeclipoption.md). It takes effect only when the **.object** parameter is passed. |

3. Ellipse<br>

| Name| Description|
| -- | -- |
| .value[0].i32 | Clip type. The parameter type is **ArkUI_ClipType**. For the ellipse type, set this parameter to **ARKUI_CLIP_TYPE_ELLIPSE**. |
| .value[1].f32 | Width of the ellipse, in vp.|
| .value[2].f32 | Height of the ellipse, in vp.|
| .object | Coordinate offset of the ellipse. The parameter type is [ArkUI_RenderNodeClipOption](capi-arkui-nativemodule-arkui-rendernodeclipoption.md). It takes effect only when the **.object** parameter is passed. |

4. Path<br>

| Name| Description|
| -- | -- |
| .value[0].i32 | Clip type. The parameter type is **ArkUI_ClipType**. For the path type, set this parameter to **ARKUI_CLIP_TYPE_PATH**. |
| .value[1].f32 | Width of the path, in vp.|
| .value[2].f32 | Height of the path, in vp.|
| .string | Command string for drawing the path. The format follows the SVG path data syntax, for example, 'M0 0 L100 100 Z'. |
| .object | Command for drawing the path. The parameter type is [ArkUI_RenderNodeClipOption](capi-arkui-nativemodule-arkui-rendernodeclipoption.md). It takes effect only when the **.object** parameter is passed. |

**Returns**

1. Rectangle<br>

| Type| Description|
| -- | -- |
| .value[0].i32 | Clip type. The parameter type is [ArkUI_ClipType](capi-native-type-visual-h.md#arkui_cliptype). For the rectangle type, **ARKUI_CLIP_TYPE_RECTANGLE** is returned. |
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
| .value[0].i32 | Clip type. The parameter type is [ArkUI_ClipType](capi-native-type-visual-h.md#arkui_cliptype). For the circle type, **ARKUI_CLIP_TYPE_CIRCLE** is returned. |
| .value[1].f32 | Width of the circle, in vp.|
| .value[2].f32 | Height of the circle, in vp.|
| .value[3]?.f32 | Horizontal coordinate offset of the circle, in vp.|
| .value[4]?.f32 | Vertical coordinate offset of the circle, in vp.|

3. Ellipse<br>

| Type| Description|
| -- | -- |
| .value[0].i32 | Clip type. The parameter type is [ArkUI_ClipType](capi-native-type-visual-h.md#arkui_cliptype). For the ellipse type, **ARKUI_CLIP_TYPE_ELLIPSE** is returned. |
| .value[1].f32 | Width of the ellipse, in vp.|
| .value[2].f32 | Height of the ellipse, in vp.|
| .value[3]?.f32 | Horizontal coordinate offset of the ellipse, in vp.|
| .value[4]?.f32 | Vertical coordinate offset of the ellipse, in vp.|

4. Path<br>

| Type| Description|
| -- | -- |
| .value[0].i32 | Clip type. The parameter type is [ArkUI_ClipType](capi-native-type-visual-h.md#arkui_cliptype). For the path type. **ARKUI_CLIP_TYPE_PATH** is returned. |
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
| .value[0...15].f32 | 16 floating-point numbers of a 4 x 4 transformation matrix, used to perform matrix transformations such as translation, rotation, and scaling on images, arranged in row-major order. In this case, the value of **size** in [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) should not be **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0...15].f32 | 16 floating-point numbers of the 4 x 4 transformation matrix. |

## NODE_SHADOW

```c
NODE_SHADOW = 28
```

Shadow attribute, which can be set, reset, and obtained as required through APIs.<br>
This attribute is mutually exclusive with **NODE_CUSTOM_SHADOW**. A component can use only one shadow attribute. When both are set, the latter overrides the former. To use a predefined shadow style, use **NODE_SHADOW**. To customize shadow parameters, use **NODE_CUSTOM_SHADOW**.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Shadow effect of the current component. The parameter type is [ArkUI_ShadowStyle](capi-native-type-visual-h.md#arkui_shadowstyle).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Shadow effect of the current component. The parameter type is [ArkUI_ShadowStyle](capi-native-type-visual-h.md#arkui_shadowstyle).|

## NODE_CUSTOM_SHADOW

```c
NODE_CUSTOM_SHADOW = 29
```

Custom shadow effect. It is mutually exclusive with **NODE_SHADOW**. A component can use only one shadow attribute. When both are set, the latter overrides the former. To use a predefined shadow style, use **NODE_SHADOW**. To customize shadow parameters, use **NODE_CUSTOM_SHADOW**. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0]?.f32 | Blur radius of the shadow. Value range: [0, +∞). Passing a negative value returns a parameter verification failure. Unit: px. Default value: **0.0**. |
| .value[1]?.i32 | Whether to enable the coloring strategy. The value **1** means to enable the coloring strategy (the color is automatically picked from around the component to adapt to the background), and **0** means the opposite (a fixed color is used). The default value is **0**. Pass **1** when the shadow color needs to automatically adapt to the surrounding background. |
| .value[2]?.f32 | Offset of the shadow along the x-axis, in px. Default value: **0.0**. |
| .value[3]?.f32 | Offset of the shadow along the y-axis, in px. Default value: **0.0**. |
| .value[4]?.i32 | Shadow type. The parameter type is [ArkUI_ShadowType](capi-native-type-visual-h.md#arkui_shadowtype). The default value is **ARKUI_SHADOW_TYPE_COLOR**. |
| .value[5]?.u32 | It specifies the shadow color when the coloring strategy is disabled (**.value[1]** is set to **0**), in 0xARGB format. For example, **0xFFFF0000** indicates red. If not passed, the default value is **0xFF000000** (black). It specifies the coloring strategy when the coloring strategy is enabled (**.value[1]** is set to **1**), and the parameter type is [ArkUI_ColorStrategy](capi-native-type-visual-h.md#arkui_colorstrategy). |
| .value[6]?.u32 | Whether to fill the shadow. The value **1** means to fill the shadow, and **0** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Blur radius of the shadow, in px.|
| .value[1].i32 | Whether the coloring strategy is enabled. The value 1 indicates the coloring strategy is enabled, and **0** indicates the opposite. |
| .value[2].f32 | Offset of the shadow along the x-axis, in px.|
| .value[3].f32 | Offset of the shadow along the y-axis, in px.|
| .value[4].i32 | Shadow type. The parameter type is [ArkUI_ShadowType](capi-native-type-visual-h.md#arkui_shadowtype), and the default value is **ARKUI_SHADOW_TYPE_COLOR**. The enumerated values include: **ARKUI_SHADOW_TYPE_COLOR** (color shadow) and **ARKUI_SHADOW_TYPE_BLUR** (blur shadow). |
| .value[5].u32 | Shadow color, in 0xARGB format. For example, **0xFFFF0000** indicates red. |
| .value[6].u32 | Whether the shadow is filled. The value **1** means that the shadow is filled, and **0** means the opposite.|

## NODE_BACKGROUND_BLUR_STYLE

```c
NODE_BACKGROUND_BLUR_STYLE = 32
```

Background blur attribute. The blur effect is applied between the background layer and the content layer of the component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Blur type. The value is an enumerated value of [ArkUI_BlurStyle](capi-native-type-visual-h.md#arkui_blurstyle).|
| .value[1]?.i32 | Color mode. The value is an enumerated value of [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode). If not specified, the default color mode of the system is used. |
| .value[2]?.i32 | Adaptive color mode. The value is an enumerated value of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor). If not specified, the default adaptive color mode is used. Pass this parameter when a fixed color picking mode is required. |
| .value[3]?.f32 | Blur degree. The value range is [0.0, 1.0]. **0.0** indicates no blur, and **1.0** indicates the maximum blur effect. If not specified, the default value is **1.0**. Pass this parameter when the content blur degree needs to be adjusted. |
| .value[4]?.f32 | Start boundary of grayscale blur, that is, the position to which black is brightened. The valid value range is 0 to 127. A larger value produces a more obvious adjustment effect. |
| .value[5]?.f32 | End boundary of grayscale blur, that is, the position to which white is darkened. The valid value range is 0 to 127. A larger value produces a more obvious adjustment effect. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Blur type. The value is an enumerated value of [ArkUI_BlurStyle](capi-native-type-visual-h.md#arkui_blurstyle).|
| .value[1].i32 | Color mode. The value is an enumerated value of [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode). The enumerated values include: **ARKUI_COLOR_MODE_LIGHT** (light mode) and **ARKUI_COLOR_MODE_DARK** (dark mode). |
| .value[2].i32 | Adaptive color mode. The value is an enumerated value of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor).|
| .value[3].f32 | Blur degree. The value range is [0.0, 1.0].|
| .value[4].f32 | Start boundary of grayscale blur.|
| .value[5].f32 | End boundary of grayscale blur.|

## NODE_TRANSFORM_CENTER

```c
NODE_TRANSFORM_CENTER = 33
```

Center point attribute for image transformation and transition, which affects the center point behavior of transformation and transition attributes such as rotation (**NODE_ROTATE**/**NODE_ROTATE_ANGLE**/**NODE_ROTATE_TRANSITION**), scaling (**NODE_SCALE**/**NODE_SCALE_TRANSITION**), and translation (**NODE_TRANSLATE**/**NODE_TRANSLATE_TRANSITION**). This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>
Note: If the coordinate is expressed in a number that represents a percentage, the attribute obtaining API returns the calculated value in vp.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0]?.f32 | X-coordinate of the center point, in vp. Default value: **0.0**. |
| .value[1]?.f32 | Y-coordinate of the center point, in vp. Default value: **0.0**. |
| .value[2]?.f32 | Z-coordinate of the center point, in vp. Default value: **0.0**. |
| .value[3]?.f32 | X-coordinate of the center point, expressed in a number that represents a percentage. The value range is [0, 1]. For example, **0.2** indicates 20%. This attribute overwrites **value[0].f32**. The default value is **0.5f**.<br>The error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned when the value is out of range. |
| .value[4]?.f32 | Y-coordinate of the center point, expressed in a number that represents a percentage. The value range is [0, 1]. For example, **0.2** indicates 20%. This attribute overwrites **value[1].f32**. The default value is **0.5f**.<br>The error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned when the value is out of range. |
| .value[5]?.f32 | Z-coordinate of the center point, expressed in a number that represents a percentage. The value range is [0, 1]. For example, **0.2** indicates 20%. This attribute overwrites **value[2].f32**. The default value is **0.0f**.<br>The error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned when the value is out of range. |

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
| .value[0].f32 | Opacity value at the end of the transition (that is, the end point). The transition changes from the current opacity to this value. |
| .value[1].i32 | Animation duration, in ms. The value must be greater than 0. |
| .value[2].i32 | Animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve).|
| .value[3]?.i32 | Animation delay duration, in ms. The default value is **0** (no delay) when this parameter is not passed. Pass this parameter when the animation needs to wait for a period of time before starting. |
| .value[4]?.i32 | Number of times the animation is played. The default value is **1** (play once) when this parameter is not passed. Pass this parameter when the animation needs to be played repeatedly. |
| .value[5]?.i32 | Animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). The default value is **ARKUI_ANIMATION_PLAY_MODE_NORMAL**. Pass this parameter when a special play mode such as reverse playback or loop playback is required. |
| .value[6]?.f32 | Animation playback speed. The default value is **1.0** (normal speed) when this parameter is not passed. Pass this parameter when the animation needs to be played faster or slower. A value greater than **1.0** indicates acceleration, and a value less than **1.0** indicates deceleration. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Opacity values of the start and end points. The value range is [0, 1]. Values beyond the range are automatically corrected to the boundary values. |
| .value[1].i32 | Animation duration, in ms.|
| .value[2].i32 | Animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve).|
| .value[3].i32 | Animation delay duration, in ms.|
| .value[4].i32 | Number of times the animation is played.|
| .value[5].i32 | Animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode).|
| .value[6].f32 | Animation playback speed.|

## NODE_ROTATE_TRANSITION

```c
NODE_ROTATE_TRANSITION = 35
```

Transition rotation attribute, which takes effect only when a component is inserted or deleted. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | X-component of the rotation vector.|
| .value[1].f32 | Y-component of the rotation vector.|
| .value[2].f32 | Z-component of the rotation vector.|
| .value[3].f32 | Angle, in degrees (°). |
| .value[4].f32 | Line of sight, that is, the distance from the viewpoint to the z=0 plane. Value range: [0, +∞). A negative value is treated as **0**. Unit: vp. Default value: **0.0**. |
| .value[5].i32 | Animation duration, in ms.|
| .value[6].i32 | Animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve).|
| .value[7]?.i32 | Animation delay duration, in ms. If not passed, the default value is **0** (no delay). Pass this parameter when the animation needs to wait for a period of time before starting. |
| .value[8]?.i32 | Number of times the animation is played.|
| .value[9]?.i32 | Animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). Default value: **ARKUI_ANIMATION_PLAY_MODE_NORMAL**. |
| .value[10]?.f32 | Animation playback speed.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | X-component of the rotation vector.|
| .value[1].f32 | Y-component of the rotation vector.|
| .value[2].f32 | Z-component of the rotation vector.|
| .value[3].f32 | Angle, in degrees (°). |
| .value[4].f32 | Line of sight, in vp. |
| .value[5].i32 | Animation duration, in ms.|
| .value[6].i32 | Animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve).|
| .value[7].i32 | Animation delay duration, in ms.|
| .value[8].i32 | Number of times the animation is played.|
| .value[9].i32 | Animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode).|
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
| .value[0].f32 | Scale factor along the x-axis. Default value: **1.0**. |
| .value[1].f32 | Scale factor along the y-axis. Default value: **1.0**. |
| .value[2].f32 | Scale factor along the z-axis. Default value: **1.0**. |
| .value[3].i32 | Animation duration, in ms.|
| .value[4].i32 | Animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve).|
| .value[5]?.i32 | Animation delay duration, in ms. If not passed, the default value is **0** (no delay). Pass this parameter when the animation needs to wait for a period of time before starting. |
| .value[6]?.i32 | Number of times the animation is played.|
| .value[7]?.i32 | Animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). The default value is **ARKUI_ANIMATION_PLAY_MODE_NORMAL**. |
| .value[8]?.f32 | Animation playback speed.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Scale factor along the x-axis.|
| .value[1].f32 | Scale factor along the y-axis.|
| .value[2].f32 | Scale factor along the z-axis.|
| .value[3].i32 | Animation duration, in ms.|
| .value[4].i32 | Animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve).|
| .value[5].i32 | Animation delay duration, in ms.|
| .value[6].i32 | Number of times the animation is played.|
| .value[7].i32 | Animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode).|
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
| .value[4].i32 | Animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve).|
| .value[5]?.i32 | Animation delay duration, in ms. If not passed, the default value is **0** (no delay). Pass this parameter when the animation needs to wait for a period of time before starting. |
| .value[6]?.i32 | Number of times the animation is played.|
| .value[7]?.i32 | Animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). The default value is **ARKUI_ANIMATION_PLAY_MODE_NORMAL**. |
| .value[8]?.f32 | Animation playback speed.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Translation distance along the x-axis, in vp.|
| .value[1].f32 | Translation distance along the y-axis, in vp.|
| .value[2].f32 | Translation distance along the z-axis, in vp.|
| .value[3].i32 | Animation duration, in ms.|
| .value[4].i32 | Animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve).|
| .value[5].i32 | Animation delay duration, in ms.|
| .value[6].i32 | Number of times the animation is played.|
| .value[7].i32 | Animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode).|
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
| .value[0].i32 | Edge from which the component slides in and out during transition. The parameter type is [ArkUI_TransitionEdge](capi-native-type-visual-h.md#arkui_transitionedge). Different enumerated values determine from which edge of the screen the component slides in and out. |
| .value[1].i32 | Animation duration, in ms.|
| .value[2].i32 | Animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve).|
| .value[3]?.i32 | Animation delay duration, in ms. The default value is **0** (no delay) when this parameter is not passed. Pass this parameter when the animation needs to wait for a period of time before starting. |
| .value[4]?.i32 | Number of times the animation is played.|
| .value[5]?.i32 | Animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode). The default value is **ARKUI_ANIMATION_PLAY_MODE_NORMAL**. |
| .value[6]?.f32 | Animation playback speed.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Transition edge. The parameter type is [ArkUI_TransitionEdge](capi-native-type-visual-h.md#arkui_transitionedge).|
| .value[1].i32 | Animation duration, in ms.|
| .value[2].i32 | Animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve).|
| .value[3].i32 | Animation delay duration, in ms.|
| .value[4].i32 | Number of times the animation is played.|
| .value[5].i32 | Animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-visual-h.md#arkui_animationplaymode).|
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
| .value[0]?.f32 | X-coordinate of the sweep gradient center relative to the upper left corner of the component, in vp. Default value: 50% of the component width. |
| .value[1]?.f32 | Y-coordinate of the sweep gradient center relative to the upper left corner of the component, in vp. If not passed, the default value is the vertical center position of the component. Pass this parameter when the gradient center needs to be offset to a specific position. |
| .value[2]?.f32 | Start point of the sweep gradient, in degrees (°). Default value: **0**. |
| .value[3]?.f32 | End point of the sweep gradient, in degrees (°). Default value: **0**. |
| .value[4]?.f32 | Rotation angle of the sweep gradient, in degrees (°). Default value: **0**. |
| .value[5]?.i32 | Whether the colors are repeated. The value **0** means that the colors are not repeated, and **1** means the opposite. If not passed, the default value is **0** (no repeat). Pass **1** when the colors need to be filled cyclically and repeatedly. |
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. |
| colors | Colors of the color stops.|
| stops | Stop positions of the color stops.|
| size | Number of colors.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | X-coordinate of the sweep gradient center relative to the upper left corner of the component. |
| .value[1].f32 | Y-coordinate of the sweep gradient center relative to the upper left corner of the component. |
| .value[2].f32 | Start point of the sweep gradient, in degrees (°). Default value: **0**. |
| .value[3].f32 | End point of the sweep gradient, in degrees (°). Default value: **0**. |
| .value[4].f32 | Rotation angle of the sweep gradient, in degrees (°). Default value: **0**. |
| .value[5].i32 | Whether the colors are repeated. The value **0** means that the colors are not repeated, and **1** means the opposite. |
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. |
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
| .value[0]?.f32 | X-coordinate of the radial gradient center relative to the upper left corner of the current component. |
| .value[1]?.f32 | Y-coordinate of the radial gradient center relative to the upper left corner of the current component. |
| .value[2]?.f32 | Radius of the radial gradient. The value range is [0, +∞), and the default value is **0**. |
| .value[3]?.i32 | Whether the colors are repeated. The value **0** means that the colors are not repeated, and **1** means the opposite. If this parameter is not passed, the default value is **0** (no repeat). |
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. |
| colors | Colors of the color stops.|
| stops | Stop positions of the color stops.|
| size | Number of colors.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | X-coordinate of the radial gradient center relative to the upper left corner of the component. |
| .value[1].f32 | Y-coordinate of the radial gradient center relative to the upper left corner of the component. |
| .value[2].f32 | Radius of the radial gradient. The default value is **0**.|
| .value[3].i32 | Whether the colors are repeated. The value **false (0)** means that the colors are not repeated, and **true (1)** means the opposite. |
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. |
| colors | Colors of the color stops.|
| stops | Stop positions of the color stops.|
| size | Number of colors.|

## NODE_MASK

```c
NODE_MASK = 45
```

Adds a mask of the specified shape to the component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| 1. rect type | .value[0].u32: fill color, in 0xARGB format.<br>.value[1].u32: stroke color, in 0xARGB format.<br>.value[2].f32: stroke width, in vp.<br>.value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-visual-h.md#arkui_masktype). The value is **ARKUI_MASK_TYPE_RECTANGLE**.<br>.value[4].f32: width of the rectangle, in vp.<br>.value[5].f32: height of the rectangle, in vp.<br>.value[6].f32: width of the rounded corner of the rectangle, in vp.<br>.value[7].f32: height of the rounded corner of the rectangle, in vp.<br>.value[8]?.f32: radius of the upper left corner of the rectangle, in vp. The default value is **0**.<br>.value[9]?.f32: radius of the lower left corner of the rectangle, in vp. The default value is **0**.<br>.value[10]?.f32: radius of the upper right corner of the rectangle, in vp. The default value is **0**.<br>.value[11]?.f32: radius of the lower right corner of the rectangle, in vp. The default value is **0**. |
| 2. Circle| .value[0].u32: fill color, in 0xARGB format.<br>.value[1].u32: stroke color, in 0xARGB format.<br>.value[2].f32: stroke width, in vp.<br>.value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-visual-h.md#arkui_masktype). The value is **ARKUI_MASK_TYPE_CIRCLE**.<br>.value[4].f32: width of the circle, in vp.<br>.value[5].f32: height of the circle, in vp.|
| 3. Ellipse| .value[0].u32: fill color, in 0xARGB format.<br>.value[1].u32: stroke color, in 0xARGB format.<br>.value[2].f32: stroke width, in vp.<br>.value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-visual-h.md#arkui_masktype). The value is **ARKUI_MASK_TYPE_ELLIPSE**.<br>.value[4].f32: width of the ellipse, in vp.<br>.value[5].f32: height of the ellipse, in vp.|
| 4. path type | .value[0].u32: fill color, in 0xARGB format.<br>.value[1].u32: stroke color, in 0xARGB format.<br>.value[2].f32: stroke width, in vp.<br>.value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-visual-h.md#arkui_masktype). The value is **ARKUI_MASK_TYPE_PATH**.<br>.value[4].f32: width of the path, in vp.<br>.value[5].f32: height of the path, in vp.<br>.string: command string for drawing the path. The format follows the SVG path data syntax, for example, 'M0 0 L100 100 Z'. |
| 5. Progress| .value[0].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-visual-h.md#arkui_masktype). The value is **ARKUI_MASK_TYPE_PROGRESS**.<br>.value[1].f32: current value of the progress indicator.<br>.value[2].f32: maximum value of the progress indicator.<br>.value[3].u32: color of the progress indicator.|

**Returns**

| Type| Description|
| -- | -- |
| 1. Rectangle| .value[0].u32: fill color, in 0xARGB format.<br>.value[1].u32: stroke color, in 0xARGB format.<br>.value[2].f32: stroke width, in vp.<br>.value[3].i32: mask type.<br>.value[4].f32: width of the rectangle, in vp.<br>.value[5].f32: height of the rectangle, in vp.<br>.value[6].f32: width of the rounded corner of the rectangle, in vp.<br>.value[7].f32: height of the rounded corner of the rectangle, in vp.<br>.value[8]?.f32: radius of the upper left corner of the rectangle, in vp.<br>.value[9]?.f32: radius of the lower left corner of the rectangle, in vp.<br>.value[10]?.f32: radius of the upper right corner of the rectangle, in vp.<br>.value[11]?.f32: radius of the lower right corner of the rectangle, in vp.|
| 2. Circle| .value[0].u32: fill color, in 0xARGB format.<br>.value[1].u32: stroke color, in 0xARGB format.<br>.value[2].f32: stroke width, in vp.<br>.value[3].i32: mask type.<br>.value[4].f32: width of the circle, in vp.<br>.value[5].f32: height of the circle, in vp.|
| 3. Ellipse| .value[0].u32: fill color, in 0xARGB format.<br>.value[1].u32: stroke color, in 0xARGB format.<br>.value[2].f32: stroke width, in vp.<br>.value[3].i32: mask type.<br>.value[4].f32: width of the ellipse, in vp.<br>.value[5].f32: height of the ellipse, in vp.|
| 4. path type | .value[0].u32: fill color, in 0xARGB format.<br>.value[1].u32: stroke color, in 0xARGB format.<br>.value[2].f32: stroke width, in vp.<br>.value[3].i32: mask type.<br>.value[4].f32: width of the path, in vp.<br>.value[5].f32: height of the path, in vp.<br>.string: command string for drawing the path. The format follows the SVG path data syntax, for example, 'M0 0 L100 100 Z'. |
| 5. Progress| .value[0].i32: mask type.<br>.value[1].f32: current value of the progress indicator.<br>.value[2].f32: maximum value of the progress indicator.<br>.value[3].u32: color of the progress indicator.|

## NODE_BLEND_MODE

```c
NODE_BLEND_MODE = 46
```

Blends the component's background with the content of the component's child node. It is used for visual composition scenarios such as overlay transparency effects and color blending. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Blend mode of the current component. The parameter type is [ArkUI_BlendMode](capi-native-type-visual-h.md#arkui_blendmode). The default value is **ARKUI_BLEND_MODE_NONE**. |
| .value[1]?.i32 | How the specified blend mode is applied. The parameter type is [ArkUI_BlendApplyType](capi-native-type-visual-h.md#arkui_blendapplytype). The default value is **BLEND_APPLY_TYPE_FAST**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Blend mode of the current component. The parameter type is [ArkUI_BlendMode](capi-native-type-visual-h.md#arkui_blendmode). The default value is **ARKUI_BLEND_MODE_NONE**.|
| .value[1].i32 | How the specified blend mode is applied. The parameter type is [ArkUI_BlendApplyType](capi-native-type-visual-h.md#arkui_blendapplytype). The default value is **BLEND_APPLY_TYPE_FAST**. The enumerated values include: **BLEND_APPLY_TYPE_FAST** (fast implementation, non-offscreen) and **BLEND_APPLY_TYPE_OFFSCREEN** (offscreen implementation). |

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
| .value[0].f32 | Contrast. If the value is **1**, the source image is displayed. A larger value indicates a higher contrast. The default value is **1**. The value range is [0, 10). If the value is out of range, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Contrast. The value range is [0, 10).|

## NODE_FOREGROUND_COLOR

```c
NODE_FOREGROUND_COLOR = 53
```

Foreground color attribute, which can be set and obtained as required through APIs. The reset API has no effect on this attribute, because the foreground color is an attribute type that cannot automatically restore its default value, and the reset operation does not change the foreground color that has been set.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Color, in 0xAARRGGBB format. For example, **0xFFFF0000** indicates red. The default value is **0xFF000000**. |
| .value[0].i32 | Coloring strategy. The value is an enumerated value of [ArkUI_ColorStrategy](capi-native-type-visual-h.md#arkui_colorstrategy). |

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

Implicit shared element transition within a component (the transition is automatically triggered when the component is inserted or deleted). This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0]?.i32 | Two components bound to the shared element. The value is **1** or **0**. By default, the out component does not continue to participate in the shared element animation when not yet deleted, which means that it stays in its original position.|
| .string | ID used to set up a binding relationship. If this attribute is set to an empty string **""**, the binding relationship is cleared. The value can be dynamically changed to refresh the binding relationship. One ID can be bound to only two components, which function as in and out components. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Two components bound to the shared element. The value is **1** or **0**. By default, the out component does not continue to participate in the shared element animation when not yet deleted, which means that it stays in its original position. |
| .string | ID used to set up a binding relationship. If this attribute is set to an empty string **""**, the binding relationship is cleared. The value can be dynamically changed to refresh the binding relationship. One ID can be bound to only two components, which function as in and out components. |

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
| .value[0].i32 | How the final state of the component's content is rendered. The value is an enumerated value of [ArkUI_RenderFit](capi-native-type-visual-h.md#arkui_renderfit).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | How the final state of the component's content is rendered. The value is an enumerated value of [ArkUI_RenderFit](capi-native-type-visual-h.md#arkui_renderfit).|

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
| .value[0].u32 | Color of the four outlines, in 0xARGB format, for example, **0xFFFF11FF**. This parameter takes effect only when **.value[0]** is passed. |
| .value[0].u32 | Color of the top outline, in 0xARGB format, for example, **0xFFFF11FF**. This parameter takes effect when the four values from **.value[0]** to **.value[3]** are passed. |
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
| .value[0].i32 | Foreground blur style. The value is an enumerated value of [ArkUI_BlurStyle](capi-native-type-visual-h.md#arkui_blurstyle).|
| .value[1]?.i32 | Color mode used for the foreground blur. The value is an enumerated value of [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode). If not passed, the default value is **ARKUI_COLOR_MODE_SYSTEM**. |
| .value[2]?.i32 | Adaptive color mode used for the foreground blur. The value is an enumerated value of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor).|
| .value[3]?.f32 | Blur degree. The value range is [0.0, 1.0].|
| .value[4]?.f32 | Brightness of black in the grayscale blur. The value range is [0,127]. If not passed, the default value is **0**. |
| .value[5]?.f32 | Degree of darkening the white color in the grayscale blur. The value range is [0,127]. If not passed, the default value is **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Foreground blur style. The value is an enumerated value of [ArkUI_BlurStyle](capi-native-type-visual-h.md#arkui_blurstyle).|
| .value[1].i32 | Color mode used for the foreground blur. The value is an enumerated value of [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode).|
| .value[2].i32 | Adaptive color mode used for the foreground blur. The value is an enumerated value of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor).|
| .value[3].f32 | Blur degree. The value range is [0.0, 1.0].|
| .value[4].f32 | Brightness of black in the grayscale blur. The value range is [0,127]. |
| .value[5].f32 | Degree of darkening the white color in the grayscale blur. The value range is [0,127]. |

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
| .object | Transition effect when the component is inserted or deleted. The parameter type is [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md). Different **TransitionEffect** values determine the animation effect type when a component appears and disappears. |

**Returns**

| Type| Description|
| -- | -- |
| .object | Transition effect when the component is inserted or deleted. The parameter type is [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md). |

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
| .value[0].f32 | Background blur radius. The value range is [0, +∞). If the value is out of range, the error code [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. Unit: px. Default value: **0.0**. |
| .value[1]?.f32 | Brightness of black in the grayscale blur. The value range is [0, 127]. If this parameter is not passed, the default value is **0**. Pass this parameter when the degree to which black areas are brightened in the blur effect needs to be finely adjusted. |
| .value[2]?.f32 | Degree of darkening the white color in the grayscale blur. The value range is [0, 127]. If this parameter is not passed, the default value is **0**. Pass this parameter when the degree to which white areas are darkened in the blur effect needs to be finely adjusted. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Background blur radius. The value range is [0, +∞). Unit: px. |
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
| .value[0].f32 | Pixel value of the image that remains unchanged when the left side of the image is stretched, in vp. Default value: **0**. |
| .value[1].f32 | Pixel value of the image that remains unchanged when the top side of the image is stretched, in vp. Default value: **0**. |
| .value[2].f32 | Pixel value of the image that remains unchanged when the right side of the image is stretched, in vp. Default value: **0**. |
| .value[3].f32 | Pixel value of the image that remains unchanged when the bottom side of the image is stretched, in vp. Default value: **0**. |

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

Component translation, with support for percentage-based translation parameters. This attribute is mutually exclusive with **NODE_TRANSLATE**. A component can use only one translation attribute. When both are set, the latter overrides the former. This attribute can be set, reset, and obtained as required through APIs.<br>
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

Component rotation with multi-axis angle control. This attribute can be reset and obtained as required through APIs. It is mutually exclusive with **NODE_ROTATE**. A component can use only one rotation attribute. When both are set, the latter overrides the former.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Rotation angle around the x-axis. Unit: degrees (°). Default value: **0**. |
| .value[1].f32 | Rotation angle around the y-axis. Unit: degrees (°). Default value: **0**. |
| .value[2].f32 | Rotation angle around the z-axis. Unit: degrees (°). Default value: **0**. |
| .value[3].f32 | Line of sight, that is, the distance from the viewpoint to the z=0 plane, in px. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Rotation angle around the x-axis. Unit: degrees (°). Default value: **0**. |
| .value[1].f32 | Rotation angle around the y-axis. Unit: degrees (°). Default value: **0**. |
| .value[2].f32 | Rotation angle around the z-axis. Unit: degrees (°). Default value: **0**. |
| .value[3].f32 | Line of sight, that is, the distance from the viewpoint to the z=0 plane, in px. The default value is **0**.|

## NODE_PIXEL_ROUND

```c
NODE_PIXEL_ROUND = 109
```

Pixel rounding policy of the component, used to avoid issues such as visual aliasing when the component is rendered at a scaled size or non-integer-pixel position. This attribute can be set, reset, and obtained as required through APIs.<br>
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

## NODE_SYSTEM_MATERIAL

```c
NODE_SYSTEM_MATERIAL = 127
```

System material attribute, which can be set, reset, and obtained as required through APIs.

This attribute is available only for devices that support system materials. Otherwise, the error code [ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) will be returned when this attribute is set. You can call [OH_ArkUI_NativeModule_GetSystemMaterialSupported](./capi-native-material-h.md#oh_arkui_nativemodule_getsystemmaterialsupported) to check whether the device supports system materials. When this error code is encountered, it is recommended to first check whether the device supports system materials. If not, this attribute should not be used.

The material effect varies depending on device computing power. A material level corresponding to a computing power level is defined by [ArkUI_MaterialLevel](./capi-native-material-h.md#arkui_materiallevel) and can be obtained through [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](./capi-native-material-h.md#oh_arkui_nativemodule_getglobalmateriallevel). On devices related to the material level [ARKUI_MATERIAL_LEVEL_SMOOTH](./capi-native-material-h.md#arkui_materiallevel), setting **NODE_SYSTEM_MATERIAL** overrides the shadow effect of **NODE_SHADOW**/**NODE_CUSTOM_SHADOW**, the outline color of **NODE_OUTLINE_COLOR**, and the outline width of **NODE_OUTLINE_WIDTH**, and changes the component background color. On devices related to the material level [ARKUI_MATERIAL_LEVEL_EXQUISITE](./capi-native-material-h.md#arkui_materiallevel) or [ARKUI_MATERIAL_LEVEL_GENTLE](./capi-native-material-h.md#arkui_materiallevel), the shadow attribute is affected and a filter effect is added to the system material layer, generating a glass-like effect.

The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| .object | System material object. The parameter type is [ArkUI_ImmersiveMaterialHandle](./capi-arkui-nativemodule-arkui-immersivematerialhandle.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | System material object. The parameter type is [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerialhandle.md). The **ArkUI_ImmersiveMaterialHandle** object in the return value is a pointer to a static member. Therefore, you do not need to and are not allowed to release the returned object using [OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy](capi-native-material-h.md#oh_arkui_nativemodule_immersivematerial_destroy). |