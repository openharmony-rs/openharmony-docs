# 监听组件布局和绘制送显事件
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @lmleon-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

从API version 16开始，NDK接口针对UI组件的布局或绘制送显完成，提供了注册与取消监听函数的方式。开发者可使用如下接口监听指定节点布局完成或者绘制送显完成的时机，并注册相应的回调函数。可使用[OH_ArkUI_RegisterLayoutCallbackOnNodeHandle](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_registerlayoutcallbackonnodehandle)注册组件布局完成的回调方法。可使用[OH_ArkUI_RegisterDrawCallbackOnNodeHandle](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_registerdrawcallbackonnodehandle)注册绘制送显完成的回调方法。可使用[OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_unregisterlayoutcallbackonnodehandle)取消组件布局完成的回调方法注册。可使用[OH_ArkUI_UnregisterDrawCallbackOnNodeHandle](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_unregisterdrawcallbackonnodehandle)取消绘制送显完成的回调方法注册。


> **说明：**
> [OH_ArkUI_RegisterLayoutCallbackOnNodeHandle](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_registerlayoutcallbackonnodehandle)和[OH_ArkUI_RegisterDrawCallbackOnNodeHandle](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_registerdrawcallbackonnodehandle)能够监听组件的布局完成或者绘制送显完成事件触发，但只能传递一个函数指针，多次调用使用最后一次的函数指针进行回调。


以下示例基于[接入ArkTS页面](ndk-access-the-arkts-page.md)章节，补充相关事件监听。
在ArkUITextNode对象中实现布局或者绘制送显完成事件注册逻辑。
<!-- @[arkUITestNode_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NativeNodeUtilsSample/entry/src/main/cpp/ArkUITextNode.h) -->

``` C
// ArkUITextNode.h
// 实现文本组件的封装类。
#ifndef MYAPPLICATION_ARKUITEXTNODE_H
#define MYAPPLICATION_ARKUITEXTNODE_H

#include <arkui/native_type.h>
#include <arkui/native_node.h>
#include <hilog/log.h>
#include "ArkUINode.h"
#include <string>

// ···
namespace NativeModule {
const unsigned int LOG_PRINT_DOMAIN = 0xFF00;
// 布局完成的回调方法
void OnLayoutCompleted(void *userData)
{
    ArkUI_NodeHandle node = (ArkUI_NodeHandle)userData;
    OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "Callback", "the text_node is layout completed");
    ArkUI_NativeNodeAPI_1 *nativeModule = NativeModuleInstance::GetInstance()->GetNativeNodeAPI();
    ArkUI_AttributeItem item = {nullptr, 0, "layout callback"};
    nativeModule->setAttribute(node, NODE_TEXT_CONTENT, &item);
}
// 绘制送显完成的回调方法
void OnDrawCompleted(void *userData)
{
    ArkUI_NodeHandle node = (ArkUI_NodeHandle)userData;
    OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "Callback", "the text_node is draw completed");
    ArkUI_NativeNodeAPI_1 *nativeModule = NativeModuleInstance::GetInstance()->GetNativeNodeAPI();
    ArkUI_AttributeItem item = {nullptr, 0, "draw callback"};
    nativeModule->setAttribute(node, NODE_TEXT_CONTENT, &item);
}
// ···
class ArkUITextNode : public ArkUINode {
public:
    ArkUITextNode()
        : ArkUINode((NativeModuleInstance::GetInstance()->GetNativeNodeAPI())->createNode(ARKUI_NODE_TEXT)) {}
    void SetFontSize(float fontSize)
    {
        ArkUI_NumberValue value[] = {{.f32 = fontSize}};
        ArkUI_AttributeItem item = {value, 1};
        nativeModule_->setAttribute(handle_, NODE_FONT_SIZE, &item);
    }
    void SetFontColor(uint32_t color)
    {
        ArkUI_NumberValue value[] = {{.u32 = color}};
        ArkUI_AttributeItem item = {value, 1};
        nativeModule_->setAttribute(handle_, NODE_FONT_COLOR, &item);
    }
    void SetTextContent(const std::string &content)
    {
        ArkUI_AttributeItem item = {nullptr, 0, content.c_str()};
        nativeModule_->setAttribute(handle_, NODE_TEXT_CONTENT, &item);
    }
    void SetTextAlign(ArkUI_TextAlignment align)
    {
        ArkUI_NumberValue value[] = {{.i32 = align}};
        ArkUI_AttributeItem item = {value, 1};
        nativeModule_->setAttribute(handle_, NODE_TEXT_ALIGN, &item);
    }
    void SetLayoutCallBack(int32_t nodeId)
    {
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "Callback", "set layout callback");
        // 注册布局完成的回调方法
        OH_ArkUI_RegisterLayoutCallbackOnNodeHandle(handle_, this, OnLayoutCompleted);
    }
    void ResetLayoutCallBack()
    {
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "Callback", "reset layout callback");
        // 取消注册布局完成的回调方法
        OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle(handle_);
    }
    void SetDrawCallBack(int32_t nodeId)
    {
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "Callback", "set draw callback");
        // 注册绘制送显完成的回调方法
        OH_ArkUI_RegisterDrawCallbackOnNodeHandle(handle_, this, OnDrawCompleted);
    }
    void ResetDrawCallBack()
    {
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "Callback", "reset draw callback");
        // 取消注册绘制送显完成的回调方法
        OH_ArkUI_UnregisterDrawCallbackOnNodeHandle(handle_);
    }
    void SetInspectorId(std::string inspectorId)
    {
        ArkUI_AttributeItem item = {nullptr, 0, inspectorId.c_str()};
        nativeModule_->setAttribute(handle_, NODE_ID, &item);
    }
    // ···
};
} // namespace NativeModule

#endif // MYAPPLICATION_ARKUITEXTNODE_H
```

<!-- @[normalTextListExample_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NativeNodeUtilsSample/entry/src/main/cpp/NormalTextListExample.h) -->

``` C
// NormalTextListExample.h
// 自定义接入入口函数

#ifndef MYAPPLICATION_NORMALTEXTLISTEXAMPLE_H
#define MYAPPLICATION_NORMALTEXTLISTEXAMPLE_H

#include "ArkUIBaseNode.h"
#include "ArkUIListItemNode.h"
#include "ArkUIListNode.h"
#include "ArkUITextNode.h"
#include <hilog/log.h>
#define SIZE_16 16
#define SIZE_100 100
#define COLOR_BACKGROUND 0xFFfffacd

namespace NativeModule {

std::shared_ptr<ArkUIBaseNode> CreateTextListExample()
{
    // 创建组件并挂载
    // 1：使用智能指针创建List组件。
    auto list = std::make_shared<ArkUIListNode>();
    list->SetPercentWidth(1);
    list->SetPercentHeight(1);
    // 2：创建ListItem子组件并挂载到List上。
    for (int32_t i = 0; i < 1; ++i) {
        auto listItem = std::make_shared<ArkUIListItemNode>();
        auto textNode = std::make_shared<ArkUITextNode>();
        textNode->SetTextContent(std::to_string(i));
        textNode->SetFontSize(SIZE_16);
        textNode->SetPercentWidth(1);
        textNode->SetHeight(SIZE_100);
        textNode->SetBackgroundColor(COLOR_BACKGROUND);
        textNode->SetTextAlign(ARKUI_TEXT_ALIGNMENT_CENTER);
        // 在当前节点注册布局回调
        textNode->SetLayoutCallBack(i);
        // 在当前节点注册绘制送显回调
        textNode->SetDrawCallBack(i);
        listItem->AddChild(textNode);
        list->AddChild(listItem);
    }
    return list;
}
} // namespace NativeModule

#endif // MYAPPLICATION_NORMALTEXTLISTEXAMPLE_H
```