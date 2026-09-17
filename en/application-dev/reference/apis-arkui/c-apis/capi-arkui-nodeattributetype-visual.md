# Visual

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_TRANSLATE

```c
NODE_TRANSLATE
```

**Description**

Defines the translate attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].f32: distance to translate along the x-axis, in vp. The default value is <b>0</b>.<br>.value[1].f32: distance to translate along the y-axis, in vp. The default value is <b>0</b>.<br>.value[2].f32: distance to translate along the z-axis, in vp. The default value is <b>0</b>. <br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].f32: distance to translate along the x-axis, in vp.<br>.value[1].f32: distance to translate along the y-axis, in vp.<br>.value[2].f32: distance to translate along the z-axis, in vp.

**Since**: 12

### NODE_SCALE

```c
NODE_SCALE
```

**Description**

Defines the scale attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].f32: scale factor along the x-axis. The default value is <b>1</b>.<br>.value[1].f32: scale factor along the y-axis. The default value is <b>1</b>. <br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].f32: scale factor along the x-axis.<br>.value[1].f32: scale factor along the y-axis.

**Since**: 12

### NODE_ROTATE

```c
NODE_ROTATE
```

**Description**

Defines the rotate attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].f32: X coordinate of the rotation axis vector. The default value is <b>0</b>.<br>.value[1].f32: Y coordinate of the rotation axis vector. The default value is <b>0</b>.<br>.value[2].f32: Z coordinate of the rotation axis vector. The default value is <b>0</b>.<br>.value[3].f32: rotation angle. The default value is <b>0</b>.<br>.value[4].f32: line of sight, that is, the distance from the viewpoint to the z=0 plane, in vp.<br>The default value is <b>0</b>. <br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].f32: X coordinate of the rotation axis vector.<br>.value[1].f32: Y coordinate of the rotation axis vector.<br>.value[2].f32: Z coordinate of the rotation axis vector.<br>.value[3].f32: rotation angle.<br>.value[4].f32: line of sight, that is, the distance from the viewpoint to the z=0 plane, in vp.

**Since**: 12

### NODE_BRIGHTNESS

```c
NODE_BRIGHTNESS
```

**Description**

Sets the brightness attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].f32: brightness value. The default value is <b>1.0</b>, and the recommended value range is [0, 2]. <br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].f32: brightness value.

**Since**: 12

### NODE_SATURATION

```c
NODE_SATURATION
```

**Description**

Sets the saturation attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute: <br>.value[0].f32: saturation value. The default value is <b>1.0</b>, and the recommended value range is [0, 50). <br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].f32: saturation value.

**Since**: 12

### NODE_BLUR

```c
NODE_BLUR
```

**Description**

Sets the blur attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute: <br>.value[0].f32: blur radius. A larger value indicates a higher blur degree. If the value is <b>0</b>,<br>the component is not blurred. The unit is vp. The default value is <b>0.0</b>. <br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].f32: blur radius. The larger the fuzzy radius, the more blurred the image. If the value is <b>0</b>, the image is not blurred. The unit is vp.

**Since**: 12

### NODE_LINEAR_GRADIENT

```c
NODE_LINEAR_GRADIENT
```

**Description**

Sets the gradient attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].f32: start angle of the linear gradient. This attribute takes effect only when<br>{@link ArkUI_LinearGradientDirection} is set to <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b>.<br>A positive value indicates a clockwise rotation from the origin, (0, 0). The default value is <b>180</b>. <br>.value[1].i32: direction of the linear gradient. When it is set, the <b>angle</b> attribute does not take effect.<br>The parameter type is {@link ArkUI_LinearGradientDirection}: <br>.value[2].i32: whether the colors are repeated. The default value is <b>false</b>. <br>.object: array of color stops, each of which consists of a color and its stop position.<br>Invalid colors are automatically skipped. <br>colors: colors of the color stops. <br>stops: stop positions of the color stops. <br>size: number of colors. <br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].f32: start angle of the linear gradient. <br>.value[1].i32: direction of the linear gradient. It does not take effect when <b>angle</b> is set. <br>.value[2].i32: whether the colors are repeated. .object: array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.

**Since**: 12

### NODE_OPACITY

```c
NODE_OPACITY
```

**Description**

Defines the opacity attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].f32: opacity value. The value ranges from 0 to 1. <br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].f32: opacity value. The value ranges from 0 to 1.

**Since**: 12

### NODE_CLIP

```c
NODE_CLIP
```

**Description**

Defines the clipping and masking attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].i32: whether to clip the component based on the parent container bounds.<br>The value <b>1</b> means to clip the component, and <b>0</b> means the opposite. <br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].i32: whether to clip the component based on the parent container bounds. The value <b>1</b> means to clip the component, and <b>0</b> means the opposite.

**Since**: 12

### NODE_CLIP_SHAPE

```c
NODE_CLIP_SHAPE
```

**Description**

Defines the clipping region on the component. This attribute can be set and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute,<br>which supports four types of shapes:<br>1. Rectangle:<br>.value[0].i32: type of shape. The parameter type is {@link ArkUI_ClipType}.<br>The value is <b>ARKUI_CLIP_TYPE_RECTANGLE</b> for the rectangle shape. <br>.value[1].f32: width of the rectangle.<br>.value[2].f32: height of rectangle.<br>.value[3].f32: width of the rounded corner of the rectangle.<br>.value[4].f32: height of the rounded corner of the rectangle.<br>.value[5]?.f32: radius of the top left corner of the rectangular shape.<br>.value[6]?.f32: radius of the bottom left corner of the rectangular shape.<br>.value[7]?.f32: radius of the top right corner of the rectangular shape.<br>.value[8]?.f32: radius of the bottom right corner of the rectangular shape.<br>?.object: clipOption of the rectangle. The parameter type is {@link ArkUI_RenderNodeClipOption} type.<br>It takes effect when only the .object parameter is passed, ArkUI_RenderNodeClipOption type is rectangle, and .size must be equal to 1.<br>2. Circle:<br>.value[0].i32: type of shape. The parameter type is {@link ArkUI_ClipType}.<br>The value is <b>ARKUI_CLIP_TYPE_CIRCLE</b> for the circle shape.<br>.value[1].f32: width of the circle.<br>.value[2].f32: height of the circle.<br>?.object: clipOption of the circle. The parameter type is {@link ArkUI_RenderNodeClipOption} type.<br>It takes effect when only the .object parameter is passed, ArkUI_RenderNodeClipOption type is circle, and .size must be equal to 1.<br>3.Ellipse:<br>.value[0].i32: type of shape. The parameter type is {@link ArkUI_ClipType}.<br>The value is <b>ARKUI_CLIP_TYPE_ELLIPSE</b> for the ellipse shape.<br>.value[1].f32: width of the ellipse.<br>.value[2].f32: height of the ellipse.<br>?.object: clipOption of the ellipse. The parameter type is {@link ArkUI_RenderNodeClipOption} type.<br>It takes effect when only the .object parameter is passed, ArkUI_RenderNodeClipOption type is ellipse, and .size must be equal to 1.<br>4. Path:<br>.value[0].i32: type of shape. The parameter type is {@link ArkUI_ClipType}.<br>The value is <b>ARKUI_CLIP_TYPE_PATH</b> for the path shape.<br>.value[1].f32: width of the path.<br>.value[2].f32: height of the path.<br>.string: command for drawing the path.<br>?.object: clipOption of the path. The parameter type is {@link ArkUI_RenderNodeClipOption} type.<br>It takes effect when only the .object parameter is passed, ArkUI_RenderNodeClipOption type is path, and .size must be equal to 1.<br>Format of the return value {@link ArkUI_AttributeItem}, which supports four types of shapes: <br>1. Rectangle:<br>.value[0].i32: type of shape. The parameter type is {@link ArkUI_ClipType}.<br>The value is <b>ARKUI_CLIP_TYPE_RECTANGLE</b> for the rectangle shape. <br>.value[1].f32: width of the rectangle.<br>.value[2].f32: height of rectangle.<br>.value[3].f32: width of the rounded corner of the rectangle.<br>.value[4].f32: height of the rounded corner of the rectangle.<br>.value[5].f32: radius of the top left corner of the rectangular shape; <br>.value[6].f32: radius of the bottom left corner of the rectangular shape; <br>.value[7].f32: radius of the top right corner of the rectangular shape; <br>.value[8].f32: radius of the bottom right corner of the rectangular shape; <br>.value[9]?.f32: horizontal coordinate offset of the rectangle. <br>.value[10]?.f32: vertical coordinate offset of the rectangle. <br>2. Circle:<br>.value[0].i32: type of shape. The parameter type is {@link ArkUI_ClipType}.<br>The value is <b>ARKUI_CLIP_TYPE_CIRCLE</b> for the circle shape.<br>.value[1].f32: width of the circle.<br>.value[2].f32: height of the circle.<br>.value[3]?.f32: horizontal coordinate offset of the circle.<br>.value[4]?.f32: vertical coordinate offset of the circle.<br>3.Ellipse:<br>.value[0].i32: type of shape. The parameter type is {@link ArkUI_ClipType}.<br>The value is <b>ARKUI_CLIP_TYPE_ELLIPSE</b> for the ellipse shape.<br>.value[1].f32: width of the ellipse.<br>.value[2].f32: height of the ellipse.<br>.value[3]?.f32: horizontal coordinate offset of the ellipse.<br>.value[4]?.f32: vertical coordinate offset of the ellipse.<br>4. Path:<br>.value[0].i32: type of shape. The parameter type is {@link ArkUI_ClipType}. The value is <b>ARKUI_CLIP_TYPE_PATH</b> for the path shape. .value[1].f32: width of the path.<br>.value[2].f32: height of the path. .string: command for drawing the path.

**Since**: 12

### NODE_TRANSFORM

```c
NODE_TRANSFORM
```

**Description**

Defines the transform attribute, which can be used to translate, rotate, and scale images. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0...15].f32: 16 floating-point numbers. <br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0...15].f32: 16 floating-point numbers.

**Since**: 12

### NODE_SHADOW

```c
NODE_SHADOW
```

**Description**

Defines the shadow attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].i32: shadow effect. The parameter type is {@link ArkUI_ShadowStyle}. <br><br>Format of the return value {@link ArkUI_AttributeItem}:<br>.value[0].i32: shadow effect. The parameter type is {@link ArkUI_ShadowStyle}.

**Since**: 12

### NODE_CUSTOM_SHADOW

```c
NODE_CUSTOM_SHADOW
```

**Description**

Defines the custom shadow effect. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0]?.f32: blur radius of the shadow, in px.<br>.value[1]?.i32: whether to enable the coloring strategy. The value <b>1</b> means to enable the coloring<br>strategy, and <b>0</b> (default value) means the opposite.<br>.value[2]?.f32: offset of the shadow along the x-axis, in px.<br>.value[3]?.f32: offset of the shadow along the y-axis, in px.<br>.value[4]?.i32: shadow type {@link ArkUI_ShadowType}. The default value is <b>ARKUI_SHADOW_TYPE_COLOR</b>.<br>.value[5]?.u32: shadow color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br>.value[6]?.u32: whether to fill the shadow. The value <b>1</b> means to fill the shadow, and <b>0</b><br>means the opposite.<br><br>Format of the return value {@link ArkUI_AttributeItem}:<br>.value[0].f32: blur radius of the shadow, in px.<br>.value[1].i32: whether to enable the coloring strategy. <br>.value[2].f32: offset of the shadow along the x-axis, in px.<br>.value[3].f32: offset of the shadow along the y-axis, in px.<br>.value[4].i32: shadow type {@link ArkUI_ShadowType}. The default value is <b>ARKUI_SHADOW_TYPE_COLOR</b>. .value[5].u32: shadow color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br>.value[6].u32: whether to fill the shadow. The value <b>1</b> means to fill the shadow, and <b>0</b> means the opposite.

**Since**: 12

### NODE_TRANSFORM_CENTER

```c
NODE_TRANSFORM_CENTER
```

**Description**

Defines the transform center attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0]?.f32: X coordinate of the center point, in vp.<br>.value[1]?.f32: Y coordinate of the center point, in vp.<br>.value[2]?.f32: Z coordinate of the center point, in vp.<br>.value[3]?.f32 : X coordinate of the center point, expressed in a number that represents a percentage.<br>For example, 0.2 indicates 20%. This attribute overwrites value[0].f32. The default value is <b>0.5f</b>. <br>.value[4]?.f32 : Y coordinate of the center point, expressed in a number that represents a percentage.<br>For example, 0.2 indicates 20%. This attribute overwrites value[1].f32. The default value is <b>0.5f</b>. <br>.value[5]?.f32 : Z coordinate of the center point, expressed in a number that represents a percentage.<br>For example, 0.2 indicates 20%. This attribute overwrites value[2].f32. The default value is <b>0.0f</b>. <br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].f32: X coordinate of the center point, in vp.<br>.value[1].f32: Y coordinate of the center point, in vp.<br>.value[2].f32: Z coordinate of the center point, in vp. Note: If the coordinate is expressed in a number that represents a percentage, the attribute obtaining API returns the calculated value in vp.

**Since**: 12

### NODE_SWEEP_GRADIENT

```c
NODE_SWEEP_GRADIENT
```

**Description**

Defines the sweep gradient effect. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0]?.f32: X coordinate of the sweep gradient center relative to the upper left corner of the component.<br>.value[1]?.f32: Y coordinate of the sweep gradient center relative to the upper left corner of the component.<br>.value[2]?.f32: start point of the sweep gradient. The default value is <b>0</b>. <br>.value[3]?.f32: end point of the sweep gradient. The default value is <b>0</b>. <br>.value[4]?.f32: rotation angle of the sweep gradient. The default value is <b>0</b>. <br>.value[5]?.i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated,<br>and <b>0</b> means the opposite.<br>.object: array of color stops, each of which consists of a color and its stop position. Invalid colors are<br>automatically skipped.<br>colors: colors of the color stops. <br>stops: stop positions of the color stops. <br>size: number of colors. <br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].f32: X coordinate of the sweep gradient center relative to the upper left corner of the component. <br>.value[1].f32: Y coordinate of the sweep gradient center relative to the upper left corner of the component. <br>.value[2].f32: start point of the sweep gradient. The default value is <b>0</b>. <br>.value[3].f32: end point of the sweep gradient. The default value is <b>0</b>. <br>.value[4].f32: rotation angle of the sweep gradient. The default value is <b>0</b>. <br>.value[5].i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated, and <b>0</b> means the opposite. .object: array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.

**Since**: 12

### NODE_RADIAL_GRADIENT

```c
NODE_RADIAL_GRADIENT
```

**Description**

Defines the radial gradient effect. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute: <br>.value[0]?.f32: X coordinate of the radial gradient center relative to the upper left corner of the component. <br>.value[1]?.f32: Y coordinate of the radial gradient center relative to the upper left corner of the component. <br>.value[2]?.f32: radius of the radial gradient. The default value is <b>0</b>. <br>.value[3]?.i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated,<br>and <b>0</b> means the opposite. <br>.object: array of color stops, each of which consists of a color and its stop position. Invalid colors are<br>automatically skipped. <br>colors: colors of the color stops. <br>stops: stop positions of the color stops. <br>size: number of colors. <br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].f32: X coordinate of the radial gradient center relative to the upper left corner of the component. <br>.value[1].f32: Y coordinate of the radial gradient center relative to the upper left corner of the component. <br>.value[2].f32: radius of the radial gradient. The default value is <b>0</b>. <br>.value[3].i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated, and <b>0</b> means the opposite. .object: array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.

**Since**: 12

### NODE_MASK

```c
NODE_MASK
```

**Description**

Adds a mask of the specified shape to the component. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute, which supports five types of<br>shapes:<br>1. Rectangle:<br>.value[0].u32 fill color, in 0xARGB format. <br>.value[1].u32: stroke color, in 0xARGB format. <br>.value[2].f32: stroke width, in vp. <br>.value[3].i32: mask type. The parameter type is {@link ArkUI_MaskType}.<br>The value is <b>ARKUI_MASK_TYPE_RECTANGLE</b> for the rectangle shape.<br>.value[4].f32: width of the rectangle.<br>.value[5].f32: height of the rectangle.<br>.value[6].f32: width of the rounded corner of the rectangle.<br>.value[7].f32: height of the rounded corner of the rectangle.<br>.value[8]?.f32: radius of the top left corner of the rectangular shape.<br>.value[9]?.f32: radius of the bottom left corner of the rectangular shape.<br>.value[10]?.f32: radius of the top right corner of the rectangular shape.<br>.value[11]?.f32: radius of the bottom right corner of the rectangular shape.<br>2. Circle:<br>.value[0].u32 fill color, in 0xARGB format. <br>.value[1].u32: stroke color, in 0xARGB format. <br>.value[2].f32: stroke width, in vp. <br>.value[3].i32: mask type. The parameter type is {@link ArkUI_MaskType}.<br>The value is <b>ARKUI_MASK_TYPE_CIRCLE</b> for the circle shape.<br>.value[4].f32: width of the circle.<br>.value[5].f32: height of the circle.<br>3. Ellipse:<br>.value[0].u32 fill color, in 0xARGB format. <br>.value[1].u32: stroke color, in 0xARGB format. <br>.value[2].f32: stroke width, in vp. <br>.value[3].i32: mask type. The parameter type is {@link ArkUI_MaskType}.<br>The value is <b>ARKUI_MASK_TYPE_ELLIPSE</b> for the ellipse shape.<br>.value[4].f32: width of the ellipse.<br>.value[5].f32: height of the ellipse.<br>4. Path:<br>.value[0].u32 fill color, in 0xARGB format. <br>.value[1].u32: stroke color, in 0xARGB format. <br>.value[2].f32: stroke width, in vp. <br>.value[3].i32: mask type. The parameter type is {@link ArkUI_MaskType}.<br>The value is <b>ARKUI_MASK_TYPE_PATH</b> for the path shape.<br>.value[4].f32: width of the path.<br>.value[5].f32: height of the path.<br>.string: command for drawing the path.<br>5. Progress:<br>.value[0].i32: mask type. The parameter type is {@link ArkUI_MaskType}.<br>The value is <b>ARKUI_MASK_TYPE_PROGRESS</b> for the progress shape.<br>.value[1].f32: current value of the progress indicator.<br>.value[2].f32: maximum value of the progress indicator.<br>.value[3].u32: color of the progress indicator, in 0xARGB format.<br><br>Format of the return value {@link ArkUI_AttributeItem}, which supports five types of shapes: 1. Rectangle: .value[0].u32 fill color, in 0xARGB format. <br>.value[1].u32: stroke color, in 0xARGB format. <br>.value[2].f32: stroke width, in vp. <br>.value[3].i32: mask type.<br>.value[4].f32: width of the rectangle.<br>.value[5].f32: height of the rectangle.<br>.value[6].f32: width of the rounded corner of the rectangle.<br>.value[7].f32: height of the rounded corner of the rectangle.<br>.value[8].f32: radius of the top left corner of the rectangular shape.<br>.value[9].f32: radius of the bottom left corner of the rectangular shape.<br>.value[10].f32: radius of the top right corner of the rectangular shape.<br>.value[11].f32: radius of the bottom right corner of the rectangular shape.<br>2. Circle:<br>.value[0].u32 fill color, in 0xARGB format. <br>.value[1].u32: stroke color, in 0xARGB format. <br>.value[2].f32: stroke width, in vp. <br>.value[3].i32: mask type.<br>.value[4].f32: width of the circle.<br>.value[5].f32: height of the circle.<br>3. Ellipse:<br>.value[0].u32 fill color, in 0xARGB format. <br>.value[1].u32: stroke color, in 0xARGB format. <br>.value[2].f32: stroke width, in vp. <br>.value[3].i32: mask type.<br>.value[4].f32: width of the ellipse.<br>.value[5].f32: height of the ellipse.<br>4. Path:<br>.value[0].u32 fill color, in 0xARGB format. <br>.value[1].u32: stroke color, in 0xARGB format. <br>.value[2].f32: stroke width, in vp. <br>.value[3].i32: mask type.<br>.value[4].f32: width of the path.<br>.value[5].f32: height of the path.<br>.string: command for drawing the path.<br>5. Progress:<br>.value[0].i32: mask type.<br>.value[1].f32: current value of the progress indicator.<br>.value[2].f32: maximum value of the progress indicator.<br>.value[3].u32: color of the progress indicator.

**Since**: 12

### NODE_BLEND_MODE

```c
NODE_BLEND_MODE
```

**Description**

Blends the component's background with the content of the component's child node. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].i32: blend mode. The parameter type is {@link ArkUI_BlendMode}. The default value is<br><b>ARKUI_BLEND_MODE_NONE</b>. <br>.value[1].?i32: how the specified blend mode is applied. The parameter type is {@link ArkUI_BlendApplyType}.<br>The default value is <b>BLEND_APPLY_TYPE_FAST</b>. <br><br>Format of the return value {@link ArkUI_AttributeItem}:<br>.value[0].i32: blend mode. The parameter type is {@link ArkUI_BlendMode}. The default value is<br><b>ARKUI_BLEND_MODE_NONE</b>. <br>.value[1].i32: how the specified blend mode is applied. The parameter type is {@link ArkUI_BlendApplyType}. The default value is <b>BLEND_APPLY_TYPE_FAST</b>.

**Since**: 12

### NODE_GRAY_SCALE

```c
NODE_GRAY_SCALE
```

**Description**

Defines the grayscale effect. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].f32: grayscale conversion ratio. The value ranges from 0 to 1.<br>For example, 0.5 indicates a 50% grayscale conversion ratio. <br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].f32: grayscale conversion ratio. The value ranges from 0 to 1.

**Since**: 12

### NODE_INVERT

```c
NODE_INVERT
```

**Description**

Inverts the image. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].f32: image inversion ratio. The value ranges from 0 to 1.<br>For example, 0.5 indicates a 50% image inversion ratio.<br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].f32: image inversion ratio. The value ranges from 0 to 1.

**Since**: 12

### NODE_SEPIA

```c
NODE_SEPIA
```

**Description**

Defines the sepia conversion ratio. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].f32: sepia conversion ratio. The value ranges from 0 to 1.<br>For example, 0.5 indicates that a 50% sepia conversion ratio.<br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].f32: sepia conversion ratio. The value ranges from 0 to 1.

**Since**: 12

### NODE_CONTRAST

```c
NODE_CONTRAST
```

**Description**

Defines the contrast attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].f32: contrast. If the value is <b>1</b>, the source image is displayed.<br>A larger value indicates a higher contrast. Value range: [0, 10).<br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].f32: contrast. Value range: [0, 10).

**Since**: 12

### NODE_FOREGROUND_COLOR

```c
NODE_FOREGROUND_COLOR
```

**Description**

Defines the foreground color attribute, which can be set, reset, and obtained as required through APIs.<br> There are two formats of {@link ArkUI_AttributeItem} for setting the attribute value:<br>1: .value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br>2: .value[0].i32: color enum {@link ArkUI_ColorStrategy}.<br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].u32: color value, in 0xARGB format.

**Since**: 12

### NODE_OUTLINE_WIDTH

```c
NODE_OUTLINE_WIDTH
```

**Description**

Sets the thickness of an element's outline.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].f32: thickness of the left outline. <br>.value[1].f32: thickness of the top outline. <br>.value[2].f32: thickness of the right outline. <br>.value[3].f32: thickness of the bottom outline. <br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].f32: thickness of the left outline. <br>.value[1].f32: thickness of the top outline. <br>.value[2].f32: thickness of the right outline. <br>.value[3].f32: thickness of the bottom outline.

**Since**: 12

### NODE_RENDER_FIT

```c
NODE_RENDER_FIT
```

**Description**

Set the component content filling method in the process of width and height animation, support property setting, property reset, property acquisition interface.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].i32 Content filling mode {@link ArkUI_RenderFit}.<br><br>Format of the return value {@link ArkUI_AttributeItem}:<br>.value[0].i32 Content filling mode {@link ArkUI_RenderFit}.

**Since**: 12

### NODE_OUTLINE_COLOR

```c
NODE_OUTLINE_COLOR
```

**Description**

External stroke color properties, support property setting, property reset and property acquisition interface.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>1: .value[0].u32: Set the border color of the four sides uniformly, using 0xargb, such as 0xFFFF11FF. <br>2: .value[0].u32: Set the top border color, represented by 0xargb, such as 0xFFFF11FF. <br>.value[1].u32: Set the right border color, represented by 0xargb, such as 0xFFFF11FF. <br>.value[2].u32: Set the lower side box color, denoted by 0xargb, such as 0xFFFF11FF. <br>.value[3].u32: Set the left border color, denoted by 0xargb, such as 0xFFFF11FF. <br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].u32: Set the top border color, represented by 0xargb, such as 0xFFFF11FF. <br>.value[1].u32: Set the right border color, represented by 0xargb, such as 0xFFFF11FF. <br>.value[2].u32: Set the lower side box color, denoted by 0xargb, such as 0xFFFF11FF. <br>.value[3].u32: Set the left border color, denoted by 0xargb, such as 0xFFFF11FF.

**Since**: 12

### NODE_RENDER_GROUP

```c
NODE_RENDER_GROUP
```

**Description**

Set whether the current component and child component are rendered off the screen first and then fused with the parent control, supporting property setting, property reset and property acquisition.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].i32: The parameter type is 1 or 0.<br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].i32: The parameter type is 1 or 0.

**Since**: 12

### NODE_COLOR_BLEND

```c
NODE_COLOR_BLEND
```

**Description**

Add color overlay effect to components, support property setting, property reset and property acquisition interface.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].u32: The color of the overlay is represented by 0xargb, such as 0xFFFF11FF. <br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].u32: The color of the overlay is represented by 0xargb, such as 0xFFFF11FF.

**Since**: 12

### NODE_FOREGROUND_BLUR_STYLE

```c
NODE_FOREGROUND_BLUR_STYLE
```

**Description**

Provide content ambiguity capability for the current component, support property setting, property reset, property acquisition interface.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].i32 Represents the content blurring style, and uses the {@link ArkUI_BlurStyle} enumeration value.<br>.value[1]?.i32 Represents the dark and light mode used by the content blur effect,<br>with the {@link ArkUI_ColorMode} enumeration value.<br>.value[2]?.i32 The color extraction mode used to represent the content blur effect takes<br>the {@link ArkUI_AdaptiveColor} enumeration value.<br>.value[3]?.f32: blur degree. The value range is [0.0, 1.0]. <br>.value[4]?.f32 It is a gray-level fuzzy parameter. The value range is [0,127].<br>.value[5]?.f32 It is a gray-level fuzzy parameter. The value range is [0,127].<br><br>Format of the return value {@link ArkUI_AttributeItem}:<br>.value[0].i32 Represents the content blurring style, and uses the {@link ArkUI_BlurStyle} enumeration value.<br>.value[1].i32 Represents the dark and light mode used by the content blur effect,<br>with the {@link ArkUI_ColorMode} enumeration value.<br>.value[2].i32 The color extraction mode used to represent the content blur effect takes<br>the {@link ArkUI_AdaptiveColor} enumeration value. .value[3].f32: blur degree. The value range is [0.0, 1.0]. <br>.value[4].f32 It is a gray-level fuzzy parameter. The value range is [0,127].<br>.value[5].f32 It is a gray-level fuzzy parameter. The value range is [0,127].

**Since**: 12

### NODE_BACKDROP_BLUR

```c
NODE_BACKDROP_BLUR = 99
```

**Description**

Defines the backdrop blur attribute, which can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].f32：backdrop blur radius, in px. The value range is [0, +∞).<br>.value[1]?.f32：grayscale blur settings that control the brightness of the black color.<br>The value range is [0, 127].<br>.value[2]?.f32：grayscale blur settings that control the darkness of the white color.<br>The value range is [0, 127].<br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].f32：backdrop blur radius, in px. The value range is [0, +∞).<br>.value[1].f32：grayscale blur settings that control the brightness of the black color.<br>The value range is [0, 127].<br>.value[2].f32：grayscale blur settings that control the darkness of the white color.<br>The value range is [0, 127].

**Since**: 15

### NODE_TRANSLATE_WITH_PERCENT

```c
NODE_TRANSLATE_WITH_PERCENT = 103
```

**Description**

Defines the translate attribute, which supports for percentile translation input, and can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].f32: distance to translate along the x-axis. The default unit is percentage.<br>The unit is vp only if value[3] exists and value[3] is 0. The default value of value[0] is <b>0</b>.<br>.value[1].f32: distance to translate along the y-axis. The default unit is percentage.<br>The unit is vp only if value[4] exists and value[4] is 0. The default value of value[1] is <b>0</b>.<br>.value[2].f32: distance to translate along the z-axis, in vp. The default value is <b>0</b>.<br>.value[3]?.i32: Whether the translation distance along the x-axis is specified as a percentage.<br> The value can be 0 or 1. When the value is 1, it is specified as a percentage.<br> For example, value[0].f32=0.1 and value[3].i32=1 indicates a 10% shift in the x direction.<br> The default value is <b>1</b>.<br>.value[4]?.i32: Whether the translation distance along the y-axis is specified as a percentage.<br> The value can be 0 or 1. When the value is 1, it is specified as a percentage.<br> For example, value[1].f32=0.1 and value[4].i32=1 indicates a 10% shift in the y direction.<br> The default value is <b>1</b>.<br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].f32: distance to translate along the x-axis. The unit depends on value[3].<br>.value[1].f32: distance to translate along the y-axis. The unit depends on value[4].<br>.value[2].f32: distance to translate along the z-axis. The unit is vp.<br>.value[3].i32: Whether the unit of the X-axis translation distance is in percentage. When value[3].i32 is 0,<br> the unit of the X-axis translation distance is vp; when value[3].i32 is 1, the unit of the X-axis translation<br> distance is percentage;<br>.value[4].i32: Whether the unit of the Y-axis translation distance is in percentage. When value[4].i32 is 0,<br> the unit of the Y-axis translation distance is vp; when value[4].i32 is 1, the unit of the Y-axis translation distance is percentage;

**Since**: 20

### NODE_ROTATE_ANGLE

```c
NODE_ROTATE_ANGLE = 104
```

**Description**

Sets component rotation with multi-axis angle control. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.value[0].f32: x-axis rotation angle. The default value is <b>0</b>. <br>.value[1].f32: y-axis rotation angle. The default value is <b>0</b>. <br>.value[2].f32: z-axis rotation angle. The default value is <b>0</b>. <br>.value[3].f32: perspective distance from the viewpoint to the z=0 plane, in px. The default value is <b>0</b>. <br><br>Format of the return value {@link ArkUI_AttributeItem}: .value[0].f32: x-axis rotation angle. The default value is <b>0</b>.<br>.value[1].f32: y-axis rotation angle. The default value is <b>0</b>. <br>.value[2].f32: z-axis rotation angle. The default value is <b>0</b>. <br>.value[3].f32: perspective distance from the viewpoint to the z=0 plane, in px. The default value is <b>0</b>.

**Since**: 20

### NODE_SYSTEM_MATERIAL

```c
NODE_SYSTEM_MATERIAL = 127
```

**Description**

Defines the system material attribute, which can be set, reset, and obtained as required through APIs. Only devices that support systemMaterial can use this attribute. Otherwise, when setting this attribute, the error code {@link ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED} will be returned.<br>Whether a device supports materials can be determined by calling<br>{@link OH_ArkUI_NativeModule_GetSystemMaterialSupported}.<br>The material effect behaves differently on devices with different level of computing powers.<br>The level is defined by {@link ArkUI_MaterialLevel}, which can be obtained by<br>{@link OH_ArkUI_NativeModule_GetGlobalMaterialLevel}.<br>On devices with the computing power level of ARKUI_MATERIAL_LEVEL_SMOOTH, it affects attributes such as the<br>backgroundColor, borderWidth, borderColor, shadow.<br>On devices with the computing power levels of ARKUI_MATERIAL_LEVEL_EXQUISITE or ARKUI_MATERIAL_LEVEL_GENTLE,<br>it affects shadow attribute and adds a filter effect at the system material layer, which can produce an effect<br>similar to glass.<br>Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.object: system material object. The parameter type is {@link ArkUI_ImmersiveMaterialHandle}.<br><br>Format of the return value {@link ArkUI_AttributeItem}:<br>.object: system material object. The parameter type is {@link ArkUI_ImmersiveMaterialHandle}.<br>The ArkUI_ImmersiveMaterialHandle object of the return value is a pointer to static member, so do not release<br>the return object by calling {@link OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy}.

**Since**: 26.0.0


