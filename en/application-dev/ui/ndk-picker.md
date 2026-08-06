# Using the Sliding Selector Picker

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

<!-- md-trans-meta sourceCommit=991702ccb72aac978749d669bbd7567b941621c2 translatedAt=2026-05-27T01:00:50.306Z pushedAt=2026-05-27T02:46:07.795Z -->
## Overview

Starting from API version 23, the ArkUI development framework provides the **Picker** container component in the NDK APIs. The **Picker** container component is used to implement user-defined option selection, supporting features such as scrolling selection, haptic feedback, and circular scrolling. By setting the selection indicator style, the **Picker** component can customize the display effect of selected items, making it suitable for scenarios such as date, time, and text selection. Starting from API version 26.0.0, the number of visible option rows and the height of each row can be configured through **NODE_PICKER_DISPLAYED_ITEM_COUNT** and **NODE_PICKER_ITEM_HEIGHT**. The semantics are consistent with [displayedItemCount](../reference/apis-arkui/arkui-ts/ts-container-ui-picker-component.md#displayeditemcount) and [itemHeight](../reference/apis-arkui/arkui-ts/ts-container-ui-picker-component.md#itemheight) on the ArkTS side [UIPickerComponent](../reference/apis-arkui/arkui-ts/ts-container-ui-picker-component.md). For detailed parameter formats, see [Information Selection Component Attribute](../reference/apis-arkui/capi-native-node-h-nodeattributetype-informationselection.md).

After [creating a picker](#creating-a-picker), you can [set picker attributes](#setting-picker-attributes) and [listen for picker events](#listening-for-picker-events).

For building UI interfaces using the NDK APIs and basic NDK usage, refer to [Integrating with ArkTS Pages](ndk-access-the-arkts-page.md).

## Creating a Picker

Call [createNode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#createnode)(ARKUI_NODE_PICKER) through [ArkUI_NativeNodeAPI_1](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md) to obtain a component object pointer, and set the relevant attributes in [ArkUI_NodeAttributeType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeattributetype) to create a **Picker** container component.

### Basic Creation Method

The following example shows how to create a **Picker** component and set basic attributes. The number of visible option rows and the height of each row are supported from API version 26.0.0 and can be set as needed. For values and default behavior, see [NODE_PICKER_DISPLAYED_ITEM_COUNT](../reference/apis-arkui/capi-native-node-h-nodeattributetype-informationselection.md#node_picker_displayed_item_count) and [NODE_PICKER_ITEM_HEIGHT](../reference/apis-arkui/capi-native-node-h-nodeattributetype-informationselection.md#node_picker_item_height).

```cpp
// Obtain the NativeNodeAPI API.
ArkUI_NativeNodeAPI_1 *api = nullptr;
OH_ArkUI_GetModuleInterface(ARKUI_NATIVE_NODE, ArkUI_NativeNodeAPI_1, api);
if (api == nullptr) {
    return nullptr;
}

// Create a Picker component.
ArkUI_NodeHandle picker = api->createNode(ARKUI_NODE_PICKER);
if (picker == nullptr) {
    return nullptr;
}

// Set the picker size.
ArkUI_NumberValue widthValue = {.f32 = 200.0f};
ArkUI_AttributeItem widthItem = {&widthValue, 1};
api->setAttribute(picker, NODE_WIDTH, &widthItem);

ArkUI_NumberValue heightValue = {.f32 = 300.0f};
ArkUI_AttributeItem heightItem = {&heightValue, 1};
api->setAttribute(picker, NODE_HEIGHT, &heightItem);

// Set the default selected item.
ArkUI_NumberValue selectedValue = {.u32 = 0};
ArkUI_AttributeItem selectedItem = {&selectedValue, 1};
api->setAttribute(picker, NODE_PICKER_OPTION_SELECTED_INDEX, &selectedItem);

// Set circular scrolling.
ArkUI_NumberValue canLoopValue = {.i32 = 1};
ArkUI_AttributeItem canLoopItem = {&canLoopValue, 1};
api->setAttribute(picker, NODE_PICKER_CAN_LOOP, &canLoopItem);

// Set haptic feedback.
ArkUI_NumberValue hapticValue = {.i32 = 1};
ArkUI_AttributeItem hapticItem = {&hapticValue, 1};
api->setAttribute(picker, NODE_PICKER_ENABLE_HAPTIC_FEEDBACK, &hapticItem);

// Set the number of visible option rows (supported since API version 26.0.0, optional).
ArkUI_NumberValue displayedCountValue = {.i32 = 5};
ArkUI_AttributeItem displayedCountItem = {&displayedCountValue, 1};
api->setAttribute(picker, NODE_PICKER_DISPLAYED_ITEM_COUNT, &displayedCountItem);

// Set the row height per line, in vp (supported since API version 26.0.0, optional).
ArkUI_NumberValue itemHeightValue = {.f32 = 48.0f};
ArkUI_AttributeItem itemHeightItem = {&itemHeightValue, 1};
api->setAttribute(picker, NODE_PICKER_ITEM_HEIGHT, &itemHeightItem);
```

### Encapsulation into a Utility Class

Refer to the implementation of the list component in the [example](ndk-access-the-arkts-page.md#example). You can encapsulate commonly used property settings of the **Picker** component into a custom utility class for subsequent use.

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
    // Basic size setting API.
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
    // Picker-specific attribute setting API.
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
    // Public helper methods.
    // ========================================
    ArkUI_NativeNodeAPI_1 *GetNodeAPI() const { return nodeApi_; }

protected:
    void OnNodeEvent(ArkUI_NodeEvent *event) override { BaseNode::OnNodeEvent(event); }

private:
    ArkUI_NativeNodeAPI_1 *nodeApi_ = nullptr;
};
```

Create a **Picker** component using the encapsulated class:

<!-- @[ContainerPickerCanLoopMakerCpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/native_type_sample/entry/src/main/cpp/ContainerPickerCanLoopMaker.cpp) -->

```cpp
auto picker = std::make_shared<ContainerPickerCanLoopMaker>();
auto data = std::make_shared<std::vector<std::string>>(MakeData());
ConfigurePicker(picker, data);
```

## Setting Picker Attributes

### Setting the Default Selected Item

By setting the `NODE_PICKER_OPTION_SELECTED_INDEX` attribute in [ArkUI_NodeAttributeType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeattributetype), you can set the default selected item index for the **Picker** component.

```cpp
picker->SetSelectedIndex(2); // Set the default selection to the third item (index starts from 0).
```

### Setting Haptic Feedback

By setting the `NODE_PICKER_ENABLE_HAPTIC_FEEDBACK` attribute, you can control whether the **Picker** component enables haptic feedback. When enabled, if the system hardware supports it, tactile feedback will be generated when the user scrolls the selector.

```cpp
picker->SetHapticFeedback(true); // Enable haptic feedback.
picker->SetHapticFeedback(false); // Disable Haptic Feedback.
```

### Setting Circular Scrolling

By setting the `NODE_PICKER_CAN_LOOP` attribute, you can control whether the **Picker** component supports circular scrolling. When set to **true**, the selector can scroll infinitely in a loop; when set to **false**, scrolling stops when reaching the beginning or end.

> **Note:**
>
> If the number of child components is less than 8, circular scrolling will not occur regardless of whether it is set to **true** or **false**.

```cpp
picker->SetCanLoop(true); // Enable circular scrolling.
picker->SetCanLoop(false); // Disable circular scrolling.
```

### Setting the Number of Visible Options and Option Row Height

Starting from API version 26.0.0, you can set the number of visible option rows via [NODE_PICKER_DISPLAYED_ITEM_COUNT](../reference/apis-arkui/capi-native-node-h-nodeattributetype-informationselection.md#node_picker_displayed_item_count) and set the height of each row (vp) via [NODE_PICKER_ITEM_HEIGHT](../reference/apis-arkui/capi-native-node-h-nodeattributetype-informationselection.md#node_picker_item_height). When not set, the defaults are 7 rows and 40 vp respectively; the value range, even-numbered row specification, and out-of-bounds behavior are consistent with [displayedItemCount](../reference/apis-arkui/arkui-ts/ts-container-ui-picker-component.md#displayeditemcount) and [itemHeight](../reference/apis-arkui/arkui-ts/ts-container-ui-picker-component.md#itemheight) of [UIPickerComponent](../reference/apis-arkui/arkui-ts/ts-container-ui-picker-component.md). In the 3D wheel style, the visible height is affected by rotation. If you increase the number of rows or row height, increase the **Picker** container height accordingly.

When using [ArkUI_NativeNodeAPI_1](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md), you can directly call `setAttribute`.

```cpp
ArkUI_NumberValue visibleCountValue = {.i32 = 5};
ArkUI_AttributeItem visibleCountItem = {&visibleCountValue, 1};
api->setAttribute(picker, NODE_PICKER_DISPLAYED_ITEM_COUNT, &visibleCountItem);

ArkUI_NumberValue itemHeightValue = {.f32 = 48.0f};
ArkUI_AttributeItem itemHeightItem = {&itemHeightValue, 1};
api->setAttribute(picker, NODE_PICKER_ITEM_HEIGHT, &itemHeightItem);
```

If using the `ContainerPickerCanLoopMaker` encapsulated above, you can call the encapsulated API.

```cpp
picker->SetDisplayedItemCount(5);   // Number of visible option rows. For specific rules, see the attribute description documentation.
picker->SetItemHeight(48.0f);        // Height per row (vp).
```

### Setting the Selection Indicator Style

By setting the `NODE_PICKER_SELECTION_INDICATOR` attribute, you can customize the selection indicator style of the **Picker** component. The selection indicator consists of two parts: background style and divider line style.

The background style indicator is set through the [ArkUI_PickerIndicatorBackground](../reference/apis-arkui/capi-arkui-nativemodule-arkui-pickerindicatorbackground.md) struct, including the background color and corner radius.

```cpp
ArkUI_PickerIndicatorBackground backgroundStyle = {
    .backgroundColor = 0x1A000000,  // Semi-transparent black background
    .topLeftRadius = 8.0f,
    .topRightRadius = 8.0f,
    .bottomLeftRadius = 8.0f,
    .bottomRightRadius = 8.0f
};
```

The divider style indicator is set through the [ArkUI_PickerIndicatorDivider](../reference/apis-arkui/capi-arkui-nativemodule-arkui-pickerindicatordivider.md) struct, including line width, color, and margins.

```cpp
ArkUI_PickerIndicatorDivider dividerStyle = {
    .strokeWidth = 2.0f,
    .dividerColor = 0xFF3366CC,  // Blue divider
    .startMargin = 10.0f,
    .endMargin = 10.0f
};
```

Combine the background style or divider style into the [ArkUI_PickerIndicatorStyle](../reference/apis-arkui/capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) struct and set it to the **Picker** component.

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

## Listening for Picker Events

The **Picker** component supports the following events:

| Event Enumeration | Event Description | API Starting Version |
|---------|------|---------|
| NODE_PICKER_EVENT_ON_CHANGE | Event triggered when an item is selected in the **Picker** component. | 23 |
| NODE_PICKER_EVENT_ON_SCROLL_STOP | Event triggered when an item is selected and scrolling stops in the **Picker** component. | 23 |

### Listening for Selection Change Events

By registering the `NODE_PICKER_EVENT_ON_CHANGE` event, you can listen for selection changes in the **Picker** component. The event callback returns the index value of the selected item.

```cpp
static void OnPickerChange(ArkUI_NodeEvent* event)
{
    auto* componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
    if (componentEvent != nullptr) {
        int32_t selectedIndex = componentEvent->data[0].i32;
        // Handling Selection Changes
    }
}

// Register Event
ArkUI_NodeEventItem eventItems[] = {
    {NODE_PICKER_EVENT_ON_CHANGE, OnPickerChange, nullptr}
};
nodeApi->registerNodeEvent(picker->GetHandle(), eventItems, 1);
```

### Listening for Scroll Stop Events

By registering the `NODE_PICKER_EVENT_ON_SCROLL_STOP` event, you can listen for selection changes when the Picker component stops scrolling. Compared to the `NODE_PICKER_EVENT_ON_CHANGE` event, this event is only triggered when scrolling stops, making it suitable for scenarios where the selection needs to be processed after scrolling is complete.

```cpp
static void OnPickerScrollStop(ArkUI_NodeEvent* event)
{
    auto* componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
    if (componentEvent != nullptr) {
        int32_t selectedIndex = componentEvent->data[0].i32;
        // Handling Selection After Scroll Stop
    }
}

// Register an event.
ArkUI_NodeEventItem eventItems[] = {
    {NODE_PICKER_EVENT_ON_SCROLL_STOP, OnPickerScrollStop, nullptr}
};
nodeApi->registerNodeEvent(picker->GetHandle(), eventItems, 1);
```

## Complete Example

### Dynamically Modifying Picker Attributes

The following example demonstrates how to dynamically modify the circular scrolling and haptic feedback properties of the **Picker** component through a button.

<!-- @[ContainerPickerCanLoopMakerCpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/native_type_sample/entry/src/main/cpp/ContainerPickerCanLoopMaker.cpp) -->

```cpp
// ---------- Generating data ----------
static std::vector<std::string> MakeData() { return {"1", "2", "3", "4", "5", "6", "7", "8", "9", "10"}; }

// ---------- Creating picker options ----------
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

// ---------- Creating a button ----------
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

// ---------- Updating button text ----------
static void UpdateButtonText(ArkUI_NativeNodeAPI_1 *api, ArkUI_NodeHandle button, const char *newText)
{
    if (api && button) {
        ArkUI_AttributeItem textItem = {.string = newText};
        api->setAttribute(button, NODE_BUTTON_LABEL, &textItem);
    }
}

// ---------- Global state management ----------
struct PickerState {
    std::shared_ptr<ContainerPickerCanLoopMaker> picker;
    ArkUI_NodeHandle button1 = nullptr;
    ArkUI_NodeHandle button2 = nullptr;
    bool canLoopEnabled = K_CAN_LOOP;
    bool hapticFeedbackEnabled = K_HAPTIC_FEEDBACK;
    ArkUI_NativeNodeAPI_1 *api = nullptr;
};

static std::shared_ptr<PickerState> g_pickerState;

// ---------- Button event callback ----------
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

// ---------- Global Event Receiver ----------
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

// ---------- Configuring Picker Appearance/Interaction ----------
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

// ---------- Building the picker overall ----------
static std::shared_ptr<ContainerPickerCanLoopMaker> BuildPicker()
{
    auto picker = std::make_shared<ContainerPickerCanLoopMaker>();
    auto data = std::make_shared<std::vector<std::string>>(MakeData());
    ConfigurePicker(picker, data);
    return picker;
}

// ---------- Main creation function ----------
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

### Different Types of Picker Options

The **Picker** component supports multiple types of options, including text, images, and combinations of images and text.

<!-- @[ContainerPickerTypesMakerCpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/native_type_sample/entry/src/main/cpp/ContainerPickerTypesMaker.cpp) -->

```cpp
// ---------- Global state ----------
struct PickerTypesState {
    int32_t curTabIndex = 0;
    ArkUI_NodeHandle textPicker = nullptr;
    ArkUI_NodeHandle imagePicker = nullptr;
    ArkUI_NodeHandle hybridPicker = nullptr;
    ArkUI_NodeHandle tabs = nullptr;
    ArkUI_NativeNodeAPI_1 *api = nullptr;
};

static std::shared_ptr<PickerTypesState> g_pickerTypesState;

// ---------- Creating text options ----------
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

// ---------- Creating image options ----------
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

// ---------- Creating combined text and image options ----------
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

// ---------- Picker event callback functions ----------
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

static void OnTextPickerChange(ArkUI_NodeEvent *event) { OnPickerChange(event, "Text"); }

static void OnTextPickerScrollStop(ArkUI_NodeEvent *event) { OnPickerScrollStop(event, "Text"); }

static void OnImagePickerChange(ArkUI_NodeEvent *event) { OnPickerChange(event, "Image"); }

static void OnImagePickerScrollStop(ArkUI_NodeEvent *event) { OnPickerScrollStop(event, "Image"); }

static void OnHybridPickerChange(ArkUI_NodeEvent *event) { OnPickerChange(event, "Image-text combination"); }

static void OnHybridPickerScrollStop(ArkUI_NodeEvent *event) { OnPickerScrollStop(event, "Image-Text Combination"); }

// ---------- Creating a picker ----------
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

// ---------- Creating a text picker ----------
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

// ---------- Creating an image picker ----------
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

// ---------- Creating an Image-Text Combination Picker ----------
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

// ---------- Creating column container ----------
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

// ---------- Tab switch event callback ----------
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

// ---------- Global event receiver ----------
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

### Multi-level Linked Picker

The following example demonstrates how to create a three-level linked **Picker** for province, city, and district, where the lower-level data is automatically updated when the province or city selection changes.

<!-- @[ContainerPickerRegionMakerCpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/native_type_sample/entry/src/main/cpp/ContainerPickerRegionMaker.cpp) -->

```cpp
// ---------- Global state ----------
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

// ---------- Initializing region data ----------
static RegionData InitRegionData()
{
    RegionData data;
    std::unordered_map<std::string, std::vector<std::string>> liaoningCities;
    liaoningCities["Shenyang"] = {"Shenhe District", "Heping District", "Hunnan District"};
    liaoningCities["Dalian City"] = {"Zhongshan District", "Jinzhou District", "Changhai County"};
    data.data["Liaoning Province"] = liaoningCities;
    std::unordered_map<std::string, std::vector<std::string>> jilinCities;
    jilinCities["Changchun City"] = {"Nanguan District", "Kuancheng District", "Chaoyang District"};
    jilinCities["Siping City"] = {"Tiexi District", "Tiedong District", "Lishu County"};
    data.data["Jilin Province"] = jilinCities;
    std::unordered_map<std::string, std::vector<std::string>> heilongjiangCities;
    heilongjiangCities["Harbin City"] = {"Daoli District", "Daowai District", "Nangang District"};
    heilongjiangCities["Mudanjiang City"] = {"Dong'an District", "Xi'an District", "Aimin District"};
    data.data["Heilongjiang Province"] = heilongjiangCities;
    return data;
}

// ---------- Creating picker options ----------
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

// ---------- Creating a picker ----------
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

// ---------- Refreshing county/district data ----------
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

// ---------- Refreshing city data ----------
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

// ---------- Event callback ----------
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

// ---------- Global event receiver ----------
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

// ---------- Creating a region picker ----------
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

### Time Picker

The following example demonstrates how to use multiple **Picker** components to create a time picker, including hour, minute, second, and AM/PM selections.

<!-- @[ContainerPickerTimeMakerCpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/native_type_sample/entry/src/main/cpp/ContainerPickerTimeMaker.cpp) -->

```cpp
// ---------- Global state management ----------
struct TimePickerState {
    // Time Picker Component
    std::shared_ptr<ContainerPickerTimeMaker> hourPicker;
    std::shared_ptr<ContainerPickerTimeMaker> minutePicker;
    std::shared_ptr<ContainerPickerTimeMaker> secondPicker;
    std::shared_ptr<ContainerPickerTimeMaker> amPmPicker;
    // Currently Selected Index
    int32_t hourIndex = 0;
    int32_t minuteIndex = 0;
    int32_t secondIndex = 0;
    int32_t amPmIndex = AM_INDEX;
    // Configuration Options
    bool showSecond = INITIAL_SHOW_SECOND_STATE;
    bool useMilitary = INITIAL_USE_MILITARY_STATE;
    bool zeroPrefix = INITIAL_ZERO_PREFIX_STATE;
    bool canLoop = INITIAL_LOOP_STATE;
    // Data Array
    std::vector<std::string> amPmArray;
    std::vector<std::string> hourArray;
    std::vector<std::string> minuteArray;
    std::vector<std::string> secondArray;
    // UI Node Handle
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

// ---------- Helper functions ----------
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
        // 24-hour format: 00-23
        for (int i = 0; i < HOURS_IN_24_HOUR_FORMAT; i++) {
            g_timePickerState->hourArray.push_back(FormatTime(i, g_timePickerState->zeroPrefix));
        }
    } else {
        // 12-hour format: 12, 01-11
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
        // Convert 12-hour format to 24-hour format
        if (g_timePickerState->amPmIndex == PM_INDEX) {
            int32_t oldHourIndex = g_timePickerState->hourIndex;
            g_timePickerState->hourIndex += AM_PM_SWITCH_HOUR;
            if (g_timePickerState->hourIndex >= HOURS_IN_24_HOUR_FORMAT) {
                g_timePickerState->hourIndex = 0;
            }
        }
    } else {
        // Convert 24-hour format to 12-hour format
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

// ---------- Recreate Time Picker Layout ----------
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
<!--no_check-->