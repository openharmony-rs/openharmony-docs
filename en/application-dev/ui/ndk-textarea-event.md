# Listening for Text Box Events
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @kangshihui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

Text boxes support various interactive behaviors, allowing you to register event listeners and obtain status information.

Real-time search: Register the [NODE_TEXT_AREA_ON_CHANGE](../../application-dev/reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype) event to receive notifications and obtain the current text content when the text box input changes.

Text filtering: Register the [NODE_TEXT_AREA_ON_WILL_INSERT](../../application-dev/reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype) event to receive notifications before text is inserted and control whether to insert text through the return value.

Layout changes during editing: Register the [NODE_TEXT_AREA_ON_EDIT_CHANGE](../../application-dev/reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype) event to receive notifications when the text box editing state changes.

The following example demonstrates how to listen for text box events and parse data based on the [Integrating with ArkTS Pages](../ui/ndk-access-the-arkts-page.md) section.

- Registering events
    
    Events are registered through a unified API. For details, see [registerNodeEvent](../../application-dev/reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent). For details about the event types supported by the text box, see the [ArkUI_NodeEventType](../../application-dev/reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype) section, searching for **NODE_TEXT_AREA_**.

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

- Registering event callbacks

    Event callbacks are registered through a unified API. For details, see [registerNodeEventReceiver](../../application-dev/reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver).

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

- Sample

   This section demonstrates core API usage only. For the complete sample project, see <!--RP1-->[TextAreaEventNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/TextAreaEventNDK)<!--RP1End-->.
    
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
