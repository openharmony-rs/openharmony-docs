# Slider

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_SLIDER_BLOCK_COLOR

```c
NODE_SLIDER_BLOCK_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SLIDER
```

**Description**

Defines the color of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].u32: color of the slider, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].u32: color of the slider, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> </ul>

**Since**: 12

### NODE_SLIDER_TRACK_COLOR

```c
NODE_SLIDER_TRACK_COLOR
```

**Description**

Defines the background color of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].u32: background color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].u32: background color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> </ul>

**Since**: 12

### NODE_SLIDER_SELECTED_COLOR

```c
NODE_SLIDER_SELECTED_COLOR
```

**Description**

Defines the color of the selected part of the slider track. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].u32: color of the selected part of the slider track, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].u32: color of the selected part of the slider track, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> </ul>

**Since**: 12

### NODE_SLIDER_SHOW_STEPS

```c
NODE_SLIDER_SHOW_STEPS
```

**Description**

Sets whether to display the stepping value. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: whether to display the stepping value. The value <b>1</b> means to display the stepping value, and <b>0</b> (default value) means the opposite.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: whether to display the stepping value. The value <b>1</b> means to display the stepping value, and <b>0</b> (default value) means the opposite.</li> </ul>

**Since**: 12

### NODE_SLIDER_BLOCK_STYLE

```c
NODE_SLIDER_BLOCK_STYLE
```

**Description**

Defines the slider shape, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: shape. The parameter type is [ArkUI_SliderBlockStyle](capi-slider-h.md#arkui_sliderblockstyle).</li> <li>.string?: depending on the shape. Optional.</li> <ul> <li>ARKUI_SLIDER_BLOCK_STYLE_IMAGE: image resource of the slider. Example: /pages/common/icon.png.</li> <li>ARKUI_SLIDER_BLOCK_STYLE_SHAPE: custom shape of the slider.</li> </ul> There are five types: **1. Rectangle:** <ul> <li>.value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-visual-h.md#arkui_shapetype). The value is <b>ARKUI_SHAPE_TYPE_RECTANGLE</b> for the rectangle shape.</li> <li>.value[2].f32: width of the rectangle.</li> <li>.value[3].f32: height of the rectangle.</li> <li>.value[4].f32: width of the rounded corner of the rectangle.</li> <li>.value[5].f32: height of the rounded corner of the rectangle.</li> </ul> **2. Circle:** <ul> <li>.value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-visual-h.md#arkui_shapetype). The value is <b>ARKUI_SHAPE_TYPE_CIRCLE</b> for the circle shape.</li> <li>.value[2].f32: width of the circle.</li> <li>.value[3].f32: height of the circle.</li> </ul> **3.Ellipse:** <ul> <li>.value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-visual-h.md#arkui_shapetype). The value is <b>ARKUI_SHAPE_TYPE_ELLIPSE</b> for the ellipse shape.</li> <li>.value[2].f32: width of the ellipse.</li> <li>.value[3].f32: height of the ellipse.</li> </ul> **4. Path:** <ul> <li>.value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-visual-h.md#arkui_shapetype). The value is <b>ARKUI_SHAPE_TYPE_PATH</b> for the path shape.</li> <li>.value[2].f32: width of the path.</li> <li>.value[3].f32: height of the path.</li> <li>.string: command for drawing the path.</li> <ul> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: shape. The parameter type is [ArkUI_SliderBlockStyle](capi-slider-h.md#arkui_sliderblockstyle).</li> <li>.string?: depending on the shape. Optional.</li> <ul> <li>ARKUI_SLIDER_BLOCK_STYLE_IMAGE: image resource of the slider. Example: /pages/common/icon.png.</li> <li>ARKUI_SLIDER_BLOCK_STYLE_SHAPE: custom shape of the slider.</li> </ul> There are five types: **1. Rectangle:** <ul> <li>.value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-visual-h.md#arkui_shapetype). The value is <b>ARKUI_SHAPE_TYPE_RECTANGLE</b> for the rectangle shape.</li> <li>.value[2].f32: width of the rectangle.</li> <li>.value[3].f32: height of the rectangle.</li> <li>.value[4].f32: width of the rounded corner of the rectangle.</li> <li>.value[5].f32: height of the rounded corner of the rectangle.</li> </ul> **2. Circle:** <ul> <li>.value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-visual-h.md#arkui_shapetype). The value is <b>ARKUI_SHAPE_TYPE_CIRCLE</b> for the circle shape.</li> <li>.value[2].f32: width of the circle.</li> <li>.value[3].f32: height of the circle.</li> </ul> **3.Ellipse:** <ul> <li>.value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-visual-h.md#arkui_shapetype). The value is <b>ARKUI_SHAPE_TYPE_ELLIPSE</b> for the ellipse shape.</li> <li>.value[2].f32: width of the ellipse.</li> <li>.value[3].f32: height of the ellipse.</li> </ul> **4. Path:** <ul> <li>.value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-visual-h.md#arkui_shapetype). The value is <b>ARKUI_SHAPE_TYPE_PATH</b> for the path shape.</li> <li>.value[2].f32: width of the path.</li> <li>.value[3].f32: height of the path.</li> <li>.string: command for drawing the path.</li> </ul> </ul>

**Since**: 12

### NODE_SLIDER_VALUE

```c
NODE_SLIDER_VALUE
```

**Description**

Defines the current value of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].f32: current value.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].f32: current value.</li> </ul>

**Since**: 12

### NODE_SLIDER_MIN_VALUE

```c
NODE_SLIDER_MIN_VALUE
```

**Description**

Defines the minimum value of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].f32: minimum value.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].f32: minimum value.</li> </ul>

**Since**: 12

### NODE_SLIDER_MAX_VALUE

```c
NODE_SLIDER_MAX_VALUE
```

**Description**

Defines the maximum value of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].f32: maximum value.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].f32: maximum value.</li> </ul>

**Since**: 12

### NODE_SLIDER_STEP

```c
NODE_SLIDER_STEP
```

**Description**

Defines the step of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].f32: step. The value range is [0.01, 100].</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].f32: step. The value range is [0.01, 100].</li> </ul>

**Since**: 12

### NODE_SLIDER_DIRECTION

```c
NODE_SLIDER_DIRECTION
```

**Description**

Defines whether the slider moves horizontally or vertically. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: whether the slider moves horizontally or vertically. The parameter type is [ArkUI_SliderDirection](capi-slider-h.md#arkui_sliderdirection).</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: whether the slider moves horizontally or vertically.</li> </ul>

**Since**: 12

### NODE_SLIDER_REVERSE

```c
NODE_SLIDER_REVERSE
```

**Description**

Defines whether the slider values are reversed. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: whether the slider values are reversed. The value <b>1</b> means that the slider values are reversed, and <b>0</b> means the opposite.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: whether the slider values are reversed. The value <b>1</b> means that the slider values are reversed, and <b>0</b> means the opposite.</li> </ul>

**Since**: 12

### NODE_SLIDER_STYLE

```c
NODE_SLIDER_STYLE
```

**Description**

Defines the style of the slider thumb and track. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: style of the slider thumb and track. The parameter type is [ArkUI_SliderStyle](capi-slider-h.md#arkui_sliderstyle).</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: style of the slider thumb and track. The parameter type is [ArkUI_SliderStyle](capi-slider-h.md#arkui_sliderstyle).</li> </ul>

**Since**: 12

### NODE_SLIDER_TRACK_THICKNESS

```c
NODE_SLIDER_TRACK_THICKNESS
```

**Description**

Sets the track thickness of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].f32: track thickness of the slider, in vp. The default value is 4.0 vp when <b>NODE_SLIDER_STYLE</b> is set to <b>ARKUI_SLIDER_STYLE_OUT_SET</b> and 20.0 vp when <b>NODE_SLIDER_STYLE</b> is set to <b>ARKUI_SLIDER_STYLE_IN_SET</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].f32: track thickness of the slider, in vp.</li> </ul>

**Since**: 12

### NODE_SLIDER_ENABLE_HAPTIC_FEEDBACK

```c
NODE_SLIDER_ENABLE_HAPTIC_FEEDBACK = 17013
```

**Description**

Defines whether haptic feedback. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: whether to feedback. The value <b>true</b> means to feedback, and <b>false</b> means the opposite.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>value[0].i32: whether to feedback. When enabling haptic feedback, you need to add "ohos.permission.VIBRATE" in the requestPermissions field of the module.json5 file to enable vibration permission.</li> </ul>

**Since**: 18

### NODE_SLIDER_PREFIX

```c
NODE_SLIDER_PREFIX
```

**Description**

Sets a custom component on the leading side of the Slider component.<br> **Attribute setting method [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter format:** <ul> <li>.object: Parameter type [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).</li> </ul> The prefix component will be placed at the start position of the Slider， typically on the left side in LTR layouts. *

**Since**: 20

### NODE_SLIDER_SUFFIX

```c
NODE_SLIDER_SUFFIX
```

**Description**

Sets a custom component on the trailing side of the Slider component.<br> **Attribute setting method {@link link ArkUI_AttributeItem} parameter format:** <ul> <li>.object: Parameter type [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).</li> </ul> The suffix component will be placed at the end position of the Slider, typically on the right side in LTR layouts. *

**Since**: 20

### NODE_SLIDER_BLOCK_LINEAR_GRADIENT_COLOR

```c
NODE_SLIDER_BLOCK_LINEAR_GRADIENT_COLOR
```

**Description**

Defines the color of the slider block. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.</li> <li>colors: colors of the color stops.</li> <li>stops: stop positions of the color stops.</li> <li>size: number of colors.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.</li> <li>colors: colors of the color stops.</li> <li>stops: stop positions of the color stops.</li> <li>size: number of colors.</li> </ul>

**Since**: 21

### NODE_SLIDER_TRACK_LINEAR_GRADIENT_COLOR

```c
NODE_SLIDER_TRACK_LINEAR_GRADIENT_COLOR
```

**Description**

Defines the background color of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.</li> <li>colors: colors of the color stops.</li> <li>stops: stop positions of the color stops.</li> <li>size: number of colors.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.</li> <li>colors: colors of the color stops.</li> <li>stops: stop positions of the color stops.</li> <li>size: number of colors.</li> </ul>

**Since**: 21

### NODE_SLIDER_SELECTED_LINEAR_GRADIENT_COLOR

```c
NODE_SLIDER_SELECTED_LINEAR_GRADIENT_COLOR
```

**Description**

Defines the color of the selected part of the slider track. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.</li> <li>colors: colors of the color stops.</li> <li>stops: stop positions of the color stops.</li> <li>size: number of colors.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.</li> <li>colors: colors of the color stops.</li> <li>stops: stop positions of the color stops.</li> <li>size: number of colors.</li> </ul>

**Since**: 21


