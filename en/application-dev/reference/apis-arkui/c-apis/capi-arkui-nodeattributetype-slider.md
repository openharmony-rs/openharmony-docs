# Slider

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

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

Background color of the slider track. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].u32: Background color, in 0xARGB format, for example, **0xFF1122FF**.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].u32: Background color, in 0xARGB format, for example, **0xFF1122FF**.</li> </ul>

**Since**: 12

### NODE_SLIDER_SELECTED_COLOR

```c
NODE_SLIDER_SELECTED_COLOR
```

**Description**

Color of the selected part of the slider track. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].u32: Color of the selected part of the slider track, in 0xARGB format, for example, **0xFF1122FF**.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].u32: Color of the selected part of the slider track, in 0xARGB format, for example, **0xFF1122FF**.</li> </ul>

**Since**: 12

### NODE_SLIDER_SHOW_STEPS

```c
NODE_SLIDER_SHOW_STEPS
```

**Description**

Whether to display the step scale value. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: Whether to display the step scale value. The value **1** means to display the step scale value, and **0** means the opposite. The default value is **0**.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: Whether the step scale value is displayed. The value **1** means that the step scale value is displayed, and **0** means the opposite. The default value is **0**.</li> </ul>

**Since**: 12

### NODE_SLIDER_BLOCK_STYLE

```c
NODE_SLIDER_BLOCK_STYLE
```

**Description**

Shape of the slider thumb. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: Shape. The parameter type is [ArkUI_SliderBlockStyle](capi-slider-h.md#arkui_sliderblockstyle).</li> <li>.string?: This parameter is optional, and its value depends on the shape.<br>**ARKUI_SLIDER_BLOCK_STYLE_IMAGE**: image resource of the slider thumb. Example: /pages/common/icon.png.<br>**ARKUI_SLIDER_BLOCK_STYLE_SHAPE**: custom shape of the slider thumb. In this case, the width and height values in the defined shape do not represent the actual size of the thumb; they are scaled proportionally to ensure the thumb displays correctly.<br>There are four types. For the path type, **.string** indicates the command string for drawing the path.</li> <li>.value[1].i32: Shape type. The parameter type is [ArkUI_ShapeType](capi-native-type-visual-h.md#arkui_shapetype). The value is **ARKUI_SHAPE_TYPE_RECTANGLE** for the rectangle type, **ARKUI_SHAPE_TYPE_CIRCLE** for the circle type, **ARKUI_SHAPE_TYPE_ELLIPSE** for the ellipse type, and **ARKUI_SHAPE_TYPE_PATH** for the path type.</li> <li>.value[2].f32: Width of the rectangle, circle, ellipse, or path type.</li> <li>.value[3].f32: Height of the rectangle, circle, ellipse, or path type.</li> <li>.value[4].f32: Width of the rounded corner of the rectangle type.</li> <li>.value[5].f32: Height of the rounded corner of the rectangle type.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: Shape. The parameter type is [ArkUI_SliderBlockStyle](capi-slider-h.md#arkui_sliderblockstyle).</li> <li>.string?: This parameter is optional, and its value depends on the shape.<br>**ARKUI_SLIDER_BLOCK_STYLE_IMAGE**: image resource of the slider thumb. Example: /pages/common/icon.png.<br>**ARKUI_SLIDER_BLOCK_STYLE_SHAPE**: custom shape of the slider thumb.<br>There are four types. For the path type, **.string** indicates the command string for drawing the path.</li> <li>.value[1].i32: Shape type. The parameter type is [ArkUI_ShapeType](capi-native-type-visual-h.md#arkui_shapetype). The value is **ARKUI_SHAPE_TYPE_RECTANGLE** for the rectangle type, **ARKUI_SHAPE_TYPE_CIRCLE** for the circle type, **ARKUI_SHAPE_TYPE_ELLIPSE** for the ellipse type, and **ARKUI_SHAPE_TYPE_PATH** for the path type.</li> <li>.value[2].f32: Width of the rectangle, circle, ellipse, or path type.</li> <li>.value[3].f32: Height of the rectangle, circle, ellipse, or path type.</li> <li>.value[4].f32: Width of the rounded corner of the rectangle type.</li> <li>.value[5].f32: Height of the rounded corner of the rectangle type.</li> </ul>

**Since**: 12

### NODE_SLIDER_VALUE

```c
NODE_SLIDER_VALUE
```

**Description**

Current value of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].f32: Current value.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].f32: Current value.</li> </ul>

**Since**: 12

### NODE_SLIDER_MIN_VALUE

```c
NODE_SLIDER_MIN_VALUE
```

**Description**

Minimum value of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].f32: Minimum value.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].f32: Minimum value.</li> </ul>

**Since**: 12

### NODE_SLIDER_MAX_VALUE

```c
NODE_SLIDER_MAX_VALUE
```

**Description**

Maximum value of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].f32: Maximum value.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].f32: Maximum value.</li> </ul>

**Since**: 12

### NODE_SLIDER_STEP

```c
NODE_SLIDER_STEP
```

**Description**

Step of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].f32: Step. The value range is [0.01, 100].</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].f32: Step. The value range is [0.01, 100].</li> </ul>

**Since**: 12

### NODE_SLIDER_DIRECTION

```c
NODE_SLIDER_DIRECTION
```

**Description**

Slider direction. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: Slider direction. The parameter type is [ArkUI_SliderDirection](capi-slider-h.md#arkui_sliderdirection).</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: Slider direction. The parameter type is [ArkUI_SliderDirection](capi-slider-h.md#arkui_sliderdirection).</li> </ul>

**Since**: 12

### NODE_SLIDER_REVERSE

```c
NODE_SLIDER_REVERSE
```

**Description**

Whether the slider values are reversed. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: Whether the slider values are reversed. The value **1** means that the slider values are reversed, and **0** means the opposite.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: Whether the slider values are reversed. The value **1** means that the slider values are reversed, and **0** means the opposite.</li> </ul>

**Since**: 12

### NODE_SLIDER_STYLE

```c
NODE_SLIDER_STYLE
```

**Description**

Style of the slider thumb and track. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: Slider style. The parameter type is [ArkUI_SliderStyle](capi-slider-h.md#arkui_sliderstyle).</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: Slider style. The parameter type is [ArkUI_SliderStyle](capi-slider-h.md#arkui_sliderstyle).</li> </ul>

**Since**: 12

### NODE_SLIDER_TRACK_THICKNESS

```c
NODE_SLIDER_TRACK_THICKNESS
```

**Description**

Track thickness of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].f32: Track thickness of the slider, in vp. The default value is 4.0 vp when **NODE_SLIDER_STYLE**<br>is set to **ARKUI_SLIDER_STYLE_OUT_SET** and 20.0 vp when **NODE_SLIDER_STYLE** is set to **ARKUI_SLIDER_STYLE_IN_SET**.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].f32: Track thickness of the slider, in vp.</li> </ul>

**Since**: 12

### NODE_SLIDER_ENABLE_HAPTIC_FEEDBACK

```c
NODE_SLIDER_ENABLE_HAPTIC_FEEDBACK = 17013
```

**Description**

Whether to enable haptic feedback. This attribute can be set, reset, and obtained as required through APIs. To enable haptic feedback, you must add **"name": "ohos.permission.VIBRATE"** under **requestPermissions** in the **module.json5** file of the project.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: Whether to enable haptic feedback. **true** to enable; **false** otherwise. The default value is **true**.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: Whether haptic feedback is enabled.</li> </ul>

**Since**: 18

### NODE_SLIDER_PREFIX

```c
NODE_SLIDER_PREFIX
```

**Description**

Custom prefix component for the start edge of the slider.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.object: The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md). The prefix component is typically placed on the left in LTR layouts.</li> </ul>

**Since**: 20

### NODE_SLIDER_SUFFIX

```c
NODE_SLIDER_SUFFIX
```

**Description**

Custom suffix component for the end edge of the slider.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.object: The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md). The suffix component is typically placed on the right in LTR layouts.</li> </ul>

**Since**: 20

### NODE_SLIDER_BLOCK_LINEAR_GRADIENT_COLOR

```c
NODE_SLIDER_BLOCK_LINEAR_GRADIENT_COLOR
```

**Description**

Linear gradient color of the slider thumb. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br>- **colors**: colors of the color stops.<br>- **stops**: stop positions of the color stops.<br>- **size**: number of colors.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br>- **colors**: colors of the color stops.<br>- **stops**: stop positions of the color stops.<br>- **size**: number of colors.</li> </ul>

**Since**: 21

### NODE_SLIDER_TRACK_LINEAR_GRADIENT_COLOR

```c
NODE_SLIDER_TRACK_LINEAR_GRADIENT_COLOR
```

**Description**

Linear gradient color of the slider track. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br>- **colors**: colors of the color stops.<br>- **stops**: stop positions of the color stops.<br>- **size**: number of colors.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br>- **colors**: colors of the color stops.<br>- **stops**: stop positions of the color stops.<br>- **size**: number of colors.</li> </ul>

**Since**: 21

### NODE_SLIDER_SELECTED_LINEAR_GRADIENT_COLOR

```c
NODE_SLIDER_SELECTED_LINEAR_GRADIENT_COLOR
```

**Description**

Linear gradient color of the selected part of the slider track. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br>- **colors**: colors of the color stops.<br>- **stops**: stop positions of the color stops.<br>- **size**: number of colors.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br>- **colors**: colors of the color stops.<br>- **stops**: stop positions of the color stops.<br>- **size**: number of colors.</li> </ul>

**Since**: 21


