# 感知UI事件
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->

ArkUI提供了面向NDK的UI事件感知接口（[ui_info_collection.h](../reference/apis-arkui/capi-ui-info-collection-h.md)），通过注册观察者/订阅的方式，以回调统一感知当前UI实例上的用户交互行为与界面变化，作为应用内智能体、UI自动化等UI感知场景的重要信息来源。接口覆盖两类事件：

- **交互事件感知**：以JSON格式统一感知点击、长按、拖动、捏合、旋转、快滑、统一拖拽和原始触摸共9类交互事件，并获取交互发生时命中的节点信息；
- **UI内容变化事件监听**：感知页面切换（Navigation、Router、Swiper、Tabs）、滚动和浮层（Dialog、Toast等）三类界面变化，通过回调获取变化的开始、结束事件及对应时间戳。

两类接口均采用观察者模型：注册时通过掩码指定关注的事件范围，关注的事件发生时框架在UI线程上调用回调，不再使用时注销。

与[绑定手势事件](ndk-bind-gesture-events.md)（自己处理某个节点上的交互）不同，事件感知是**只读的全局观察**：无需逐节点绑定回调，不改变任何交互行为，适合以旁观者身份持续收集整个页面上的事件数据。

## 适用场景

- **应用内智能体**：感知用户的点击、滑动、拖拽等操作及命中的节点，结合页面切换、弹窗显示等内容变化事件，提供上下文相关的辅助建议或执行后续操作。
- **自动化测试**：在测试框架中校验交互逻辑是否触发、页面切换与滚动是否完成、交互发生的坐标与命中节点是否符合预期。
- **交互行为埋点与监控**：以统一格式收集用户交互数据，用于用户体验分析、操作回放等。
- **页面体验监控**：基于内容变化事件的START/END配对与时间戳，统计页面切换耗时、动效完成时机、弹窗停留时长等指标。

上述场景的共同特点是：消费方需要**进程内、实时、全量**的事件流，而不参与交互处理本身。

## 开发准备

引入头文件并链接动态库。两类事件感知能力均由`ui_info_collection.h`提供，事件数据均通过[OH_ArkUI_NativeModule_UIJsonWrapper](../reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md)封装的JSON对象交付。

```c
#include <hilog/log.h>                  // 日志输出
#include <arkui/native_type.h>          // ArkUI_ContextHandle
#include <arkui/native_node_napi.h>     // OH_ArkUI_GetContextFromNapiValue
#include <arkui/ui_info_collection.h>   // UI事件感知接口
#include <arkui/ui_json_wrapper.h>      // JSON封装对象访问
```

在CMakeLists.txt中链接libace_ndk.z.so：

```cmake
target_link_libraries(entry PUBLIC libace_ndk.z.so)
```

ArkTS侧将`getUIContext()`返回的UIContext对象传给Native模块，在Native侧通过[OH_ArkUI_GetContextFromNapiValue()](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getcontextfromnapivalue)映射为`ArkUI_ContextHandle`后再注册。后文示例代码来自[应用示例](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NdkUIEventObserver)，示例中`LOG_PRINT_DOMAIN`为自定义的hilog日志域常量。

## 交互事件感知

### 可感知的事件类型

`eventMask`由[OH_ArkUI_NativeModule_UIInfoCollection_InteractionEventType](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollection_interactioneventtype)的枚举值按位或组合而成：

| 事件类型 | 枚举值 | 触发时机 | 事件数据字段 |
| -- | -- | -- | -- |
| 点击手势（Tap） | `..._EVENT_TAP` | 节点上绑定的TapGesture识别成功 | id、point、count、fingers |
| 点击事件（Click） | `..._EVENT_CLICK` | 节点上设置的onClick等内置点击事件识别成功 | id、point、count、fingers |
| 长按（LongPress） | `..._EVENT_LONG_PRESS` | 长按完成（抬起）时上报一次 | id、point、actualDuration、action |
| 拖动手势（Pan） | `..._EVENT_PAN` | 拖动开始、结束或取消 | id、point、direction、action |
| 捏合（Pinch） | `..._EVENT_PINCH` | 捏合开始、结束或取消；scale仅在结束时携带 | id、point、fingers、action、scale |
| 旋转（Rotation） | `..._EVENT_ROTATION` | 旋转开始、结束或取消；angle仅在结束时携带 | id、point、fingers、action、angle |
| 快滑（Swipe） | `..._EVENT_SWIPE` | 滑动完成（抬起且速度达标）时上报一次 | id、downPoint、upPoint、direction、speed、actualSpeed |
| 统一拖拽（Drag） | `..._EVENT_DRAG` | 统一拖拽开始、结束 | 见下方说明 |
| 原始触摸（Touch） | `..._EVENT_TOUCH` | 任意手指按下或抬起 | action、fingerId、point；按下时还携带id |

交互事件数据顶层结构为`{"schemaVersion": 1, "type": "<事件类型>", ...}`，所有位置坐标均相对于屏幕（显示器），单位为物理像素（px），节点以`id`（节点ID）标识。各事件类型的详细字段说明，可参考[OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback()](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectioninteractionjsoncallback)。

### 手势事件

- **Tap与Click的区别**：Tap对应开发者显式绑定的[点击手势](ndk-bind-gesture-events.md)（TapGesture），Click对应组件内置的点击事件（onClick）；两者数据结构相同，一次"单击组件"通常只会触发其中一种。
- **完成型手势**：Tap、Click、Swipe在交互完成时各上报一次；长按手势同样只在完成时上报（`action`固定为`"end"`），并在`actualDuration`中携带实际按压时长（毫秒）。
- **连续型手势**：Pan、Pinch、Rotation携带`action`字段（`"start"`、`"end"`、`"cancel"`），用于区分交互阶段；Pinch的`scale`和Rotation的`angle`仅在`"end"`时携带。
- 手势事件的`id`为手势绑定的节点ID。

### 统一拖拽（Drag）

统一拖拽事件在拖拽开始（`action`为`"start"`）时携带`id`（拖拽源节点）、`point`、`hostName`（所属应用包名）和`actualDuration`（从按下到开始拖拽的时长）；在拖拽结束（`action`为`"end"`）时携带`point`、`dropResult`（`"success"`或`"fail"`）、`hostName`，仅在拖拽成功时携带`id`（此次为放置目标节点ID）。

### 原始触摸（Touch）

原始触摸事件在**事件分发层**感知，早于手势识别，且**不要求命中任何可交互组件**：

- 按下（`action`为`"down"`）时携带命中节点的`id`（触摸命中链上的首个节点）；抬起（`action`为`"up"`）时不携带节点ID。
- 触摸取消（cancel）不会上报给观察者。
- 原始触摸与手势事件互补：需要"用户正在按压某节点"这类瞬时信号时使用Touch，需要"一次完整交互的结果"时使用对应手势事件。

### 约束与注意事项

- **线程要求**：注册、注销和事件回调均须在UI主线程上执行，从非UI线程调用注册/注销接口会导致进程终止。
- **借用语义**：回调中的`json`对象为借用对象，仅在本次回调执行期间有效，不得保留或在回调返回后使用；需要留存数据时，必须在回调内通过[OH_ArkUI_NativeModule_UIJsonWrapperGetData()](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetdata)和[OH_ArkUI_NativeModule_UIJsonWrapperGetSize()](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetsize)读取并拷贝数据，也不得调用Destroy销毁该对象。
- **eventMask**：仅TAP至TOUCH之间的标志位有效，范围外的位会被忽略；未包含任何有效标志位时返回[ARKUI_ERROR_CODE_PARAM_INVALID](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)。
- **多观察者**：同一个UI实例可注册多个观察者；使用相同的callback和userData重复注册会创建新的独立观察者，各自持有独立的注册ID。
- **注销纪律**：观察者不再使用时必须注销；注销后回调不再触发。回调内可以安全注销观察者（包括自身）。
- **只读感知**：感知能力不改变任何手势识别、命中测试和事件分发行为；未注册任何观察者时几乎没有开销。

### 开发步骤

1. 实现事件回调。回调通过JSON封装对象接收事件数据，在回调内完成解析或拷贝。

    <!-- @[interaction_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkUIEventObserver/entry/src/main/cpp/InteractionObserver.h) -->

    ```c
    // 事件回调：json为借用对象，仅在本函数执行期间有效
    static void OnInteractionEvent(const OH_ArkUI_NativeModule_UIJsonWrapper *json, void *userData)
    {
        const char *data = OH_ArkUI_NativeModule_UIJsonWrapperGetData(json);
        uint32_t size = OH_ArkUI_NativeModule_UIJsonWrapperGetSize(json);
        if (data == nullptr || size == 0) {
            return;
        }
        // 需要留存数据时必须在本回调内拷贝，例如：
        // std::string payload(data, size);
        // 此处仅打印事件JSON
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "InteractionObserver",
            "interaction event: %{public}s", data);
    }
    ```

2. 注册观察者（须在UI线程调用）。

    <!-- @[interaction_register](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkUIEventObserver/entry/src/main/cpp/InteractionObserver.h) -->

    ```c
    // 注册观察者（须在UI线程调用），context为当前UI实例的上下文
    static void RegisterInteractionObserver(ArkUI_ContextHandle context)
    {
        // 按需组合关注的事件类型，此处以全部事件为例
        uint32_t eventMask =
            OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_TAP |
            OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_CLICK |
            OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_LONG_PRESS |
            OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_PAN |
            OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_PINCH |
            OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_ROTATION |
            OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_SWIPE |
            OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_DRAG |
            OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_TOUCH;

        ArkUI_ErrorCode code = OH_ArkUI_NativeModule_UIInfoCollectionRegisterInteractionObserver(
            context, eventMask, &g_interactionObserverId, OnInteractionEvent, nullptr);
        if (code != ARKUI_ERROR_CODE_NO_ERROR) {
            OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "InteractionObserver",
                "register failed, error code: %{public}d", static_cast<int>(code));
        }
    }
    ```

    ArkTS侧将`getUIContext()`返回的UIContext对象传给Native模块，在Native侧通过[OH_ArkUI_GetContextFromNapiValue()](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getcontextfromnapivalue)映射为`ArkUI_ContextHandle`后再注册：

    <!-- @[interaction_napi](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkUIEventObserver/entry/src/main/cpp/napi_init.cpp) -->

    ```c
    // ArkTS侧传入getUIContext()获取的UIContext对象，映射为ArkUI_ContextHandle后注册观察者
    static napi_value RegisterInteractionObserverJs(napi_env env, napi_callback_info info)
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
        RegisterInteractionObserver(context);
        return nullptr;
    }
    ```

3. 不再使用时注销观察者（须在UI线程调用）。

    <!-- @[interaction_unregister](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkUIEventObserver/entry/src/main/cpp/InteractionObserver.h) -->

    ```c
    // 注销观察者（须在UI线程调用）
    static void UnregisterInteractionObserver()
    {
        OH_ArkUI_NativeModule_UIInfoCollectionUnregisterInteractionObserver(g_interactionObserverId);
        g_interactionObserverId = 0;
    }
    ```

## 监听UI内容变化事件

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

### 事件详情JSON

通过[OH_ArkUI_NativeModule_UIContentChangeEventGetContentChangeEventJson()](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventgetcontentchangeeventjson)获取事件详情JSON，顶层包含`schemaVersion`字段，并携带以下字段：

| 字段 | 类型 | 说明 |
| -- | -- | -- |
| schemaVersion | integer | 固定为1 |
| eventType | integer | 0～11，与GetType返回值相等 |
| category | string | `page`（页面切换）/ `scroll`（滚动）/ `overlay`（浮层）；Swiper、Tabs属于page |
| targetNode | object | 事件目标节点：`{"id": "42", "type": "Scroll"}`，id为节点ID字符串，type为ArkUI组件名 |
| triggerNode | object或null | 引起内容变化的触发节点；页面/滚动事件为null；浮层事件在可提供时返回 |
| overlayType | string或null | 浮层类型：`dialog`、`customDialog`、`actionSheet`、`popup`、`menu`、`toast`、`overlay`；Sheet/ContentCover为`dialog`；其他类别为null |
| subtree | object或null | 目标节点子树快照；仅在PAGE_CHANGE_END与OVERLAY_SHOW事件中包含 |

此外，[OH_ArkUI_NativeModule_UIContentChangeEventGetTimestamp()](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventgettimestamp)可获取事件的单调时间戳（单位纳秒，不表示日历时间），用于耗时统计；[OH_ArkUI_NativeModule_UIContentChangeEventGetContext()](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventgetcontext)可获取事件关联的UI上下文（借用句柄）。

### 约束与限制

不同组件在事件采集上的行为存在差异，使用时须注意：

1. **Swiper自动播放期间事件被抑制**：Swiper开启自动播放（autoplay）时，为避免高频回调，该Swiper的START/END/CANCEL事件默认均不上报（不仅抑制自动翻页动作）；如需感知该Swiper的切换事件，需关闭autoplay。活动切换过程中开启autoplay，旧周期不会补发END/CANCEL，关闭后新周期正常上报。

2. **程序化滚动的高频抑制**：scrollTo、scrollBy等接口实现的自动化滚动同样会触发滚动事件；高频自动化滚动场景下，建议注册时在`ignoreMask`中设置`IGNORE_SCROLLTO`或`IGNORE_SCROLLBY`忽略对应来源的整个滚动周期，避免高频回调。无实际位移的调用（如滚动到当前位置）不会产生事件。

3. **Toast瞬时消息**：Toast为瞬时消息，其显示与消失会产生OVERLAY_SHOW/HIDE事件；不关注Toast的场景建议在`ignoreMask`中设置`IGNORE_TOAST`忽略。

4. **浮层事件的覆盖范围**：仅能覆盖本应用进程内由ArkUI管理的浮层；无法覆盖由UIExtension承载的跨进程系统级弹窗、Web组件内部的弹窗事件，以及XComponent内自绘制内容中的弹窗事件。

5. **END事件以动效结束为准**：页面路由、抛滑、Swiper、Tabs切换的END事件均在动效结束后上报，不会在动效期间上报：PAGE_CHANGE_END在路由转场完成后、SCROLL_END在滚动交互及后续惯性滚动均结束后、SWIPER_END/TABS_END在切换动画完成后上报。每个控件的事件相互独立触发。

6. **可能存在有START没有END的情况**：Swiper、Tabs、页面路由等切换到一半松手回弹、页面未实际变化时，不会上报END，而是上报对应的CANCEL事件（SWIPER_CANCEL/TABS_CANCEL）。CANCEL仅通知给收到该周期START的订阅（即`withStart`为`true`时），取消周期不会再上报END。

### 开发步骤

1. 实现事件回调。回调在UI线程上同步执行，事件快照为借用对象，仅在本次回调返回前有效，需要在回调内完成读取或拷贝。

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

2. 注册订阅（须在UI线程调用），通过`withStart`、`eventMask`和`ignoreMask`按需选择事件。

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

    与交互事件感知相同，ArkTS侧传入`getUIContext()`获取的UIContext对象，在Native侧映射为`ArkUI_ContextHandle`后再注册：

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

3. 不再使用时注销订阅（须在UI线程调用）。

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

注册与注销接口均通过返回值报告错误，错误码定义见[ArkUI_ErrorCode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)。

交互事件感知（RegisterInteractionObserver / UnregisterInteractionObserver）：

| 错误码 | 触发条件 | 处理建议 |
| -- | -- | -- |
| ARKUI_ERROR_CODE_UI_CONTEXT_INVALID | uiContext为空 | 检查UI上下文获取链路，如UIContext对象是否已映射成功 |
| ARKUI_ERROR_CODE_PARAM_INVALID | eventMask不含任何有效标志位、callback为空、registerID为空 | 检查掩码取值是否只包含受支持的枚举位，并传入非空回调和输出参数 |
| ARKUI_ERROR_CODE_CAPI_INIT_ERROR | 系统不支持交互感知能力 | 升级系统版本（不低于26.1.0） |

UI内容变化事件（RegisterUIContentChangeEvent / UnRegisterUIContentChangeEvent）：

| 错误码 | 触发条件 | 处理建议 |
| -- | -- | -- |
| ARKUI_ERROR_CODE_UI_CONTEXT_INVALID | uiContext为空 | 同上 |
| ARKUI_ERROR_CODE_CALLBACK_INVALID | callback为空 | 同上 |
| ARKUI_ERROR_CODE_PARAM_INVALID | eventMask为0、eventMask或ignoreMask含未知标志位、subscriptionId为空 | 检查掩码取值是否只包含受支持的枚举位 |
| ARKUI_ERROR_CODE_CAPI_INIT_ERROR | 系统不支持内容变化感知能力 | 升级系统版本（不低于26.1.0） |

操作失败时，注册ID/订阅ID输出参数指向的值不会被修改，可在注销前依据返回值判断注册是否有效。

### 线程约束

两类接口的注册、注销都必须在UI线程上调用，**从非UI线程调用会导致进程终止**；事件回调均在注册时指定的UI上下文所关联的UI线程上同步执行。如业务逻辑运行在非UI线程，须先通过`emitter`、任务投递等方式切换回UI线程再调用。

### 借用对象生命周期

回调中收到的数据均为借用对象，仅在本次回调执行期间有效：

- 交互事件的`json`封装对象、内容变化事件的`event`快照、GetContext返回的句柄、GetContentChangeEventJson返回的JSON封装对象及其中的字符串，均不得保留引用或在回调返回后继续使用；
- 不得调用Destroy销毁；
- 需要留存数据时，必须在回调内拷贝（如复制JSON字符串内容）。

### 空事件详情

内容变化事件无法提供目标节点时，GetContentChangeEventJson调用仍成功返回，但事件详情JSON可能为空（GetSize为0），消费方解析前应先判空。

### 回调中注销

在回调中注销观察者/订阅是允许的，且不会改变当前正在分发的这一批回调；注销成功后，后续事件不再触发对应回调。

## 事件数据示例

以下为交互事件的数据示例（坐标为屏幕物理像素）：

```json
{"schemaVersion": 1, "type": "Tap", "id": 12, "point": [540, 1210], "count": 1, "fingers": 1}
```

```json
{"schemaVersion": 1, "type": "Click", "id": 12, "point": [540, 1210], "count": 1, "fingers": 1}
```

```json
{"schemaVersion": 1, "type": "LongPress", "id": 12, "point": [540, 1210], "actualDuration": 1520, "action": "end"}
```

```json
{"schemaVersion": 1, "type": "Pan", "id": 8, "point": [542, 1230], "direction": 3, "action": "start"}
```

```json
{"schemaVersion": 1, "type": "Pinch", "id": 8, "point": [[512, 1100], [570, 1310]], "fingers": 2, "action": "end", "scale": 1.5}
```

```json
{"schemaVersion": 1, "type": "Rotation", "id": 8, "point": [[512, 1100], [570, 1310]], "fingers": 2, "action": "end", "angle": 45.0}
```

```json
{"schemaVersion": 1, "type": "Swipe", "id": 5, "downPoint": [[540, 1500]], "upPoint": [[540, 900]], "direction": 4, "speed": 800.0, "actualSpeed": 842.5}
```

```json
{"schemaVersion": 1, "type": "Drag", "action": "start", "id": 5, "point": [540, 1500], "hostName": "com.example.demo", "actualDuration": 320}
```

```json
{"schemaVersion": 1, "type": "Drag", "action": "end", "point": [540, 800], "dropResult": "success", "id": 9, "hostName": "com.example.demo"}
```

```json
{"schemaVersion": 1, "type": "Touch", "action": "down", "fingerId": 0, "point": [540, 1210], "id": 12}
```

```json
{"schemaVersion": 1, "type": "Touch", "action": "up", "fingerId": 0, "point": [541, 1212]}
```

以下为UI内容变化事件详情JSON的数据示例：

```json
{"schemaVersion": 1, "eventType": 10, "category": "page", "targetNode": {"id": "42", "type": "Tabs"}, "triggerNode": null, "overlayType": null, "subtree": null}
```

```json
{"schemaVersion": 1, "eventType": 4, "category": "overlay", "targetNode": {"id": "56", "type": "Dialog"}, "triggerNode": {"id": "12", "type": "Button"}, "overlayType": "dialog", "subtree": {"id": "56", "type": "Dialog", "children": []}}
```

## 相关文档

- [ui_info_collection.h参考文档](../reference/apis-arkui/capi-ui-info-collection-h.md)
- [ui_json_wrapper.h参考文档](../reference/apis-arkui/capi-ui-json-wrapper-h.md)
- [ArkUI_ErrorCode错误码](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)
- [绑定手势事件](ndk-bind-gesture-events.md)
- [绑定拖拽事件](ndk-drag-event.md)
