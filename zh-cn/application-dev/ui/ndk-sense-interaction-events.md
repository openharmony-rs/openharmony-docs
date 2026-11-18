# 感知用户交互事件
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->

ArkUI提供了面向NDK的交互事件感知接口（[ui_info_collection.h](../reference/apis-arkui/capi-ui-info-collection-h.md)），通过注册观察者的方式，以JSON格式统一感知当前UI实例上发生的用户交互行为，并获取交互发生时命中的节点信息。

与[绑定手势事件](ndk-bind-gesture-events.md)（自己处理某个节点上的交互）不同，交互感知是**只读的全局观察**：无需逐节点绑定回调，不改变任何交互行为，适合以旁观者身份持续收集整个页面上的交互数据。

## 适用场景

- **应用内智能体**：感知用户的点击、滑动、拖拽等操作及其命中的节点，结合UI树信息，提供上下文相关的辅助建议或执行后续操作。
- **自动化测试**：在测试框架中校验交互逻辑是否触发、交互发生的坐标与命中节点是否符合预期。
- **交互行为埋点与监控**：以统一格式收集用户交互数据，用于用户体验分析、操作回放等。

上述场景的共同特点是：消费方需要**进程内、实时、全量**的交互事件流，而不参与交互处理本身。

## 接口说明

接口采用观察者模型：

1. 调用[OH_ArkUI_NativeModule_UIInfoCollectionRegisterInteractionObserver()](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectionregisterinteractionobserver)注册观察者，通过`eventMask`按位或指定关注的事件类型；
2. 关注的事件发生时，框架在UI线程上调用回调，通过[OH_ArkUI_NativeModule_UIJsonWrapper](../reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md)交付JSON格式的事件数据；
3. 不再使用时，调用[OH_ArkUI_NativeModule_UIInfoCollectionUnregisterInteractionObserver()](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectionunregisterinteractionobserver)注销。

事件数据顶层结构为`{"schemaVersion": 1, "type": "<事件类型>", ...}`，所有位置坐标均相对于屏幕（显示器），单位为物理像素（px），节点以`id`（节点ID）标识。

## 可感知的事件类型

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

各事件类型的详细字段说明，可参考[OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback()](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectioninteractionjsoncallback)。

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

## 约束与注意事项

- **线程要求**：注册、注销和事件回调均须在UI主线程上执行。
- **借用语义**：回调中的`json`对象为借用对象，仅在本次回调执行期间有效，不得保留或在回调返回后使用；需要留存数据时，必须在回调内通过[OH_ArkUI_NativeModule_UIJsonWrapperGetData()](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetdata)和[OH_ArkUI_NativeModule_UIJsonWrapperGetSize()](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetsize)读取并拷贝数据，也不得调用Destroy销毁该对象。
- **eventMask**：仅TAP至TOUCH之间的标志位有效，范围外的位会被忽略；未包含任何有效标志位时返回[ARKUI_ERROR_CODE_PARAM_INVALID](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)。
- **多观察者**：同一个UI实例可注册多个观察者；使用相同的callback和userData重复注册会创建新的独立观察者，各自持有独立的注册ID。
- **注销纪律**：观察者不再使用时必须注销；注销后回调不再触发。回调内可以安全注销观察者（包括自身）。
- **只读感知**：感知能力不改变任何手势识别、命中测试和事件分发行为；未注册任何观察者时几乎没有开销。

## 开发步骤

以下步骤介绍如何注册交互事件观察者并处理回调，示例代码来自[应用示例](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NdkUIEventObserver)。

1. 准备开发环境，引入头文件并链接动态库。

    ```c
    #include <hilog/log.h>                  // 日志输出
    #include <arkui/native_type.h>          // ArkUI_ContextHandle
    #include <arkui/ui_info_collection.h>   // 交互感知接口
    #include <arkui/ui_json_wrapper.h>      // JSON封装对象访问
    ```

    在CMakeLists.txt中链接libace_ndk.z.so：

    ```cmake
    target_link_libraries(entry PUBLIC libace_ndk.z.so)
    ```

2. 实现事件回调。回调通过JSON封装对象接收事件数据，在回调内完成解析或拷贝。

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

3. 注册观察者（须在UI线程调用）。

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

4. 不再使用时注销观察者（须在UI线程调用）。

    <!-- @[interaction_unregister](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkUIEventObserver/entry/src/main/cpp/InteractionObserver.h) -->

    ```c
    // 注销观察者（须在UI线程调用）
    static void UnregisterInteractionObserver()
    {
        OH_ArkUI_NativeModule_UIInfoCollectionUnregisterInteractionObserver(g_interactionObserverId);
        g_interactionObserverId = 0;
    }
    ```

## 事件数据示例

以下为各事件类型的数据示例（坐标为屏幕物理像素）：

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

## 相关文档

- [ui_info_collection.h参考文档](../reference/apis-arkui/capi-ui-info-collection-h.md)
- [ui_json_wrapper.h参考文档](../reference/apis-arkui/capi-ui-json-wrapper-h.md)
- [ArkUI_ErrorCode错误码](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)
- [监听UI内容变化事件](ndk-listen-to-content-change-events.md)
- [绑定手势事件](ndk-bind-gesture-events.md)
- [绑定拖拽事件](ndk-drag-event.md)
