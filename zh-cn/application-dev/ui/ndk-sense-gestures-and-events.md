# 监听全局手势
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

从API版本26.1.0开始，可以通过[OH_ArkUI_NativeModule_UIInfoCollectionRegisterInteractionObserver](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectionregisterinteractionobserver)接口为指定的UI实例注册交互事件观察者，全局感知点击、长按、拖动、捏合、旋转、快滑、统一拖拽和原始触摸共9类交互事件。事件以JSON描述，携带交互发生时命中的节点信息，通过回调通知。

观察者是**只读的全局观察**：与[绑定手势事件](ndk-bind-gesture-events.md)（自己处理某个节点上的交互）不同，观察者无需逐节点绑定回调，不改变任何手势识别、命中测试和事件分发行为，适合应用内智能体、自动化测试、交互埋点等需要进程内、实时、全量事件流的场景。

## 约束与限制

| 约束项 | 说明 |
| --- | --- |
| 线程要求 | 注册、注销和事件回调均须在UI主线程上执行，从非UI线程调用注册/注销接口会导致进程终止。 |
| 借用语义 | 回调中的json对象为借用对象，仅在本次回调执行期间有效，不得保留或在回调返回后使用，也不得调用[OH_ArkUI_NativeModule_UIJsonWrapperDestroy](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy)销毁；需要留存数据时必须在回调内拷贝。 |
| eventMask | 仅TAP至TOUCH之间的标志位有效，范围外的位会被忽略；未包含任何有效标志位时接口同步返回[ARKUI_ERROR_CODE_PARAM_INVALID](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)。 |
| 多观察者 | 同一UI实例可注册多个观察者；使用相同的callback和userData组合重复注册，会创建新的独立观察者并分配新的注册ID。 |
| 注销纪律 | 观察者不再使用时必须注销；注销后回调不再触发。回调内可以安全注销观察者（包括自身），不会改变当前正在分发的这一批回调。 |
| 只读感知 | 感知不改变任何交互行为；未注册任何观察者时几乎没有开销。 |
| 坐标 | 所有位置坐标相对于屏幕（显示器），单位为物理像素（px）。 |

## 接口说明

[OH_ArkUI_NativeModule_UIInfoCollectionRegisterInteractionObserver](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectionregisterinteractionobserver)([ArkUI_ContextHandle](../reference/apis-arkui/capi-arkui-nativemodule-arkui-context8h.md) uiContext, uint32_t eventMask, uint32_t \*registerID, [OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectioninteractionjsoncallback) callback, void \*userData) 为指定的UI实例注册交互事件观察者，观察者仅接收eventMask指定类型的事件回调。

callback不能为空，事件数据通过[OH_ArkUI_NativeModule_UIJsonWrapper](../reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md)封装的JSON对象在回调中交付。不再使用观察者时，必须调用[OH_ArkUI_NativeModule_UIInfoCollectionUnregisterInteractionObserver](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectionunregisterinteractionobserver)(registerID)注销。

## 交互事件说明

事件通过JSON字符串描述，顶层结构如下。

```json
{
    "schemaVersion": 1,
    "type": "<事件类型>"
}
```

其中，schemaVersion表示事件格式的版本号，当前固定为1；type表示事件类型；其余字段随事件类型不同而不同，节点以id（节点ID）标识。

注册时通过eventMask指定关注的事件范围，eventMask由[OH_ArkUI_NativeModule_UIInfoCollection_InteractionEventType](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollection_interactioneventtype)定义的枚举值按位或组合而成。该枚举除表示无事件的NONE外，其余枚举值均为位标志，其标识的事件与type的取值一一对应。

type取值及对应说明如下。

| 事件 | 枚举值 | 触发时机 | 事件数据字段 |
| --- | --- | --- | --- |
| 点击手势（Tap） | OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_TAP | 节点上绑定的TapGesture识别成功 | id、point、count、fingers |
| 点击事件（Click） | OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_CLICK | 节点上设置的onClick等内置点击事件识别成功 | id、point、count、fingers |
| 长按（LongPress） | OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_LONG_PRESS | 长按完成（抬起）时上报一次 | id、point、actualDuration、action |
| 拖动手势（Pan） | OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_PAN | 拖动开始、结束或取消 | id、point、direction、action |
| 捏合（Pinch） | OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_PINCH | 捏合开始、结束或取消；scale仅在结束时携带 | id、point、fingers、action、scale |
| 旋转（Rotation） | OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_ROTATION | 旋转开始、结束或取消；angle仅在结束时携带 | id、point、fingers、action、angle |
| 快滑（Swipe） | OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_SWIPE | 滑动完成（抬起且速度达标）时上报一次 | id、downPoint、upPoint、direction、speed、actualSpeed |
| 统一拖拽（Drag） | OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_DRAG | 统一拖拽开始、结束 | 见下方说明 |
| 原始触摸（Touch） | OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_TOUCH | 任意手指按下或抬起 | action、fingerId、point；按下时还携带id |

Tap与Click的区别：Tap对应开发者显式绑定的TapGesture，Click对应组件内置的onClick等点击事件；两者数据结构相同，一次“单击组件”通常只会触发其中一种。Tap、Click、Swipe、LongPress为完成型事件，在交互完成时各上报一次；其中LongPress的action固定为end，并在actualDuration中携带实际按压时长（毫秒）。Pan、Pinch、Rotation为连续型事件，携带action字段（start、end、cancel）区分交互阶段；Pinch的scale和Rotation的angle仅在end时携带。

统一拖拽（Drag）在开始（action为start）时携带id（拖拽源节点）、point、hostName（所属应用包名）和actualDuration（从按下到开始拖拽的时长）；在结束（action为end）时携带point、dropResult（success或fail）和hostName，仅在拖拽成功时携带id（此次为放置目标节点ID）。

原始触摸（Touch）在事件分发层感知，早于手势识别，且不要求命中任何可交互组件：按下（action为down）时携带命中节点的id，抬起（action为up）时不携带节点ID；触摸取消不会上报给观察者。

各事件的JSON示例依次如下（坐标为屏幕物理像素）。

- 点击手势的示例。

  ```json
  { "schemaVersion": 1, "type": "Tap", "id": 12, "point": [540, 1210], "count": 1, "fingers": 1 }
  ```

- 点击事件的示例。

  ```json
  { "schemaVersion": 1, "type": "Click", "id": 12, "point": [540, 1210], "count": 1, "fingers": 1 }
  ```

- 长按完成的示例。

  ```json
  { "schemaVersion": 1, "type": "LongPress", "id": 12, "point": [540, 1210], "actualDuration": 1520, "action": "end" }
  ```

- 拖动开始的示例。

  ```json
  { "schemaVersion": 1, "type": "Pan", "id": 8, "point": [542, 1230], "direction": 3, "action": "start" }
  ```

- 捏合结束的示例。

  ```json
  { "schemaVersion": 1, "type": "Pinch", "id": 8, "point": [[512, 1100], [570, 1310]], "fingers": 2, "action": "end", "scale": 1.5 }
  ```

- 旋转结束的示例。

  ```json
  { "schemaVersion": 1, "type": "Rotation", "id": 8, "point": [[512, 1100], [570, 1310]], "fingers": 2, "action": "end", "angle": 45.0 }
  ```

- 快滑的示例。

  ```json
  { "schemaVersion": 1, "type": "Swipe", "id": 5, "downPoint": [[540, 1500]], "upPoint": [[540, 900]], "direction": 4, "speed": 800.0, "actualSpeed": 842.5 }
  ```

- 统一拖拽开始和结束的示例。

  ```json
  { "schemaVersion": 1, "type": "Drag", "action": "start", "id": 5, "point": [540, 1500], "hostName": "com.example.demo", "actualDuration": 320 }
  ```

  ```json
  { "schemaVersion": 1, "type": "Drag", "action": "end", "point": [540, 800], "dropResult": "success", "id": 9, "hostName": "com.example.demo" }
  ```

- 原始触摸按下和抬起的示例。

  ```json
  { "schemaVersion": 1, "type": "Touch", "action": "down", "fingerId": 0, "point": [540, 1210], "id": 12 }
  ```

  ```json
  { "schemaVersion": 1, "type": "Touch", "action": "up", "fingerId": 0, "point": [541, 1212] }
  ```

## 开发步骤

以注册观察者并感知交互事件为例，先引入头文件。

```C++
#include <hilog/log.h>
#include <arkui/native_node_napi.h>
#include <arkui/ui_info_collection.h>
#include <arkui/ui_json_wrapper.h>

#define LOG_DOMAIN 0x0000
#define LOG_TAG "GestureEventObserver"
```

示例中uiContext为目标UI实例的[ArkUI_ContextHandle](../reference/apis-arkui/capi-arkui-nativemodule-arkui-context8h.md)。ArkTS侧通过getUIContext()获取UIContext并传给Native模块，在Native侧通过[OH_ArkUI_GetContextFromNapiValue()](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getcontextfromnapivalue)映射为ArkUI_ContextHandle后再注册。

<!-- @[interaction_observer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/GestureEventObserver/entry/src/main/cpp/NativeEntry.cpp) -->

```C++
// 事件回调：json为借用对象，仅在本函数执行期间有效。
static void OnInteractionEvent(const OH_ArkUI_NativeModule_UIJsonWrapper* json, void* userData)
{
    const char* data = OH_ArkUI_NativeModule_UIJsonWrapperGetData(json);
    if (data == nullptr || OH_ArkUI_NativeModule_UIJsonWrapperGetSize(json) == 0) {
        return;
    }
    // 需要留存数据时必须在本回调内拷贝，例如：std::string payload(data, size);
    OH_LOG_Print(LOG_APP, LOG_INFO, LOG_DOMAIN, LOG_TAG, "interaction event: %{public}s", data);
}

// 通过ArkUI_ContextHandle注册交互事件观察者（须在UI线程调用），感知全部9类交互事件。
void RegisterObserverCommand(ArkUI_ContextHandle uiContext)
{
    // 按需组合关注的事件类型，此处以全部事件为例。
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

    ArkUI_ErrorCode ret = OH_ArkUI_NativeModule_UIInfoCollectionRegisterInteractionObserver(
        uiContext, eventMask, &g_observerId, OnInteractionEvent, nullptr);
    if (ret != ARKUI_ERROR_CODE_NO_ERROR) {
        OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_DOMAIN, LOG_TAG,
            "register observer failed, error code: %{public}d", static_cast<int>(ret));
    }
}

// 注销交互事件观察者（须在UI线程调用）。
void UnregisterObserverCommand()
{
    OH_ArkUI_NativeModule_UIInfoCollectionUnregisterInteractionObserver(g_observerId);
    g_observerId = 0;
}
```

注册与注销接口均通过同步返回值报告结果，各取值如下：

- 注册返回值：[ARKUI_ERROR_CODE_NO_ERROR](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)、[ARKUI_ERROR_CODE_PARAM_INVALID](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)（必填指针为空或eventMask未包含任何受支持的标志位）、[ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)（UI上下文为空或无效）、[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)（Native实现不可用）
- 注销返回值：[ARKUI_ERROR_CODE_NO_ERROR](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)、[ARKUI_ERROR_CODE_PARAM_INVALID](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)（注册ID无效）、[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)

注册失败时registerID被置为0。CAPI_INIT_ERROR通常意味着当前系统未包含该能力，可确认运行环境的API版本为26.1.0及以上。
