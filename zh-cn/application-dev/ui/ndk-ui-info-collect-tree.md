# 采集控件树信息

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

从API版本26.1.0开始，应用可以采集控件树信息，读取UI实例中的节点层级、节点ID和属性。应用可根据采集结果定位目标节点，或按需获取组件的交互信息、无障碍信息及高阶属性。

## 约束与限制

采集范围、结果大小和线程条件会影响请求是否成功，调用前应确认以下限制。

- 同步和异步采集接口均须在目标实例的UI线程调用，要求见[OH_ArkUI_NativeModule_UIAgentGetTreeJson](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagentgettreejson)与[OH_ArkUI_NativeModule_UIAgentGetTreeJsonAsync](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagentgettreejsonasync)的接口声明。
- 前一个异步树请求尚未完成时，再次提交异步请求会返回[ARKUI_ERROR_CODE_COMMAND_UNFINISHED](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)。
- 单次结果最多包含5000个节点，JSON大小不超过5 MiB。大小限制以紧凑格式JSON字节数为准；选择美化格式输出时，缩进和换行会增加字节数，格式化输出本身超过5 MiB的请求同样失败。超限时整体失败，采集结果为空。
- 本接口只采集应用进程内的树形结构，如果应用使用了[Web](../reference/apis-arkweb/arkts-basic-components-web.md)、[UIExtension](../reference/apis-arkui/js-apis-arkui-uiExtension.md)跨进程组件或[XComponent](../reference/apis-arkui/arkui-ts/ts-basic-components-xcomponent.md)，其内部内容不会采集。
- 字段未出现时，不应直接视为取值为false或0，应按附录[控件树采集结果的字段解析](ndk-ui-appendix.md#控件树采集结果的字段解析)中该字段的输出条件判断语义。
- 异步返回方式不会消除UI线程上的采集开销。控件树过于复杂的场景下进行采集可能严重影响应用正常业务或内存占用。避免高频调用采集接口。

## 接口说明

控件树采集关键接口如下表所示。具体API说明详见API参考[ui_info_collection.h](../reference/apis-arkui/capi-ui-info-collection-h.md)。

### 请求对象管理

**表1** 请求对象管理关键接口功能介绍

| 接口名                                                                                                                                                  | 描述                     |
| --------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequestCreate](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestcreate)   | 创建全量树或可见树请求。 |
| [OH_ArkUI_NativeModule_UIAgentTreeRequestDestroy](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestdestroy) | 销毁请求对象。           |

### 采集配置

各配置接口的用途如下，参数、默认值、适用请求类型和返回值以[ui_info_collection.h](../reference/apis-arkui/capi-ui-info-collection-h.md)中的接口声明为准：

**表2** 采集配置关键接口功能介绍

| 接口名                                                                                                                                                                                                | 描述                           |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterPureLayoutNodes](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetfilterpurelayoutnodes)             | 设置是否过滤纯布局节点。       |
| [OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterOccludedNodes](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetfilteroccludednodes)                 | 设置是否过滤被完全遮挡的节点。 |
| [OH_ArkUI_NativeModule_UIAgentTreeRequestSetOcclusionOpacityThreshold](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetocclusionopacitythreshold)     | 设置遮挡方不透明度阈值。       |
| [OH_ArkUI_NativeModule_UIAgentTreeRequestSetInteractionInfo](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetinteractioninfo)                         | 设置是否采集交互信息。         |
| [OH_ArkUI_NativeModule_UIAgentTreeRequestSetAccessibilityInfo](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetaccessibilityinfo)                     | 设置是否采集无障碍信息。       |
| [OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectVisualProperties](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetcollectvisualproperties)         | 设置是否采集高阶视觉属性。     |
| [OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectFunctionalProperties](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetcollectfunctionalproperties) | 设置是否采集高阶功能属性。     |

各开关相互独立，不会自动开启其他属性组；属性开关对应的字段组明细见附录[控件树采集结果的字段解析](ndk-ui-appendix.md#控件树采集结果的字段解析)。遮挡不透明度阈值的取值范围、默认值和生效条件以[OH_ArkUI_NativeModule_UIAgentTreeRequestSetOcclusionOpacityThreshold](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetocclusionopacitythreshold)接口声明为准。采集只读取控件的配置和状态，不会因此触发快捷键、执行布局或调用事件回调。

### 采集入口

**表3** 采集入口关键接口功能介绍

| 接口名                                                                                                                                              | 描述       |
| ----------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| [OH_ArkUI_NativeModule_UIAgentGetTreeJson](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagentgettreejson)           | 同步采集。 |
| [OH_ArkUI_NativeModule_UIAgentGetTreeJsonAsync](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagentgettreejsonasync) | 异步采集。 |

## 过滤规则与输出示例

先按任务选择树范围和属性开关，再根据实际字段路径、类型及出现条件解析结果。

### 纯布局节点判定

开启[OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterPureLayoutNodes](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetfilterpurelayoutnodes)后，框架先判断节点是否属于候选节点范围，再判断节点是否具有需要保留的语义、交互、状态或显示信息；仅当节点是候选类型且无任何保留信息时，才会从结果树中省略；采集根节点不受该规则约束，始终保留。过滤只改变返回的JSON树，不修改应用的真实控件树，也不新增表示过滤状态的key。被省略节点的保留子节点会按原顺序提升到最近保留祖先的`$children`中；没有可保留子节点的节点从结果树中消失。

- **候选节点**：[Row](../reference/apis-arkui/arkui-ts/ts-container-row.md)、[Column](../reference/apis-arkui/arkui-ts/ts-container-column.md)、[Stack](../reference/apis-arkui/arkui-ts/ts-container-stack.md)、[Flex](../reference/apis-arkui/arkui-ts/ts-container-flex.md)和[RelativeContainer](../reference/apis-arkui/arkui-ts/ts-container-relativecontainer.md)。

候选节点还需通过保留判定，以下为逆向条件，命中任意一类即被保留，不会从结果树中省略：

- **组件标识**：通过[id](../reference/apis-arkui/arkui-ts/ts-universal-attributes-component-id.md#id)设置非空标识的节点会保留，结果中通过compid表示该标识。
- **无障碍语义**：设置非空的[accessibilityText](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitytext)、[accessibilityDescription](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitydescription)或[accessibilityRole](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilityrole18)，取值为true的[accessibilityGroup](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitygroup)，有效的[accessibilityVirtualNode](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilityvirtualnode11)，或已显式设置（显式设置为false时同样有效）的[accessibilitySelected](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilityselected13)、[accessibilityChecked](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitychecked13)等状态属性。
- **交互与焦点**：配置[onClick](../reference/apis-arkui/arkui-ts/ts-universal-events-click.md#onclick)、[onTouch](../reference/apis-arkui/arkui-ts/ts-universal-events-touch.md#ontouch)、[onMouse](../reference/apis-arkui/arkui-ts/ts-universal-mouse-key.md#onmouse)、[手势](../reference/apis-arkui/arkui-ts/ts-gesture-settings.md)、非空的[responseRegion](../reference/apis-arkui/arkui-ts/ts-universal-attributes-touch-target.md#responseregion)、非默认的[hitTestBehavior](../reference/apis-arkui/arkui-ts/ts-universal-attributes-hit-test-behavior.md#hittestbehavior)、[focusable](../reference/apis-arkui/arkui-ts/ts-universal-attributes-focus.md#focusable)、[tabIndex](../reference/apis-arkui/arkui-ts/ts-universal-attributes-focus.md#tabindex9)或有效的[keyboardShortcut](../reference/apis-arkui/arkui-ts/ts-universal-events-keyboardshortcut.md#keyboardshortcut)等能力的节点会保留。
- **回调与状态**：配置[onDragStart](../reference/apis-arkui/arkui-ts/ts-universal-events-drag-drop.md#ondragstart)、[onAppear](../reference/apis-arkui/arkui-ts/ts-universal-events-show-hide.md#onappear)、[onAreaChange](../reference/apis-arkui/arkui-ts/ts-universal-component-area-change-event.md#onareachange)、[onSizeChange](../reference/apis-arkui/arkui-ts/ts-universal-component-size-change-event.md#onsizechange)等回调，或通过[enabled](../reference/apis-arkui/arkui-ts/ts-universal-attributes-enable.md#enabled)显式禁用节点。
- **显示与位置**：布局容器自身需要呈现外观或位置时，也可能保留。例如，非透明的[backgroundColor](../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor)、[border](../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#border)等配置能使节点保留。位置与尺寸属性的设置情况不参与判定，详见[常见问题](#常见问题)。

### 节点输出示例

同一节点可以同时具有默认信息、交互信息、无障碍信息和两个高阶属性组。字段是否出现以实际返回为准，不能凭schemaVersion推断某个可选属性一定存在，解析时按实际类型和完整路径检查。视觉和功能字段分别直接写入advanced.visual和advanced.functional。详细key、值类型和说明分别见附录中的[高阶视觉字段](ndk-ui-appendix.md#高阶视觉字段)和[高阶功能字段](ndk-ui-appendix.md#高阶功能字段)。以下为Text节点的局部格式示意，省略其余字段；数值仅用于说明类型，不是固定采集结果。

```json
{
  "$type": "Text",
  "clickable": true,
  "accessibilityContent": "示例文本",
  "advanced": {
    "visual": {
      "fontScale": 1,
      "fontWeightScale": 1,
      "from TextEngine paragraphs_ info": {
        "DidExceedMaxLines": false,
        "GetTextWidth": 120,
        "GetHeight": 24,
        "GetLineCount": 1,
        "GetLongestLine": 120,
        "GetLongestLineWithIndent": 120
      }
    },
    "functional": {
      "BindSelectionMenu": true
    }
  }
}
```

## 开发步骤

以下步骤以[示例工程](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection)为上下文，取得目标UI实例后创建请求、采集并解析结果。同步和异步是可选路径，不需要依次执行。各接口返回值的判断与处理建议见[异常处理](#异常处理)；错误码定义和完整取值以各接口声明及[ArkUI_ErrorCode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)为准。

开发流程如下：

| 阶段       | 主要任务                                                                             | 说明                         |
| ------------ | -------------------------------------------------------------------------------------- | ------------------------------ |
| 准备       | [准备工程和目标页面](#准备工程和目标页面)、[管理上下文生命周期](#管理上下文生命周期) | 取得并复用Context。          |
| 配置       | [创建并配置请求](#创建并配置请求)                                                    | 选定树类型并设置采集开关。   |
| 采集       | [同步采集并读取结果](#同步采集并读取结果)或[异步采集并清理结果](#异步采集并清理结果) | 同步与异步二选一。           |
| 解析       | [解析结果并从页面调用](#解析结果并从页面调用)                                        | 校验协议版本并定位目标节点。 |
| 返回值处理 | [异常处理](#异常处理)                                                                | 按错误码分支处理。           |

### 准备工程和目标页面

通用NDK工程创建、ArkTS与Native桥接及构建配置见[基于NDK构建UI概述](ndk-build-ui-overview.md)和[接入ArkTS页面](ndk-access-the-arkts-page.md)。本专题使用包含相关接口的API版本26.1.0或后续版本的SDK，并确保设备实现与SDK匹配。示例工程的Native依赖配置见[CMakeLists.txt](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/CMakeLists.txt)。

树采集使用`<arkui/ui_info_collection.h>`，JSON对象使用`<arkui/ui_json_wrapper.h>`。请求结果的构造、读取及销毁规则见[UI信息数据格式说明](ndk-ui-info-data-structure.md)。

[TreePage.ets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/ets/pages/TreePage.ets)包含普通输入框和隐藏节点。应用通过当前页面的[UIContext](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md)取得[ArkUI_ContextHandle](../reference/apis-arkui/capi-arkui-nativemodule-arkui-context8h.md)，并从UI线程事件调用采集。树中的整数节点ID与组件通过.id()设置的字符串标识不同，业务定位时需区分两者。

### 管理上下文生命周期

上下文句柄与UI实例的有效期分别管理，获取、复用和退出处理需遵循下列限制。

> **说明：**
>
> 当前[OH_ArkUI_GetContextFromNapiValue](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getcontextfromnapivalue)没有公开的句柄释放方法，重复获取的句柄无法释放。下面的桥接片段用于演示调用方式，不能作为反复获取句柄的完整方案。请勿自行编写释放逻辑，或对句柄调用free、delete。

在同一有效UI实例的多次业务操作之间，应集中保存并复用已经获取的句柄，避免每次采集都重新获取。多实例应分别管理，不跨窗口复用；实例退出后停止使用其句柄发起请求。缓存只减少重复获取；重复获取的句柄目前无法释放，缓存也不延长UI实例本身的生命周期。

若异步请求仍在进行，句柄、业务数据和结果对象需分别按对应接口的生命周期要求管理。当前没有句柄释放方法，反复获取句柄可能产生泄漏；接口提供释放方法后，请按其接口说明执行清理。

### 创建并配置请求

[napi_init.cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/napi_init.cpp)中的CreateRequest根据页面选项创建全量树或可见树请求，并分别设置五个开关。

<!-- @[ui_tree_create_request](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/napi_init.cpp) -->

```C++
Request CreateRequest(napi_env env, napi_value options)
{
    Request request(nullptr, OH_ArkUI_NativeModule_UIAgentTreeRequestDestroy);
    bool visible = false;
    std::array<bool, TREE_OPTION_COUNT> flags {};
    const char* names[] = {"filterLayout", "interaction", "accessibility", "visual", "functional"};
    if (!ReadBool(env, options, "visibleOnly", visible)) {
        return request;
    }
    for (size_t index = 0; index < flags.size(); ++index) {
        if (!ReadBool(env, options, names[index], flags[index])) {
            return request;
        }
    }
    OH_ArkUI_NativeModule_UIAgentTreeRequest* raw = nullptr;
    auto code = OH_ArkUI_NativeModule_UIAgentTreeRequestCreate(visible ?
        OH_ARKUI_NATIVE_MODULE_UI_AGENT_TREE_VISIBLE : OH_ARKUI_NATIVE_MODULE_UI_AGENT_TREE_FULL, &raw);
    request.reset(raw);
    if (code != ARKUI_ERROR_CODE_NO_ERROR) {
        Throw(env, "tree request", code);
        return request;
    }
    using Setter = ArkUI_ErrorCode (*)(OH_ArkUI_NativeModule_UIAgentTreeRequest*, bool);
    const Setter setters[] = {
        OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterPureLayoutNodes,
        OH_ArkUI_NativeModule_UIAgentTreeRequestSetInteractionInfo,
        OH_ArkUI_NativeModule_UIAgentTreeRequestSetAccessibilityInfo,
        OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectVisualProperties,
        OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectFunctionalProperties
    };
    for (size_t index = 0; index < flags.size(); ++index) {
        code = setters[index](request.get(), flags[index]);
        if (code != ARKUI_ERROR_CODE_NO_ERROR) {
            Throw(env, "tree option", code);
            request.reset();
            break;
        }
    }
    return request;
}
```

创建请求时只需设置本次采集需要的选项；纯布局节点的完整判定与层级变化见[纯布局节点判定](#纯布局节点判定)。示例仅演示五个采集开关，未包含遮挡过滤和遮挡不透明度阈值；这两个选项需按接口说明单独配置。

### 同步采集并读取结果

同一文件中的CollectTree检查Context和请求后调用同步接口，将结果复制为ArkTS字符串并销毁JSONWrapper。JsonString的读取规则见[读取JSONWrapper内容](ndk-ui-info-data-structure.md#读取jsonwrapper内容)。

<!-- @[ui_tree_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/napi_init.cpp) -->

```C++
napi_value CollectTree(napi_env env, napi_callback_info info)
{
    napi_value args[2];
    if (!Arguments(env, info, TREE_ARG_COUNT, args)) {
        return nullptr;
    }
    auto request = CreateRequest(env, args[OPTIONS_ARG]);
    if (!request) {
        return nullptr;
    }
    auto context = GetContext(env, args[CONTEXT_ARG]);
    if (!context) {
        return nullptr;
    }
    OH_ArkUI_NativeModule_UIJsonWrapper* json = nullptr;
    auto code = OH_ArkUI_NativeModule_UIAgentGetTreeJson(context, request.get(),
        OH_ARKUI_NATIVE_MODULE_UI_JSON_COMPACT, &json);
    if (code != ARKUI_ERROR_CODE_NO_ERROR) {
        return Throw(env, "tree collection", code);
    }
    auto result = JsonString(env, json);
    OH_ArkUI_NativeModule_UIJsonWrapperDestroy(json);
    return result;
}
```

### 异步采集并清理结果

CollectTreeAsync仍从目标UI线程提交，返回示例自行封装的Promise。提交后即可销毁请求对象，不必保留到回调结束；业务数据和结果对象分别管理。异步回调可能在提交调用返回前发生，应在提交前准备好回调所需业务数据。

<!-- @[ui_tree_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/napi_init.cpp) -->

```C++
napi_value CollectTreeAsync(napi_env env, napi_callback_info info)
{
    napi_value args[2];
    if (!Arguments(env, info, TREE_ARG_COUNT, args)) {
        return nullptr;
    }
    auto request = CreateRequest(env, args[OPTIONS_ARG]);
    if (!request) {
        return nullptr;
    }
    auto context = GetContext(env, args[CONTEXT_ARG]);
    if (!context) {
        return nullptr;
    }
    napi_value promise = nullptr;
    auto token = AddPending(env, promise);
    if (token) {
        uint64_t requestId = 0;
        auto code = OH_ArkUI_NativeModule_UIAgentGetTreeJsonAsync(context, request.get(),
            OH_ARKUI_NATIVE_MODULE_UI_JSON_COMPACT, OnTree, reinterpret_cast<void*>(token), &requestId);
        RejectSubmission(token, code);
    }
    return promise;
}
```

OnTree处理回调结果。完成回调把JSONWrapper所有权转移给应用，owned负责销毁；即使示例页面已退出、不再存在对应Pending任务，也会清理迟到结果。TakePending、Reject及Promise封装均位于同一示例文件，不属于平台新增能力。

<!-- @[ui_tree_complete](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/napi_init.cpp) -->

```C++
void OnTree(ArkUI_ContextHandle context, uint64_t requestId, ArkUI_ErrorCode code,
    OH_ArkUI_NativeModule_UIJsonWrapper* json, void* userData)
{
    std::unique_ptr<OH_ArkUI_NativeModule_UIJsonWrapper,
        decltype(&OH_ArkUI_NativeModule_UIJsonWrapperDestroy)> owned(json, OH_ArkUI_NativeModule_UIJsonWrapperDestroy);
    auto job = TakePending(reinterpret_cast<uintptr_t>(userData));
    if (!job) {
        return;
    }
    napi_handle_scope scope = nullptr;
    if (napi_open_handle_scope(job->owner->env, &scope) != napi_ok) {
        return;
    }
    if (code != ARKUI_ERROR_CODE_NO_ERROR) {
        Reject(job, "tree completion", code);
    } else {
        auto value = JsonString(job->owner->env, json);
        if (value) {
            napi_resolve_deferred(job->owner->env, job->deferred, value);
        } else {
            Reject(job, "JSON bridge", -1);
        }
    }
    napi_close_handle_scope(job->owner->env, scope);
}
```

### 解析结果并从页面调用

结果的schemaVersion为协议版本，treeInfo为根节点对象或null。应用按`$children`遍历，并通过compid匹配组件字符串标识、读取`$ID`整数标识。页面变化后重新获取目标，不把快照中的节点ID视为长期有效引用。

[Collection.ets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/ets/common/Collection.ets)声明当前示例使用的字段类型，并提供解析与查找函数。字段模型仅供应用读取所需信息，不是替代SDK声明的结构体。

<!-- @[ui_tree_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/ets/common/Collection.ets) -->

```TypeScript
export interface TreeNode {
  $ID?: number;
  $type?: string;
  compid?: string;
  $children?: TreeNode[];
}
export interface TreeEnvelope {
  schemaVersion: number;
  treeInfo: TreeNode | null;
}
```

<!-- @[ui_tree_parse_find](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/ets/common/Collection.ets) -->

```TypeScript
export function parseTree(value: string): TreeEnvelope {
  const tree = JSON.parse(value) as TreeEnvelope;
  if (tree.schemaVersion !== 1) {
    throw new Error('Unsupported tree schema');
  }
  return tree;
}

export function findNode(tree: TreeEnvelope, componentId: string): TreeNode | undefined {
  if (tree.treeInfo === null) {
    return undefined;
  }
  const nodes: TreeNode[] = [tree.treeInfo];
  while (nodes.length > 0) {
    const node = nodes.pop();
    if (node === undefined) {
      continue;
    }
    if (node.compid === componentId) {
      return node;
    }
    if (node.$children !== undefined) {
      for (const child of node.$children) {
        nodes.push(child);
      }
    }
  }
  return undefined;
}
```

TreePage中的collect方法传入六个选项，选择同步或异步路径，再显示解析后的目标。页面状态、导入和生命周期函数在同一文件中；active用于防止结果更新已退出的页面，不取消框架请求。

<!-- @[ui_tree_page_collect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/ets/pages/TreePage.ets) -->

```TypeScript
private async collect(asynchronous: boolean): Promise<void> {
  if (this.busy) { return; }
  this.busy = true;
  const options: TreeOptions = {
    visibleOnly: this.visibleOnly, filterLayout: this.filterLayout,
    interaction: this.interaction, accessibility: this.accessibility,
    visual: this.visual, functional: this.functional
  };
  try {
    const context = this.getUIContext();
    const value = asynchronous ? await nativeUi.collectTreeAsync(context, options) :
      nativeUi.collectTree(context, options);
    if (!this.active) { return; }
    const tree = parseTree(value);
    const target = findNode(tree, 'treeTarget');
    const hidden = findNode(tree, 'hiddenTarget');
    this.status = `schema=${tree.schemaVersion}; target=${target !== undefined}; ` +
      `hidden=${hidden !== undefined}; nodes=${countNodes(tree)}`;
    this.result = target === undefined ? value.slice(0, OUTPUT_LIMIT) :
      JSON.stringify(target, null, 2).slice(0, OUTPUT_LIMIT);
  } catch (error) {
    if (this.active) { this.status = failure(error); }
  } finally {
    if (this.active) { this.busy = false; }
  }
}
```

## 异常处理

各接口的返回值按请求创建与配置、同步采集、异步提交与回调三个阶段组织，处理建议如下。

### 处理请求创建与配置返回值

[OH_ArkUI_NativeModule_UIAgentTreeRequestCreate](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestcreate)用于创建请求对象，返回值取值及可能原因见接口声明和[ArkUI_ErrorCode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)。创建成功后配置并使用请求，最后通过配套销毁接口销毁；请求为空时检查对象创建结果，不继续设置选项。请求销毁函数没有返回值。

| 处理场景             | 建议处理                                          |
| ---------------------- | --------------------------------------------------- |
| 树类型或输出参数无效 | 使用声明的全量树/可见树枚举，并提供有效输出存储。 |
| 请求对象无法分配     | 减少资源占用后重试，不要在循环中反复重试。        |

示例演示的五个开关函数只需判断配置是否成功。遮挡过滤和遮挡不透明度阈值函数还需检查树类型和阈值范围：

| 配置场景             | 建议处理                         |
| ---------------------- | ---------------------------------- |
| 对全量树开启遮挡过滤 | 改用可见树请求，或关闭遮挡过滤。 |
| 设置遮挡不透明度阈值 | 修正阈值和树类型后再配置。       |

### 处理同步采集返回值

[OH_ArkUI_NativeModule_UIAgentGetTreeJson](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagentgettreejson)执行同步采集。返回值定义见接口声明和[ArkUI_ErrorCode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)。采集成功时读取结果并销毁JSONWrapper对象，treeInfo为null仍可能是正常结果。

| 处理场景           | 建议处理                                                |
| -------------------- | --------------------------------------------------------- |
| 请求或参数无效     | 检查请求创建结果和参数，使用接口声明的枚举值。          |
| Context或线程无效  | 在有效实例中重新获取Context，并将调用安排到目标UI线程。 |
| 结果过大或资源不足 | 缩小采集范围、减少属性，或启用适用的过滤选项。          |
| 其他公开接口失败   | 记录返回值和调用条件，不按未公开原因细分业务分支。      |

### 处理异步提交与回调结果

[OH_ArkUI_NativeModule_UIAgentGetTreeJsonAsync](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagentgettreejsonasync)的直接返回值用于判断请求是否受理，不代表采集成功；具体定义见接口声明和[ArkUI_ErrorCode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)。请求已受理后通过回调检查采集结果。

| 提交场景           | 建议处理                                       |
| -------------------- | ------------------------------------------------ |
| 请求参数或回调无效 | 修正请求、回调、请求ID输出参数或格式后再提交。 |
| UI实例或线程无效   | 在有效实例的UI线程重新提交。                   |
| 前一异步请求未完成 | 等前次回调完成后再决定是否提交，不反复重试。   |

回调参数中的错误码（示例中为code）表示采集结果；JSON对象的所有权规则见[OH_ArkUI_NativeModule_UIAgentJsonCallback](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagentjsoncallback)的参数说明。不要把同步接口的完整返回值表当作异步提交接口的直接返回值清单。

## 常见问题

以下问题覆盖采集结果结构、字段解析和异步回调的常见疑问，帮助区分过滤结果与调用失败。

### 为什么返回的节点数少于页面中声明的组件数

采集结果受树类型、节点是否已经创建、纯布局过滤、遮挡过滤及内容边界组件影响。先使用全量树并关闭纯布局过滤检查结构，再逐项开启选项比较差异；可见树开启遮挡过滤后，被完全遮挡的节点也会从结果中移除。不要假设采集会创建尚未实例化的懒加载内容。

### 为什么不能仅凭属性设置或当前位置判断节点是否被省略

显示与位置的判定依据是节点相对父节点的偏移信息，包括布局产生的实际偏移和节点存在过的偏移量；判断节点去留，应依据偏移信息及其他保留条件，而非属性设置情况。典型场景有三类：

- 仅设置[width](../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#width)、[height](../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#height)等尺寸属性，或将[offset](../reference/apis-arkui/arkui-ts/ts-universal-attributes-location.md#offset)、[position](../reference/apis-arkui/arkui-ts/ts-universal-attributes-location.md#position)设置为零偏移，且布局后相对父节点无偏移的节点，仍会作为纯布局容器被省略。
- 未设置任何位置属性，但因父节点布局产生偏移的节点，不会被省略。
- 当前位置为(0, 0)、但存在过偏移量的节点，同样不会被省略。


### 采集成功但treeInfo为null是采集失败吗

不是。treeInfo为根节点对象或null，空采集内容仍可能对应成功的JSON对象；按无根节点处理并跳过遍历，结果对象仍按所有权规则释放。

### 为什么采集结果中缺少部分字段或advanced对象

字段未出现时，原因随所处层级（advanced对象、属性组、字段）而异，不应默认其取值为false或0。各字段是否输出，以附录[控件树采集结果的字段解析](ndk-ui-appendix.md#控件树采集结果的字段解析)中该字段的说明为准。可按下列层次排查：

- **advanced对象未输出**：视觉和功能开关均关闭时，组件节点不输出advanced对象；开关开启后，语法节点（不对应具体组件，如JsView节点、Span、ForEach等），以及内容边界组件（Web、UIExtension、XComponent等）的节点（内部内容不展开）仍不输出advanced；其余组件节点始终输出。
- **属性组为空对象**：开启的属性组没有可采集字段时，组对象为`{}`，不代表采集失败。
- **字段未输出**，常见原因包括：
  - 开关未开启：交互信息、无障碍信息、高阶视觉、高阶功能开关分别控制各自的字段组。
  - 字段不属于该组件：各字段表按组件列出适用字段，如scrollAxis仅适用于Swiper。
  - 属性未设置：组件未设置对应属性时，相关字段不输出，如compid、backgroundColor。
  - 特定输出条件：如active、visible仅在对应状态为false时输出，未出现即表示相反状态；opacity仅在已设置且不等于1.0时输出。

### 为什么读取不到含点号的字段

需先区分两种情况：`$attrs`是节点上的嵌套对象，其中的字段（如Toggle的isOn、Swiper的scrollAxis）按`node.$attrs.isOn`层级读取，点访问有效；padding.right则是包含点号的完整key名称，位于advanced.visual下，读取方式为visual["padding.right"]，不能按visual.padding.right逐级取值。除嵌套路径外，key的大小写、空格和标点均属于名称的一部分。

### 异步采集的回调为什么可能在提交调用返回前执行

提交后请求即进入异步流程，回调可能在提交调用返回前发生，应在提交前准备好回调所需业务数据。回调返回的是采集执行时的界面，不是提交请求时的界面。提交后即可销毁请求对象，业务数据和结果对象分别按生命周期管理。

### 采集结果中的节点ID能否长期保存用于后续查找

不能。采集结果是界面快照，页面变化后应重新获取目标，不把快照中的节点ID视为长期有效引用。树中的`$ID`整数标识与组件通过.id()设置的compid字符串标识不同，定位时需区分两者。

### 如何处理结果过大

收到[ARKUI_ERROR_CODE_RESULT_TOO_LARGE](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)时，按业务需要选择可见树、关闭不需要的高阶属性、启用纯布局过滤，或在可见树请求上开启遮挡过滤。接口不提供分页，不应连续重试相同的大请求。
