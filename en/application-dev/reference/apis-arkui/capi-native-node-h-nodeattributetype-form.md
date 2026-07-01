# ArkUI_NodeAttributeType (Form Component Attribute)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao; @liyi0309-->
<!--Designer: @houguobiao; @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side for form components including **Toggle**, **Button**, **CheckBox**, **CheckBoxGroup**, **Slider**, and **Radio**.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## NODE_TOGGLE_SELECTED_COLOR

```c
NODE_TOGGLE_SELECTED_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TOGGLE = 5000
```

Background color of the component when it is selected.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Background color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Background color, in 0xARGB format.|

## NODE_TOGGLE_SWITCH_POINT_COLOR

```c
NODE_TOGGLE_SWITCH_POINT_COLOR = 5001
```

Color of the circular thumb for the component of the switch type. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Color of the circular thumb, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Color of the circular thumb, in 0xARGB format.|

## NODE_TOGGLE_VALUE

```c
NODE_TOGGLE_VALUE = 5002
```

Toggle value of the component of the switch type. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable the toggle. The value **true** means to enable the toggle.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the toggle is enabled.|

## NODE_TOGGLE_UNSELECTED_COLOR

```c
NODE_TOGGLE_UNSELECTED_COLOR = 5003
```

Color of the component when it is deselected. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Background color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Background color, in 0xARGB format.|

## NODE_BUTTON_LABEL

```c
NODE_BUTTON_LABEL = MAX_NODE_SCOPE_NUM * ARKUI_NODE_BUTTON = 9000
```

Button text content. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Default text content.|

**Returns**

| Type| Description|
| -- | -- |
| .string| Default text content.|

## NODE_BUTTON_TYPE

```c
NODE_BUTTON_TYPE = 9001
```

Button type. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Button type. The parameter type is [ArkUI_ButtonType](capi-button-h.md#arkui_buttontype). The default value is **ARKUI_BUTTON_TYPE_CAPSULE**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Button type. The parameter type is [ArkUI_ButtonType](capi-button-h.md#arkui_buttontype). The default value is **ARKUI_BUTTON_TYPE_CAPSULE**.|

## NODE_BUTTON_MIN_FONT_SCALE

```c
NODE_BUTTON_MIN_FONT_SCALE = 9002
```

Minimum font scale factor for the button. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 18


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Minimum font scale factor for the button. The default unit is fp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Minimum font scale factor for the button. The default unit is fp.|

## NODE_BUTTON_MAX_FONT_SCALE

```c
NODE_BUTTON_MAX_FONT_SCALE = 9003
```

Maximum font scale factor for the button. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 18


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Maximum font scale factor for the button. The default unit is fp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Maximum font scale factor for the button. The default unit is fp.|

## NODE_CHECKBOX_SELECT

```c
NODE_CHECKBOX_SELECT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX = 11000
```

Whether the [CheckBox](arkui-ts/ts-basic-components-checkbox.md) component is selected. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the component is selected. The value **1** means that the component is selected, and **0** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the component is selected. The value **1** means that the component is selected, and **0** means the opposite.|

## NODE_CHECKBOX_SELECT_COLOR

```c
NODE_CHECKBOX_SELECT_COLOR = 11001
```

Color of the [CheckBox](arkui-ts/ts-basic-components-checkbox.md) component when it is selected. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Color of the check box when it is selected, in 0xARGB format, for example, **0xFF1122FF**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Color of the check box when it is selected, in 0xARGB format, for example, **0xFF1122FF**.|

## NODE_CHECKBOX_UNSELECT_COLOR

```c
NODE_CHECKBOX_UNSELECT_COLOR = 11002
```

Border color of the [CheckBox](arkui-ts/ts-basic-components-checkbox.md) component when it is not selected. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Border color, in 0xARGB format, for example, **0xFF1122FF**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Border color, in 0xARGB format, for example, **0xFF1122FF**.|

## NODE_CHECKBOX_MARK

```c
NODE_CHECKBOX_MARK = 11003
```

Internal mark style of the [CheckBox](arkui-ts/ts-basic-components-checkbox.md) component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Border color, in 0xARGB format, for example, **0xFF1122FF**.|
| .value[1]?.f32 | Size of the internal mark, in vp. This parameter is optional.|
| .value[2]?.f32 | Stroke width of the internal mark, in vp. This parameter is optional. The default value is **2**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Border color, in 0xARGB format, for example, **0xFF1122FF**.|
| .value[1].f32 | Size of the internal mark, in vp.|
| .value[2].f32 | Stroke width of the internal mark, in vp. The default value is **2**.|

## NODE_CHECKBOX_SHAPE

```c
NODE_CHECKBOX_SHAPE = 11004
```

Shape of the **CheckBox** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Component shape. The parameter type is [ArkUI_CheckboxShape](capi-checkbox-h.md#arkui_checkboxshape).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Component shape. The parameter type is [ArkUI_CheckboxShape](capi-checkbox-h.md#arkui_checkboxshape).|

## NODE_CHECKBOX_NAME

```c
NODE_CHECKBOX_NAME = 11005
```

Name of the **CheckBox** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| .string | Component name.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Component name.|

## NODE_CHECKBOX_GROUP

```c
NODE_CHECKBOX_GROUP = 11006
```

Name of the **CheckboxGroup** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| .string | Component name.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Component name.|

## NODE_SLIDER_BLOCK_COLOR

```c
NODE_SLIDER_BLOCK_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SLIDER = 17000
```

Color of the slider thumb. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Color of the slider thumb, in 0xARGB format, for example, **0xFF1122FF**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Color of the slider thumb, in 0xARGB format, for example, **0xFF1122FF**.|

## NODE_SLIDER_TRACK_COLOR

```c
NODE_SLIDER_TRACK_COLOR = 17001
```

Background color of the slider track. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Background color, in 0xARGB format, for example, **0xFF1122FF**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Background color, in 0xARGB format, for example, **0xFF1122FF**.|

## NODE_SLIDER_SELECTED_COLOR

```c
NODE_SLIDER_SELECTED_COLOR = 17002
```

Color of the selected part of the slider track. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Color of the selected part of the slider track, in 0xARGB format, for example, **0xFF1122FF**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Color of the selected part of the slider track, in 0xARGB format, for example, **0xFF1122FF**.|

## NODE_SLIDER_SHOW_STEPS

```c
NODE_SLIDER_SHOW_STEPS = 17003
```

Whether to display the step scale value. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to display the step scale value. The value **1** means to display the step scale value, and **0** means the opposite. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the step scale value is displayed. The value **1** means that the step scale value is displayed, and **0** means the opposite. The default value is **0**.|

## NODE_SLIDER_BLOCK_STYLE

```c
NODE_SLIDER_BLOCK_STYLE = 17004
```

Shape of the slider thumb. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Shape. The parameter type is [ArkUI_SliderBlockStyle](capi-slider-h.md#arkui_sliderblockstyle).|
| .string? | This parameter is optional, and its value depends on the shape.<br>**ARKUI_SLIDER_BLOCK_STYLE_IMAGE**: image resource of the slider thumb. Example: /pages/common/icon.png.<br>**ARKUI_SLIDER_BLOCK_STYLE_SHAPE**: custom shape of the slider thumb. In this case, the width and height values in the defined shape do not represent the actual size of the thumb; they are scaled proportionally to ensure the thumb displays correctly.<br>There are four types. For the path type, **.string** indicates the command string for drawing the path.|
| .value[1].i32 | Shape type. The parameter type is [ArkUI_ShapeType](capi-native-type-visual-h.md#arkui_shapetype). The value is **ARKUI_SHAPE_TYPE_RECTANGLE** for the rectangle type, **ARKUI_SHAPE_TYPE_CIRCLE** for the circle type, **ARKUI_SHAPE_TYPE_ELLIPSE** for the ellipse type, and **ARKUI_SHAPE_TYPE_PATH** for the path type.|
| .value[2].f32 | Width of the rectangle, circle, ellipse, or path type.|
| .value[3].f32 | Height of the rectangle, circle, ellipse, or path type.|
| .value[4].f32 | Width of the rounded corner of the rectangle type.|
| .value[5].f32 | Height of the rounded corner of the rectangle type.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Shape. The parameter type is [ArkUI_SliderBlockStyle](capi-slider-h.md#arkui_sliderblockstyle).|
| .string? | This parameter is optional, and its value depends on the shape.<br>**ARKUI_SLIDER_BLOCK_STYLE_IMAGE**: image resource of the slider thumb. Example: /pages/common/icon.png.<br>**ARKUI_SLIDER_BLOCK_STYLE_SHAPE**: custom shape of the slider thumb.<br>There are four types. For the path type, **.string** indicates the command string for drawing the path.|
| .value[1].i32 | Shape type. The parameter type is [ArkUI_ShapeType](capi-native-type-visual-h.md#arkui_shapetype). The value is **ARKUI_SHAPE_TYPE_RECTANGLE** for the rectangle type, **ARKUI_SHAPE_TYPE_CIRCLE** for the circle type, **ARKUI_SHAPE_TYPE_ELLIPSE** for the ellipse type, and **ARKUI_SHAPE_TYPE_PATH** for the path type.|
| .value[2].f32 | Width of the rectangle, circle, ellipse, or path type.|
| .value[3].f32 | Height of the rectangle, circle, ellipse, or path type.|
| .value[4].f32 | Width of the rounded corner of the rectangle type.|
| .value[5].f32 | Height of the rounded corner of the rectangle type.|

## NODE_SLIDER_VALUE

```c
NODE_SLIDER_VALUE = 17005
```

Current value of the slider. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Current value.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Current value.|

## NODE_SLIDER_MIN_VALUE

```c
NODE_SLIDER_MIN_VALUE = 17006
```

Minimum value of the slider. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Minimum value.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Minimum value.|

## NODE_SLIDER_MAX_VALUE

```c
NODE_SLIDER_MAX_VALUE = 17007
```

Maximum value of the slider. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Maximum value.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Maximum value.|

## NODE_SLIDER_STEP

```c
NODE_SLIDER_STEP = 17008
```

Step of the slider. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Step. The value range is [0.01, 100].|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Step. The value range is [0.01, 100].|

## NODE_SLIDER_DIRECTION

```c
NODE_SLIDER_DIRECTION = 17009
```

Slider direction. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Slider direction. The parameter type is [ArkUI_SliderDirection](capi-slider-h.md#arkui_sliderdirection).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Slider direction. The parameter type is [ArkUI_SliderDirection](capi-slider-h.md#arkui_sliderdirection).|

## NODE_SLIDER_REVERSE

```c
NODE_SLIDER_REVERSE = 17010
```

Whether the slider values are reversed. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the slider values are reversed. The value **1** means that the slider values are reversed, and **0** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the slider values are reversed. The value **1** means that the slider values are reversed, and **0** means the opposite.|

## NODE_SLIDER_STYLE

```c
NODE_SLIDER_STYLE = 17011
```

Style of the slider thumb and track. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Slider style. The parameter type is [ArkUI_SliderStyle](capi-slider-h.md#arkui_sliderstyle).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Slider style. The parameter type is [ArkUI_SliderStyle](capi-slider-h.md#arkui_sliderstyle).|

## NODE_SLIDER_TRACK_THICKNESS

```c
NODE_SLIDER_TRACK_THICKNESS = 17012
```

Track thickness of the slider. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Track thickness of the slider, in vp. The default value is 4.0 vp when **NODE_SLIDER_STYLE** is set to **ARKUI_SLIDER_STYLE_OUT_SET** and 20.0 vp when **NODE_SLIDER_STYLE** is set to **ARKUI_SLIDER_STYLE_IN_SET**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Track thickness of the slider, in vp.|

## NODE_SLIDER_ENABLE_HAPTIC_FEEDBACK

```c
NODE_SLIDER_ENABLE_HAPTIC_FEEDBACK = 17013
```

Whether to enable haptic feedback. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>
To enable haptic feedback, you must add **"name": "ohos.permission.VIBRATE"** under **requestPermissions** in the **module.json5** file of the project.<br>

**Since:** 18


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Whether to enable haptic feedback. **true** to enable; **false** otherwise. The default value is **true**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Whether haptic feedback is enabled.|

## NODE_SLIDER_PREFIX

```c
NODE_SLIDER_PREFIX = 17014
```

Custom prefix component for the start edge of the slider.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| .object | The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md). The prefix component is typically placed on the left in LTR layouts.|

## NODE_SLIDER_SUFFIX

```c
NODE_SLIDER_SUFFIX = 17015
```

Custom suffix component for the end edge of the slider.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| .object | The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md). The suffix component is typically placed on the right in LTR layouts.|

## NODE_SLIDER_BLOCK_LINEAR_GRADIENT_COLOR

```c
NODE_SLIDER_BLOCK_LINEAR_GRADIENT_COLOR = 17016
```

Color of the slider thumb. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br>- **colors**: colors of the color stops.<br>- **stops**: stop positions of the color stops.<br>- **size**: number of colors.|

**Returns**

| Type| Description|
| -- | -- |
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position.<br>- **colors**: colors of the color stops.<br>- **stops**: stop positions of the color stops.<br>- **size**: number of colors.|

## NODE_SLIDER_TRACK_LINEAR_GRADIENT_COLOR

```c
NODE_SLIDER_TRACK_LINEAR_GRADIENT_COLOR = 17017
```

Linear gradient color of the slider track. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br>- **colors**: colors of the color stops.<br>- **stops**: stop positions of the color stops.<br>- **size**: number of colors.|

**Returns**

| Type| Description|
| -- | -- |
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position.<br>- **colors**: colors of the color stops.<br>- **stops**: stop positions of the color stops.<br>- **size**: number of colors.|

## NODE_SLIDER_SELECTED_LINEAR_GRADIENT_COLOR

```c
NODE_SLIDER_SELECTED_LINEAR_GRADIENT_COLOR = 17018
```

Linear gradient color of the selected part of the slider track. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br>- **colors**: colors of the color stops.<br>- **stops**: stop positions of the color stops.<br>- **size**: number of colors.|

**Returns**

| Type| Description|
| -- | -- |
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position.<br>- **colors**: colors of the color stops.<br>- **stops**: stop positions of the color stops.<br>- **size**: number of colors.|

## NODE_RADIO_CHECKED

```c
NODE_RADIO_CHECKED = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RADIO = 18000
```

Whether the radio button is selected. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the radio button is selected. The default value is **false**. **true**: The radio button is selected. **false**: The radio button is not selected.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the radio button is selected.|

## NODE_RADIO_STYLE

```c
NODE_RADIO_STYLE = 18001
```

Style of the radio button in selected or deselected state. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0]?.u32 | Color of the background when the radio button is selected, in 0xARGB format. The default value is **0xFF007DFF**.|
| .value[1]?.u32 | Color of the border when the radio button is deselected, in 0xARGB format. The default value is **0xFF182431**.|
| .value[2]?.u32 | Color of the indicator when the radio button is selected, in 0xARGB format. The default value is **0xFFFFFFFF**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Color of the background when the radio button is selected, in 0xARGB format. The default value is **0xFF007DFF**.|
| .value[1].u32 | Color of the border when the radio button is deselected, in 0xARGB format. The default value is **0xFF182431**.|
| .value[2].u32 | Color of the indicator when the radio button is selected, in 0xARGB format. The default value is **0xFFFFFFFF**.|

## NODE_RADIO_VALUE

```c
NODE_RADIO_VALUE = 18002
```

Current value of the radio button. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Current value of the radio button.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Current value of the radio button.|

## NODE_RADIO_GROUP

```c
NODE_RADIO_GROUP = 18003
```

Name of the group to which the radio button belongs. Only one radio button in a given group can be selected at a time. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Name of the group to which the radio button belongs.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Name of the group to which the radio button belongs.|

## NODE_CHECKBOX_GROUP_NAME

```c
NODE_CHECKBOX_GROUP_NAME = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX_GROUP = 21000
```

Name of the **CheckboxGroup** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| .string | Component name.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Component name.|

## NODE_CHECKBOX_GROUP_SELECT_ALL

```c
NODE_CHECKBOX_GROUP_SELECT_ALL = 21001
```

Whether to select all check boxes in the [CheckBoxGroup](arkui-ts/ts-basic-components-checkboxgroup.md) component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to select all check boxes in the **CheckBoxGroup** component. The value **1** means to select all check boxes, and **0** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether all check boxes are selected. The value **1** means that all check boxes are selected, and **0** means the opposite.|

## NODE_CHECKBOX_GROUP_SELECTED_COLOR

```c
NODE_CHECKBOX_GROUP_SELECTED_COLOR = 21002
```

Color for the selected state of the [CheckBoxGroup](arkui-ts/ts-basic-components-checkboxgroup.md) component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Color of the selected state, in 0xARGB format, for example, **0xFF1122FF**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Color for the selected state of the [CheckBoxGroup](arkui-ts/ts-basic-components-checkboxgroup.md) component, in 0xARGB format, for example, **0xFF1122FF**.|

## NODE_CHECKBOX_GROUP_UNSELECTED_COLOR

```c
NODE_CHECKBOX_GROUP_UNSELECTED_COLOR = 21003
```

Border color for the unselected state of the [CheckBoxGroup](arkui-ts/ts-basic-components-checkboxgroup.md) component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Border color, in 0xARGB format, for example, **0xFF1122FF**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Border color, in 0xARGB format, for example, **0xFF1122FF**.|

## NODE_CHECKBOX_GROUP_MARK

```c
NODE_CHECKBOX_GROUP_MARK = 21004
```

Internal mark style of the [CheckBoxGroup](arkui-ts/ts-basic-components-checkboxgroup.md) component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Border color, in 0xARGB format, for example, **0xFF1122FF**.|
| .value[1]?.f32 | Size of the internal mark, in vp. This parameter is optional.|
| .value[2]?.f32 | Stroke width of the internal mark, in vp. This parameter is optional. The default value is **2**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Border color, in 0xARGB format, for example, **0xFF1122FF**.|
| .value[1]?.f32 | Size of the internal mark, in vp. This parameter is optional.|
| .value[2]?.f32 | Stroke width of the internal mark, in vp. This parameter is optional. The default value is **2**.|

## NODE_CHECKBOX_GROUP_SHAPE

```c
NODE_CHECKBOX_GROUP_SHAPE = 21005
```

Shape of the [CheckBoxGroup](arkui-ts/ts-basic-components-checkboxgroup.md) component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Component shape. The parameter type is [ArkUI_CheckboxShape](capi-checkbox-h.md#arkui_checkboxshape).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Component shape. The parameter type is [ArkUI_CheckboxShape](capi-checkbox-h.md#arkui_checkboxshape).|
