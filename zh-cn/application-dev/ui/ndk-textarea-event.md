# 监听输入框事件
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @kangshihui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

输入框包含多种交互行为，开发者可注册事件监听并获取状态。

要实现实时搜索功能，可注册[NODE_TEXT_AREA_ON_CHANGE](../../application-dev/reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)事件，输入框文本发生变化时会收到通知，并能获取当前文本内容。

要实现文字过滤功能，可注册[NODE_TEXT_AREA_ON_WILL_INSERT](../../application-dev/reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)事件，在文字即将插入前会收到通知，通过返回值控制文字是否插入。

要实现用户编辑文字前后页面布局的不同，可注册[NODE_TEXT_AREA_ON_EDIT_CHANGE](../../application-dev/reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)事件，输入框编辑状态切换时会收到通知。

以下示例基于[接入ArkTS页面章节](../ui/ndk-access-the-arkts-page.md)，说明如何监听输入框的事件及数据解析。

- 注册事件
    
    事件注册有统一接口，详情请参见[registerNodeEvent](../../application-dev/reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent)。输入框支持的事件类型，请参见[NativeNode组件支持的事件类型定义](../../application-dev/reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)，搜索前缀NODE_TEXT_AREA_。

    <!-- @[obtain_create_textarea](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextAreaEventNDK/entry/src/main/cpp/manager.cpp) -->
    
    ``` C++
    ArkUI_NodeHandle text = nodeApi->createNode(ARKUI_NODE_TEXT);
    ArkUI_NumberValue textWidth[] = {{.f32 = 300}};
    ArkUI_AttributeItem textWidthItem = {.value = textWidth, .size = 1};
    nodeApi->setAttribute(text, NODE_WIDTH, &textWidthItem);
    // ···
    ArkUI_NodeHandle selectionText = nodeApi->createNode(ARKUI_NODE_TEXT);
    ArkUI_NumberValue selectionTextWidth[] = {{.f32 = 300}};
    ArkUI_AttributeItem selectionTextWidthItem = {.value = selectionTextWidth, .size = 1};
    nodeApi->setAttribute(selectionText, NODE_WIDTH, &selectionTextWidthItem);
    // ···
    const ArkUI_AttributeItem *attributeItem = nodeApi->getAttribute(textArea, NODE_UNIQUE_ID);
    auto id = attributeItem->value[0].i32;
    nodeApi->registerNodeEvent(textArea, NODE_TEXT_AREA_ON_CHANGE, id, text);
    nodeApi->registerNodeEvent(textArea, NODE_TEXT_AREA_ON_PASTE, id, text);
    nodeApi->registerNodeEvent(textArea, NODE_TEXT_AREA_ON_TEXT_SELECTION_CHANGE, id, selectionText);
    ```

- 注册事件回调

    事件回调注册有统一接口，详情请参见[registerNodeEventReceiver](../../application-dev/reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver)。

    <!-- @[obtain_textarea_NodeEventReceiver](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextAreaEventNDK/entry/src/main/cpp/manager.cpp) -->
    
    ``` C++
    nodeApi->registerNodeEventReceiver([](ArkUI_NodeEvent *event) {
        ArkUI_NodeEventType eventType = OH_ArkUI_NodeEvent_GetEventType(event);
        ArkUI_AttributeItem content;
        if (eventType == NODE_TEXT_AREA_ON_CHANGE || eventType == NODE_TEXT_AREA_ON_PASTE) {
            ArkUI_StringAsyncEvent *stringEvent = OH_ArkUI_NodeEvent_GetStringAsyncEvent(event);
            content = {.string = stringEvent->pStr };
        } else if (eventType == NODE_TEXT_AREA_ON_TEXT_SELECTION_CHANGE) {
            ArkUI_NodeComponentEvent *componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
            std::stringstream selectContent;
            selectContent << "start: " << componentEvent->data[0].i32 << " , end: " << componentEvent->data[1].i32;
            content = {.string = selectContent.str().c_str() };
        } else {
            return;
        }
        ArkUI_NodeHandle textNode = reinterpret_cast<ArkUI_NodeHandle>(OH_ArkUI_NodeEvent_GetUserData(event));
        if (textNode) {
            ArkUI_NativeNodeAPI_1 *nodeApi = reinterpret_cast<ArkUI_NativeNodeAPI_1 *>(
                OH_ArkUI_QueryModuleInterfaceByName(ARKUI_NATIVE_NODE, "ArkUI_NativeNodeAPI_1"));
            nodeApi->setAttribute(textNode, NODE_TEXT_CONTENT, &content);
        }
    });
    ```

- 完整示例

   本篇示例仅提供核心接口的调用方法，完整的示例工程请参考<!--RP1-->[TextAreaEventNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/TextAreaEventNDK)<!--RP1End-->。
    
    <!-- @[obtain_textarea_all](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextAreaEventNDK/entry/src/main/cpp/manager.cpp) -->
    
    ``` C++
    #include "manager.h"
    #include <sstream>
    #include <arkui/native_interface.h>
    #include <arkui/styled_string.h>
    
    namespace NativeNode::Manager {
    constexpr int32_t NUM_10 = 10;
    constexpr int32_t NUM_28 = 28;
    constexpr int32_t NUM_400 = 400;
    NodeManager &NodeManager::GetInstance()
    {
        static NodeManager instance;
        return instance;
    }
    
    void NodeManager::SetXComponent(OH_NativeXComponent *xComponent) { xComponent_ = xComponent; }
    
    void NodeManager::CreateTextAreaNode()
    {
        if (!xComponent_) {
            return;
        }
        ArkUI_NativeNodeAPI_1 *nodeApi = reinterpret_cast<ArkUI_NativeNodeAPI_1 *>(
            OH_ArkUI_QueryModuleInterfaceByName(ARKUI_NATIVE_NODE, "ArkUI_NativeNodeAPI_1"));
        if (nodeApi == nullptr) {
            return;
        }
        ArkUI_NodeHandle column = nodeApi->createNode(ARKUI_NODE_COLUMN);
        ArkUI_NumberValue colWidth[] = {{.f32 = 300}};
        ArkUI_AttributeItem widthItem = {.value = colWidth, .size = 1};
        nodeApi->setAttribute(column, NODE_WIDTH, &widthItem);
    
        ArkUI_NodeHandle text = nodeApi->createNode(ARKUI_NODE_TEXT);
        ArkUI_NumberValue textWidth[] = {{.f32 = 300}};
        ArkUI_AttributeItem textWidthItem = {.value = textWidth, .size = 1};
        nodeApi->setAttribute(text, NODE_WIDTH, &textWidthItem);
        ArkUI_NumberValue textHeight[] = {{.f32 = 100}};
        ArkUI_AttributeItem textHeightItem = {.value = textHeight, .size = 1};
        nodeApi->setAttribute(text, NODE_HEIGHT, &textHeightItem);
        
        nodeApi->addChild(column, text);
        
        ArkUI_NodeHandle selectionText = nodeApi->createNode(ARKUI_NODE_TEXT);
        ArkUI_NumberValue selectionTextWidth[] = {{.f32 = 300}};
        ArkUI_AttributeItem selectionTextWidthItem = {.value = selectionTextWidth, .size = 1};
        nodeApi->setAttribute(selectionText, NODE_WIDTH, &selectionTextWidthItem);
        nodeApi->addChild(column, selectionText);
        ArkUI_NodeHandle textArea = nodeApi->createNode(ARKUI_NODE_TEXT_AREA);
        ArkUI_NumberValue textAreaWidth[] = {{.f32 = 300}};
        ArkUI_AttributeItem textAreaWidthItem = {.value = textAreaWidth, .size = 1};
        nodeApi->setAttribute(textArea, NODE_WIDTH, &textAreaWidthItem);
    
        ArkUI_NumberValue borderWidth[] = {{.f32 = 1}};
        ArkUI_AttributeItem borderWidthItem = {.value = borderWidth, .size = 1};
        nodeApi->setAttribute(textArea, NODE_BORDER_WIDTH, &borderWidthItem);
    
        const ArkUI_AttributeItem *attributeItem = nodeApi->getAttribute(textArea, NODE_UNIQUE_ID);
        auto id = attributeItem->value[0].i32;
        nodeApi->registerNodeEvent(textArea, NODE_TEXT_AREA_ON_CHANGE, id, text);
        nodeApi->registerNodeEvent(textArea, NODE_TEXT_AREA_ON_PASTE, id, text);
        nodeApi->registerNodeEvent(textArea, NODE_TEXT_AREA_ON_TEXT_SELECTION_CHANGE, id, selectionText);
        TextAreaNodeEventReceiver(nodeApi);
        nodeApi->addChild(column, textArea);
        OH_NativeXComponent_AttachNativeRootNode(xComponent_, column);
    }
    
    void NodeManager::TextAreaNodeEventReceiver(ArkUI_NativeNodeAPI_1* nodeApi)
    {
        nodeApi->registerNodeEventReceiver([](ArkUI_NodeEvent *event) {
            ArkUI_NodeEventType eventType = OH_ArkUI_NodeEvent_GetEventType(event);
            ArkUI_AttributeItem content;
            if (eventType == NODE_TEXT_AREA_ON_CHANGE || eventType == NODE_TEXT_AREA_ON_PASTE) {
                ArkUI_StringAsyncEvent *stringEvent = OH_ArkUI_NodeEvent_GetStringAsyncEvent(event);
                content = {.string = stringEvent->pStr };
            } else if (eventType == NODE_TEXT_AREA_ON_TEXT_SELECTION_CHANGE) {
                ArkUI_NodeComponentEvent *componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
                std::stringstream selectContent;
                selectContent << "start: " << componentEvent->data[0].i32 << " , end: " << componentEvent->data[1].i32;
                content = {.string = selectContent.str().c_str() };
            } else {
                return;
            }
            ArkUI_NodeHandle textNode = reinterpret_cast<ArkUI_NodeHandle>(OH_ArkUI_NodeEvent_GetUserData(event));
            if (textNode) {
                ArkUI_NativeNodeAPI_1 *nodeApi = reinterpret_cast<ArkUI_NativeNodeAPI_1 *>(
                    OH_ArkUI_QueryModuleInterfaceByName(ARKUI_NATIVE_NODE, "ArkUI_NativeNodeAPI_1"));
                nodeApi->setAttribute(textNode, NODE_TEXT_CONTENT, &content);
            }
        });
    }
    } // namespace NativeNode::Manager
    ```


![textarea_getstringevent](figures/textarea_getstringevent.gif)