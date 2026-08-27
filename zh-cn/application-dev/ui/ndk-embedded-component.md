# 通过EmbeddedComponent拉起EmbeddedUIExtensionAbility
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

ArkUI在Native侧提供的能力是ArkTS的子集，某些能力不会在Native侧提供，例如声明式UI语法、自定义struct组件及UI系统预置UI组件库。


从API version 20开始，ArkUI开发框架提供了Native侧嵌入EmbeddedComponent组件的能力，此能力依赖于EmbeddedComponent机制。EmbeddedComponent用于支持在当前页面嵌入同一应用内其他EmbeddedUIExtensionAbility提供的UI。EmbeddedUIExtensionAbility在独立进程中运行，负责页面布局和渲染。此功能主要用于有进程隔离需求的模块化开发场景。


> **说明：**
>
> - 使用OH_ArkUI_EmbeddedComponentOption_Create获取ArkUI_EmbeddedComponentOption后，可以使用OH_ArkUI_EmbeddedComponentOption_SetOnError设置onError回调，使用OH_ArkUI_EmbeddedComponentOption_SetOnTerminated设置onTerminated回调。可以使用OH_ArkUI_NodeUtils_MoveTo迁移节点。
>
> - 使用OH_ArkUI_EmbeddedComponentOption_SetOnTerminated设置onTerminated回调时，返回的want参数只支持解析提供方返回的key-value，不支持嵌套解析。
>
> - 在EmbeddedComponentOption属性设置完成后，调用OH_ArkUI_EmbeddedComponentOption_Dispose释放内存，避免内存泄漏。
>
> - EmbeddedComponent组件需要使用setAttribute设置宽高才能显示。

本示例展示EmbeddedComponent组件NDK的基础使用方式，ability相关使用请参考EmbeddedComponent。示例应用的bundleName为"com.example.uiextensionandaccessibility"，同一应用下被拉起的EmbeddedUIExtensionAbility为"ExampleEmbeddedAbility"。本示例仅支持在具有多进程权限的设备上运行，例如PC/2in1。

<!-- @[embeddedComponentCTest_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility/entry/src/main/cpp/embedded/embedded.cpp) -->

``` C++
#include <arkui/native_node.h>
#include <arkui/native_type.h>
#include <AbilityKit/ability_base/want.h> //引用元能力want头文件

// 注册事件
void onError(int32_t code, const char *name, const char *message) {}
void onTerminated(int32_t code, AbilityBase_Want *want) {}
const unsigned int LOG_PRINT_DOMAIN = 0xFF00;
#define SIZE_300 300 // 节点的宽/高数值，单位 vp（用于设置 NODE_WIDTH/NODE_HEIGHT）
#define PARAMETER_ERROR_CODE 401 // 参数错误码（OH_ArkUI_NodeContent_AddNode返回值表示入参非法）
// ...
    // 创建节点
    ArkUI_NodeHandle embeddedNode = nodeAPI->createNode(ARKUI_NODE_EMBEDDED_COMPONENT);
    // 设置属性
    AbilityBase_Element Element = {.bundleName = "com.example.uiextensionandaccessibility",
                                   .abilityName = "ExampleEmbeddedAbility",
                                   .moduleName = "entry"};       // 由元能力提供接口
    AbilityBase_Want *want = OH_AbilityBase_CreateWant(Element); // 由元能力提供接口
    if (want == nullptr) {
        OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "AbilityBase_Want", "CreateWant failed");
        return nullptr;
    }
    ArkUI_AttributeItem itemobjwant = {.object = want};
    nodeAPI->setAttribute(embeddedNode, NODE_EMBEDDED_COMPONENT_WANT, &itemobjwant);

    auto embeddedNode_option = OH_ArkUI_EmbeddedComponentOption_Create();
    auto onErrorCallback = onError;
    auto onTerminatedCallback = onTerminated;
    OH_ArkUI_EmbeddedComponentOption_SetOnError(embeddedNode_option, onErrorCallback);
    OH_ArkUI_EmbeddedComponentOption_SetOnTerminated(embeddedNode_option, onTerminatedCallback);

    ArkUI_AttributeItem itemobjembeddedNode = {.object = embeddedNode_option};
    nodeAPI->setAttribute(embeddedNode, NODE_EMBEDDED_COMPONENT_OPTION, &itemobjembeddedNode);
    // 属性设置完成后释放 embeddedNode_option 资源，避免内存泄漏
    OH_ArkUI_EmbeddedComponentOption_Dispose(embeddedNode_option);

    // 设置基本属性，如宽高
    ArkUI_NumberValue value[] = {{.f32 = SIZE_300}};
    ArkUI_AttributeItem item = {value, sizeof(value) / sizeof(ArkUI_NumberValue)};
    nodeAPI->setAttribute(embeddedNode, NODE_WIDTH, &item);
    nodeAPI->setAttribute(embeddedNode, NODE_HEIGHT, &item);

    // 创建Column
    ArkUI_NodeHandle column = nodeAPI->createNode(ARKUI_NODE_COLUMN);
    nodeAPI->setAttribute(column, NODE_WIDTH, &item);
    ArkUI_NumberValue column_bc[] = {{.u32 = 0xFFFF00BB}};
    ArkUI_AttributeItem column_item = {column_bc, 1};
    nodeAPI->setAttribute(column, NODE_BACKGROUND_COLOR, &column_item);
    ArkUI_AttributeItem column_id = {.string = "Column_CAPI"};
    nodeAPI->setAttribute(column, NODE_ID, &column_id);

    // 上树
    nodeAPI->addChild(column, embeddedNode);
```
