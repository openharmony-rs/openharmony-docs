# Visual

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_CUSTOM_SHADOW

```c
NODE_CUSTOM_SHADOW
```

**Description**

User-defined shadow effect, which is mutually exclusive with NODE_SHADOW. A component can use only one shadow attribute setting mode. If the shadow attribute setting mode is set at the same time, the shadow attribute setting mode overrides the shadow attribute setting mode. To use the predefined shadow style, use NODE_SHADOW. To customize shadow parameters, use NODE_CUSTOM_SHADOW. Interfaces for setting, resetting, and obtaining attributes are supported. <br>The format of the return value of the attribute setting method parameter and attribute obtaining method [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is as follows: Parameters: * * <ul> <li>.value[0]?.f32: shadow blur radius. The value range is[0, + △). If a negative value is transferred, a parameter verification failure is returned. The unit is px. The default value is 0.0. </li> <li>.value[1]?.i32: Indicates whether to enable intelligent color obtaining. The value 0 indicates that intelligent color obtaining is disabled(fixed colors are used). The value 1 indicates that intelligent color obtaining is enabled(colors are automatically obtained from the surrounding area of the component to adapt to the background). The default value is disabled. </li> <li>.value[2]?.f32: X-axis offset of the shadow. The unit is px. The default value is 0.0. </li> <li>.value[3]?.f32: offset of the shadow on the Y axis. The unit is px. The default value is 0.0. </li> <li>.value[4]?.i32: shadow type. The parameter type is [ArkUI_ShadowType](capi-native-type-visual-h.md#arkui_shadowtype). The default value is ARKUI_SHADOW_TYPE_COLOR. </li> <li>.value[5]?.u32: indicates the shadow color when intelligent color selection is disabled(.value[1] is 0). The value is in the format of 0xAARRGGBB. For example, 0xFFFF0000 indicates red. If this parameter is not specified, the default value is 0xFF000000(black). When intelligent color selection is enabled(.value[1] is set to 1), this parameter indicates the color policy. The enumerated value of [ArkUI_ColorStrategy](capi-native-type-visual-h.md#arkui_colorstrategy) is used. </li> <li>.value[6]?.u32: indicates whether the shadow is filled. The value 0 indicates that the shadow is not filled, and the value 1 indicates that the shadow is filled. </li> </ul> Return: * * <ul> <li>.value[0].f32: shadow blur radius, in px. </li> <li>.value[1].i32: indicates whether to enable intelligent color obtaining. The value 0 indicates that intelligent color obtaining is disabled, and the value 1 indicates that intelligent color obtaining is enabled. </li> <li>.value[2].f32: X-axis offset of the shadow, in px. </li> <li>.value[3].f32: offset of the shadow on the Y axis, in px. </li> <li>.value[4].i32: shadow type. The parameter type is [ArkUI_ShadowType](capi-native-type-visual-h.md#arkui_shadowtype). The default value is RKUI_SHADOW_TYPE_COLOR. The options are as follows: RKUI_SHADOW_TYPE_COLOR(color shadow) and RKUI_SHADOW_TYPE_BLUR( blur shadow). </li> <li>.value[5].u32: shadow color. The value is in the format of 0xAARRGGBB. For example, 0xFFFF0000 indicates red. </li> <li>.value[6].u32: indicates whether the shadow is filled. The value 0 indicates that the shadow is not filled, and the value 1 indicates that the shadow is filled. </li> </ul>

<!--Device-NODE_CUSTOM_SHADOW--><!--Device-NODE_CUSTOM_SHADOW-End-->

**Since**: 12

### NODE_MASK

```c
NODE_MASK
```

**Description**

The mask of the specified shape is added to the component. The attribute setting, attribute reset, and attribute obtaining interfaces are supported. <br>The format of the return value of the attribute setting method parameter and attribute obtaining method [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is as follows: **Parameters: * *
1. Rectangle type: <ul> <li>.value[0].u32: fill color. The value type is 0xAARRGGBB. </li> <li>.value[1].u32: stroke color. The type is 0xAARRGGBB. </li> <li>.value[2].f32: stroke width, in vp. </li> <li>.value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-visual-h.md#arkui_masktype), RKUI_MASK_TYPE_RECKNOWNLE. </li> <li>.value[4].f32: rectangle width, in vp. </li> <li>.value[5].f32: rectangle height, in vp. </li> <li>.value[6].f32: width of the rounded corner of the rectangle, in vp. </li> <li>.value[7].f32: height of the rounded corner of the rectangle, in vp. </li> <li>.value[8]?.f32: radius of the upper left corner of the rectangle, in vp. The default value is 0. </li> <li>.value[9]?.f32: radius of the lower left corner of the rectangle, in vp. The default value is 0. </li> <li>.value[10]?.f32: radius of the upper right corner of the rectangle, in vp. The default value is 0. </li> <li>.value[11]?.f32: radius of the lower right corner of the rectangle, in vp. The default value is 0. </li> </ul>
2. Circle type: <ul> <li>.value[0].u32: fill color. The value type is 0xAARRGGBB. </li> <li>.value[1].u32: stroke color. The type is 0xAARRGGBB. </li> <li>.value[2].f32: stroke width, in vp. </li> <li>.value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-visual-h.md#arkui_masktype), RKUI_MASK_TYPE_CIRCLE. </li> <li>.value[4].f32: circle width, in vp. </li> <li>.value[5].f32: circle height, in vp. </li> </ul>
3. ellipse type: <ul> <li>.value[0].u32: fill color. The value type is 0xAARRGGBB. </li> <li>.value[1].u32: stroke color. The type is 0xAARRGGBB. </li> <li>.value[2].f32: stroke width, in vp. </li> <li>.value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-visual-h.md#arkui_masktype), RKUI_MASK_TYPE_ELLIPSE. </li> <li>.value[4].f32: width of the ellipse, in vp. </li> <li>.value[5].f32: height of the ellipse, in vp. </li> </ul>
4. Path type: <ul> <li>.value[0].u32: fill color. The value type is 0xAARRGGBB. </li> <li>.value[1].u32: stroke color. The type is 0xAARRGGBB. </li> <li>.value[2].f32: stroke width, in vp. </li> <li>.value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-visual-h.md#arkui_masktype), RKUI_MASK_TYPE_PATH. </li> <li>.value[4].f32: path width, in vp. </li> <li>.value[5].f32: path height, in vp. </li> <li>.string: command string for drawing a path. The format complies with the SVG path data syntax, for example, 'M0 0 L100 100 Z'. </li> </ul>
5. Progress type: <ul> <li>.value[0].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-visual-h.md#arkui_masktype), RKUI_MASK_TYPE_PROGRESS. </li> <li>.value[1].f32: Current value of the progress mask. </li> <li>.value[2].f32: maximum value of the progress mask. </li> <li>.value[3].u32: color of the progress mask. </li> </ul> **Return to: * *
1. Rectangle type: <ul> <li>.value[0].u32: fill color. The value type is 0xAARRGGBB. </li> <li>.value[1].u32: stroke color. The type is 0xAARRGGBB. </li> <li>.value[2].f32: stroke width, in vp. </li> <li>.value[3].i32: mask type. </li> <li>.value[4].f32: rectangle width, in vp. </li> <li>.value[5].f32: rectangle height, in vp. </li> <li>.value[6].f32: width of the rounded corner of the rectangle, in vp. </li> <li>.value[7].f32: height of the rounded corner of the rectangle, in vp. </li> <li>.value[8].f32: radius of the upper left corner of the rectangle, in vp. </li> <li>.value[9].f32: radius of the lower left corner of a rectangle, in vp. </li> <li>.value[10].f32: radius of the upper right corner of the rectangle, in vp. </li> <li>.value[11].f32: radius of the lower right corner of the rectangle, in vp. </li> </ul>
2. Circle type: <ul> <li>.value[0].u32: fill color. The value type is 0xAARRGGBB. </li> <li>.value[1].u32: stroke color. The type is 0xAARRGGBB. </li> <li>.value[2].f32: stroke width, in vp. </li> <li>.value[3].i32: mask type. </li> <li>.value[4].f32: circle width, in vp. </li> <li>.value[5].f32: circle height, in vp. </li> </ul>
3. ellipse type: <ul> <li>.value[0].u32: fill color. The value type is 0xAARRGGBB. </li> <li>.value[1].u32: stroke color. The type is 0xAARRGGBB. </li> <li>.value[2].f32: stroke width, in vp. </li> <li>.value[3].i32: mask type. </li> <li>.value[4].f32: width of the ellipse, in vp. </li> <li>.value[5].f32: height of the ellipse, in vp. </li> </ul>
4. Path type: <ul> <li>.value[0].u32: fill color. The value type is 0xAARRGGBB. </li> <li>.value[1].u32: stroke color. The type is 0xAARRGGBB. </li> <li>.value[2].f32: stroke width, in vp. </li> <li>.value[3].i32: mask type. </li> <li>.value[4].f32: path width, in vp. </li> <li>.value[5].f32: path height, in vp. </li> <li>.string: command string for drawing a path. </li> </ul>
5. Progress type: <ul> <li>.value[0].i32: mask type. </li> <li>.value[1].f32: Current value of the progress mask. </li> <li>.value[2].f32: maximum value of the progress mask. </li> <li>.value[3].u32: color of the progress mask. </li> </ul>

<!--Device-NODE_MASK--><!--Device-NODE_MASK-End-->

**Since**: 12

### NODE_FOREGROUND_COLOR

```c
NODE_FOREGROUND_COLOR
```

**Description**

Foreground color attribute, which supports attribute setting and attribute obtaining interfaces. The attribute resetting interface has no effect. The foreground color is an attribute type that cannot be automatically restored to the default value. Therefore, the reset operation does not change the preset foreground color. <br>The format of the return value of the attribute setting method parameter and attribute obtaining method [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is as follows: **Parameters: * * <ul> <li>.value[0].u32: color value. The value is of the 0xAARRGGBB type. For example, 0xFFFF0000 indicates red. The default value is 0xFF000000. Used to directly specify a color value. </li> <li>.value[0].i32: color value enumeration [ArkUI_ColorStrategy](capi-native-type-visual-h.md#arkui_colorstrategy). </li> </ul> **Return to: * * <ul> <li>.value[0].u32: color value. The value type is 0xAARRGGBB. </li> </ul>

<!--Device-NODE_FOREGROUND_COLOR--><!--Device-NODE_FOREGROUND_COLOR-End-->

**Since**: 12

### NODE_OUTLINE_COLOR

```c
NODE_OUTLINE_COLOR
```

**Description**

Outer stroke color attribute, which supports attribute setting, attribute resetting, and attribute obtaining interfaces. <br>The format of the return value of the attribute setting method parameter and attribute obtaining method [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is as follows: **Parameters: * *
1. If only .value[0] is transferred, set the border colors of the four edges. <ul> <li>.value[0].u32: Set the border colors of the four edges in a unified manner. The color is represented by 0xAARRGGBB, for example, 0xFFFF11FF. </li> </ul>
2. When values ranging from.value[0] to.value[3] are transferred, set the border colors of the four edges respectively. <ul> <li>.value[0].u32: color of the upper border. The color is represented by 0xAARRGGBB, for example, 0xFFFF11FF. </li> <li>.value[1].u32: color of the border on the right. The color is represented by 0xAARRGGBB, for example, 0xFFFF11FF. </li> <li>.value[2].u32: indicates the lower border color, which is represented by 0xAARRGGBB, for example, 0xFFFF11FF. </li> <li>.value[3].u32: color of the left border. The color is represented by 0xAARRGGBB, for example, 0xFFFF11FF. </li> </ul> **Return to: * * <ul> <li>.value[0].u32: color of the upper border. The color is represented by 0xAARRGGBB, for example, 0xFFFF11FF. </li> <li>.value[1].u32: color of the border on the right. The color is represented by 0xAARRGGBB, for example, 0xFFFF11FF. </li> <li>.value[2].u32: indicates the lower border color, which is represented by 0xAARRGGBB, for example, 0xFFFF11FF. </li> <li>.value[3].u32: color of the left border. The color is represented by 0xAARRGGBB, for example, 0xFFFF11FF. </li> </ul>

<!--Device-NODE_OUTLINE_COLOR--><!--Device-NODE_OUTLINE_COLOR-End-->

**Since**: 12

### NODE_COLOR_BLEND

```c
NODE_COLOR_BLEND
```

**Description**

Adds the color overlay effect for the widget, and supports the interface for setting, resetting, and obtaining attributes. <br>The format of the return value of the attribute setting method parameter and attribute obtaining method [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is as follows: **Parameters: * * <ul> <li>.value[0].u32: overlay color, represented by 0xAARRGGBB. The default value is 0x00000000. </li> </ul> **Return to: * * <ul> <li>.value[0].u32: superimposed color, represented by 0xAARRGGBB, for example, 0xFFFF11FF. </li> </ul>

<!--Device-NODE_COLOR_BLEND--><!--Device-NODE_COLOR_BLEND-End-->

**Since**: 12


