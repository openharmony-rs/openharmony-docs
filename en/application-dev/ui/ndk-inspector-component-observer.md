# Listening for Component Layout and Drawing Events
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @lmleon-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

Since API version 16, NDK APIs provides functions for registering and unregistering callbacks for UI component layout completion and drawing completion events. You can use the following APIs to listen for when specific node layouts are completed or when drawing is finished, and register corresponding callbacks: Use [OH_ArkUI_RegisterLayoutCallbackOnNodeHandle](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_registerlayoutcallbackonnodehandle) to register a layout completion callback. Use [OH_ArkUI_RegisterDrawCallbackOnNodeHandle](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_registerdrawcallbackonnodehandle) to register a drawing completion callback. Use [OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_unregisterlayoutcallbackonnodehandle) to unregister a layout completion callback. Use [OH_ArkUI_UnregisterDrawCallbackOnNodeHandle](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_unregisterdrawcallbackonnodehandle) to unregister a drawing completion callback.


> **NOTE**
> [OH_ArkUI_RegisterLayoutCallbackOnNodeHandle](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_registerlayoutcallbackonnodehandle) and [OH_ArkUI_RegisterDrawCallbackOnNodeHandle](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_registerdrawcallbackonnodehandle) can be used to listen for component layout completion or drawing completion events, but only one function pointer can be registered, which means subsequent calls will overwrite the previous callbacks.


The following example is based on the [Integrating with ArkTS Pages](ndk-access-the-arkts-page.md) section, supplementing related event listening.
It implements layout and drawing completion event registration logic in the **ArkUITextNode** object.
```c
// ArkUITextNode.h
// Implement an encapsulation class for the text component.

#ifndef MYAPPLICATION_ARKUITEXTNODE_H
#define MYAPPLICATION_ARKUITEXTNODE_H

#include <arkui/native_type.h>
#include <arkui/native_node.h>
#include <hilog/log.h>
#include "ArkUINode.h"
#include <string>

namespace NativeModule {
const unsigned int LOG_PRINT_DOMAIN = 0xFF00;
// Layout completion callback
void OnLayoutCompleted(void* userData) {
    ArkUI_NodeHandle node = (ArkUI_NodeHandle)userData;
    OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "Callback", "the text_node is layout completed");
    ArkUI_NativeNodeAPI_1 *nativeModule = NativeModuleInstance::GetInstance()->GetNativeNodeAPI();
    ArkUI_AttributeItem item = {nullptr, 0, "layout callback"};
    nativeModule->setAttribute(node, NODE_TEXT_CONTENT, &item);
}
// Drawing completion callback
void OnDrawCompleted(void* userData) {
    ArkUI_NodeHandle node = (ArkUI_NodeHandle)userData;
    OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "Callback", "the text_node is draw completed");
    ArkUI_NativeNodeAPI_1 *nativeModule = NativeModuleInstance::GetInstance()->GetNativeNodeAPI();
    ArkUI_AttributeItem item = {nullptr, 0, "draw callback"};
    nativeModule->setAttribute(node, NODE_TEXT_CONTENT, &item);
}

class ArkUITextNode : public ArkUINode {
public:
    ArkUITextNode()
        : ArkUINode((NativeModuleInstance::GetInstance()->GetNativeNodeAPI())->createNode(ARKUI_NODE_TEXT)) {}
    void SetFontSize(float fontSize) {
        assert(handle_);
        ArkUI_NumberValue value[] = {{.f32 = fontSize}};
        ArkUI_AttributeItem item = {value, 1};
        nativeModule_->setAttribute(handle_, NODE_FONT_SIZE, &item);
    }
    void SetFontColor(uint32_t color) {
        assert(handle_);
        ArkUI_NumberValue value[] = {{.u32 = color}};
        ArkUI_AttributeItem item = {value, 1};
        nativeModule_->setAttribute(handle_, NODE_FONT_COLOR, &item);
    }
    void SetTextContent(const std::string &content) {
        assert(handle_);
        ArkUI_AttributeItem item = {nullptr, 0, content.c_str()};
        nativeModule_->setAttribute(handle_, NODE_TEXT_CONTENT, &item);
    }
    void SetTextAlign(ArkUI_TextAlignment align) {
        assert(handle_);
        ArkUI_NumberValue value[] = {{.i32 = align}};
        ArkUI_AttributeItem item = {value, 1};
        nativeModule_->setAttribute(handle_, NODE_TEXT_ALIGN, &item);
    }
    void SetLayoutCallBack(int32_t nodeId) {
        assert(handle_);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "Callback", "set layout callback");
        // Register a layout completion callback.
        OH_ArkUI_RegisterLayoutCallbackOnNodeHandle(handle_, this, OnLayoutCompleted);
    }
    void ResetLayoutCallBack() {
        assert(handle_);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "Callback", "reset layout callback");
        // Unregister the layout completion callback.
        OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle(handle_);
    }
    void SetDrawCallBack(int32_t nodeId) {
        assert(handle_);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "Callback", "set draw callback");
        // Register a drawing completion callback.
        OH_ArkUI_RegisterDrawCallbackOnNodeHandle(handle_, this, OnDrawCompleted);
    }
    void ResetDrawCallBack() {
        assert(handle_);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "Callback", "reset draw callback");
        // Unregister the drawing completion callback.
        OH_ArkUI_UnregisterDrawCallbackOnNodeHandle(handle_);
    }
    void SetInspectorId(std::string inspectorId) {
        ArkUI_AttributeItem item = {nullptr, 0, inspectorId.c_str()};
        nativeModule_->setAttribute(handle_, NODE_ID, &item);
    }
};
} // namespace NativeModule

#endif // MYAPPLICATION_ARKUITEXTNODE_H
```

```c
// NormalTextListExample.h
// Define custom NDK API entry functions.

#ifndef MYAPPLICATION_NORMALTEXTLISTEXAMPLE_H
#define MYAPPLICATION_NORMALTEXTLISTEXAMPLE_H

#include "ArkUIBaseNode.h"
#include "ArkUIListItemNode.h"
#include "ArkUIListNode.h"
#include "ArkUITextNode.h"
#include <hilog/log.h>

namespace NativeModule {

std::shared_ptr<ArkUIBaseNode> CreateTextListExample() {
    // Create and mount the component.
    // 1: Use smart pointers to create a List component.
    auto list = std::make_shared<ArkUIListNode>();
    list->SetPercentWidth(1);
    list->SetPercentHeight(1);
    // 2: Create a ListItem child component and mount it to the List component.
    for (int32_t i = 0; i < 1; ++i) {
        auto listItem = std::make_shared<ArkUIListItemNode>();
        auto textNode = std::make_shared<ArkUITextNode>();
        textNode->SetTextContent(std::to_string(i));
        textNode->SetFontSize(16);
        textNode->SetPercentWidth(1);
        textNode->SetHeight(100);
        textNode->SetBackgroundColor(0xFFfffacd);
        textNode->SetTextAlign(ARKUI_TEXT_ALIGNMENT_CENTER);
        // Register a layout callback for the current node.
        textNode->SetLayoutCallBack(i);
        // Register rendering display callback for the current node.
        textNode->SetDrawCallBack(i);
        listItem->AddChild(textNode);
        list->AddChild(listItem);
    }
    return list;
}
} // namespace NativeModule

#endif // MYAPPLICATION_NORMALTEXTLISTEXAMPLE_H
```
