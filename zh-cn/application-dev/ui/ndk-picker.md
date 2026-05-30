# 使用滑动选择器Picker

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

从API version 23开始，ArkUI开发框架在NDK接口提供了Picker容器组件。Picker容器组件用于实现用户自定义选项的选择操作，支持滚动选择、触感反馈、循环滚动等功能。Picker组件通过设置选择指示器样式，可以自定义选中项的显示效果，适用于日期选择、时间选择、文本选择等场景。从API版本26.0.0开始，可通过`NODE_PICKER_DISPLAYED_ITEM_COUNT`、`NODE_PICKER_ITEM_HEIGHT`配置可见选项行数与每行行高，语义与ArkTS侧[UIPickerComponent](../reference/apis-arkui/arkui-ts/ts-container-ui-picker-component.md)的[displayedItemCount](../reference/apis-arkui/arkui-ts/ts-container-ui-picker-component.md#displayeditemcount)、[itemHeight](../reference/apis-arkui/arkui-ts/ts-container-ui-picker-component.md#itemheight)一致；详细参数格式见[信息选择类组件相关属性](../reference/apis-arkui/capi-native-node-h-nodeattributetype-informationselection.md)。

[创建Picker](#创建picker)后，可以[设置Picker属性](#设置picker属性)，并[监听Picker事件](#监听picker事件)。

使用NDK接口构建UI界面以及NDK基本使用，可以参考[接入ArkTS页面](ndk-access-the-arkts-page.md)。

## 创建Picker

通过[ArkUI_NativeNodeAPI_1](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md)调用[createNode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#createnode)(ARKUI_NODE_PICKER)得到组件对象指针，并设置[ArkUI_NodeAttributeType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeattributetype)中的相关属性，可以创建一个Picker容器组件。

### 基本创建方式

以下示例展示了创建Picker组件并设置基本属性的方法，其中可见选项行数与每行行高从API版本26.0.0起支持，可按需设置；取值与默认行为见[NODE_PICKER_DISPLAYED_ITEM_COUNT](../reference/apis-arkui/capi-native-node-h-nodeattributetype-informationselection.md#node_picker_displayed_item_count)、[NODE_PICKER_ITEM_HEIGHT](../reference/apis-arkui/capi-native-node-h-nodeattributetype-informationselection.md#node_picker_item_height)。

```cpp
// 获取NativeNodeAPI接口
ArkUI_NativeNodeAPI_1 *api = nullptr;
OH_ArkUI_GetModuleInterface(ARKUI_NATIVE_NODE, ArkUI_NativeNodeAPI_1, api);
if (api == nullptr) {
    return nullptr;
}

// 创建Picker组件
ArkUI_NodeHandle picker = api->createNode(ARKUI_NODE_PICKER);
if (picker == nullptr) {
    return nullptr;
}

// 设置Picker尺寸
ArkUI_NumberValue widthValue = {.f32 = 200.0f};
ArkUI_AttributeItem widthItem = {&widthValue, 1};
api->setAttribute(picker, NODE_WIDTH, &widthItem);

ArkUI_NumberValue heightValue = {.f32 = 300.0f};
ArkUI_AttributeItem heightItem = {&heightValue, 1};
api->setAttribute(picker, NODE_HEIGHT, &heightItem);

// 设置默认选中项
ArkUI_NumberValue selectedValue = {.u32 = 0};
ArkUI_AttributeItem selectedItem = {&selectedValue, 1};
api->setAttribute(picker, NODE_PICKER_OPTION_SELECTED_INDEX, &selectedItem);

// 设置循环滚动
ArkUI_NumberValue canLoopValue = {.i32 = 1};
ArkUI_AttributeItem canLoopItem = {&canLoopValue, 1};
api->setAttribute(picker, NODE_PICKER_CAN_LOOP, &canLoopItem);

// 设置触感反馈
ArkUI_NumberValue hapticValue = {.i32 = 1};
ArkUI_AttributeItem hapticItem = {&hapticValue, 1};
api->setAttribute(picker, NODE_PICKER_ENABLE_HAPTIC_FEEDBACK, &hapticItem);

// 设置可见选项行数（API版本26.0.0起支持，可选）
ArkUI_NumberValue displayedCountValue = {.i32 = 5};
ArkUI_AttributeItem displayedCountItem = {&displayedCountValue, 1};
api->setAttribute(picker, NODE_PICKER_DISPLAYED_ITEM_COUNT, &displayedCountItem);

// 设置每行行高，单位vp（API版本26.0.0起支持，可选）
ArkUI_NumberValue itemHeightValue = {.f32 = 48.0f};
ArkUI_AttributeItem itemHeightItem = {&itemHeightValue, 1};
api->setAttribute(picker, NODE_PICKER_ITEM_HEIGHT, &itemHeightItem);
```

### 封装为工具类

参考[示例](ndk-access-the-arkts-page.md#示例)中列表组件的实现方式，可以将Picker组件常用的属性设置封装到自定义的工具类中方便后续使用。

<!-- @[ContainerPickerCanLoopMakerH](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/native_type_sample/entry/src/main/cpp/ContainerPickerCanLoopMaker.h) -->

```cpp
class ContainerPickerCanLoopMaker : public BaseNode {
public:
    static ArkUI_NodeHandle CreateNativeNode();

    ContainerPickerCanLoopMaker()
        : BaseNode(NodeApiInstance::GetInstance()->GetNativeNodeAPI()->createNode(ARKUI_NODE_PICKER)),
          nodeApi_(NodeApiInstance::GetInstance()->GetNativeNodeAPI())
    {
        if (!IsNotNull(nodeApi_) || !IsNotNull(GetHandle())) {
            return;
        }
    }

    ~ContainerPickerCanLoopMaker() override = default;

    // ========================================
    // 基础尺寸设置接口
    // ========================================
    void SetPickerSize(float width, float height) { SetSize(width, height); }

    void SetPickerSizePercent(float widthPercent, float heightPercent) { SetSizePercent(widthPercent, heightPercent); }

    void SetPickerWidthPercent(float widthPercent)
    {
        SetAttributeFloat32(nodeApi_, GetHandle(), NODE_WIDTH_PERCENT, widthPercent);
    }

    void SetPickerHeightPercent(float heightPercent)
    {
        SetAttributeFloat32(nodeApi_, GetHandle(), NODE_HEIGHT_PERCENT, heightPercent);
    }

    // ========================================
    // Picker特有属性设置接口
    // ========================================
    void SetSelectedIndex(uint32_t index)
    {
        if (!IsNotNull(nodeApi_) || !IsNotNull(GetHandle())) {
            return;
        }
        ArkUI_NumberValue selectedIndexValue = {.u32 = index};
        ArkUI_AttributeItem selectedIndexItem = {&selectedIndexValue,
                                                 sizeof(selectedIndexValue) / sizeof(ArkUI_NumberValue)};
        nodeApi_->setAttribute(GetHandle(), NODE_PICKER_OPTION_SELECTED_INDEX, &selectedIndexItem);
    }

    void SetCanLoop(bool canLoop)
    {
        if (!IsNotNull(nodeApi_) || !IsNotNull(GetHandle())) {
            return;
        }
        ArkUI_NumberValue canLoopValue = {.i32 = canLoop ? 1 : 0};
        ArkUI_AttributeItem canLoopItem = {&canLoopValue, sizeof(canLoopValue) / sizeof(ArkUI_NumberValue)};
        nodeApi_->setAttribute(GetHandle(), NODE_PICKER_CAN_LOOP, &canLoopItem);
    }

    void SetHapticFeedback(bool enabled)
    {
        if (!IsNotNull(nodeApi_) || !IsNotNull(GetHandle())) {
            return;
        }
        ArkUI_NumberValue enableHapticFeedbackValue = {.i32 = enabled ? 1 : 0};
        ArkUI_AttributeItem enableHapticFeedbackItem = {&enableHapticFeedbackValue,
                                                        sizeof(enableHapticFeedbackValue) / sizeof(ArkUI_NumberValue)};
        nodeApi_->setAttribute(GetHandle(), NODE_PICKER_ENABLE_HAPTIC_FEEDBACK, &enableHapticFeedbackItem);
    }

    void SetDisplayedItemCount(int32_t count)
    {
        if (!IsNotNull(nodeApi_) || !IsNotNull(GetHandle())) {
            return;
        }
        ArkUI_NumberValue displayedCountValue = {.i32 = count};
        ArkUI_AttributeItem displayedCountItem = {&displayedCountValue,
                                                  sizeof(displayedCountValue) / sizeof(ArkUI_NumberValue)};
        nodeApi_->setAttribute(GetHandle(), NODE_PICKER_DISPLAYED_ITEM_COUNT, &displayedCountItem);
    }

    void SetItemHeight(float heightVp)
    {
        if (!IsNotNull(nodeApi_) || !IsNotNull(GetHandle())) {
            return;
        }
        ArkUI_NumberValue itemHeightValue = {.f32 = heightVp};
        ArkUI_AttributeItem itemHeightItem = {&itemHeightValue, sizeof(itemHeightValue) / sizeof(ArkUI_NumberValue)};
        nodeApi_->setAttribute(GetHandle(), NODE_PICKER_ITEM_HEIGHT, &itemHeightItem);
    }

    void SetSelectionIndicatorBackground(uint32_t backgroundColor, float cornerRadius = 10.0f)
    {
        if (!IsNotNull(nodeApi_) || !IsNotNull(GetHandle())) {
            return;
        }
        ArkUI_PickerIndicatorStyle *indicatorStyle =
            OH_ArkUI_PickerIndicatorStyle_Create(ARKUI_PICKER_INDICATOR_BACKGROUND);
        if (indicatorStyle == nullptr) {
            return;
        }
        ArkUI_PickerIndicatorBackground background = {.backgroundColor = backgroundColor,
                                                      .topLeftRadius = cornerRadius,
                                                      .topRightRadius = cornerRadius,
                                                      .bottomLeftRadius = cornerRadius,
                                                      .bottomRightRadius = cornerRadius};
        OH_ArkUI_PickerIndicatorStyle_ConfigureBackground(indicatorStyle, &background);
        ArkUI_AttributeItem selectionIndicatorItem = {.object = indicatorStyle};
        nodeApi_->setAttribute(GetHandle(), NODE_PICKER_SELECTION_INDICATOR, &selectionIndicatorItem);
    }

    void SetSelectionIndicatorDivider(uint32_t dividerColor, float strokeWidth = 2.0f, float startMargin = 20.0f,
                                      float endMargin = 20.0f)
    {
        if (!IsNotNull(nodeApi_) || !IsNotNull(GetHandle())) {
            return;
        }
        ArkUI_PickerIndicatorStyle *indicatorStyle =
            OH_ArkUI_PickerIndicatorStyle_Create(ARKUI_PICKER_INDICATOR_DIVIDER);
        if (indicatorStyle == nullptr) {
            return;
        }
        ArkUI_PickerIndicatorDivider divider = {.strokeWidth = strokeWidth,
                                                .dividerColor = dividerColor,
                                                .startMargin = startMargin,
                                                .endMargin = endMargin};
        OH_ArkUI_PickerIndicatorStyle_ConfigureDivider(indicatorStyle, &divider);
        ArkUI_AttributeItem selectionIndicatorItem = {.object = indicatorStyle};
        nodeApi_->setAttribute(GetHandle(), NODE_PICKER_SELECTION_INDICATOR, &selectionIndicatorItem);
    }

    // ========================================
    // 公共辅助方法
    // ========================================
    ArkUI_NativeNodeAPI_1 *GetNodeAPI() const { return nodeApi_; }

protected:
    void OnNodeEvent(ArkUI_NodeEvent *event) override { BaseNode::OnNodeEvent(event); }

private:
    ArkUI_NativeNodeAPI_1 *nodeApi_ = nullptr;
};
```

使用封装后的类创建Picker组件：

<!-- @[ContainerPickerCanLoopMakerCpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/native_type_sample/entry/src/main/cpp/ContainerPickerCanLoopMaker.cpp) -->

```cpp
auto picker = std::make_shared<ContainerPickerCanLoopMaker>();
auto data = std::make_shared<std::vector<std::string>>(MakeData());
ConfigurePicker(picker, data);
```

## 设置Picker属性

### 设置默认选中项

通过设置[ArkUI_NodeAttributeType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeattributetype)中的`NODE_PICKER_OPTION_SELECTED_INDEX`属性，可以设置Picker组件的默认选中项索引。

```cpp
picker->SetSelectedIndex(2); // 设置默认选中第3项（索引从0开始）
```

### 设置触感反馈

通过设置`NODE_PICKER_ENABLE_HAPTIC_FEEDBACK`属性，可以控制Picker组件是否启用触感反馈。开启后，当用户滚动选择器时，如果系统硬件支持，会产生触控反馈。

```cpp
picker->SetHapticFeedback(true); // 启用触感反馈
picker->SetHapticFeedback(false); // 禁用触感反馈
```

### 设置循环滚动

通过设置`NODE_PICKER_CAN_LOOP`属性，可以控制Picker组件是否支持循环滚动。设置为true时，选择器可以无限循环滚动；设置为false时，滚动到首尾时会停止。

> **说明：**
>
> 如果子组件的个数小于8个，无论设置为true还是false，都不会循环滚动。

```cpp
picker->SetCanLoop(true); // 支持循环滚动
picker->SetCanLoop(false); // 不支持循环滚动
```

### 设置可见选项数量与选项行高

从API版本26.0.0开始，可通过[NODE_PICKER_DISPLAYED_ITEM_COUNT](../reference/apis-arkui/capi-native-node-h-nodeattributetype-informationselection.md#node_picker_displayed_item_count)设置可见选项行数，通过[NODE_PICKER_ITEM_HEIGHT](../reference/apis-arkui/capi-native-node-h-nodeattributetype-informationselection.md#node_picker_item_height)设置每一行的高度（vp）。未设置时，默认分别为7行与40vp；取值范围、偶数行数规范及越界行为与[UIPickerComponent](../reference/apis-arkui/arkui-ts/ts-container-ui-picker-component.md)的[displayedItemCount](../reference/apis-arkui/arkui-ts/ts-container-ui-picker-component.md#displayeditemcount)、[itemHeight](../reference/apis-arkui/arkui-ts/ts-container-ui-picker-component.md#itemheight)一致。立体滚轮样式下可视高度会受旋转影响，若增大行数或行高，请相应增大Picker容器高度。

使用[ArkUI_NativeNodeAPI_1](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md)时可直接调用`setAttribute`。

```cpp
ArkUI_NumberValue visibleCountValue = {.i32 = 5};
ArkUI_AttributeItem visibleCountItem = {&visibleCountValue, 1};
api->setAttribute(picker, NODE_PICKER_DISPLAYED_ITEM_COUNT, &visibleCountItem);

ArkUI_NumberValue itemHeightValue = {.f32 = 48.0f};
ArkUI_AttributeItem itemHeightItem = {&itemHeightValue, 1};
api->setAttribute(picker, NODE_PICKER_ITEM_HEIGHT, &itemHeightItem);
```

若使用上文封装的`ContainerPickerCanLoopMaker`，可调用已封装的接口。

```cpp
picker->SetDisplayedItemCount(5);   // 可见选项行数，具体规则见属性说明文档
picker->SetItemHeight(48.0f);        // 每行高度（vp）
```

### 设置选择指示器样式

通过设置`NODE_PICKER_SELECTION_INDICATOR`属性，可以自定义Picker组件的选择指示器样式。选择指示器包括背景样式和分割线样式两部分。

背景样式指示器通过[ArkUI_PickerIndicatorBackground](../reference/apis-arkui/capi-arkui-nativemodule-arkui-pickerindicatorbackground.md)结构体设置，包括背景颜色和圆角半径。

```cpp
ArkUI_PickerIndicatorBackground backgroundStyle = {
    .backgroundColor = 0x1A000000,  // 半透明黑色背景
    .topLeftRadius = 8.0f,
    .topRightRadius = 8.0f,
    .bottomLeftRadius = 8.0f,
    .bottomRightRadius = 8.0f
};
```

分割线样式指示器通过[ArkUI_PickerIndicatorDivider](../reference/apis-arkui/capi-arkui-nativemodule-arkui-pickerindicatordivider.md)结构体设置，包括线宽、颜色和边距。

```cpp
ArkUI_PickerIndicatorDivider dividerStyle = {
    .strokeWidth = 2.0f,
    .dividerColor = 0xFF3366CC,  // 蓝色分割线
    .startMargin = 10.0f,
    .endMargin = 10.0f
};
```

将背景样式或分割线样式组合到[ArkUI_PickerIndicatorStyle](../reference/apis-arkui/capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)结构体中，并设置给Picker组件。

```cpp
ArkUI_PickerIndicatorStyle indicatorStyle1 = {
    .background = backgroundStyle
};
picker->SetSelectionIndicator(&indicatorStyle1);

ArkUI_PickerIndicatorStyle indicatorStyle2 = {
    .divider = dividerStyle
};
picker->SetSelectionIndicator(&indicatorStyle2);
```

## 监听Picker事件

Picker组件支持以下事件：

| 事件枚举 | 事件说明 | API起始版本 |
|---------|------|---------|
| NODE_PICKER_EVENT_ON_CHANGE | Picker组件中选择某项时触发的事件。 | 23 |
| NODE_PICKER_EVENT_ON_SCROLL_STOP | Picker组件中选择某项且滚动停止时触发的事件。 | 23 |

### 监听选择变化事件

通过注册`NODE_PICKER_EVENT_ON_CHANGE`事件，可以监听Picker组件的选择变化。事件回调中会返回选中项的索引值。

```cpp
static void OnPickerChange(ArkUI_NodeEvent* event)
{
    auto* componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
    if (componentEvent != nullptr) {
        int32_t selectedIndex = componentEvent->data[0].i32;
        // 处理选择变化
    }
}

// 注册事件
ArkUI_NodeEventItem eventItems[] = {
    {NODE_PICKER_EVENT_ON_CHANGE, OnPickerChange, nullptr}
};
nodeApi->registerNodeEvent(picker->GetHandle(), eventItems, 1);
```

### 监听滚动停止事件

通过注册`NODE_PICKER_EVENT_ON_SCROLL_STOP`事件，可以监听Picker组件滚动停止时的选择变化。与`NODE_PICKER_EVENT_ON_CHANGE`事件相比，该事件只在滚动停止时触发，适合需要在滚动完成后再处理选择的场景。

```cpp
static void OnPickerScrollStop(ArkUI_NodeEvent* event)
{
    auto* componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
    if (componentEvent != nullptr) {
        int32_t selectedIndex = componentEvent->data[0].i32;
        // 处理滚动停止后的选择
    }
}

// 注册事件
ArkUI_NodeEventItem eventItems[] = {
    {NODE_PICKER_EVENT_ON_SCROLL_STOP, OnPickerScrollStop, nullptr}
};
nodeApi->registerNodeEvent(picker->GetHandle(), eventItems, 1);
```

## 完整示例

### 动态修改Picker属性

以下示例演示了如何通过按钮动态修改Picker的循环滚动和触感反馈属性。

<!-- @[ContainerPickerCanLoopMakerCpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/native_type_sample/entry/src/main/cpp/ContainerPickerCanLoopMaker.cpp) -->

```cpp
// ---------- 生成数据 ----------
static std::vector<std::string> MakeData() { return {"1", "2", "3", "4", "5", "6", "7", "8", "9", "10"}; }

// ---------- 创建Picker选项 ----------
static ArkUI_NodeHandle CreatePickerOption(ArkUI_NativeNodeAPI_1 *api, const std::string &data)
{
    ArkUI_NodeHandle textNode = api->createNode(ARKUI_NODE_TEXT);
    if (textNode == nullptr) {
        return nullptr;
    }
    ArkUI_AttributeItem contentItem = {.string = data.c_str()};
    api->setAttribute(textNode, NODE_TEXT_CONTENT, &contentItem);
    ArkUI_NumberValue alignmentValue = {.i32 = ARKUI_TEXT_CONTENT_ALIGN_CENTER};
    ArkUI_AttributeItem alignmentItem = {&alignmentValue, sizeof(alignmentValue) / sizeof(ArkUI_NumberValue)};
    api->setAttribute(textNode, NODE_TEXT_CONTENT_ALIGN, &alignmentItem);
    return textNode;
}

// ---------- 创建按钮 ----------
static ArkUI_NodeHandle CreateButton(ArkUI_NativeNodeAPI_1 *api, const char *buttonText, int32_t eventId)
{
    ArkUI_NodeHandle button = api->createNode(ARKUI_NODE_BUTTON);
    if (button == nullptr) {
        return nullptr;
    }
    ArkUI_AttributeItem textItem = {.string = buttonText};
    api->setAttribute(button, NODE_BUTTON_LABEL, &textItem);
    ArkUI_NumberValue widthValue = {.f32 = K_BUTTON_WIDTH};
    ArkUI_AttributeItem widthItem = {&widthValue, sizeof(widthValue) / sizeof(ArkUI_NumberValue)};
    api->setAttribute(button, NODE_WIDTH, &widthItem);
    ArkUI_NumberValue heightValue = {.f32 = K_BUTTON_HEIGHT};
    ArkUI_AttributeItem heightItem = {&heightValue, sizeof(heightValue) / sizeof(ArkUI_NumberValue)};
    api->setAttribute(button, NODE_HEIGHT, &heightItem);
    ArkUI_NumberValue marginValue = {.f32 = K_BUTTON_MARGIN};
    ArkUI_AttributeItem marginItem = {&marginValue, sizeof(marginValue) / sizeof(ArkUI_NumberValue)};
    api->setAttribute(button, NODE_MARGIN, &marginItem);
    ArkUI_NumberValue enabledValue = {.i32 = true};
    ArkUI_AttributeItem enabledItem = {&enabledValue, sizeof(enabledValue) / sizeof(ArkUI_NumberValue)};
    api->setAttribute(button, NODE_ENABLED, &enabledItem);
    api->registerNodeEvent(button, NODE_ON_CLICK, eventId, nullptr);
    return button;
}

// ---------- 更新按钮文本 ----------
static void UpdateButtonText(ArkUI_NativeNodeAPI_1 *api, ArkUI_NodeHandle button, const char *newText)
{
    if (api && button) {
        ArkUI_AttributeItem textItem = {.string = newText};
        api->setAttribute(button, NODE_BUTTON_LABEL, &textItem);
    }
}

// ---------- 全局状态管理 ----------
struct PickerState {
    std::shared_ptr<ContainerPickerCanLoopMaker> picker;
    ArkUI_NodeHandle button1 = nullptr;
    ArkUI_NodeHandle button2 = nullptr;
    bool canLoopEnabled = K_CAN_LOOP;
    bool hapticFeedbackEnabled = K_HAPTIC_FEEDBACK;
    ArkUI_NativeNodeAPI_1 *api = nullptr;
};

static std::shared_ptr<PickerState> g_pickerState;

// ---------- 按钮事件回调函数 ----------
static void OnButton1Clicked(ArkUI_NodeEvent *event)
{
    if (!g_pickerState || !g_pickerState->picker || !g_pickerState->api) {
        return;
    }
    g_pickerState->canLoopEnabled = !g_pickerState->canLoopEnabled;
    g_pickerState->picker->SetCanLoop(g_pickerState->canLoopEnabled);
    std::string buttonText = g_pickerState->canLoopEnabled ? "canLoop: true" : "canLoop: false";
    UpdateButtonText(g_pickerState->api, g_pickerState->button1, buttonText.c_str());
    ArkUI_NumberValue colorValue;
    ArkUI_AttributeItem colorItem;
    if (g_pickerState->canLoopEnabled) {
        colorValue.u32 = K_BUTTON_BG_COLOR;
    } else {
        colorValue.u32 = K_BUTTON_DISABLED_COLOR;
    }
    colorItem = {&colorValue, 1};
    g_pickerState->api->setAttribute(g_pickerState->button1, NODE_BACKGROUND_COLOR, &colorItem);
}

static void OnButton2Clicked(ArkUI_NodeEvent *event)
{
    if (!g_pickerState || !g_pickerState->picker || !g_pickerState->api) {
        return;
    }
    g_pickerState->hapticFeedbackEnabled = !g_pickerState->hapticFeedbackEnabled;
    g_pickerState->picker->SetHapticFeedback(g_pickerState->hapticFeedbackEnabled);
    std::string buttonText = g_pickerState->hapticFeedbackEnabled ? "hapticFeedback: true" : "hapticFeedback: false";
    UpdateButtonText(g_pickerState->api, g_pickerState->button2, buttonText.c_str());
    ArkUI_NumberValue colorValue;
    ArkUI_AttributeItem colorItem;
    if (g_pickerState->hapticFeedbackEnabled) {
        colorValue.u32 = K_BUTTON_BG_COLOR;
    } else {
        colorValue.u32 = K_BUTTON_DISABLED_COLOR;
    }
    colorItem = {&colorValue, 1};
    g_pickerState->api->setAttribute(g_pickerState->button2, NODE_BACKGROUND_COLOR, &colorItem);
}

// ---------- 全局事件接收器 ----------
static void OnEventReceive(ArkUI_NodeEvent *event)
{
    if (event == nullptr) {
        return;
    }
    int32_t eventId = OH_ArkUI_NodeEvent_GetTargetId(event);
    if (eventId == K_BUTTON_1_EVENT_ID) {
        OnButton1Clicked(event);
    } else if (eventId == K_BUTTON_2_EVENT_ID) {
        OnButton2Clicked(event);
    }
}

// ---------- 配置 Picker 外观/交互 ----------
static void ConfigurePicker(const std::shared_ptr<ContainerPickerCanLoopMaker> &picker,
                            const std::shared_ptr<std::vector<std::string>> &data)
{
    if (!picker || !picker->GetHandle()) {
        return;
    }
    picker->SetPickerWidthPercent(K_PICKER_WIDTH_RATIO);
    picker->SetPickerHeightPercent(K_PICKER_HEIGHT_RATIO);
    picker->SetSelectedIndex(K_INITIAL_SELECTED_INDEX);
    picker->SetCanLoop(K_CAN_LOOP);
    picker->SetHapticFeedback(K_HAPTIC_FEEDBACK);
    picker->SetSelectionIndicatorBackground(K_INDICATOR_BG_COLOR, K_INDICATOR_CORNER_RADIUS);
    ArkUI_NativeNodeAPI_1 *api = picker->GetNodeAPI();
    if (api && data) {
        for (size_t i = 0; i < data->size(); ++i) {
            ArkUI_NodeHandle textNode = CreatePickerOption(api, (*data)[i]);
            if (textNode != nullptr) {
                api->addChild(picker->GetHandle(), textNode);
            }
        }
    }
}

// ---------- 整体构建 Picker ----------
static std::shared_ptr<ContainerPickerCanLoopMaker> BuildPicker()
{
    auto picker = std::make_shared<ContainerPickerCanLoopMaker>();
    auto data = std::make_shared<std::vector<std::string>>(MakeData());
    ConfigurePicker(picker, data);
    return picker;
}

// ---------- 主创建函数 ----------
ArkUI_NodeHandle ContainerPickerCanLoopMaker::CreateNativeNode()
{
    ArkUI_NativeNodeAPI_1 *api = nullptr;
    OH_ArkUI_GetModuleInterface(ARKUI_NATIVE_NODE, ArkUI_NativeNodeAPI_1, api);
    if (api == nullptr) {
        return nullptr;
    }
    ArkUI_NodeHandle rootContainer = api->createNode(ARKUI_NODE_COLUMN);
    if (rootContainer == nullptr) {
        return nullptr;
    }
    ArkUI_NumberValue widthValue = {.f32 = 1.0f};
    ArkUI_AttributeItem widthItem = {&widthValue, sizeof(widthValue) / sizeof(ArkUI_NumberValue)};
    api->setAttribute(rootContainer, NODE_WIDTH_PERCENT, &widthItem);
    ArkUI_NumberValue heightValue = {.f32 = 1.0f};
    ArkUI_AttributeItem heightItem = {&heightValue, sizeof(heightValue) / sizeof(ArkUI_NumberValue)};
    api->setAttribute(rootContainer, NODE_HEIGHT_PERCENT, &heightItem);
    std::shared_ptr<ContainerPickerCanLoopMaker> picker = BuildPicker();
    if (picker && picker->GetHandle() != nullptr) {
        api->addChild(rootContainer, picker->GetHandle());
    }
    ArkUI_NodeHandle buttonContainer = api->createNode(ARKUI_NODE_ROW);
    if (buttonContainer != nullptr) {
        ArkUI_NumberValue alignValue = {.i32 = ARKUI_FLEX_ALIGNMENT_CENTER};
        ArkUI_AttributeItem alignItem = {&alignValue, sizeof(alignValue) / sizeof(ArkUI_NumberValue)};
        api->setAttribute(buttonContainer, NODE_ROW_JUSTIFY_CONTENT, &alignItem);
        g_pickerState = std::make_shared<PickerState>();
        g_pickerState->picker = picker;
        g_pickerState->api = api;
        g_pickerState->button1 = CreateButton(api, "canLoop: true", K_BUTTON_1_EVENT_ID);
        if (g_pickerState->button1 != nullptr) {
            ArkUI_NumberValue colorValue = {.u32 = K_BUTTON_BG_COLOR};
            ArkUI_AttributeItem colorItem = {&colorValue, 1};
            api->setAttribute(g_pickerState->button1, NODE_BACKGROUND_COLOR, &colorItem);
            api->addChild(buttonContainer, g_pickerState->button1);
        }
        g_pickerState->button2 = CreateButton(api, "hapticFeedback: true", K_BUTTON_2_EVENT_ID);
        if (g_pickerState->button2 != nullptr) {
            ArkUI_NumberValue colorValue = {.u32 = K_BUTTON_BG_COLOR};
            ArkUI_AttributeItem colorItem = {&colorValue, 1};
            api->setAttribute(g_pickerState->button2, NODE_BACKGROUND_COLOR, &colorItem);
            api->addChild(buttonContainer, g_pickerState->button2);
        }
        api->addChild(rootContainer, buttonContainer);
    }
    api->registerNodeEventReceiver(&OnEventReceive);
    return rootContainer;
}
```

### 不同类型的Picker选项

Picker组件支持多种类型的选项，包括文本、图片和图文组合。

<!-- @[ContainerPickerTypesMakerCpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/native_type_sample/entry/src/main/cpp/ContainerPickerTypesMaker.cpp) -->

```cpp
// ---------- 全局状态 ----------
struct PickerTypesState {
    int32_t curTabIndex = 0;
    ArkUI_NodeHandle textPicker = nullptr;
    ArkUI_NodeHandle imagePicker = nullptr;
    ArkUI_NodeHandle hybridPicker = nullptr;
    ArkUI_NodeHandle tabs = nullptr;
    ArkUI_NativeNodeAPI_1 *api = nullptr;
};

static std::shared_ptr<PickerTypesState> g_pickerTypesState;

// ---------- 创建文本选项 ----------
static ArkUI_NodeHandle CreateTextOption(ArkUI_NativeNodeAPI_1 *api, const char *text)
{
    ArkUI_NodeHandle textNode = api->createNode(ARKUI_NODE_TEXT);
    if (textNode == nullptr) {
        return nullptr;
    }
    ArkUI_AttributeItem contentItem = {.string = text};
    api->setAttribute(textNode, NODE_TEXT_CONTENT, &contentItem);
    ArkUI_NumberValue alignmentValue = {.i32 = ARKUI_TEXT_CONTENT_ALIGN_CENTER};
    ArkUI_AttributeItem alignmentItem = {&alignmentValue, sizeof(alignmentValue) / sizeof(ArkUI_NumberValue)};
    api->setAttribute(textNode, NODE_TEXT_CONTENT_ALIGN, &alignmentItem);
    return textNode;
}

// ---------- 创建图片选项 ----------
static ArkUI_NodeHandle CreateImageOption(ArkUI_NativeNodeAPI_1 *api, const char *imagePath)
{
    ArkUI_NodeHandle imageNode = api->createNode(ARKUI_NODE_IMAGE);
    if (imageNode == nullptr) {
        return nullptr;
    }
    ArkUI_AttributeItem srcItem = {.string = imagePath};
    api->setAttribute(imageNode, NODE_IMAGE_SRC, &srcItem);
    return imageNode;
}

// ---------- 创建图文组合选项 ----------
static ArkUI_NodeHandle CreateHybridOption(ArkUI_NativeNodeAPI_1 *api, const char *symbolPath, const char *text)
{
    ArkUI_NodeHandle rowNode = api->createNode(ARKUI_NODE_ROW);
    if (rowNode == nullptr) {
        return nullptr;
    }
    ArkUI_NumberValue alignValue = {.i32 = ARKUI_FLEX_ALIGNMENT_CENTER};
    ArkUI_AttributeItem alignItem = {&alignValue, sizeof(alignValue) / sizeof(ArkUI_NumberValue)};
    api->setAttribute(rowNode, NODE_ROW_JUSTIFY_CONTENT, &alignItem);
    ArkUI_NodeHandle symbolNode = api->createNode(ARKUI_NODE_IMAGE);
    if (symbolNode != nullptr) {
        ArkUI_AttributeItem symbolSrcItem = {.string = symbolPath};
        api->setAttribute(symbolNode, NODE_IMAGE_SRC, &symbolSrcItem);
        ArkUI_NumberValue heightValue = {.f32 = 20.0f};
        ArkUI_AttributeItem heightItem = {&heightValue, sizeof(heightValue) / sizeof(ArkUI_NumberValue)};
        api->setAttribute(symbolNode, NODE_HEIGHT, &heightItem);
        ArkUI_NumberValue widthValue = {.f32 = 20.0f};
        ArkUI_AttributeItem widthItem = {&widthValue, sizeof(widthValue) / sizeof(ArkUI_NumberValue)};
        api->setAttribute(symbolNode, NODE_WIDTH, &widthItem);
        ArkUI_NumberValue marginValue = {.f32 = 5.0f};
        ArkUI_AttributeItem marginItem = {&marginValue, sizeof(marginValue) / sizeof(ArkUI_NumberValue)};
        api->setAttribute(symbolNode, NODE_MARGIN, &marginItem);
        api->addChild(rowNode, symbolNode);
    }
    ArkUI_NodeHandle textNode = CreateTextOption(api, text);
    if (textNode != nullptr) {
        ArkUI_NumberValue marginValue = {.f32 = 5.0f};
        ArkUI_AttributeItem marginItem = {&marginValue, sizeof(marginValue) / sizeof(ArkUI_NumberValue)};
        api->setAttribute(textNode, NODE_MARGIN, &marginItem);
        api->addChild(rowNode, textNode);
    }
    return rowNode;
}

// ---------- Picker事件回调函数 ----------
static void OnPickerChange(ArkUI_NodeEvent *event, const char *pickerType)
{
    if (!event) {
        return;
    }
    ArkUI_NodeComponentEvent *componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
    if (componentEvent == nullptr) {
        return;
    }
    int32_t selectedIndex = componentEvent->data[0].i32;
    printf("%s Picker item changed: index = %d\n", pickerType, selectedIndex);
}

static void OnPickerScrollStop(ArkUI_NodeEvent *event, const char *pickerType)
{
    if (!event) {
        return;
    }
    ArkUI_NodeComponentEvent *componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
    if (componentEvent == nullptr) {
        return;
    }
    int32_t selectedIndex = componentEvent->data[0].i32;
    printf("%s Picker scroll stopped: index = %d\n", pickerType, selectedIndex);
}

static void OnTextPickerChange(ArkUI_NodeEvent *event) { OnPickerChange(event, "文本"); }

static void OnTextPickerScrollStop(ArkUI_NodeEvent *event) { OnPickerScrollStop(event, "文本"); }

static void OnImagePickerChange(ArkUI_NodeEvent *event) { OnPickerChange(event, "图片"); }

static void OnImagePickerScrollStop(ArkUI_NodeEvent *event) { OnPickerScrollStop(event, "图片"); }

static void OnHybridPickerChange(ArkUI_NodeEvent *event) { OnPickerChange(event, "图文组合"); }

static void OnHybridPickerScrollStop(ArkUI_NodeEvent *event) { OnPickerScrollStop(event, "图文组合"); }

// ---------- 创建Picker ----------
static ArkUI_NodeHandle CreatePicker(ArkUI_NativeNodeAPI_1 *api, const std::vector<ArkUI_NodeHandle> &options,
                                     int32_t changeEventId, int32_t scrollStopEventId)
{
    ArkUI_NodeHandle picker = api->createNode(ARKUI_NODE_PICKER);
    if (picker == nullptr) {
        return nullptr;
    }
    ArkUI_NumberValue widthValue = {.f32 = K_PICKER_WIDTH};
    ArkUI_AttributeItem widthItem = {&widthValue, sizeof(widthValue) / sizeof(ArkUI_NumberValue)};
    api->setAttribute(picker, NODE_WIDTH, &widthItem);
    ArkUI_NumberValue canLoopValue = {.i32 = 1};
    ArkUI_AttributeItem canLoopItem = {&canLoopValue, sizeof(canLoopValue) / sizeof(ArkUI_NumberValue)};
    api->setAttribute(picker, NODE_PICKER_CAN_LOOP, &canLoopItem);
    ArkUI_NumberValue hapticValue = {.i32 = 0};
    ArkUI_AttributeItem hapticItem = {&hapticValue, sizeof(hapticValue) / sizeof(ArkUI_NumberValue)};
    api->setAttribute(picker, NODE_PICKER_ENABLE_HAPTIC_FEEDBACK, &hapticItem);
    ArkUI_PickerIndicatorStyle *indicatorStyle = OH_ArkUI_PickerIndicatorStyle_Create(ARKUI_PICKER_INDICATOR_DIVIDER);
    if (indicatorStyle != nullptr) {
        ArkUI_PickerIndicatorDivider divider = {
            .strokeWidth = 2.0f, .dividerColor = 0xFF0000FF, .startMargin = 20.0f, .endMargin = 20.0f};
        OH_ArkUI_PickerIndicatorStyle_ConfigureDivider(indicatorStyle, &divider);
        ArkUI_AttributeItem selectionIndicatorItem = {.object = indicatorStyle};
        api->setAttribute(picker, NODE_PICKER_SELECTION_INDICATOR, &selectionIndicatorItem);
    }
    for (const auto &option : options) {
        if (option != nullptr) {
            api->addChild(picker, option);
        }
    }
    if (changeEventId > 0) {
        api->registerNodeEvent(picker, NODE_PICKER_EVENT_ON_CHANGE, changeEventId, nullptr);
    }
    if (scrollStopEventId > 0) {
        api->registerNodeEvent(picker, NODE_PICKER_EVENT_ON_SCROLL_STOP, scrollStopEventId, nullptr);
    }
    return picker;
}

// ---------- 创建文本Picker ----------
static ArkUI_NodeHandle CreateTextPicker(ArkUI_NativeNodeAPI_1 *api)
{
    std::vector<ArkUI_NodeHandle> options;
    options.reserve(K_ITEM_COUNT);
    for (int i = 0; i < K_ITEM_COUNT; i++) {
        ArkUI_NodeHandle textOption = CreateTextOption(api, K_TEXT_ITEMS[i]);
        options.push_back(textOption);
    }
    return CreatePicker(api, options, K_TEXT_PICKER_CHANGE_ID, K_TEXT_PICKER_SCROLL_STOP_ID);
}

// ---------- 创建图片Picker ----------
static ArkUI_NodeHandle CreateImagePicker(ArkUI_NativeNodeAPI_1 *api)
{
    std::vector<ArkUI_NodeHandle> options;
    options.reserve(K_ITEM_COUNT);
    for (int i = 0; i < K_ITEM_COUNT; i++) {
        ArkUI_NodeHandle imageOption = CreateImageOption(api, K_IMAGE_PATHS[i]);
        options.push_back(imageOption);
    }
    return CreatePicker(api, options, K_IMAGE_PICKER_CHANGE_ID, K_IMAGE_PICKER_SCROLL_STOP_ID);
}

// ---------- 创建图文组合Picker ----------
static ArkUI_NodeHandle CreateHybridPicker(ArkUI_NativeNodeAPI_1 *api)
{
    std::vector<ArkUI_NodeHandle> options;
    options.reserve(K_ITEM_COUNT);
    for (int i = 0; i < K_ITEM_COUNT; i++) {
        ArkUI_NodeHandle hybridOption = CreateHybridOption(api, K_SYMBOL_PATHS[i], K_TEXT_ITEMS[i]);
        options.push_back(hybridOption);
    }
    return CreatePicker(api, options, K_HYBRID_PICKER_CHANGE_ID, K_HYBRID_PICKER_SCROLL_STOP_ID);
}

// ---------- 创建Column容器 ----------
static ArkUI_NodeHandle CreateColumnContainer(ArkUI_NativeNodeAPI_1 *api, ArkUI_NodeHandle picker)
{
    ArkUI_NodeHandle column = api->createNode(ARKUI_NODE_COLUMN);
    if (column == nullptr) {
        return nullptr;
    }
    ArkUI_NumberValue marginValue = {.f32 = K_COLUMN_MARGIN};
    ArkUI_AttributeItem marginItem = {&marginValue, sizeof(marginValue) / sizeof(ArkUI_NumberValue)};
    api->setAttribute(column, NODE_MARGIN, &marginItem);
    ArkUI_NumberValue alignValue = {.i32 = ARKUI_FLEX_ALIGNMENT_CENTER};
    ArkUI_AttributeItem alignItem = {&alignValue, sizeof(alignValue) / sizeof(ArkUI_NumberValue)};
    api->setAttribute(column, NODE_COLUMN_JUSTIFY_CONTENT, &alignItem);
    if (picker != nullptr) {
        api->addChild(column, picker);
    }
    return column;
}

// ---------- Tab切换事件回调 ----------
static void OnTabChange(ArkUI_NodeEvent *event)
{
    if (!g_pickerTypesState || !event) {
        return;
    }
    ArkUI_NodeComponentEvent *componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
    if (componentEvent == nullptr) {
        return;
    }
    int32_t selectedIndex = componentEvent->data[0].i32;
    g_pickerTypesState->curTabIndex = selectedIndex;
    printf("Tab changed to index: %d\n", selectedIndex);
}

// ---------- 全局事件接收器 ----------
static void OnEventReceive(ArkUI_NodeEvent *event)
{
    if (event == nullptr) {
        return;
    }
    int32_t eventId = OH_ArkUI_NodeEvent_GetTargetId(event);
    switch (eventId) {
        case K_TAB_CHANGE_EVENT_ID:
            OnTabChange(event);
            break;
        case K_TEXT_PICKER_CHANGE_ID:
            OnTextPickerChange(event);
            break;
        case K_TEXT_PICKER_SCROLL_STOP_ID:
            OnTextPickerScrollStop(event);
            break;
        case K_IMAGE_PICKER_CHANGE_ID:
            OnImagePickerChange(event);
            break;
        case K_IMAGE_PICKER_SCROLL_STOP_ID:
            OnImagePickerScrollStop(event);
            break;
        case K_HYBRID_PICKER_CHANGE_ID:
            OnHybridPickerChange(event);
            break;
        case K_HYBRID_PICKER_SCROLL_STOP_ID:
            OnHybridPickerScrollStop(event);
            break;
        default:
            break;
        }
}
```

### 多级联动Picker

以下示例演示了如何创建省市区三级联动的Picker，当省份或城市选择变化时，自动更新下级数据。

<!-- @[ContainerPickerRegionMakerCpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/native_type_sample/entry/src/main/cpp/ContainerPickerRegionMaker.cpp) -->

```cpp
// ---------- 全局状态 ----------
struct RegionPickerState {
    RegionData regionData;
    int32_t provinceIndex = 0;
    int32_t cityIndex = 0;
    int32_t countyIndex = 0;
    std::vector<std::string> provinces;
    std::vector<std::string> cities;
    std::vector<std::string> counties;
    ArkUI_NodeHandle provincePicker = nullptr;
    ArkUI_NodeHandle cityPicker = nullptr;
    ArkUI_NodeHandle countyPicker = nullptr;
    ArkUI_NativeNodeAPI_1 *api = nullptr;
};

static std::shared_ptr<RegionPickerState> g_regionState;

// ---------- 初始化地区数据 ----------
static RegionData InitRegionData()
{
    RegionData data;
    std::unordered_map<std::string, std::vector<std::string>> liaoningCities;
    liaoningCities["沈阳市"] = {"沈河区", "和平区", "浑南区"};
    liaoningCities["大连市"] = {"中山区", "金州区", "长海县"};
    data.data["辽宁省"] = liaoningCities;
    std::unordered_map<std::string, std::vector<std::string>> jilinCities;
    jilinCities["长春市"] = {"南关区", "宽城区", "朝阳区"};
    jilinCities["四平市"] = {"铁西区", "铁东区", "梨树县"};
    data.data["吉林省"] = jilinCities;
    std::unordered_map<std::string, std::vector<std::string>> heilongjiangCities;
    heilongjiangCities["哈尔滨市"] = {"道里区", "道外区", "南岗区"};
    heilongjiangCities["牡丹江市"] = {"东安区", "西安区", "爱民区"};
    data.data["黑龙江省"] = heilongjiangCities;
    return data;
}

// ---------- 创建Picker选项 ----------
static ArkUI_NodeHandle CreatePickerOption(ArkUI_NativeNodeAPI_1 *api, const std::string &text)
{
    ArkUI_NodeHandle textNode = api->createNode(ARKUI_NODE_TEXT);
    if (textNode == nullptr) {
        return nullptr;
    }
    ArkUI_AttributeItem contentItem = {.string = text.c_str()};
    api->setAttribute(textNode, NODE_TEXT_CONTENT, &contentItem);
    ArkUI_NumberValue alignmentValue = {.i32 = ARKUI_TEXT_CONTENT_ALIGN_CENTER};
    ArkUI_AttributeItem alignmentItem = {&alignmentValue, sizeof(alignmentValue) / sizeof(ArkUI_NumberValue)};
    api->setAttribute(textNode, NODE_TEXT_CONTENT_ALIGN, &alignmentItem);
    return textNode;
}

// ---------- 创建Picker ----------
static ArkUI_NodeHandle CreatePicker(ArkUI_NativeNodeAPI_1 *api, const std::vector<std::string> &options,
                                     uint32_t selectedIndex, int32_t changeEventId, int32_t scrollStopEventId)
{
    ArkUI_NodeHandle picker = api->createNode(ARKUI_NODE_PICKER);
    if (picker == nullptr) {
        return nullptr;
    }
    ArkUI_NumberValue widthValue = {.f32 = K_PICKER_WIDTH_RATIO};
    ArkUI_AttributeItem widthItem = {&widthValue, sizeof(widthValue) / sizeof(ArkUI_NumberValue)};
    api->setAttribute(picker, NODE_WIDTH_PERCENT, &widthItem);
    ArkUI_NumberValue selectedValue = {.u32 = selectedIndex};
    ArkUI_AttributeItem selectedItem = {&selectedValue, sizeof(selectedValue) / sizeof(ArkUI_NumberValue)};
    api->setAttribute(picker, NODE_PICKER_OPTION_SELECTED_INDEX, &selectedItem);
    ArkUI_NumberValue canLoopValue = {.i32 = K_CAN_LOOP ? 1 : 0};
    ArkUI_AttributeItem canLoopItem = {&canLoopValue, sizeof(canLoopValue) / sizeof(ArkUI_NumberValue)};
    api->setAttribute(picker, NODE_PICKER_CAN_LOOP, &canLoopItem);
    ArkUI_NumberValue hapticValue = {.i32 = K_HAPTIC_FEEDBACK ? 1 : 0};
    ArkUI_AttributeItem hapticItem = {&hapticValue, sizeof(hapticValue) / sizeof(ArkUI_NumberValue)};
    api->setAttribute(picker, NODE_PICKER_ENABLE_HAPTIC_FEEDBACK, &hapticItem);
    ArkUI_PickerIndicatorStyle *indicatorStyle = OH_ArkUI_PickerIndicatorStyle_Create(ARKUI_PICKER_INDICATOR_DIVIDER);
    if (indicatorStyle != nullptr) {
        ArkUI_PickerIndicatorDivider divider = {
            .strokeWidth = 2.0f, .dividerColor = K_DIVIDER_COLOR, .startMargin = 20.0f, .endMargin = 20.0f};
        OH_ArkUI_PickerIndicatorStyle_ConfigureDivider(indicatorStyle, &divider);
        ArkUI_AttributeItem selectionIndicatorItem = {.object = indicatorStyle};
        api->setAttribute(picker, NODE_PICKER_SELECTION_INDICATOR, &selectionIndicatorItem);
    }
    for (const auto &option : options) {
        ArkUI_NodeHandle textNode = CreatePickerOption(api, option);
        if (textNode != nullptr) {
            api->addChild(picker, textNode);
        }
    }
    if (changeEventId > 0) {
        api->registerNodeEvent(picker, NODE_PICKER_EVENT_ON_CHANGE, changeEventId, nullptr);
    }
    if (scrollStopEventId > 0) {
        api->registerNodeEvent(picker, NODE_PICKER_EVENT_ON_SCROLL_STOP, scrollStopEventId, nullptr);
    }
    return picker;
}

// ---------- 刷新县区数据 ----------
static void RefreshCounties()
{
    if (!g_regionState || !g_regionState->api) {
        return;
    }
    if (g_regionState->provinceIndex < 0 ||
        g_regionState->provinceIndex >= static_cast<int32_t>(g_regionState->provinces.size()) ||
        g_regionState->cityIndex < 0 ||
        g_regionState->cityIndex >= static_cast<int32_t>(g_regionState->cities.size())) {
        g_regionState->counties.clear();
        return;
    }
    std::string currentProvince = g_regionState->provinces[g_regionState->provinceIndex];
    std::string currentCity = g_regionState->cities[g_regionState->cityIndex];
    auto provinceIt = g_regionState->regionData.data.find(currentProvince);
    if (provinceIt == g_regionState->regionData.data.end()) {
        g_regionState->counties.clear();
        return;
    }
    auto cityIt = provinceIt->second.find(currentCity);
    if (cityIt == provinceIt->second.end()) {
        g_regionState->counties.clear();
        return;
    }
    g_regionState->counties = cityIt->second;
    g_regionState->countyIndex = 0;
    if (g_regionState->countyPicker && g_regionState->api) {
        ArkUI_NodeHandle child = g_regionState->api->getFirstChild(g_regionState->countyPicker);
        while (child != nullptr) {
            ArkUI_NodeHandle next = g_regionState->api->getNextSibling(child);
            g_regionState->api->removeChild(g_regionState->countyPicker, child);
            child = next;
        }
        for (const auto &county : g_regionState->counties) {
            ArkUI_NodeHandle textNode = CreatePickerOption(g_regionState->api, county);
            if (textNode != nullptr) {
                g_regionState->api->addChild(g_regionState->countyPicker, textNode);
            }
        }
        ArkUI_NumberValue selectedValue = {.u32 = 0};
        ArkUI_AttributeItem selectedItem = {&selectedValue, sizeof(selectedValue) / sizeof(ArkUI_NumberValue)};
        g_regionState->api->setAttribute(g_regionState->countyPicker, NODE_PICKER_OPTION_SELECTED_INDEX, &selectedItem);
    }
}

// ---------- 刷新城市数据 ----------
static void RefreshCities()
{
    if (!g_regionState || !g_regionState->api) {
        return;
    }
    if (g_regionState->provinceIndex < 0 ||
        g_regionState->provinceIndex >= static_cast<int32_t>(g_regionState->provinces.size())) {
        return;
    }
    std::string currentProvince = g_regionState->provinces[g_regionState->provinceIndex];
    auto provinceIt = g_regionState->regionData.data.find(currentProvince);
    if (provinceIt == g_regionState->regionData.data.end()) {
        g_regionState->cities.clear();
        return;
    }
    g_regionState->cities.clear();
    for (const auto &cityPair : provinceIt->second) {
        g_regionState->cities.push_back(cityPair.first);
    }
    g_regionState->cityIndex = 0;
    if (g_regionState->cityPicker && g_regionState->api) {
        ArkUI_NodeHandle child = g_regionState->api->getFirstChild(g_regionState->cityPicker);
        while (child != nullptr) {
            ArkUI_NodeHandle next = g_regionState->api->getNextSibling(child);
            g_regionState->api->removeChild(g_regionState->cityPicker, child);
            child = next;
        }
        for (const auto &city : g_regionState->cities) {
            ArkUI_NodeHandle textNode = CreatePickerOption(g_regionState->api, city);
            if (textNode != nullptr) {
                g_regionState->api->addChild(g_regionState->cityPicker, textNode);
            }
        }
        ArkUI_NumberValue selectedValue = {.u32 = 0};
        ArkUI_AttributeItem selectedItem = {&selectedValue, sizeof(selectedValue) / sizeof(ArkUI_NumberValue)};
        g_regionState->api->setAttribute(g_regionState->cityPicker, NODE_PICKER_OPTION_SELECTED_INDEX, &selectedItem);
    }
    RefreshCounties();
}

// ---------- 事件回调函数 ----------
static void OnProvinceChange(ArkUI_NodeEvent *event)
{
    if (!g_regionState || !event) {
        return;
    }
    ArkUI_NodeComponentEvent *componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
    if (componentEvent == nullptr) {
        return;
    }
    int32_t selectedIndex = componentEvent->data[0].i32;
    g_regionState->provinceIndex = selectedIndex;
    RefreshCities();
}

static void OnProvinceScrollStop(ArkUI_NodeEvent *event)
{
    if (!g_regionState || !event) {
        return;
    }
    ArkUI_NodeComponentEvent *componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
    if (componentEvent == nullptr) {
        return;
    }
    int32_t selectedIndex = componentEvent->data[0].i32;
    g_regionState->provinceIndex = selectedIndex;
}

static void OnCityChange(ArkUI_NodeEvent *event)
{
    if (!g_regionState || !event) {
        return;
    }
    ArkUI_NodeComponentEvent *componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
    if (componentEvent == nullptr) {
        return;
    }
    int32_t selectedIndex = componentEvent->data[0].i32;
    g_regionState->cityIndex = selectedIndex;
    RefreshCounties();
}

static void OnCityScrollStop(ArkUI_NodeEvent *event)
{
    if (!g_regionState || !event) {
        return;
    }
    ArkUI_NodeComponentEvent *componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
    if (componentEvent == nullptr) {
        return;
    }
    int32_t selectedIndex = componentEvent->data[0].i32;
    g_regionState->cityIndex = selectedIndex;
}

static void OnCountyChange(ArkUI_NodeEvent *event)
{
    if (!g_regionState || !event) {
        return;
    }
    ArkUI_NodeComponentEvent *componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
    if (componentEvent == nullptr) {
        return;
    }
    int32_t selectedIndex = componentEvent->data[0].i32;
    g_regionState->countyIndex = selectedIndex;
}

static void OnCountyScrollStop(ArkUI_NodeEvent *event)
{
    if (!g_regionState || !event) {
        return;
    }
    ArkUI_NodeComponentEvent *componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
    if (componentEvent == nullptr) {
        return;
    }
    int32_t selectedIndex = componentEvent->data[0].i32;
    g_regionState->countyIndex = selectedIndex;
}

// ---------- 全局事件接收器 ----------
static void OnEventReceive(ArkUI_NodeEvent *event)
{
    if (event == nullptr) {
        return;
    }
    int32_t eventId = OH_ArkUI_NodeEvent_GetTargetId(event);
    switch (eventId) {
        case K_PROVINCE_CHANGE_ID:
            OnProvinceChange(event);
            break;
        case K_PROVINCE_SCROLL_STOP_ID:
            OnProvinceScrollStop(event);
            break;
        case K_CITY_CHANGE_ID:
            OnCityChange(event);
            break;
        case K_CITY_SCROLL_STOP_ID:
            OnCityScrollStop(event);
            break;
        case K_COUNTY_CHANGE_ID:
            OnCountyChange(event);
            break;
        case K_COUNTY_SCROLL_STOP_ID:
            OnCountyScrollStop(event);
            break;
        default:
            break;
    }
}

// ---------- 创建地区选择器 ----------
static ArkUI_NodeHandle CreateRegionPicker(ArkUI_NativeNodeAPI_1 *api)
{
    if (!api) {
        return nullptr;
    }
    g_regionState = std::make_shared<RegionPickerState>();
    g_regionState->api = api;
    g_regionState->regionData = InitRegionData();
    for (const auto &provincePair : g_regionState->regionData.data) {
        g_regionState->provinces.push_back(provincePair.first);
    }
    RefreshCities();
    ArkUI_NodeHandle rootContainer = api->createNode(ARKUI_NODE_COLUMN);
    if (!rootContainer) {
        return nullptr;
    }
    ArkUI_NumberValue rootWidthValue = {.f32 = 1.0f};
    ArkUI_AttributeItem rootWidthItem = {&rootWidthValue, 1};
    api->setAttribute(rootContainer, NODE_WIDTH_PERCENT, &rootWidthItem);
    ArkUI_NumberValue rootHeightValue = {.f32 = 1.0f};
    ArkUI_AttributeItem rootHeightItem = {&rootHeightValue, 1};
    api->setAttribute(rootContainer, NODE_HEIGHT_PERCENT, &rootHeightItem);
    ArkUI_NodeHandle rowContainer = api->createNode(ARKUI_NODE_ROW);
    if (!rowContainer) {
        api->disposeNode(rootContainer);
        return nullptr;
    }
    ArkUI_NumberValue rowWidthValue = {.f32 = K_ROW_WIDTH_RATIO};
    ArkUI_AttributeItem rowWidthItem = {&rowWidthValue, 1};
    api->setAttribute(rowContainer, NODE_WIDTH_PERCENT, &rowWidthItem);
    ArkUI_NumberValue justifyValue = {.i32 = ARKUI_FLEX_ALIGNMENT_CENTER};
    ArkUI_AttributeItem justifyItem = {&justifyValue, 1};
    api->setAttribute(rowContainer, NODE_ROW_JUSTIFY_CONTENT, &justifyItem);
    g_regionState->provincePicker =
        CreatePicker(api, g_regionState->provinces, 0, K_PROVINCE_CHANGE_ID, K_PROVINCE_SCROLL_STOP_ID);
    g_regionState->cityPicker = CreatePicker(api, g_regionState->cities, 0, K_CITY_CHANGE_ID, K_CITY_SCROLL_STOP_ID);
    g_regionState->countyPicker =
        CreatePicker(api, g_regionState->counties, 0, K_COUNTY_CHANGE_ID, K_COUNTY_SCROLL_STOP_ID);
    if (g_regionState->provincePicker) {
        api->addChild(rowContainer, g_regionState->provincePicker);
    }
    if (g_regionState->cityPicker) {
        api->addChild(rowContainer, g_regionState->cityPicker);
    }
    if (g_regionState->countyPicker) {
        api->addChild(rowContainer, g_regionState->countyPicker);
    }
    api->addChild(rootContainer, rowContainer);
    return rootContainer;
}
```

### 时间选择器

以下示例演示了如何使用多个Picker创建时间选择器，包括小时、分钟、秒和AM/PM选择。

<!-- @[ContainerPickerTimeMakerCpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/native_type_sample/entry/src/main/cpp/ContainerPickerTimeMaker.cpp) -->

```cpp
// ---------- 全局状态管理 ----------
struct TimePickerState {
    // 时间选择器组件
    std::shared_ptr<ContainerPickerTimeMaker> hourPicker;
    std::shared_ptr<ContainerPickerTimeMaker> minutePicker;
    std::shared_ptr<ContainerPickerTimeMaker> secondPicker;
    std::shared_ptr<ContainerPickerTimeMaker> amPmPicker;
    // 当前选中索引
    int32_t hourIndex = 0;
    int32_t minuteIndex = 0;
    int32_t secondIndex = 0;
    int32_t amPmIndex = AM_INDEX;
    // 配置选项
    bool showSecond = INITIAL_SHOW_SECOND_STATE;
    bool useMilitary = INITIAL_USE_MILITARY_STATE;
    bool zeroPrefix = INITIAL_ZERO_PREFIX_STATE;
    bool canLoop = INITIAL_LOOP_STATE;
    // 数据数组
    std::vector<std::string> amPmArray;
    std::vector<std::string> hourArray;
    std::vector<std::string> minuteArray;
    std::vector<std::string> secondArray;
    // UI节点句柄
    ArkUI_NodeHandle statusLabel = nullptr;
    ArkUI_NodeHandle toggleLoop = nullptr;
    ArkUI_NodeHandle toggleSecond = nullptr;
    ArkUI_NodeHandle toggleMilitary = nullptr;
    ArkUI_NodeHandle toggleDigits = nullptr;
    ArkUI_NodeHandle pickersRow = nullptr;
    ArkUI_NodeHandle controlPanel = nullptr;
    ArkUI_NativeNodeAPI_1 *api = nullptr;
};

static std::shared_ptr<TimePickerState> g_timePickerState;

// ---------- 辅助函数 ----------
static std::string FormatTime(int32_t number, bool zeroPrefix)
{
    if (zeroPrefix && number < SINGLE_DIGIT_THRESHOLD) {
        return "0" + std::to_string(number);
    }
    return std::to_string(number);
}

static void RegenerateHourArray()
{
    if (!g_timePickerState) {
        return;
    }
    g_timePickerState->hourArray.clear();
    if (g_timePickerState->useMilitary) {
        // 24小时制: 00-23
        for (int i = 0; i < HOURS_IN_24_HOUR_FORMAT; i++) {
            g_timePickerState->hourArray.push_back(FormatTime(i, g_timePickerState->zeroPrefix));
        }
    } else {
        // 12小时制: 12, 01-11
        if (g_timePickerState->zeroPrefix) {
            g_timePickerState->hourArray.push_back(std::to_string(FIRST_HOUR_IN_12_HOUR_FORMAT));
            for (int i = 1; i <= LAST_HOUR_IN_12_HOUR_FORMAT; i++) {
                g_timePickerState->hourArray.push_back(FormatTime(i, true));
            }
        } else {
            g_timePickerState->hourArray.push_back(std::to_string(FIRST_HOUR_IN_12_HOUR_FORMAT));
            for (int i = 1; i <= LAST_HOUR_IN_12_HOUR_FORMAT; i++) {
                g_timePickerState->hourArray.push_back(std::to_string(i));
            }
        }
    }
}

static void RegenerateMinuteSecondArray()
{
    if (!g_timePickerState) {
        return;
    }
    g_timePickerState->minuteArray.clear();
    g_timePickerState->secondArray.clear();
    for (int i = 0; i < MINUTES_IN_HOUR; i++) {
        std::string formatted = FormatTime(i, g_timePickerState->zeroPrefix);
        g_timePickerState->minuteArray.push_back(formatted);
        g_timePickerState->secondArray.push_back(formatted);
    }
}

static void LogMinuteSecondArray()
{
    if (!g_timePickerState) {
        return;
    }
    std::cout << "Regenerated minute/second array (" << (g_timePickerState->zeroPrefix ? "2-digit" : "1-digit")
              << "): ";
    for (int i = 0; i < LOG_DISPLAY_ITEM_COUNT && i < static_cast<int>(g_timePickerState->minuteArray.size()); i++) {
        std::cout << g_timePickerState->minuteArray[i] << " ";
    }
    if (g_timePickerState->minuteArray.size() > LOG_DISPLAY_ITEM_COUNT) {
        std::cout << "... ";
    }
    std::cout << std::endl;
}

static ArkUI_NodeHandle CreateTextOption(const std::string &text)
{
    if (!g_timePickerState || !g_timePickerState->api) {
        return nullptr;
    }
    ArkUI_NodeHandle textNode = g_timePickerState->api->createNode(ARKUI_NODE_TEXT);
    if (!textNode) {
        return nullptr;
    }
    ArkUI_AttributeItem contentItem = {.string = text.c_str()};
    g_timePickerState->api->setAttribute(textNode, NODE_TEXT_CONTENT, &contentItem);
    return textNode;
}

static void RemoveAllChildren(ArkUI_NodeHandle parent)
{
    if (!parent || !g_timePickerState || !g_timePickerState->api) {
        return;
    }
    auto api = g_timePickerState->api;
    uint32_t childCount = api->getTotalChildCount(parent);
    for (int32_t i = childCount - 1; i >= 0; i--) {
        ArkUI_NodeHandle child = api->getChildAt(parent, i);
        if (child) {
            api->removeChild(parent, child);
            api->disposeNode(child);
        }
    }
}

static void UpdatePickerOptions(ArkUI_NodeHandle pickerHandle, const std::vector<std::string> &newOptions)
{
    if (!pickerHandle || !g_timePickerState || !g_timePickerState->api) {
        return;
    }
    auto api = g_timePickerState->api;
    RemoveAllChildren(pickerHandle);
    for (const auto &option : newOptions) {
        ArkUI_NodeHandle textNode = CreateTextOption(option);
        if (textNode) {
            api->addChild(pickerHandle, textNode);
        }
    }
}

static void ConvertHourIndexForTimeFormat()
{
    if (!g_timePickerState) {
        return;
    }
    if (g_timePickerState->useMilitary) {
        // 12小时制转24小时制
        if (g_timePickerState->amPmIndex == PM_INDEX) {
            int32_t oldHourIndex = g_timePickerState->hourIndex;
            g_timePickerState->hourIndex += AM_PM_SWITCH_HOUR;
            if (g_timePickerState->hourIndex >= HOURS_IN_24_HOUR_FORMAT) {
                g_timePickerState->hourIndex = 0;
            }
        }
    } else {
        // 24小时制转12小时制
        int32_t oldHourIndex = g_timePickerState->hourIndex;
        if (oldHourIndex >= AM_PM_SWITCH_HOUR) {
            g_timePickerState->amPmIndex = PM_INDEX;
            g_timePickerState->hourIndex = oldHourIndex - AM_PM_SWITCH_HOUR;
        } else {
            g_timePickerState->amPmIndex = AM_INDEX;
            g_timePickerState->hourIndex = (oldHourIndex == 0) ? 0 : oldHourIndex;
        }
    }
}

static void AdjustIndicesToValidRange()
{
    if (!g_timePickerState) {
        return;
    }
    if (g_timePickerState->hourIndex >= static_cast<int32_t>(g_timePickerState->hourArray.size())) {
        g_timePickerState->hourIndex = 0;
    }
    if (g_timePickerState->minuteIndex >= static_cast<int32_t>(g_timePickerState->minuteArray.size())) {
        g_timePickerState->minuteIndex = 0;
    }
    if (g_timePickerState->secondIndex >= static_cast<int32_t>(g_timePickerState->secondArray.size())) {
        g_timePickerState->secondIndex = 0;
    }
}

static void SetPickerIndicatorStyle(ArkUI_NodeHandle pickerHandle)
{
    if (!pickerHandle || !g_timePickerState || !g_timePickerState->api) {
        return;
    }
    auto api = g_timePickerState->api;
    ArkUI_PickerIndicatorStyle *indicatorStyle =
        OH_ArkUI_PickerIndicatorStyle_Create(ARKUI_PICKER_INDICATOR_BACKGROUND);
    if (indicatorStyle != nullptr) {
        ArkUI_PickerIndicatorBackground background = {.backgroundColor = INDICATOR_BACKGROUND_COLOR,
                                                      .topLeftRadius = PICKER_CORNER_RADIUS,
                                                      .topRightRadius = PICKER_CORNER_RADIUS,
                                                      .bottomLeftRadius = PICKER_CORNER_RADIUS,
                                                      .bottomRightRadius = PICKER_CORNER_RADIUS};
        OH_ArkUI_PickerIndicatorStyle_ConfigureBackground(indicatorStyle, &background);
        ArkUI_AttributeItem selectionIndicatorItem = {.object = indicatorStyle};
        api->setAttribute(pickerHandle, NODE_PICKER_SELECTION_INDICATOR, &selectionIndicatorItem);
    }
}

static bool CreateTimePicker(std::shared_ptr<ContainerPickerTimeMaker> &picker, const std::vector<std::string> &data,
                             int32_t selectedIndex, int32_t changeEventId, int32_t scrollStopEventId)
{
    if (!g_timePickerState || !g_timePickerState->pickersRow) {
        return false;
    }
    picker = std::make_shared<ContainerPickerTimeMaker>();
    if (!picker || !picker->GetHandle()) {
        return false;
    }
    ArkUI_NodeHandle pickerHandle = picker->GetHandle();
    auto api = g_timePickerState->api;
    picker->SetPickerWidthPercent(PICKER_WIDTH_PERCENT);
    picker->SetPickerHeightPercent(PICKER_HEIGHT_RATIO);
    picker->SetSelectedIndex(static_cast<uint32_t>(selectedIndex));
    picker->SetCanLoop(g_timePickerState->canLoop);
    picker->SetHapticFeedback(true);
    SetPickerIndicatorStyle(pickerHandle);
    UpdatePickerOptions(pickerHandle, data);
    if (pickerHandle) {
        api->registerNodeEvent(pickerHandle, NODE_PICKER_EVENT_ON_CHANGE, changeEventId, nullptr);
        api->registerNodeEvent(pickerHandle, NODE_PICKER_EVENT_ON_SCROLL_STOP, scrollStopEventId, nullptr);
    }
    api->addChild(g_timePickerState->pickersRow, pickerHandle);
    return true;
}

static void ClearExistingPickers()
{
    if (!g_timePickerState) {
        return;
    }
    if (g_timePickerState->pickersRow && g_timePickerState->api) {
        RemoveAllChildren(g_timePickerState->pickersRow);
    }
    g_timePickerState->hourPicker.reset();
    g_timePickerState->minutePicker.reset();
    g_timePickerState->secondPicker.reset();
    g_timePickerState->amPmPicker.reset();
}

static void PrepareTimeData()
{
    if (!g_timePickerState) {
        return;
    }
    RegenerateHourArray();
    RegenerateMinuteSecondArray();
    ConvertHourIndexForTimeFormat();
    AdjustIndicesToValidRange();
    g_timePickerState->amPmArray = {"AM", "PM"};
}

static void CreateAmPmPickerIfNeeded()
{
    if (!g_timePickerState || g_timePickerState->useMilitary) {
        return;
    }
    CreateTimePicker(g_timePickerState->amPmPicker, g_timePickerState->amPmArray, g_timePickerState->amPmIndex,
                     EVENT_AMPM_CHANGE, EVENT_AMPM_SCROLL_STOP);
}

static void CreateHourPicker()
{
    if (!g_timePickerState) {
        return;
    }
    CreateTimePicker(g_timePickerState->hourPicker, g_timePickerState->hourArray, g_timePickerState->hourIndex,
                     EVENT_HOUR_CHANGE, EVENT_HOUR_SCROLL_STOP);
}

static void CreateMinutePicker()
{
    if (!g_timePickerState) {
        return;
    }
    CreateTimePicker(g_timePickerState->minutePicker, g_timePickerState->minuteArray, g_timePickerState->minuteIndex,
                     EVENT_MINUTE_CHANGE, EVENT_MINUTE_SCROLL_STOP);
}

static void CreateSecondPickerIfNeeded()
{
    if (!g_timePickerState || !g_timePickerState->showSecond) {
        return;
    }
    CreateTimePicker(g_timePickerState->secondPicker, g_timePickerState->secondArray, g_timePickerState->secondIndex,
                     EVENT_SECOND_CHANGE, EVENT_SECOND_SCROLL_STOP);
}

static void CreateAllPickers()
{
    CreateAmPmPickerIfNeeded();
    CreateHourPicker();
    CreateMinutePicker();
    CreateSecondPickerIfNeeded();
}

// ---------- 重新创建时间选择器布局 ----------
static void RecreateTimePickerLayout()
{
    if (!g_timePickerState || !g_timePickerState->api || !g_timePickerState->pickersRow) {
        return;
    }
    ClearExistingPickers();
    PrepareTimeData();
    CreateAllPickers();
}

static ArkUI_NodeHandle CreateToggleButton(const char *label, bool initialState, int32_t eventId)
{
    if (!g_timePickerState || !g_timePickerState->api) {
        return nullptr;
    }
    auto api = g_timePickerState->api;
    ArkUI_NodeHandle row = api->createNode(ARKUI_NODE_ROW);
    if (!row) {
        return nullptr;
    }
    ArkUI_NumberValue justifyValue = {.i32 = ARKUI_FLEX_ALIGNMENT_SPACE_BETWEEN};
    ArkUI_AttributeItem justifyItem = {&justifyValue, 1};
    api->setAttribute(row, NODE_ROW_JUSTIFY_CONTENT, &justifyItem);
    ArkUI_NumberValue alignValue = {.i32 = ARKUI_FLEX_ALIGNMENT_CENTER};
    ArkUI_AttributeItem alignItem = {&alignValue, 1};
    api->setAttribute(row, NODE_ROW_ALIGN_ITEMS, &alignItem);
    ArkUI_NumberValue widthValue = {.f32 = 200.0f};
    ArkUI_AttributeItem widthItem = {&widthValue, 1};
    api->setAttribute(row, NODE_WIDTH, &widthItem);
    ArkUI_NumberValue marginValue = {.f32 = 5.0f};
    ArkUI_AttributeItem marginItem = {&marginValue, 1};
    api->setAttribute(row, NODE_MARGIN, &marginItem);
    ArkUI_NodeHandle toggle = api->createNode(ARKUI_NODE_TOGGLE);
    if (!toggle) {
        api->disposeNode(row);
        return nullptr;
    }
    ArkUI_NumberValue stateValue = {.i32 = initialState ? 1 : 0};
    ArkUI_AttributeItem stateItem = {&stateValue, 1};
    api->setAttribute(toggle, NODE_TOGGLE_VALUE, &stateItem);
    api->registerNodeEvent(toggle, NODE_ON_CLICK, eventId, nullptr);
    ArkUI_NodeHandle text = api->createNode(ARKUI_NODE_TEXT);
    if (text) {
        ArkUI_AttributeItem textItem = {.string = label};
        api->setAttribute(text, NODE_TEXT_CONTENT, &textItem);
        ArkUI_NumberValue fontSizeValue = {.f32 = 20.0f};
        ArkUI_AttributeItem fontSizeItem = {&fontSizeValue, 1};
        api->setAttribute(text, NODE_FONT_SIZE, &fontSizeItem);
    }
    api->addChild(row, toggle);
    if (text) {
        api->addChild(row, text);
    }
    return row;
}

static void UpdateToggleState(ArkUI_NodeHandle toggleRow, bool isOn)
{
    if (!toggleRow || !g_timePickerState || !g_timePickerState->api) {
        return;
    }
    auto api = g_timePickerState->api;
    ArkUI_NodeHandle toggle = api->getFirstChild(toggleRow);
    if (toggle) {
        ArkUI_NumberValue stateValue = {.i32 = isOn ? 1 : 0};
        ArkUI_AttributeItem stateItem = {&stateValue, 1};
        api->setAttribute(toggle, NODE_TOGGLE_VALUE, &stateItem);
    }
}

static void UpdateStatusLabel()
{
    if (!g_timePickerState || !g_timePickerState->statusLabel || !g_timePickerState->api) {
        return;
    }
    std::string currentTime = "selected time: ";
    if (!g_timePickerState->useMilitary && !g_timePickerState->amPmArray.empty()) {
        currentTime += g_timePickerState->amPmArray[g_timePickerState->amPmIndex] + " ";
    }
    if (!g_timePickerState->hourArray.empty() &&
        g_timePickerState->hourIndex < static_cast<int32_t>(g_timePickerState->hourArray.size())) {
        currentTime += g_timePickerState->hourArray[g_timePickerState->hourIndex] + ":";
    } else {
        currentTime += "00:";
    }
    if (!g_timePickerState->minuteArray.empty() &&
        g_timePickerState->minuteIndex < static_cast<int32_t>(g_timePickerState->minuteArray.size())) {
        currentTime += g_timePickerState->minuteArray[g_timePickerState->minuteIndex];
    } else {
        currentTime += "00";
    }
    if (g_timePickerState->showSecond && !g_timePickerState->secondArray.empty() &&
        g_timePickerState->secondIndex < static_cast<int32_t>(g_timePickerState->secondArray.size())) {
        currentTime += ":" + g_timePickerState->secondArray[g_timePickerState->secondIndex];
    }
    ArkUI_AttributeItem contentItem = {.string = currentTime.c_str()};
    g_timePickerState->api->setAttribute(g_timePickerState->statusLabel, NODE_TEXT_CONTENT, &contentItem);
}

static void OnHourChange(int32_t selectedIndex)
{
    if (!g_timePickerState) {
        return;
    }
    g_timePickerState->hourIndex = selectedIndex;
    UpdateStatusLabel();
}

static void OnMinuteChange(int32_t selectedIndex)
{
    if (!g_timePickerState) {
        return;
    }
    g_timePickerState->minuteIndex = selectedIndex;
    UpdateStatusLabel();
}

static void OnSecondChange(int32_t selectedIndex)
{
    if (!g_timePickerState) {
        return;
    }
    g_timePickerState->secondIndex = selectedIndex;
    UpdateStatusLabel();
}

static void OnAmPmChange(int32_t selectedIndex)
{
    if (!g_timePickerState) {
        return;
    }
    g_timePickerState->amPmIndex = selectedIndex;
    UpdateStatusLabel();
}

static void UpdatePickerLoopState(std::shared_ptr<ContainerPickerTimeMaker> picker, bool canLoop)
{
    if (picker && picker->GetHandle()) {
        picker->SetCanLoop(canLoop);
    }
}

static void OnToggleLoop()
{
    if (!g_timePickerState || !g_timePickerState->api) {
        return;
    }
    g_timePickerState->canLoop = !g_timePickerState->canLoop;
    UpdatePickerLoopState(g_timePickerState->hourPicker, g_timePickerState->canLoop);
    UpdatePickerLoopState(g_timePickerState->minutePicker, g_timePickerState->canLoop);
    UpdatePickerLoopState(g_timePickerState->secondPicker, g_timePickerState->canLoop);
    UpdatePickerLoopState(g_timePickerState->amPmPicker, g_timePickerState->canLoop);
    if (g_timePickerState->toggleLoop) {
        UpdateToggleState(g_timePickerState->toggleLoop, g_timePickerState->canLoop);
    }
}

static void OnToggleSecond()
{
    if (!g_timePickerState || !g_timePickerState->api) {
        return;
    }
    g_timePickerState->showSecond = !g_timePickerState->showSecond;
    RecreateTimePickerLayout();
    if (g_timePickerState->toggleSecond) {
        UpdateToggleState(g_timePickerState->toggleSecond, g_timePickerState->showSecond);
    }
    UpdateStatusLabel();
}

static void OnToggleMilitary()
{
    if (!g_timePickerState || !g_timePickerState->api) {
        return;
    }
    g_timePickerState->useMilitary = !g_timePickerState->useMilitary;
    RecreateTimePickerLayout();
    if (g_timePickerState->toggleMilitary) {
        UpdateToggleState(g_timePickerState->toggleMilitary, g_timePickerState->useMilitary);
    }
    UpdateStatusLabel();
}

static void OnToggleDigits()
{
    if (!g_timePickerState || !g_timePickerState->api) {
        return;
    }
    g_timePickerState->zeroPrefix = !g_timePickerState->zeroPrefix;
    RegenerateHourArray();
    RegenerateMinuteSecondArray();
    if (g_timePickerState->hourPicker && g_timePickerState->hourPicker->GetHandle()) {
        UpdatePickerOptions(g_timePickerState->hourPicker->GetHandle(), g_timePickerState->hourArray);
    }
    if (g_timePickerState->minutePicker && g_timePickerState->minutePicker->GetHandle()) {
        UpdatePickerOptions(g_timePickerState->minutePicker->GetHandle(), g_timePickerState->minuteArray);
    }
    if (g_timePickerState->secondPicker && g_timePickerState->secondPicker->GetHandle()) {
        UpdatePickerOptions(g_timePickerState->secondPicker->GetHandle(), g_timePickerState->secondArray);
    }
    if (g_timePickerState->toggleDigits) {
        UpdateToggleState(g_timePickerState->toggleDigits, g_timePickerState->zeroPrefix);
    }
    UpdateStatusLabel();
}

static ArkUI_NodeHandle CreateRootContainer()
{
    ArkUI_NativeNodeAPI_1 *api = nullptr;
    OH_ArkUI_GetModuleInterface(ARKUI_NATIVE_NODE, ArkUI_NativeNodeAPI_1, api);
    if (!api) {
        return nullptr;
    }
    ArkUI_NodeHandle rootContainer = api->createNode(ARKUI_NODE_COLUMN);
    if (!rootContainer) {
        return nullptr;
    }
    ArkUI_NumberValue widthValue = {.f32 = 1.0f};
    ArkUI_AttributeItem widthItem = {&widthValue, 1};
    api->setAttribute(rootContainer, NODE_WIDTH_PERCENT, &widthItem);
    ArkUI_NumberValue heightValue = {.f32 = 1.0f};
    ArkUI_AttributeItem heightItem = {&heightValue, 1};
    api->setAttribute(rootContainer, NODE_HEIGHT_PERCENT, &heightItem);
    ArkUI_NumberValue bgColorValue = {.u32 = 0xFFFFFFFF};
    ArkUI_AttributeItem bgColorItem = {&bgColorValue, 1};
    api->setAttribute(rootContainer, NODE_BACKGROUND_COLOR, &bgColorItem);
    ArkUI_NumberValue justifyValue = {.i32 = ARKUI_FLEX_ALIGNMENT_CENTER};
    ArkUI_AttributeItem justifyItem = {&justifyValue, 1};
    api->setAttribute(rootContainer, NODE_COLUMN_JUSTIFY_CONTENT, &justifyItem);
    ArkUI_NumberValue alignValue = {.i32 = ARKUI_HORIZONTAL_ALIGNMENT_CENTER};
    ArkUI_AttributeItem alignItem = {&alignValue, 1};
    api->setAttribute(rootContainer, NODE_COLUMN_ALIGN_ITEMS, &alignItem);
    return rootContainer;
}

static ArkUI_NodeHandle CreatePickersRowContainer()
{
    if (!g_timePickerState || !g_timePickerState->api) {
        return nullptr;
    }
    ArkUI_NodeHandle row = g_timePickerState->api->createNode(ARKUI_NODE_ROW);
    if (!row) {
        return nullptr;
    }
    ArkUI_NumberValue alignValue = {.i32 = ARKUI_FLEX_ALIGNMENT_CENTER};
    ArkUI_AttributeItem alignItem = {&alignValue, 1};
    g_timePickerState->api->setAttribute(row, NODE_ROW_ALIGN_ITEMS, &alignItem);
    ArkUI_NumberValue justifyValue = {.i32 = ARKUI_FLEX_ALIGNMENT_CENTER};
    ArkUI_AttributeItem justifyItem = {&justifyValue, 1};
    g_timePickerState->api->setAttribute(row, NODE_ROW_JUSTIFY_CONTENT, &justifyItem);
    return row;
}

static void CreateStatusLabel(ArkUI_NodeHandle rootContainer)
{
    if (!g_timePickerState || !g_timePickerState->api || !rootContainer) {
        return;
    }
    auto api = g_timePickerState->api;
    ArkUI_NodeHandle statusText = api->createNode(ARKUI_NODE_TEXT);
    if (!statusText) {
        return;
    }
    g_timePickerState->statusLabel = statusText;
    ArkUI_NumberValue marginValue = {.f32 = 5.0f};
    ArkUI_AttributeItem marginItem = {&marginValue, 1};
    api->setAttribute(statusText, NODE_MARGIN, &marginItem);
    ArkUI_NumberValue widthValue = {.f32 = 0.8f};
    ArkUI_AttributeItem widthItem = {&widthValue, 1};
    api->setAttribute(statusText, NODE_WIDTH_PERCENT, &widthItem);
    ArkUI_NumberValue alignValue = {.i32 = ARKUI_TEXT_CONTENT_ALIGN_CENTER};
    ArkUI_AttributeItem alignItem = {&alignValue, 1};
    api->setAttribute(statusText, NODE_TEXT_CONTENT_ALIGN, &alignItem);
    ArkUI_NumberValue fontSizeValue = {.f32 = 20.0f};
    ArkUI_AttributeItem fontSizeItem = {&fontSizeValue, 1};
    api->setAttribute(statusText, NODE_FONT_SIZE, &fontSizeItem);
    ArkUI_NumberValue borderValue = {.f32 = 1.0f};
    ArkUI_AttributeItem borderItem = {&borderValue, 1};
    api->setAttribute(statusText, NODE_BORDER_WIDTH, &borderItem);
    ArkUI_NodeHandle statusRow = api->createNode(ARKUI_NODE_ROW);
    if (statusRow) {
        api->addChild(statusRow, statusText);
        api->addChild(rootContainer, statusRow);
    }
}

static void CreateControlPanel(ArkUI_NodeHandle rootContainer)
{
    if (!g_timePickerState || !g_timePickerState->api || !rootContainer) {
        return;
    }
    auto api = g_timePickerState->api;
    g_timePickerState->controlPanel = api->createNode(ARKUI_NODE_COLUMN);
    if (!g_timePickerState->controlPanel) {
        return;
    }
    g_timePickerState->toggleLoop = CreateToggleButton("loop", g_timePickerState->canLoop, EVENT_TOGGLE_LOOP);
    if (g_timePickerState->toggleLoop) {
        api->addChild(g_timePickerState->controlPanel, g_timePickerState->toggleLoop);
    }
    g_timePickerState->toggleSecond =
        CreateToggleButton("show second", g_timePickerState->showSecond, EVENT_TOGGLE_SECOND);
    if (g_timePickerState->toggleSecond) {
        api->addChild(g_timePickerState->controlPanel, g_timePickerState->toggleSecond);
    }
    g_timePickerState->toggleMilitary =
        CreateToggleButton("use military", g_timePickerState->useMilitary, EVENT_TOGGLE_MILITARY);
    if (g_timePickerState->toggleMilitary) {
        api->addChild(g_timePickerState->controlPanel, g_timePickerState->toggleMilitary);
    }
    g_timePickerState->toggleDigits =
        CreateToggleButton("2-digits", g_timePickerState->zeroPrefix, EVENT_TOGGLE_DIGITS);
    if (g_timePickerState->toggleDigits) {
        api->addChild(g_timePickerState->controlPanel, g_timePickerState->toggleDigits);
    }
    api->addChild(rootContainer, g_timePickerState->controlPanel);
}

static void InitializeTimePickerData()
{
    if (!g_timePickerState) {
        return;
    }
    g_timePickerState->amPmArray = {"AM", "PM"};
    RegenerateHourArray();
    RegenerateMinuteSecondArray();
    LogMinuteSecondArray();
}

static void OnEventReceive(ArkUI_NodeEvent *event)
{
    if (!event) {
        return;
    }
    int32_t eventId = OH_ArkUI_NodeEvent_GetTargetId(event);
    if (eventId == EVENT_HOUR_CHANGE) {
        ArkUI_NodeComponentEvent *componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
        if (componentEvent) {
            OnHourChange(componentEvent->data[0].i32);
        }
    } else if (eventId == EVENT_MINUTE_CHANGE) {
        ArkUI_NodeComponentEvent *componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
        if (componentEvent) {
            OnMinuteChange(componentEvent->data[0].i32);
        }
    } else if (eventId == EVENT_SECOND_CHANGE) {
        ArkUI_NodeComponentEvent *componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
        if (componentEvent) {
            OnSecondChange(componentEvent->data[0].i32);
        }
    } else if (eventId == EVENT_AMPM_CHANGE) {
        ArkUI_NodeComponentEvent *componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
        if (componentEvent) {
            OnAmPmChange(componentEvent->data[0].i32);
        }
    } else if (eventId == EVENT_TOGGLE_LOOP) {
        OnToggleLoop();
    } else if (eventId == EVENT_TOGGLE_SECOND) {
        OnToggleSecond();
    } else if (eventId == EVENT_TOGGLE_MILITARY) {
        OnToggleMilitary();
    } else if (eventId == EVENT_TOGGLE_DIGITS) {
        OnToggleDigits();
    }
}
```
