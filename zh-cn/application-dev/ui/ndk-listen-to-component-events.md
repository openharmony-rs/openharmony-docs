# 监听组件事件
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->


NDK接口针对UI组件的事件，提供了监听函数的方式。首先，可使用[addNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#addnodeeventreceiver)函数添加组件事件的监听器，该监听器会监听该组件上发生的所有事件，例如：点击事件、焦点事件。然后，可使用[registerNodeEvent](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent)函数声明组件的哪些事件需要监听，NDK接口支持的事件范围通过[ArkUI_NodeEventType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)枚举值定义。


> **说明：**
> - 事件注册需要声明[addNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#addnodeeventreceiver)监听器注册和[registerNodeEvent](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent)事件类型，监听器只能监听已声明的事件。
> 
> - 需要关注事件的反注册逻辑，如在组件销毁前调用[removeNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#removenodeeventreceiver)移除事件监听器，[unregisterNodeEvent](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#unregisternodeevent)通知ArkUI框架已监听的事件不再需要监听。
> 
> - [addNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#addnodeeventreceiver)可以添加多个函数指针，每个函数指针都会在对应事件触发时触发，对应的[removeNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#removenodeeventreceiver)需要传递对应的函数指针用于移除监听。
> 
> - [registerNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver)是全局监听函数，不同于[addNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#addnodeeventreceiver)，[registerNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver)能够监听所有Native组件的事件触发，但只能传递一个函数指针，多次调用使用最后一次的函数指针进行回调，释放时使用[unregisterNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#unregisternodeeventreceiver)进行释放。


以下示例基于[接入ArkTS页面](ndk-access-the-arkts-page.md)章节，补充相关事件监听。详细代码请参考[完整示例](ndk-listen-to-component-events.md#完整示例)。


- 事件注册和事件解注册

  通过addNodeEventReceiver对节点绑定事件处理函数，接着通过调用registerNodeEvent注册对应的事件。

  > **说明：**
  > 
  > 事件监听函数的入参[ArkUI_NodeEvent](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nodeevent.md)* event只在函数回调周期内生效，不推荐对该指针进行缓存或者进行异步处理。

    定义[ArkUI_NativeNodeAPI_1](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md)类型的指针：
    <!-- @[define_node](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/Common.h) -->
    
    ``` C
    ArkUI_NativeNodeAPI_1 *nodeAPI = nullptr;
    ```

    调用[OH_ArkUI_GetModuleInterface](../reference/apis-arkui/capi-native-interface-h.md#oh_arkui_getmoduleinterface)接口给定义的指针赋值：
    <!-- @[get_module_interface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/NativeEntry.cpp) -->
    
    ``` C++
    OH_ArkUI_GetModuleInterface(ARKUI_NATIVE_NODE, ArkUI_NativeNodeAPI_1, nodeAPI);
    ```

    定义事件触发回调函数：
    <!-- @[node_event_receiver](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/Function.h) -->
    
    ``` C
    void NodeEventReceiver(ArkUI_NodeEvent *event) {
      // 设置对应的事件类型触发时进行的操作，如NODE_ON_CLICK_EVENT
    };
    ```

    创建一个节点，将事件触发回调函数绑定到该节点并进行事件注册：
    <!-- @[create_and_register_node](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/Function.h) -->
    
    ``` C
    auto button = nodeAPI->createNode(ARKUI_NODE_BUTTON);
    nodeAPI->addNodeEventReceiver(button, NodeEventReceiver);
    nodeAPI->registerNodeEvent(button, NODE_ON_CLICK_EVENT, 0, nullptr);
    ```

  详细的事件类型请参考[ArkUI_NodeEventType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)。

  通过unregisterNodeEvent解注册对应的事件类型，再通过removeNodeEventReceiver卸载事件处理函数。

    解注册对应的事件类型：
    <!-- @[unregister_node_event](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/Function.h) -->
    
    ``` C
    nodeAPI->unregisterNodeEvent(button, NODE_ON_CLICK_EVENT);
    ```

    卸载事件处理函数：
    <!-- @[remove_node_evect_receiver](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/Function.h) -->
    
    ``` C
    nodeAPI->removeNodeEventReceiver(button, NodeEventReceiver);
    ```


- 全局事件监听

  使用registerNodeEventReceiver注册全局的事件处理函数，对事件进行统一的处理，结束后可使用unregisterNodeEventReceiver进行释放。

    注册全局的事件处理函数：
    <!-- @[register_global_event](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/Function.h) -->
    
    ``` C
    nodeAPI->registerNodeEventReceiver([](ArkUI_NodeEvent *event) {
        // 从组件事件中获取基础事件对象
        auto *inputEvent = OH_ArkUI_NodeEvent_GetInputEvent(event);
        // 从组件事件获取事件类型
        auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
        // ···
        switch (eventType) {
            case NODE_ON_CLICK_EVENT: {
                // 触发点击事件所进行的操作，从基础事件获取事件信息
                // ···
            }
            default: {
                break;
            }
        }
    });
    ```

    解注册全局的事件处理函数：
    <!-- @[unregister_node_event_receicer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/Function.h) -->
    
    ``` C
    nodeAPI->unregisterNodeEventReceiver();
    ```


- 获取事件信息

  ArkUI框架提供了[OH_ArkUI_NodeEvent_GetInputEvent()](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeevent_getinputevent)接口，用于从输入交互相关的组件事件（如NODE_ON_CLICK_EVENT、NODE_TOUCH_EVENT等，具体可参见每个枚举定义的说明）中获取基础事件对象。然后，可通过调用[OH_ArkUI_PointerEvent_GetDisplayX()](../reference/apis-arkui/capi-ui-input-event-h.md#oh_arkui_pointerevent_getdisplayx)、[OH_ArkUI_PointerEvent_GetDisplayXByIndex()](../reference/apis-arkui/capi-ui-input-event-h.md#oh_arkui_pointerevent_getdisplayxbyindex)、[OH_ArkUI_UIInputEvent_GetAction()](../reference/apis-arkui/capi-ui-input-event-h.md#oh_arkui_uiinputevent_getaction)和[OH_ArkUI_UIInputEvent_GetEventTime()](../reference/apis-arkui/capi-ui-input-event-h.md#oh_arkui_uiinputevent_geteventtime)等接口，从基础事件中获取更多信息。应用根据获取的事件信息，在事件执行过程中实现差异化交互逻辑。

    定义处理各类型事件的函数：
    <!-- @[handle_event_functions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/NormalNodeExample.h) -->
    
    ``` C
    // 处理点击事件
    void HandleClickEvent(ArkUI_NodeEvent *event, ArkUI_UIInputEvent *inputEvent)
    {
        auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "Click event triggered (eventType=%{public}d)", eventType);
    
        auto x = OH_ArkUI_PointerEvent_GetX(inputEvent);
        auto y = OH_ArkUI_PointerEvent_GetY(inputEvent);
        auto displayX = OH_ArkUI_PointerEvent_GetDisplayX(inputEvent);
        auto displayY = OH_ArkUI_PointerEvent_GetDisplayY(inputEvent);
        auto windowX = OH_ArkUI_PointerEvent_GetWindowX(inputEvent);
        auto windowY = OH_ArkUI_PointerEvent_GetWindowY(inputEvent);
        auto pointerCount = OH_ArkUI_PointerEvent_GetPointerCount(inputEvent);
        auto xByIndex = OH_ArkUI_PointerEvent_GetXByIndex(inputEvent, 0);
        auto yByIndex = OH_ArkUI_PointerEvent_GetYByIndex(inputEvent, 0);
        auto displayXByIndex = OH_ArkUI_PointerEvent_GetDisplayXByIndex(inputEvent, 0);
        auto displayYByIndex = OH_ArkUI_PointerEvent_GetDisplayYByIndex(inputEvent, 0);
        auto windowXByIndex = OH_ArkUI_PointerEvent_GetWindowXByIndex(inputEvent, 0);
        auto windowYByIndex = OH_ArkUI_PointerEvent_GetWindowYByIndex(inputEvent, 0);
        auto pointerId = OH_ArkUI_PointerEvent_GetPointerId(inputEvent, 0);
        auto pressure = OH_ArkUI_PointerEvent_GetPressure(inputEvent, 0);
        auto action = OH_ArkUI_UIInputEvent_GetAction(inputEvent);
        auto eventTime = OH_ArkUI_UIInputEvent_GetEventTime(inputEvent);
        auto sourceType = OH_ArkUI_UIInputEvent_GetSourceType(inputEvent);
        auto type = OH_ArkUI_UIInputEvent_GetType(inputEvent);
    
        std::string eventInfo =
            "x: " + std::to_string(x) + ", y: " + std::to_string(y) +
            ", displayX: " + std::to_string(displayX) + ", displayY: " + std::to_string(displayY) +
            ", windowX: " + std::to_string(windowX) + ", windowY: " + std::to_string(windowY) +
            ", pointerCount: " + std::to_string(pointerCount) + ", xByIndex: " + std::to_string(xByIndex) +
            ", yByIndex: " + std::to_string(yByIndex) +
            ", displayXByIndex: " + std::to_string(displayXByIndex) +
            ", displayYByIndex: " + std::to_string(displayYByIndex) +
            ", windowXByIndex: " + std::to_string(windowXByIndex) +
            ", windowYByIndex: " + std::to_string(windowYByIndex) +
            ", pointerId: " + std::to_string(pointerId) + ", pressure: " + std::to_string(pressure) +
            ", action: " + std::to_string(action) + ", eventTime: " + std::to_string(eventTime) +
            ", sourceType: " + std::to_string(sourceType) + ", type: " + std::to_string(type);
    
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "ClickEvent: %{public}s", eventInfo.c_str());
    }
    
    // 处理焦点事件
    void HandleFocusEvent(ArkUI_NodeEvent *event)
    {
        auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "Focus event triggered (eventType=%{public}d)", eventType);
        auto nodeHandle = OH_ArkUI_NodeEvent_GetNodeHandle(event);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "FocusEvent: nodeHandle=%{public}p", nodeHandle);
    }
    
    // 处理失焦事件
    void HandleBlurEvent(ArkUI_NodeEvent *event)
    {
        auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "Blur event triggered (eventType=%{public}d)", eventType);
        auto nodeHandle = OH_ArkUI_NodeEvent_GetNodeHandle(event);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "BlurEvent: nodeHandle=%{public}p", nodeHandle);
    }
    
    // 处理悬停事件
    void HandleHoverEvent(ArkUI_NodeEvent *event, ArkUI_UIInputEvent *inputEvent)
    {
        auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "Hover event triggered (eventType=%{public}d)", eventType);
        auto x = OH_ArkUI_PointerEvent_GetX(inputEvent);
        auto y = OH_ArkUI_PointerEvent_GetY(inputEvent);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "HoverEvent: x=%{public}f, y=%{public}f", x, y);
    }
    
    // 处理键盘事件
    void HandleKeyEvent(ArkUI_NodeEvent *event, ArkUI_UIInputEvent *inputEvent)
    {
        auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "Key event triggered (eventType=%{public}d)", eventType);
    
        // 获取按键键码
        auto keyCode = OH_ArkUI_KeyEvent_GetKeyCode(inputEvent);
        // 获取按键类型
        auto keyType = OH_ArkUI_KeyEvent_GetType(inputEvent);
        // 获取按键键值
        const char *keyText = OH_ArkUI_KeyEvent_GetKeyText(inputEvent);
        // 获取Unicode码值
        auto unicode = OH_ArkUI_KeyEvent_GetUnicode(inputEvent);
        // 获取按键动作
        auto action = OH_ArkUI_UIInputEvent_GetAction(inputEvent);
    
        // 获取CapsLock状态
        bool capsLockOn = false;
        auto capsLockResult = OH_ArkUI_KeyEvent_IsCapsLockOn(inputEvent, &capsLockOn);
    
        std::string keyInfo = "keyCode: " + std::to_string(keyCode) +
            ", keyType: " + std::to_string(keyType) +
            ", keyText: " + (keyText ? keyText : "null") +
            ", unicode: " + std::to_string(unicode) +
            ", action: " + std::to_string(action) +
            ", capsLock: " + (capsLockOn ? "ON" : "OFF");
    
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "KeyEvent: %{public}s", keyInfo.c_str());
    }
    
    // 处理鼠标事件
    void HandleMouseEvent(ArkUI_NodeEvent *event, ArkUI_UIInputEvent *inputEvent)
    {
        auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "Mouse event triggered (eventType=%{public}d)", eventType);
    
        // 获取坐标信息
        auto x = OH_ArkUI_PointerEvent_GetX(inputEvent);
        auto y = OH_ArkUI_PointerEvent_GetY(inputEvent);
        // 获取鼠标按键类型
        auto mouseButton = OH_ArkUI_MouseEvent_GetMouseButton(inputEvent);
        // 获取鼠标动作类型
        auto mouseAction = OH_ArkUI_MouseEvent_GetMouseAction(inputEvent);
        // 获取鼠标移动增量
        auto deltaX = OH_ArkUI_MouseEvent_GetRawDeltaX(inputEvent);
        auto deltaY = OH_ArkUI_MouseEvent_GetRawDeltaY(inputEvent);
        // 获取事件时间
        auto eventTime = OH_ArkUI_UIInputEvent_GetEventTime(inputEvent);
    
        std::string mouseInfo = "x: " + std::to_string(x) +
            ", y: " + std::to_string(y) +
            ", button: " + std::to_string(mouseButton) +
            ", action: " + std::to_string(mouseAction) +
            ", deltaX: " + std::to_string(deltaX) +
            ", deltaY: " + std::to_string(deltaY) +
            ", eventTime: " + std::to_string(eventTime);
    
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "MouseEvent: %{public}s", mouseInfo.c_str());
    }
    ```

    注册节点事件：
    <!-- @[register_node_events](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/NormalNodeExample.h) -->
    
    ``` C
    // 注册节点事件
    void RegisterNodeEvents(ArkUI_NativeNodeAPI_1 *nodeAPI,
                            std::shared_ptr<ArkUIButtonNode> button,
                            std::shared_ptr<ArkUITextInputNode> textInput,
                            std::shared_ptr<ArkUIColumnNode> hoverColumn)
    {
        // 注册点击事件
        nodeAPI->registerNodeEvent(button->GetHandle(), NODE_ON_CLICK_EVENT, 0, nullptr);
        // 注册焦点事件
        nodeAPI->registerNodeEvent(textInput->GetHandle(), NODE_ON_FOCUS, 0, nullptr);
        // 注册失焦事件
        nodeAPI->registerNodeEvent(textInput->GetHandle(), NODE_ON_BLUR, 0, nullptr);
        // 注册悬停事件
        nodeAPI->registerNodeEvent(hoverColumn->GetHandle(), NODE_ON_HOVER_EVENT, 0, nullptr);
        // 注册键盘事件
        nodeAPI->registerNodeEvent(textInput->GetHandle(), NODE_ON_KEY_EVENT, 0, nullptr);
        // 注册鼠标事件
        nodeAPI->registerNodeEvent(hoverColumn->GetHandle(), NODE_ON_MOUSE, 0, nullptr);
    }
    ```

    注册全局事件监听器，通过switch-case分发到对应的处理函数：
    <!-- @[register_global_event_receiver](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/NormalNodeExample.h) -->
    
    ``` C
    // 注册全局事件监听器
    void RegisterGlobalEventReceiver(ArkUI_NativeNodeAPI_1 *nodeAPI)
    {
        nodeAPI->registerNodeEventReceiver([](ArkUI_NodeEvent *event) {
            auto *inputEvent = OH_ArkUI_NodeEvent_GetInputEvent(event);
            auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
    
            OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                         "Event received: eventType=%{public}d", eventType);
    
            auto nodeHandle = OH_ArkUI_NodeEvent_GetNodeHandle(event);
            OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                         "NodeHandle: nodeHandle=%{public}p", nodeHandle);
    
            switch (eventType) {
                case NODE_ON_CLICK_EVENT:
                    HandleClickEvent(event, inputEvent);
                    break;
                case NODE_ON_FOCUS:
                    HandleFocusEvent(event);
                    break;
                case NODE_ON_BLUR:
                    HandleBlurEvent(event);
                    break;
                case NODE_ON_HOVER_EVENT:
                    HandleHoverEvent(event, inputEvent);
                    break;
                case NODE_ON_KEY_EVENT:
                    HandleKeyEvent(event, inputEvent);
                    break;
                case NODE_ON_MOUSE:
                    HandleMouseEvent(event, inputEvent);
                    break;
                default:
                    break;
            }
        });
    }
    ```


- 深浅色变更事件

  ArkUI开发框架在NDK接口提供了以组件为注册单位的系统深浅色变更事件，系统通过在深浅色变更时通知注册在组件上的回调，实现NDK侧的深浅色变更能力。

  > **说明：**
  > - 一个回调内可以自行设计多个组件的深浅色变更。
  > - 同一组件仅能注册一个系统深浅变更回调。
  > - 建议注册在页面内不会被销毁的节点，防止因节点销毁导致的回调失效。

    <!-- @[shade_change_event](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/Function.h) -->
    
    ``` C
    struct ColorModeInfo {
        const char* lightMsg;
        const char* darkMsg;
    };
    
    // 注册回调函数
    void onColorModeChange(ArkUI_SystemColorMode colorMode, void *userData)
    {
        ColorModeInfo* info = static_cast<ColorModeInfo*>(userData);
        if (colorMode == ARKUI_SYSTEM_COLOR_MODE_LIGHT) {
            OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "[Sample_NdkAddInteractionEvent]",
                         "NdkAddInteractionEvent_Light mode: ", info->lightMsg);
        } else if (colorMode == ARKUI_SYSTEM_COLOR_MODE_DARK) {
            OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "[Sample_NdkAddInteractionEvent]",
                         "NdkAddInteractionEvent_Dark mode: ", info->darkMsg);
        }
    }
    
    ArkUI_NodeHandle testColorModeChange(ArkUI_NativeNodeAPI_1 *nodeAPI) {
        ArkUI_NodeHandle text = nodeAPI->createNode(ARKUI_NODE_TEXT);
        static ColorModeInfo info = {"Light mode", "Dark mode"};
        OH_ArkUI_RegisterSystemColorModeChangeEvent(text, &info, onColorModeChange);
    
        ArkUI_AttributeItem itemstring = {nullptr, 0, ("test_light_dark")};
        nodeAPI->setAttribute(text, NODE_TEXT_CONTENT, &itemstring);
    
        return text;
    }
    ```


## 完整示例

1. ArkUIButtonNode对象中实现Button组件封装。
    <!-- @[Cpp_ArkUIButtonNode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/ArkUIButtonNode.h) -->
    
    ``` C
    // ArkUIButtonNode.h
    #ifndef MYAPPLICATION_ARKUIBUTTONNODE_H
    #define MYAPPLICATION_ARKUIBUTTONNODE_H
    
    #include "ArkUINode.h"
    #include <string>
    
    namespace NativeModule {
    
    class ArkUIButtonNode : public ArkUINode {
    public:
        ArkUIButtonNode()
            : ArkUINode((NativeModuleInstance::GetInstance()->GetNativeNodeAPI())->createNode(ARKUI_NODE_BUTTON)) {}
    
        ~ArkUIButtonNode() override {}
    
        void SetLabel(const std::string &label)
        {
            ArkUI_AttributeItem item = {nullptr, 0, label.c_str()};
            nativeModule_->setAttribute(handle_, NODE_BUTTON_LABEL, &item);
        }
    };
    
    } // namespace NativeModule
    
    #endif // MYAPPLICATION_ARKUIBUTTONNODE_H
    ```

2. ArkUIColumnNode对象中实现Column组件封装。
    <!-- @[Cpp_ArkUIColumnNode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/ArkUIColumnNode.h) -->
    
    ``` C
    // ArkUIColumnNode.h
    #ifndef MYAPPLICATION_ARKUICOLUMNNODE_H
    #define MYAPPLICATION_ARKUICOLUMNNODE_H
    
    #include "ArkUINode.h"
    
    namespace NativeModule {
    
    class ArkUIColumnNode : public ArkUINode {
    public:
        ArkUIColumnNode()
            : ArkUINode((NativeModuleInstance::GetInstance()->GetNativeNodeAPI())->createNode(ARKUI_NODE_COLUMN)) {}
    
        ~ArkUIColumnNode() override {}
    };
    
    } // namespace NativeModule
    
    #endif // MYAPPLICATION_ARKUICOLUMNNODE_H
    ```

3. ArkUITextInputNode对象中实现TextInput组件封装。
    <!-- @[Cpp_ArkUITextInputNode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/ArkUITextInputNode.h) -->
    
    ``` C
    // ArkUITextInputNode.h
    #ifndef MYAPPLICATION_ARKUITEXTINPUTNODE_H
    #define MYAPPLICATION_ARKUITEXTINPUTNODE_H
    
    #include "ArkUINode.h"
    #include <string>
    
    namespace NativeModule {
    
    class ArkUITextInputNode : public ArkUINode {
    public:
        ArkUITextInputNode()
            : ArkUINode((NativeModuleInstance::GetInstance()->GetNativeNodeAPI())->createNode(ARKUI_NODE_TEXT_INPUT)) {}
    
        ~ArkUITextInputNode() override {}
    
        void SetPlaceholder(const std::string &placeholder)
        {
            ArkUI_AttributeItem item = {nullptr, 0, placeholder.c_str()};
            nativeModule_->setAttribute(handle_, NODE_TEXT_INPUT_PLACEHOLDER, &item);
        }
    
        void SetType(ArkUI_TextInputType type)
        {
            ArkUI_NumberValue value[] = {{.i32 = type}};
            ArkUI_AttributeItem item = {value, 1};
            nativeModule_->setAttribute(handle_, NODE_TEXT_INPUT_TYPE, &item);
        }
    };
    
    } // namespace NativeModule
    
    #endif // MYAPPLICATION_ARKUITEXTINPUTNODE_H
    ```

4. 在NormalNodeExample对象中实现事件处理函数和事件注册逻辑。

    <!-- @[Cpp_NormalNodeExample](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/NormalNodeExample.h) -->
    
    ``` C
    // NormalNodeExample.h
    // 添加交互事件示例
    #ifndef MYAPPLICATION_NORMALNODEEXAMPLE_H
    #define MYAPPLICATION_NORMALNODEEXAMPLE_H
    
    #include "ArkUIColumnNode.h"
    #include "ArkUIButtonNode.h"
    #include "ArkUITextInputNode.h"
    #include "ArkUITextNode.h"
    #include "NativeModule.h"
    #include <arkui/native_key_event.h>
    #include <arkui/ui_input_event.h>
    #include <hilog/log.h>
    #include <string>
    
    #define DEFAULT_BLANK 20
    #define DEFAULT_COMPONENT_HEIGHT 50.0f
    #define DEFAULT_FONT_SIZE 16.0f
    #define DEFAULT_SPACING 10.0f
    #define DEFAULT_RADIUS 20.0f
    
    namespace NativeModule {
    
    #define LOG_PRINT_DOMAIN 0x0001
    
    // 创建Button组件
    std::shared_ptr<ArkUIButtonNode> CreateButtonComponent()
    {
        auto button = std::make_shared<ArkUIButtonNode>();
        button->SetPercentWidth(1.0f);
        button->SetHeight(DEFAULT_COMPONENT_HEIGHT);
        button->SetLabel("test click");
        button->SetMargin(DEFAULT_BLANK, 0, DEFAULT_BLANK, 0);
        return button;
    }
    
    // 创建TextInput组件
    std::shared_ptr<ArkUITextInputNode> CreateTextInputComponent()
    {
        auto textInput = std::make_shared<ArkUITextInputNode>();
        textInput->SetPercentWidth(1.0f);
        textInput->SetHeight(DEFAULT_COMPONENT_HEIGHT);
        textInput->SetPlaceholder("test focus/blur/key");
        textInput->SetMargin(0, 0, DEFAULT_BLANK, 0);
        return textInput;
    }
    
    // 创建悬停区域Column组件
    std::shared_ptr<ArkUIColumnNode> CreateHoverColumnComponent()
    {
        auto hoverColumn = std::make_shared<ArkUIColumnNode>();
        hoverColumn->SetPercentWidth(1.0f);
        hoverColumn->SetHeight(DEFAULT_COMPONENT_HEIGHT);
        hoverColumn->SetBackgroundColor(0xFFF5F5F5);
        hoverColumn->SetBorderRadius(DEFAULT_RADIUS);
    
        auto hoverText = std::make_shared<ArkUITextNode>();
        hoverText->SetTextContent("test hover/mouse");
        hoverText->SetFontSize(DEFAULT_FONT_SIZE);
        hoverColumn->AddChild(hoverText);
    
        return hoverColumn;
    }
    
    // 处理点击事件
    void HandleClickEvent(ArkUI_NodeEvent *event, ArkUI_UIInputEvent *inputEvent)
    {
        auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "Click event triggered (eventType=%{public}d)", eventType);
    
        auto x = OH_ArkUI_PointerEvent_GetX(inputEvent);
        auto y = OH_ArkUI_PointerEvent_GetY(inputEvent);
        auto displayX = OH_ArkUI_PointerEvent_GetDisplayX(inputEvent);
        auto displayY = OH_ArkUI_PointerEvent_GetDisplayY(inputEvent);
        auto windowX = OH_ArkUI_PointerEvent_GetWindowX(inputEvent);
        auto windowY = OH_ArkUI_PointerEvent_GetWindowY(inputEvent);
        auto pointerCount = OH_ArkUI_PointerEvent_GetPointerCount(inputEvent);
        auto xByIndex = OH_ArkUI_PointerEvent_GetXByIndex(inputEvent, 0);
        auto yByIndex = OH_ArkUI_PointerEvent_GetYByIndex(inputEvent, 0);
        auto displayXByIndex = OH_ArkUI_PointerEvent_GetDisplayXByIndex(inputEvent, 0);
        auto displayYByIndex = OH_ArkUI_PointerEvent_GetDisplayYByIndex(inputEvent, 0);
        auto windowXByIndex = OH_ArkUI_PointerEvent_GetWindowXByIndex(inputEvent, 0);
        auto windowYByIndex = OH_ArkUI_PointerEvent_GetWindowYByIndex(inputEvent, 0);
        auto pointerId = OH_ArkUI_PointerEvent_GetPointerId(inputEvent, 0);
        auto pressure = OH_ArkUI_PointerEvent_GetPressure(inputEvent, 0);
        auto action = OH_ArkUI_UIInputEvent_GetAction(inputEvent);
        auto eventTime = OH_ArkUI_UIInputEvent_GetEventTime(inputEvent);
        auto sourceType = OH_ArkUI_UIInputEvent_GetSourceType(inputEvent);
        auto type = OH_ArkUI_UIInputEvent_GetType(inputEvent);
    
        std::string eventInfo =
            "x: " + std::to_string(x) + ", y: " + std::to_string(y) +
            ", displayX: " + std::to_string(displayX) + ", displayY: " + std::to_string(displayY) +
            ", windowX: " + std::to_string(windowX) + ", windowY: " + std::to_string(windowY) +
            ", pointerCount: " + std::to_string(pointerCount) + ", xByIndex: " + std::to_string(xByIndex) +
            ", yByIndex: " + std::to_string(yByIndex) +
            ", displayXByIndex: " + std::to_string(displayXByIndex) +
            ", displayYByIndex: " + std::to_string(displayYByIndex) +
            ", windowXByIndex: " + std::to_string(windowXByIndex) +
            ", windowYByIndex: " + std::to_string(windowYByIndex) +
            ", pointerId: " + std::to_string(pointerId) + ", pressure: " + std::to_string(pressure) +
            ", action: " + std::to_string(action) + ", eventTime: " + std::to_string(eventTime) +
            ", sourceType: " + std::to_string(sourceType) + ", type: " + std::to_string(type);
    
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "ClickEvent: %{public}s", eventInfo.c_str());
    }
    
    // 处理焦点事件
    void HandleFocusEvent(ArkUI_NodeEvent *event)
    {
        auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "Focus event triggered (eventType=%{public}d)", eventType);
        auto nodeHandle = OH_ArkUI_NodeEvent_GetNodeHandle(event);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "FocusEvent: nodeHandle=%{public}p", nodeHandle);
    }
    
    // 处理失焦事件
    void HandleBlurEvent(ArkUI_NodeEvent *event)
    {
        auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "Blur event triggered (eventType=%{public}d)", eventType);
        auto nodeHandle = OH_ArkUI_NodeEvent_GetNodeHandle(event);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "BlurEvent: nodeHandle=%{public}p", nodeHandle);
    }
    
    // 处理悬停事件
    void HandleHoverEvent(ArkUI_NodeEvent *event, ArkUI_UIInputEvent *inputEvent)
    {
        auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "Hover event triggered (eventType=%{public}d)", eventType);
        auto x = OH_ArkUI_PointerEvent_GetX(inputEvent);
        auto y = OH_ArkUI_PointerEvent_GetY(inputEvent);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "HoverEvent: x=%{public}f, y=%{public}f", x, y);
    }
    
    // 处理键盘事件
    void HandleKeyEvent(ArkUI_NodeEvent *event, ArkUI_UIInputEvent *inputEvent)
    {
        auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "Key event triggered (eventType=%{public}d)", eventType);
    
        // 获取按键键码
        auto keyCode = OH_ArkUI_KeyEvent_GetKeyCode(inputEvent);
        // 获取按键类型
        auto keyType = OH_ArkUI_KeyEvent_GetType(inputEvent);
        // 获取按键键值
        const char *keyText = OH_ArkUI_KeyEvent_GetKeyText(inputEvent);
        // 获取Unicode码值
        auto unicode = OH_ArkUI_KeyEvent_GetUnicode(inputEvent);
        // 获取按键动作
        auto action = OH_ArkUI_UIInputEvent_GetAction(inputEvent);
    
        // 获取CapsLock状态
        bool capsLockOn = false;
        auto capsLockResult = OH_ArkUI_KeyEvent_IsCapsLockOn(inputEvent, &capsLockOn);
    
        std::string keyInfo = "keyCode: " + std::to_string(keyCode) +
            ", keyType: " + std::to_string(keyType) +
            ", keyText: " + (keyText ? keyText : "null") +
            ", unicode: " + std::to_string(unicode) +
            ", action: " + std::to_string(action) +
            ", capsLock: " + (capsLockOn ? "ON" : "OFF");
    
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "KeyEvent: %{public}s", keyInfo.c_str());
    }
    
    // 处理鼠标事件
    void HandleMouseEvent(ArkUI_NodeEvent *event, ArkUI_UIInputEvent *inputEvent)
    {
        auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "Mouse event triggered (eventType=%{public}d)", eventType);
    
        // 获取坐标信息
        auto x = OH_ArkUI_PointerEvent_GetX(inputEvent);
        auto y = OH_ArkUI_PointerEvent_GetY(inputEvent);
        // 获取鼠标按键类型
        auto mouseButton = OH_ArkUI_MouseEvent_GetMouseButton(inputEvent);
        // 获取鼠标动作类型
        auto mouseAction = OH_ArkUI_MouseEvent_GetMouseAction(inputEvent);
        // 获取鼠标移动增量
        auto deltaX = OH_ArkUI_MouseEvent_GetRawDeltaX(inputEvent);
        auto deltaY = OH_ArkUI_MouseEvent_GetRawDeltaY(inputEvent);
        // 获取事件时间
        auto eventTime = OH_ArkUI_UIInputEvent_GetEventTime(inputEvent);
    
        std::string mouseInfo = "x: " + std::to_string(x) +
            ", y: " + std::to_string(y) +
            ", button: " + std::to_string(mouseButton) +
            ", action: " + std::to_string(mouseAction) +
            ", deltaX: " + std::to_string(deltaX) +
            ", deltaY: " + std::to_string(deltaY) +
            ", eventTime: " + std::to_string(eventTime);
    
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                     "MouseEvent: %{public}s", mouseInfo.c_str());
    }
    
    // 注册节点事件
    void RegisterNodeEvents(ArkUI_NativeNodeAPI_1 *nodeAPI,
                            std::shared_ptr<ArkUIButtonNode> button,
                            std::shared_ptr<ArkUITextInputNode> textInput,
                            std::shared_ptr<ArkUIColumnNode> hoverColumn)
    {
        // 注册点击事件
        nodeAPI->registerNodeEvent(button->GetHandle(), NODE_ON_CLICK_EVENT, 0, nullptr);
        // 注册焦点事件
        nodeAPI->registerNodeEvent(textInput->GetHandle(), NODE_ON_FOCUS, 0, nullptr);
        // 注册失焦事件
        nodeAPI->registerNodeEvent(textInput->GetHandle(), NODE_ON_BLUR, 0, nullptr);
        // 注册悬停事件
        nodeAPI->registerNodeEvent(hoverColumn->GetHandle(), NODE_ON_HOVER_EVENT, 0, nullptr);
        // 注册键盘事件
        nodeAPI->registerNodeEvent(textInput->GetHandle(), NODE_ON_KEY_EVENT, 0, nullptr);
        // 注册鼠标事件
        nodeAPI->registerNodeEvent(hoverColumn->GetHandle(), NODE_ON_MOUSE, 0, nullptr);
    }
    
    // 注册全局事件监听器
    void RegisterGlobalEventReceiver(ArkUI_NativeNodeAPI_1 *nodeAPI)
    {
        nodeAPI->registerNodeEventReceiver([](ArkUI_NodeEvent *event) {
            auto *inputEvent = OH_ArkUI_NodeEvent_GetInputEvent(event);
            auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
    
            OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                         "Event received: eventType=%{public}d", eventType);
    
            auto nodeHandle = OH_ArkUI_NodeEvent_GetNodeHandle(event);
            OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "[InteractionEventExample]",
                         "NodeHandle: nodeHandle=%{public}p", nodeHandle);
    
            switch (eventType) {
                case NODE_ON_CLICK_EVENT:
                    HandleClickEvent(event, inputEvent);
                    break;
                case NODE_ON_FOCUS:
                    HandleFocusEvent(event);
                    break;
                case NODE_ON_BLUR:
                    HandleBlurEvent(event);
                    break;
                case NODE_ON_HOVER_EVENT:
                    HandleHoverEvent(event, inputEvent);
                    break;
                case NODE_ON_KEY_EVENT:
                    HandleKeyEvent(event, inputEvent);
                    break;
                case NODE_ON_MOUSE:
                    HandleMouseEvent(event, inputEvent);
                    break;
                default:
                    break;
            }
        });
    }
    
    // 创建交互事件示例
    std::shared_ptr<ArkUIBaseNode> CreateExample()
    {
        auto *nodeAPI = NativeModuleInstance::GetInstance()->GetNativeNodeAPI();
    
        auto column = std::make_shared<ArkUIColumnNode>();
        column->SetPercentWidth(1.0f);
        column->SetPercentHeight(1.0f);
    
        // 创建Button组件用于注册点击事件
        auto button = CreateButtonComponent();
        column->AddChild(button);
    
        // 创建TextInput组件用于注册焦点、失焦、键盘事件
        auto textInput = CreateTextInputComponent();
        column->AddChild(textInput);
    
        // 创建Column组件用于注册悬停、鼠标事件
        auto hoverColumn = CreateHoverColumnComponent();
        column->AddChild(hoverColumn);
    
        // 注册各组件的节点事件
        RegisterNodeEvents(nodeAPI, button, textInput, hoverColumn);
    
        // 设置全局事件监听器
        RegisterGlobalEventReceiver(nodeAPI);
    
        return column;
    }
    
    } // namespace NativeModule
    
    #endif // MYAPPLICATION_NORMALNODEEXAMPLE_H
    ```

   由于使用了日志相关接口，需要在CMakeLists.txt中添加对libhilog_ndk.z.so的引用，如下：
   
   ```text
   add_library(entry SHARED napi_init.cpp NativeEntry.cpp)
   target_link_libraries(entry PUBLIC libace_napi.z.so libace_ndk.z.so libhilog_ndk.z.so)
   ```
