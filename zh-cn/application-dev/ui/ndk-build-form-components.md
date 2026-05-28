# 构建表单组件
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyi0309-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

ArkUI NDK提供了多种表单组件，包括[按钮（Button）](./arkts-common-components-button.md)、滑动条[Slider](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md)、[切换按钮（Toggle）](./arkts-common-components-switch.md)、复选框[Checkbox](../reference/apis-arkui/arkui-ts/ts-basic-components-checkbox.md)、复选框组[CheckboxGroup](../reference/apis-arkui/arkui-ts/ts-basic-components-checkboxgroup.md)和[单选框（Radio）](./arkts-common-components-radio-button.md)。这些组件是用户交互的基础元素，可以用于构建丰富的表单界面。

表单组件的相关接口定义在[native_node.h](../reference/apis-arkui/capi-native-node-h.md)中。

本文提供表单组件NDK开发指导，查询之前需要先接入ArkTS页面，具体请参考[接入ArkTS页面](./ndk-access-the-arkts-page.md)。

## Button按钮组件

Button组件用于创建可点击的按钮，支持多种按钮类型和样式设置。

### 创建Button组件

使用[createNode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#createnode)接口创建Button组件，节点类型为ARKUI_NODE_BUTTON。

<!-- @[button_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeFormExample/entry/src/main/cpp/demo/formTest.cpp) -->

``` C++
std::shared_ptr<NativeModule::ArkUIBaseNode> CreateButtonExample()
{
    auto column = std::make_shared<NativeModule::ArkUIColumnNode>();
    column->SetWidth(1, true);
    column->SetHeight(1, true);
    column->SetBackgroundColor(0x33ff0000);
    column->SetPadding(PARAM_20, false);
    auto button = std::make_shared<NativeModule::ArkUIButtonNode>();
    button->SetButtonLabel("This is a Normal Button");
    button->SetMaxFontScale(1.0);
    auto circleBtn = std::make_shared<NativeModule::ArkUIButtonNode>();
    circleBtn->SetButtonLabel("Circle");
    circleBtn->SetButtonType(ARKUI_BUTTON_TYPE_CIRCLE);
    circleBtn->SetMargin(PARAM_20, false);
    column->AddChild(button);
    column->AddChild(circleBtn);
    // 将Column添加到Content中
    return column;
}
```

### 设置Button类型

Button组件支持通过设置NODE_BUTTON_TYPE属性实现不同的按钮类型，包括普通按钮、胶囊按钮、圆形按钮和圆角矩形按钮。按钮类型对应枚举请参考[ArkUI_ButtonType](../reference/apis-arkui/capi-native-type-h.md#arkui_buttontype)。

下述示例将按钮类型设置为ARKUI_BUTTON_TYPE_CIRCLE圆形按钮。

<!-- @[button_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeFormExample/entry/src/main/cpp/demo/formTest.cpp) -->

``` C++
auto circleBtn = std::make_shared<NativeModule::ArkUIButtonNode>();
circleBtn->SetButtonLabel("Circle");
circleBtn->SetButtonType(ARKUI_BUTTON_TYPE_CIRCLE);
circleBtn->SetMargin(PARAM_20, false);
```

### Button属性

Button独有属性如下，具体说明请参考[ArkUI_NodeAttributeType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeattributetype)中的枚举定义。

| 属性 | 说明 |
|------|------|
| NODE_BUTTON_LABEL | 设置按钮文本标签。 |
| NODE_BUTTON_TYPE | 设置按钮类型。 |
| NODE_BUTTON_MIN_FONT_SCALE | 设置最小字体缩放比例。从API version 18开始支持。|
| NODE_BUTTON_MAX_FONT_SCALE | 设置最大字体缩放比例。从API version 18开始支持。|

## Slider滑动条组件

Slider组件用于创建滑动条，用户可以通过拖动滑块来选择数值。

### 创建Slider组件

使用[createNode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#createnode)接口创建Slider组件，节点类型为ARKUI_NODE_SLIDER。

<!-- @[slider_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeFormExample/entry/src/main/cpp/demo/formTest.cpp) -->

``` C++
std::shared_ptr<NativeModule::ArkUIBaseNode> CreateSliderExample()
{
    auto column = std::make_shared<NativeModule::ArkUIColumnNode>();
    column->SetWidth(1, true);
    column->SetHeight(1, true);
    column->SetBackgroundColor(0x33ff0000);
    column->SetPadding(PARAM_20, false);
    auto sliderInSet = std::make_shared<NativeModule::ArkUISliderNode>();
    sliderInSet->SetSliderValue(PARAM_50);
    sliderInSet->SetSliderStep(PARAM_10);
    sliderInSet->SetSliderStyle(ARKUI_SLIDER_STYLE_IN_SET);
    sliderInSet->SetBlockColor(0xFF00FF00);
    sliderInSet->SetTrackColor(0xFFFFFF00);
    auto sliderOutSet = std::make_shared<NativeModule::ArkUISliderNode>();
    sliderOutSet->SetSliderValue(PARAM_50);
    sliderOutSet->SetSliderStep(PARAM_10);
    sliderOutSet->SetSliderStyle(ARKUI_SLIDER_STYLE_OUT_SET);
    sliderOutSet->SetMargin(PARAM_20, false);
    sliderOutSet->SetSliderDirection(ARKUI_SLIDER_DIRECTION_VERTICAL);
    sliderOutSet->SetIsReverse(true);
    sliderOutSet->SetIsShowSteps(true);
    column->AddChild(sliderInSet);
    column->AddChild(sliderOutSet);
    return column;
}
```

### 设置Slider样式

Slider支持两种样式，通过[ARKUI_SliderStyle](../reference/apis-arkui/capi-native-type-h.md#arkui_sliderstyle)枚举定义：

- ARKUI_SLIDER_STYLE_OUT_SET：滑块在滑动条外（默认值）。
- ARKUI_SLIDER_STYLE_IN_SET：滑块在滑动条内。

如下示例代码创建了ARKUI_SLIDER_STYLE_IN_SET样式的Slider组件并设置了滑块和滑轨颜色。

<!-- @[slider_inset_style](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeFormExample/entry/src/main/cpp/demo/formTest.cpp) -->

``` C++
auto sliderInSet = std::make_shared<NativeModule::ArkUISliderNode>();
sliderInSet->SetSliderValue(PARAM_50);
sliderInSet->SetSliderStep(PARAM_10);
sliderInSet->SetSliderStyle(ARKUI_SLIDER_STYLE_IN_SET);
sliderInSet->SetBlockColor(0xFF00FF00);
sliderInSet->SetTrackColor(0xFFFFFF00);
```

### 设置Slider方向和步进

Slider支持设置滑动方向（水平或垂直）、是否反向以及是否显示步进刻度。

<!-- @[slider_outset_style](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeFormExample/entry/src/main/cpp/demo/formTest.cpp) -->

``` C++
auto sliderOutSet = std::make_shared<NativeModule::ArkUISliderNode>();
sliderOutSet->SetSliderValue(PARAM_50);
sliderOutSet->SetSliderStep(PARAM_10);
sliderOutSet->SetSliderStyle(ARKUI_SLIDER_STYLE_OUT_SET);
sliderOutSet->SetMargin(PARAM_20, false);
sliderOutSet->SetSliderDirection(ARKUI_SLIDER_DIRECTION_VERTICAL);
sliderOutSet->SetIsReverse(true);
sliderOutSet->SetIsShowSteps(true);
```

### Slider属性

Slider独有属性如下，具体说明请参考[ArkUI_NodeAttributeType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeattributetype)中的枚举定义。

| 属性 | 说明 |
|------|------|
| NODE_SLIDER_VALUE | 设置当前进度值。 |
| NODE_SLIDER_MIN_VALUE | 设置最小值。 |
| NODE_SLIDER_MAX_VALUE | 设置最大值。 |
| NODE_SLIDER_STEP | 设置滑动步长。 |
| NODE_SLIDER_DIRECTION | 设置滑动条方向。 |
| NODE_SLIDER_REVERSE | 设置是否反向。 |
| NODE_SLIDER_STYLE | 设置滑动条样式。 |
| NODE_SLIDER_BLOCK_COLOR | 设置滑块颜色。 |
| NODE_SLIDER_TRACK_COLOR | 设置轨道颜色。 |
| NODE_SLIDER_SELECTED_COLOR | 设置已选择部分颜色。 |
| NODE_SLIDER_SHOW_STEPS | 设置是否显示步进刻度。 |

## Toggle开关组件

Toggle组件用于创建开关，用户可以在开和关两种状态之间切换。

### 创建Toggle组件

使用[createNode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#createnode)接口创建Toggle组件，节点类型为ARKUI_NODE_TOGGLE。

<!-- @[toggle_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeFormExample/entry/src/main/cpp/demo/formTest.cpp) -->

``` C++
std::shared_ptr<NativeModule::ArkUIBaseNode> CreateToggleExample()
{
    auto column = std::make_shared<NativeModule::ArkUIColumnNode>();
    column->SetWidth(1, true);
    column->SetHeight(1, true);
    column->SetBackgroundColor(0x33ff0000);
    column->SetPadding(PARAM_20, false);
    auto toggle = std::make_shared<NativeModule::ArkUIToggleNode>();
    toggle->SetSelectedColor(0xFFFF0000);
    toggle->SetUnSelectedColor(0xFF0000FF);
    toggle->SetSwitchPointColor(0xFF00FF00);
    column->AddChild(toggle);

    return column;
}
```

### 设置Toggle样式

可以设置Toggle开启状态背景色、关闭状态背景色以及滑块颜色。

<!-- @[toggle_colors](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeFormExample/entry/src/main/cpp/demo/formTest.cpp) -->

``` C++
toggle->SetSelectedColor(0xFFFF0000);
toggle->SetUnSelectedColor(0xFF0000FF);
toggle->SetSwitchPointColor(0xFF00FF00);
```

### Toggle属性

Toggle独有属性如下，具体说明请参考[ArkUI_NodeAttributeType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeattributetype)中的枚举定义。

| 属性 | 说明 |
|------|------|
| NODE_TOGGLE_VALUE | 设置开关状态。 |
| NODE_TOGGLE_SELECTED_COLOR | 设置开启状态背景色。 |
| NODE_TOGGLE_UNSELECTED_COLOR | 设置关闭状态背景色。 |
| NODE_TOGGLE_SWITCH_POINT_COLOR | 设置滑块颜色。 |

## Checkbox复选框组件

Checkbox组件用于创建复选框，用户可以选中或取消选中。CheckboxGroup用于管理多个复选框，实现全选等操作。

### 创建Checkbox组件

使用[createNode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#createnode)接口创建Checkbox组件，节点类型为ARKUI_NODE_CHECKBOX。

<!-- @[checkbox_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeFormExample/entry/src/main/cpp/demo/formTest.cpp) -->

``` C++
std::shared_ptr<NativeModule::ArkUIBaseNode> CreateCheckboxExample()
{
    auto column = std::make_shared<NativeModule::ArkUIColumnNode>();
    column->SetWidth(1, true);
    column->SetHeight(1, true);
    column->SetBackgroundColor(0x33ff0000);
    column->SetPadding(PARAM_20, false);
    auto checkbox1 = std::make_shared<NativeModule::ArkUICheckboxNode>();
    auto checkbox2 = std::make_shared<NativeModule::ArkUICheckboxNode>();
    auto checkbox3 = std::make_shared<NativeModule::ArkUICheckboxNode>();
    auto checkboxGroup = std::make_shared<NativeModule::ArkUICheckboxGroupNode>();
    checkboxGroup->SetCheckboxGroupName("check_group");
    checkbox1->SetCheckboxGroup("check_group");
    checkbox1->SetSelectColor(0xFFFF0000);
    checkbox2->SetCheckboxGroup("check_group");
    checkbox2->SetUnSelectColor(0xFFFF0000);
    checkbox3->SetCheckboxGroup("check_group");
    checkbox3->SetCheckboxShape(ArkUI_CHECKBOX_SHAPE_ROUNDED_SQUARE);
    checkbox1->SetCheckboxName("check_group1");
    checkbox2->SetCheckboxName("check_group2");
    checkbox3->SetCheckboxName("check_group3");

    column->AddChild(checkboxGroup);
    column->AddChild(checkbox1);
    column->AddChild(checkbox2);
    column->AddChild(checkbox3);

    // 将Column添加到Content中
    return column;
}
```

### 创建CheckboxGroup

CheckboxGroup用于管理同一组内的多个复选框，节点类型为ARKUI_NODE_CHECKBOX_GROUP。

<!-- @[checkbox_group](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeFormExample/entry/src/main/cpp/demo/formTest.cpp) -->

``` C++
auto checkboxGroup = std::make_shared<NativeModule::ArkUICheckboxGroupNode>();
checkboxGroup->SetCheckboxGroupName("check_group");
```

### 设置Checkbox属性

可以设置复选框的选中颜色、未选中颜色、形状以及所属组名。

<!-- @[checkbox_properties](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeFormExample/entry/src/main/cpp/demo/formTest.cpp) -->

``` C++
checkbox1->SetCheckboxGroup("check_group");
checkbox1->SetSelectColor(0xFFFF0000);
checkbox2->SetCheckboxGroup("check_group");
checkbox2->SetUnSelectColor(0xFFFF0000);
checkbox3->SetCheckboxGroup("check_group");
checkbox3->SetCheckboxShape(ArkUI_CHECKBOX_SHAPE_ROUNDED_SQUARE);
checkbox1->SetCheckboxName("check_group1");
checkbox2->SetCheckboxName("check_group2");
checkbox3->SetCheckboxName("check_group3");
```

### Checkbox属性

Checkbox独有属性如下，具体说明请参考[ArkUI_NodeAttributeType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeattributetype)中的枚举定义。

| 属性 | 说明 |
|------|------|
| NODE_CHECKBOX_SELECT | 设置是否选中。|
| NODE_CHECKBOX_SELECT_COLOR | 设置选中状态颜色。|
| NODE_CHECKBOX_UNSELECT_COLOR | 设置未选中状态颜色。|
| NODE_CHECKBOX_MARK | 设置勾选标记样式。|
| NODE_CHECKBOX_SHAPE | 设置复选框形状。|
| NODE_CHECKBOX_NAME | 设置复选框名称。从API version 15开始支持。|
| NODE_CHECKBOX_GROUP | 设置复选框组名称，用于CheckboxGroup管理。从API version 15开始支持。|

### CheckboxGroup属性

CheckboxGroup独有属性如下，具体说明请参考[ArkUI_NodeAttributeType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeattributetype)中的枚举定义。

| 属性 | 说明 |
|------|------|
| NODE_CHECKBOX_GROUP_NAME | 设置复选框组名称。从API version 15开始支持。|
| NODE_CHECKBOX_GROUP_SELECT_ALL | 设置是否全选。从API version 15开始支持。|
| NODE_CHECKBOX_GROUP_SELECTED_COLOR | 设置选中状态颜色。从API version 15开始支持。|
| NODE_CHECKBOX_GROUP_UNSELECTED_COLOR | 设置未选中状态颜色。从API version 15开始支持。|
| NODE_CHECKBOX_GROUP_MARK | 设置勾选标记样式。从API version 15开始支持。|
| NODE_CHECKBOX_GROUP_SHAPE | 设置复选框形状。从API version 15开始支持。|

## Radio单选按钮组件

Radio组件用于创建单选按钮，同一组内的单选按钮只能选中一个。

### 创建Radio组件

使用[createNode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#createnode)接口创建Radio组件，节点类型为ARKUI_NODE_RADIO。

<!-- @[radio_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeFormExample/entry/src/main/cpp/demo/formTest.cpp) -->

``` C++
std::shared_ptr<NativeModule::ArkUIBaseNode> CreateRadioExample()
{
    auto column = std::make_shared<NativeModule::ArkUIColumnNode>();
    column->SetWidth(1, true);
    column->SetHeight(1, true);
    column->SetBackgroundColor(0x33ff0000);
    column->SetPadding(PARAM_20, false);
    auto radio1 = std::make_shared<NativeModule::ArkUIRadioNode>();
    auto radio2 = std::make_shared<NativeModule::ArkUIRadioNode>();
    auto radio3 = std::make_shared<NativeModule::ArkUIRadioNode>();
    radio1->SetIsOn(true);
    radio1->SetRadioGroup("radio_group");
    radio2->SetRadioGroup("radio_group");
    radio3->SetRadioGroup("radio_group");
    radio3->SetRadioStyle(0xFFFF0000, 0xFF00FF00, 0xFF00FFFF);

    column->AddChild(radio1);
    column->AddChild(radio2);
    column->AddChild(radio3);

    return column;
}
```

### 设置Radio组

同一组内的Radio组件只能选中一个，通过设置相同的组名实现互斥。

<!-- @[radio_group](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeFormExample/entry/src/main/cpp/demo/formTest.cpp) -->

``` C++
radio1->SetIsOn(true);
radio1->SetRadioGroup("radio_group");
radio2->SetRadioGroup("radio_group");
radio3->SetRadioGroup("radio_group");
```

### 设置Radio样式

可以设置单选按钮的样式，包括未选中状态颜色、选中状态内部圆环颜色和选中状态外环颜色。

<!-- @[radio_style](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeFormExample/entry/src/main/cpp/demo/formTest.cpp) -->

``` C++
radio3->SetRadioStyle(0xFFFF0000, 0xFF00FF00, 0xFF00FFFF);
```

### Radio属性

Radio独有属性如下，具体说明请参考[ArkUI_NodeAttributeType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeattributetype)中的枚举定义。

| 属性 | 说明 |
|------|------|
| NODE_RADIO_CHECKED | 设置是否选中。 |
| NODE_RADIO_STYLE | 设置单选按钮样式（未选中颜色、选中内部圆环颜色、选中外环颜色）。 |
| NODE_RADIO_VALUE | 设置单选按钮值。 |
| NODE_RADIO_GROUP | 设置所属组名，同一组内的Radio互斥。 |

