# 监听UI内容变化事件
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->

ArkUI提供了面向NDK的UI内容变化事件订阅接口（[ui_info_collection.h](../reference/apis-arkui/capi-ui-info-collection-h.md)），新增页面变化事件监听能力：应用通过注册订阅，以回调方式获取当前界面变化的开始、结束等事件及对应时间戳，作为UI感知的重要信息，适用于应用内智能体上下文感知、自动化测试校验、页面体验监控（如页面加载耗时、动效完成时机统计）等场景。

可监听的界面变化分为三个事件类别：

- **页面切换**：Navigation、Router的页面切换，以及Swiper、Tabs的页签切换；
- **滚动**：可滚动组件（Scroll、List、Grid、WaterFlow等）的滚动，包含手势滚动、抛滑惯性滚动和程序化滚动；
- **浮层**：Dialog、CustomDialog、ActionSheet、Popup、Menu、Toast、Sheet、ContentCover及OverlayManager浮层等的显示与消失。

回调仅在注册时指定的UI上下文所关联的**UI线程**上触发；注册与注销接口也仅限UI线程调用，从非UI线程调用会导致进程终止。

## 接口规格

### 事件类别与忽略类型

`eventMask`由[OH_ArkUI_NativeModule_UIContentChangeEventCategory](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventcategory)的枚举值按位或组合而成；`ignoreMask`由[OH_ArkUI_NativeModule_UIContentChangeIgnoreType](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeignoretype)的枚举值按位或组合而成：

| 事件类别 | 枚举值 | 说明 |
| -- | -- | -- |
| 页面切换 | `..._EVENT_CATEGORY_PAGE` | Navigation、Router、Swiper和Tabs的切换事件 |
| 滚动 | `..._EVENT_CATEGORY_SCROLL` | 滚动事件，不区分滚动子类型，如需忽略特定来源请在`ignoreMask`中设置对应标志 |
| 浮层 | `..._EVENT_CATEGORY_OVERLAY` | 模态、菜单、弹窗等浮层事件 |
| 全部 | `..._EVENT_CATEGORY_ALL` | 所有受支持的事件类别 |

| 可忽略类型 | 枚举值 | 说明 |
| -- | -- | -- |
| scrollBy滚动 | `..._CONTENTCHANGE_IGNORE_SCROLLBY` | 忽略按指定偏移量滚动（[scrollBy](arkts-ts-container-scroll.md#scrollby9)）触发的整个滚动周期 |
| scrollTo滚动 | `..._CONTENTCHANGE_IGNORE_SCROLLTO` | 忽略滚动到指定位置（[scrollTo](arkts-ts-container-scroll.md#scrollto9)）触发的整个滚动周期 |
| Toast | `..._CONTENTCHANGE_IGNORE_TOAST` | 忽略Toast提示事件的显示与消失 |

### 事件类型

事件类型由[OH_ArkUI_NativeModule_UIContentChangeEventType](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventtype)定义，回调中通过[OH_ArkUI_NativeModule_UIContentChangeEventGetType()](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventgettype)获取：

| 事件类型 | 枚举值 | 说明 |
| -- | -- | -- |
| 页面切换开始 | `..._EVENT_PAGE_CHANGE_START` | Navigation/Router页面切换开始 |
| 页面切换结束 | `..._EVENT_PAGE_CHANGE_END` | Navigation/Router页面切换结束 |
| 滚动开始 | `..._EVENT_SCROLL_START` | 滚动开始 |
| 滚动结束 | `..._EVENT_SCROLL_END` | 滚动交互及其后续的惯性滚动均已结束 |
| 浮层显示完成 | `..._EVENT_OVERLAY_SHOW` | 浮层显示完成 |
| 浮层消失完成 | `..._EVENT_OVERLAY_HIDE` | 浮层消失完成 |
| Swiper切换开始 | `..._EVENT_SWIPER_START` | Swiper切换开始 |
| Swiper切换完成 | `..._EVENT_SWIPER_END` | Swiper切换完成；如果存在过渡动画，则该动画也已完成 |
| Swiper切换取消 | `..._EVENT_SWIPER_CANCEL` | Swiper切换中断，并回弹到起始索引 |
| Tabs切换开始 | `..._EVENT_TABS_START` | Tabs切换开始 |
| Tabs切换完成 | `..._EVENT_TABS_END` | Tabs切换完成 |
| Tabs切换取消 | `..._EVENT_TABS_CANCEL` | Tabs切换开始后被取消，并回弹到切换开始时的索引 |

其中START与CANCEL事件仅在注册时`withStart`为`true`的情况下输出，且CANCEL仅会通知给已收到对应周期START的订阅。

### 核心函数

| 函数 | 说明 |
| -- | -- |
| [OH_ArkUI_NativeModule_RegisterUIContentChangeEvent()](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_registeruicontentchangeevent) | 注册订阅。每次成功调用创建一个独立订阅，返回的订阅ID非零且在该UI上下文内唯一 |
| [OH_ArkUI_NativeModule_UnRegisterUIContentChangeEvent()](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_unregisteruicontentchangeevent) | 注销订阅。成功后后续事件不再触发该订阅的回调 |
| [OH_ArkUI_NativeModule_UIContentChangeEventGetType()](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventgettype) | 从事件快照获取事件类型 |
| [OH_ArkUI_NativeModule_UIContentChangeEventGetTimestamp()](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventgettimestamp) | 获取事件的单调时间戳，单位为纳秒，不表示日历时间 |
| [OH_ArkUI_NativeModule_UIContentChangeEventGetContext()](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventgetcontext) | 获取事件关联的UI上下文，返回借用句柄 |
| [OH_ArkUI_NativeModule_UIContentChangeEventGetContentChangeEventJson()](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventgetcontentchangeeventjson) | 获取事件详情JSON，通过[OH_ArkUI_NativeModule_UIJsonWrapper](../reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md)封装返回 |

### 事件详情JSON

事件详情JSON顶层包含`schemaVersion`字段，并携带以下字段：

| 字段 | 类型 | 说明 |
| -- | -- | -- |
| schemaVersion | integer | 固定为1 |
| eventType | integer | 0～11，与GetType返回值相等 |
| category | string | `page`（页面切换）/ `scroll`（滚动）/ `overlay`（浮层）；Swiper、Tabs属于page |
| targetNode | object | 事件目标节点：`{"id": "42", "type": "Scroll"}`，id为节点ID字符串，type为ArkUI组件名 |
| triggerNode | object或null | 引起内容变化的触发节点；页面/滚动事件为null；浮层事件在可提供时返回 |
| overlayType | string或null | 浮层类型：`dialog`、`customDialog`、`actionSheet`、`popup`、`menu`、`toast`、`overlay`；Sheet/ContentCover为`dialog`；其他类别为null |
| subtree | object或null | 目标节点子树快照；仅在PAGE_CHANGE_END与OVERLAY_SHOW事件中包含 |

## 约束与限制

不同组件在该场景下采集到的信息存在差异，使用时须注意：

1. **Swiper自动播放期间事件被抑制**：Swiper开启自动播放（autoplay）时，为避免高频回调，该Swiper的START/END/CANCEL事件默认均不上报（不仅抑制自动翻页动作）；如需感知该Swiper的切换事件，需关闭autoplay。活动切换过程中开启autoplay，旧周期不会补发END/CANCEL，关闭后新周期正常上报。

2. **程序化滚动的高频抑制**：scrollTo、scrollBy等接口实现的自动化滚动同样会触发滚动事件；高频自动化滚动场景下，建议注册时在`ignoreMask`中设置`IGNORE_SCROLLTO`或`IGNORE_SCROLLBY`忽略对应来源的整个滚动周期，避免高频回调。无实际位移的调用（如滚动到当前位置）不会产生事件。

3. **Toast瞬时消息**：Toast为瞬时消息，其显示与消失会产生OVERLAY_SHOW/HIDE事件；不关注Toast的场景建议在`ignoreMask`中设置`IGNORE_TOAST`忽略。

4. **浮层事件的覆盖范围**：仅能覆盖本应用进程内由ArkUI管理的浮层；无法覆盖由UIExtension承载的跨进程系统级弹窗、Web组件内部的弹窗事件，以及XComponent内自绘制内容中的弹窗事件。

5. **END事件以动效结束为准**：页面路由、抛滑、Swiper、Tabs切换的END事件均在动效结束后上报，不会在动效期间上报：PAGE_CHANGE_END在路由转场完成后、SCROLL_END在滚动交互及后续惯性滚动均结束后、SWIPER_END/TABS_END在切换动画完成后上报。每个控件的事件相互独立触发。

6. **可能存在有START没有END的情况**：Swiper、Tabs、页面路由等切换到一半松手回弹、页面未实际变化时，不会上报END，而是上报对应的CANCEL事件（SWIPER_CANCEL/TABS_CANCEL）。CANCEL仅通知给收到该周期START的订阅（即`withStart`为`true`时），取消周期不会再上报END。

## 开发步骤

以下步骤介绍页面变化监听功能的完整开发流程，示例代码来自[应用示例](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NdkUIEventObserver)。所有接口仅限UI线程调用。

1. 准备开发环境，引入头文件并链接动态库。

    ```c
    #include "arkui/native_type.h"           // ArkUI_ContextHandle
    #include "arkui/ui_info_collection.h"    // 内容变化事件订阅接口
    #include "arkui/ui_json_wrapper.h"       // JSON封装对象访问
    ```

    在CMakeLists.txt中链接libace_ndk.z.so：

    ```cmake
    target_link_libraries(entry PUBLIC libace_ndk.z.so)
    ```

2. 实现事件回调。回调在UI线程上同步执行，事件快照为借用对象，仅在本次回调返回前有效，需要在回调内完成读取或拷贝。

    <!-- @[content_change_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkUIEventObserver/entry/src/main/cpp/ContentChangeObserver.h) -->

    ```c
    // 内容变化事件回调：event为借用的事件快照，仅在本函数执行期间有效
    static void OnContentChangeEvent(const OH_ArkUI_NativeModule_UIContentChangeEvent *event, void *userData)
    {
        // 获取事件类型
        OH_ArkUI_NativeModule_UIContentChangeEventType type = OH_ARKUI_NATIVEMODULE_EVENT_PAGE_CHANGE_START;
        OH_ArkUI_NativeModule_UIContentChangeEventGetType(event, &type);
        // 获取事件完成时刻的单调时间戳（纳秒）
        uint64_t timestamp = 0;
        OH_ArkUI_NativeModule_UIContentChangeEventGetTimestamp(event, &timestamp);
        // 获取事件详情JSON：wrapper为借用对象，仅在本回调内有效，不得Destroy或在回调外使用
        const OH_ArkUI_NativeModule_UIJsonWrapper *json = nullptr;
        ArkUI_ErrorCode code = OH_ArkUI_NativeModule_UIContentChangeEventGetContentChangeEventJson(event, &json);
        if (code == ARKUI_ERROR_CODE_NO_ERROR && json != nullptr) {
            const char *data = OH_ArkUI_NativeModule_UIJsonWrapperGetData(json);
            OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "ContentChangeObserver",
                "type: %{public}d, timestamp: %{public}llu, json: %{public}s",
                static_cast<int>(type), static_cast<unsigned long long>(timestamp), data != nullptr ? data : "");
        }
    }
    ```

3. 注册订阅（须在UI线程调用），通过`withStart`、`eventMask`和`ignoreMask`按需选择事件。

    <!-- @[content_change_register](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkUIEventObserver/entry/src/main/cpp/ContentChangeObserver.h) -->

    ```c
    // 注册内容变化事件订阅（须在UI线程调用），context为当前UI实例的上下文
    static void RegisterContentChange(ArkUI_ContextHandle context)
    {
        // withStart为true时接收START/CANCEL事件，false时仅接收END/SHOW/HIDE事件
        bool withStart = true;
        // 订阅全部事件类别：页面切换（Navigation/Router/Swiper/Tabs）、滚动、浮层
        uint32_t eventMask = OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_ALL;
        // 按需忽略scrollBy、scrollTo或Toast触发的事件，此处全部接收
        uint32_t ignoreMask = 0;

        ArkUI_ErrorCode code = OH_ArkUI_NativeModule_RegisterUIContentChangeEvent(context, withStart, eventMask,
            ignoreMask, nullptr, OnContentChangeEvent, &g_contentChangeSubscriptionId);
        if (code != ARKUI_ERROR_CODE_NO_ERROR) {
            OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "ContentChangeObserver",
                "register failed, error code: %{public}d", static_cast<int>(code));
        }
    }
    ```

    ArkTS侧将`getUIContext()`返回的UIContext对象传给Native模块，在Native侧通过[OH_ArkUI_GetContextFromNapiValue()](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getcontextfromnapivalue)映射为`ArkUI_ContextHandle`后再注册：

    <!-- @[content_change_napi](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkUIEventObserver/entry/src/main/cpp/napi_init.cpp) -->

    ```c
    // ArkTS侧传入getUIContext()获取的UIContext对象，映射为ArkUI_ContextHandle后注册订阅
    static napi_value RegisterContentChangeJs(napi_env env, napi_callback_info info)
    {
        size_t argc = 1;
        napi_value args[1] = { nullptr };
        napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
        if (argc < 1) {
            return nullptr;
        }
        ArkUI_ContextHandle context = nullptr;
        int32_t ret = OH_ArkUI_GetContextFromNapiValue(env, args[0], &context);
        if (ret != ARKUI_ERROR_CODE_NO_ERROR || context == nullptr) {
            return nullptr;
        }
        RegisterContentChange(context);
        return nullptr;
    }
    ```

4. 不再使用时注销订阅（须在UI线程调用）。

    <!-- @[content_change_unregister](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkUIEventObserver/entry/src/main/cpp/ContentChangeObserver.h) -->

    ```c
    // 注销订阅（须在UI线程调用），context为当前UI实例的上下文
    static void UnregisterContentChange(ArkUI_ContextHandle context)
    {
        OH_ArkUI_NativeModule_UnRegisterUIContentChangeEvent(context, g_contentChangeSubscriptionId);
        g_contentChangeSubscriptionId = 0;
    }
    ```

## 异常处理

### 错误码

注册与注销接口通过返回值报告错误，错误码定义见[ArkUI_ErrorCode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)：

| 错误码 | 触发条件 | 处理建议 |
| -- | -- | -- |
| ARKUI_ERROR_CODE_UI_CONTEXT_INVALID | uiContext为空 | 检查UI上下文获取链路，如UIContext对象是否已映射成功 |
| ARKUI_ERROR_CODE_CALLBACK_INVALID | callback为空 | 传入非空回调 |
| ARKUI_ERROR_CODE_PARAM_INVALID | eventMask为0、eventMask或ignoreMask含未知标志位、subscriptionId为空 | 检查掩码取值是否只包含受支持的枚举位 |
| ARKUI_ERROR_CODE_CAPI_INIT_ERROR | 系统不支持内容变化感知能力 | 升级系统版本（不低于26.1.0） |

注册失败时subscriptionId指向的值不会被修改，可在注销前依据返回值判断订阅是否有效。

### 线程约束违规

注册、注销接口必须在UI线程上调用，**从非UI线程调用会导致进程终止**。如业务逻辑运行在非UI线程，须先通过`emitter`、任务投递等方式切换回UI线程再调用。

### 借用对象生命周期

回调收到的event事件快照、GetContext返回的句柄、GetContentChangeEventJson返回的JSON封装对象及其中的字符串，均为借用对象，仅在本次回调执行期间有效：

- 不得保留引用或在回调返回后继续使用；
- 不得调用Destroy销毁；
- 需要留存数据时，必须在回调内拷贝（如复制JSON字符串内容）。

### 空事件详情

无法提供目标节点时，GetContentChangeEventJson调用仍成功返回，但事件详情JSON可能为空（GetSize为0），消费方解析前应先判空。

### 回调中注销

在回调中注销订阅是允许的，且不会改变当前正在分发的这一批回调；注销成功后，后续事件不再触发该订阅的回调。

## 相关文档

- [ui_info_collection.h参考文档](../reference/apis-arkui/capi-ui-info-collection-h.md)
- [ui_json_wrapper.h参考文档](../reference/apis-arkui/capi-ui-json-wrapper-h.md)
- [ArkUI_ErrorCode错误码](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)
- [感知用户交互事件](ndk-sense-interaction-events.md)
- [OH_ArkUI_GetContextFromNapiValue()](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getcontextfromnapivalue)
