# 滑动条

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_SLIDER_BLOCK_COLOR

```c
NODE_SLIDER_BLOCK_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SLIDER
```

**描述：**

Defines the color of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: color of the slider, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li><br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.value[0].u32: color of the slider, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> </ul>

**起始版本：** 12

### NODE_SLIDER_TRACK_COLOR

```c
NODE_SLIDER_TRACK_COLOR
```

**描述：**

Defines the background color of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: background color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.value[0].u32: background color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> </ul>

**起始版本：** 12

### NODE_SLIDER_SELECTED_COLOR

```c
NODE_SLIDER_SELECTED_COLOR
```

**描述：**

Defines the color of the selected part of the slider track. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: color of the selected part of the slider track, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.value[0].u32: color of the selected part of the slider track, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> </ul>

**起始版本：** 12

### NODE_SLIDER_SHOW_STEPS

```c
NODE_SLIDER_SHOW_STEPS
```

**描述：**

Sets whether to display the stepping value. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to display the stepping value. The value <b>1</b> means to display the stepping value,<br>and <b>0</b> (default value) means the opposite.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.value[0].i32: whether to display the stepping value. The value <b>1</b> means to display the stepping value, and <b>0</b> (default value) means the opposite.</li> </ul>

**起始版本：** 12

### NODE_SLIDER_BLOCK_STYLE

```c
NODE_SLIDER_BLOCK_STYLE
```

**描述：**

Defines the slider shape, which can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: shape. The parameter type is {@link ArkUI_SliderBlockStyle}.</li> <br><li>.string?: depending on the shape. Optional.</li> <br></ul><br>ARKUI_SLIDER_BLOCK_STYLE_IMAGE: image resource of the slider. Example: /pages/common/icon.png. <br>ARKUI_SLIDER_BLOCK_STYLE_SHAPE: custom shape of the slider. <br>There are five types:<br>1. Rectangle:<br>.value[1].i32: type of shape. The parameter type is {@link ArkUI_ShapeType}.<br>The value is <b>ARKUI_SHAPE_TYPE_RECTANGLE</b> for the rectangle shape.<br>.value[2].f32: width of the rectangle.<br>.value[3].f32: height of the rectangle.<br>.value[4].f32: width of the rounded corner of the rectangle.<br>.value[5].f32: height of the rounded corner of the rectangle.<br>2. Circle:<br>.value[1].i32: type of shape. The parameter type is {@link ArkUI_ShapeType}.<br>The value is <b>ARKUI_SHAPE_TYPE_CIRCLE</b> for the circle shape.<br>.value[2].f32: width of the circle.<br>.value[3].f32: height of the circle.<br>3.Ellipse:<br>.value[1].i32: type of shape. The parameter type is {@link ArkUI_ShapeType}.<br>The value is <b>ARKUI_SHAPE_TYPE_ELLIPSE</b> for the ellipse shape.<br>.value[2].f32: width of the ellipse.<br>.value[3].f32: height of the ellipse;<br>4. Path:<br>.value[1].i32: type of shape. The parameter type is {@link ArkUI_ShapeType}.<br>The value is <b>ARKUI_SHAPE_TYPE_PATH</b> for the path shape.<br>.value[2].f32: width of the path.<br>.value[3].f32: height of the path.<br>.string: command for drawing the path.<br><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: shape. The parameter type is {@link ArkUI_SliderBlockStyle}.</li> <br><li>.string?: depending on the shape. Optional.</li> <br></ul><br>ARKUI_SLIDER_BLOCK_STYLE_IMAGE: image resource of the slider. Example: /pages/common/icon.png. <br>ARKUI_SLIDER_BLOCK_STYLE_SHAPE: custom shape of the slider. <br>There are five types:<br>1. Rectangle:<br>.value[1].i32: type of shape. The parameter type is {@link ArkUI_ShapeType}.<br>The value is <b>ARKUI_SHAPE_TYPE_RECTANGLE</b> for the rectangle shape.<br>.value[2].f32: width of the rectangle.<br>.value[3].f32: height of the rectangle.<br>.value[4].f32: width of the rounded corner of the rectangle.<br>.value[5].f32: height of the rounded corner of the rectangle.<br>2. Circle:<br>.value[1].i32: type of shape. The parameter type is {@link ArkUI_ShapeType}.<br>The value is <b>ARKUI_SHAPE_TYPE_CIRCLE</b> for the circle shape.<br>.value[2].f32: width of the circle.<br>.value[3].f32: height of the circle.<br>3.Ellipse:<br>.value[1].i32: type of shape. The parameter type is {@link ArkUI_ShapeType}.<br>The value is <b>ARKUI_SHAPE_TYPE_ELLIPSE</b> for the ellipse shape.<br>.value[2].f32: width of the ellipse.<br>.value[3].f32: height of the ellipse;<br>4. Path:<br>.value[1].i32: type of shape. The parameter type is {@link ArkUI_ShapeType}. The value is <b>ARKUI_SHAPE_TYPE_PATH</b> for the path shape. .value[2].f32: width of the path.<br>.value[3].f32: height of the path. .string: command for drawing the path.

**起始版本：** 12

### NODE_SLIDER_VALUE

```c
NODE_SLIDER_VALUE
```

**描述：**

Defines the current value of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: current value.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.value[0].f32: current value.</li> </ul>

**起始版本：** 12

### NODE_SLIDER_MIN_VALUE

```c
NODE_SLIDER_MIN_VALUE
```

**描述：**

Defines the minimum value of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: minimum value.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.value[0].f32: minimum value.</li> </ul>

**起始版本：** 12

### NODE_SLIDER_MAX_VALUE

```c
NODE_SLIDER_MAX_VALUE
```

**描述：**

Defines the maximum value of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: maximum value.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.value[0].f32: maximum value.</li> </ul>

**起始版本：** 12

### NODE_SLIDER_STEP

```c
NODE_SLIDER_STEP
```

**描述：**

Defines the step of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: step. The value range is [0.01, 100].</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.value[0].f32: step. The value range is [0.01, 100].</li> </ul>

**起始版本：** 12

### NODE_SLIDER_DIRECTION

```c
NODE_SLIDER_DIRECTION
```

**描述：**

Defines whether the slider moves horizontally or vertically. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether the slider moves horizontally or vertically.<br>The parameter type is {@link ArkUI_SliderDirection}.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.value[0].i32: whether the slider moves horizontally or vertically.</li> </ul>

**起始版本：** 12

### NODE_SLIDER_REVERSE

```c
NODE_SLIDER_REVERSE
```

**描述：**

Defines whether the slider values are reversed. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether the slider values are reversed. The value <b>1</b> means that the slider values are<br>reversed, and <b>0</b> means the opposite.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.value[0].i32: whether the slider values are reversed. The value <b>1</b> means that the slider values are reversed, and <b>0</b> means the opposite.</li> </ul>

**起始版本：** 12

### NODE_SLIDER_STYLE

```c
NODE_SLIDER_STYLE
```

**描述：**

Defines the style of the slider thumb and track. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: style of the slider thumb and track. The parameter type is {@link ArkUI_SliderStyle}.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: style of the slider thumb and track. The parameter type is {@link ArkUI_SliderStyle}.</li> </ul>

**起始版本：** 12

### NODE_SLIDER_TRACK_THICKNESS

```c
NODE_SLIDER_TRACK_THICKNESS
```

**描述：**

Sets the track thickness of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: track thickness of the slider, in vp. The default value is 4.0 vp when <b>NODE_SLIDER_STYLE</b><br>is set to <b>ARKUI_SLIDER_STYLE_OUT_SET</b> and 20.0 vp when <b>NODE_SLIDER_STYLE</b> is set to<br><b>ARKUI_SLIDER_STYLE_IN_SET</b>.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.value[0].f32: track thickness of the slider, in vp.</li> </ul>

**起始版本：** 12

### NODE_SLIDER_ENABLE_HAPTIC_FEEDBACK

```c
NODE_SLIDER_ENABLE_HAPTIC_FEEDBACK = 17013
```

**描述：**

Defines whether haptic feedback. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to feedback. The value <b>true</b> means to feedback, and<br><b>false</b> means the opposite.</li><br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>value[0].i32: whether to feedback. When enabling haptic feedback, you need to add "ohos.permission.VIBRATE" in the requestPermissions field of the module.json5 file to enable vibration permission.</li> </ul>

**起始版本：** 18

### NODE_SLIDER_PREFIX

```c
NODE_SLIDER_PREFIX
```

**描述：**

Sets a custom component on the leading side of the Slider component.<br> **Attribute setting method {@link ArkUI_AttributeItem} parameter format:**<br><ul><br><li>.object: Parameter type {@link ArkUI_NodeHandle}.</li> </ul> The prefix component will be placed at the start position of the Slider， typically on the left side in LTR layouts. *

**起始版本：** 20

### NODE_SLIDER_SUFFIX

```c
NODE_SLIDER_SUFFIX
```

**描述：**

Sets a custom component on the trailing side of the Slider component.<br> **Attribute setting method {@link link ArkUI_AttributeItem} parameter format:**<br><ul><br><li>.object: Parameter type {@link ArkUI_NodeHandle}.</li> </ul> The suffix component will be placed at the end position of the Slider, typically on the right side in LTR layouts. *

**起始版本：** 20

### NODE_SLIDER_BLOCK_LINEAR_GRADIENT_COLOR

```c
NODE_SLIDER_BLOCK_LINEAR_GRADIENT_COLOR
```

**描述：**

Defines the color of the slider block. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: array of color stops, each of which consists of a color and its stop position.<br>The parameter type is {@link ArkUI_ColorStop}. Invalid colors are automatically skipped.</li> <br><li>colors: colors of the color stops.</li> <br><li>stops: stop positions of the color stops.</li> <br><li>size: number of colors.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.object: array of color stops, each of which consists of a color and its stop position.<br>The parameter type is {@link ArkUI_ColorStop}. Invalid colors are automatically skipped.</li> <li>colors: colors of the color stops.</li> <li>stops: stop positions of the color stops.</li> <li>size: number of colors.</li> </ul>

**起始版本：** 21

### NODE_SLIDER_TRACK_LINEAR_GRADIENT_COLOR

```c
NODE_SLIDER_TRACK_LINEAR_GRADIENT_COLOR
```

**描述：**

Defines the background color of the slider. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: array of color stops, each of which consists of a color and its stop position.<br>The parameter type is {@link ArkUI_ColorStop}. Invalid colors are automatically skipped.</li> <br><li>colors: colors of the color stops.</li> <br><li>stops: stop positions of the color stops.</li> <br><li>size: number of colors.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.object: array of color stops, each of which consists of a color and its stop position.<br>The parameter type is {@link ArkUI_ColorStop}. Invalid colors are automatically skipped.</li> <li>colors: colors of the color stops.</li> <li>stops: stop positions of the color stops.</li> <li>size: number of colors.</li> </ul>

**起始版本：** 21

### NODE_SLIDER_SELECTED_LINEAR_GRADIENT_COLOR

```c
NODE_SLIDER_SELECTED_LINEAR_GRADIENT_COLOR
```

**描述：**

Defines the color of the selected part of the slider track. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: array of color stops, each of which consists of a color and its stop position.<br>The parameter type is {@link ArkUI_ColorStop}. Invalid colors are automatically skipped.</li> <br><li>colors: colors of the color stops.</li> <br><li>stops: stop positions of the color stops.</li> <br><li>size: number of colors.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.object: array of color stops, each of which consists of a color and its stop position.<br>The parameter type is {@link ArkUI_ColorStop}. Invalid colors are automatically skipped.</li> <li>colors: colors of the color stops.</li> <li>stops: stop positions of the color stops.</li> <li>size: number of colors.</li> </ul>

**起始版本：** 21


