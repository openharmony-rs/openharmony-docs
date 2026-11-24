# 事件末端拦截再分发开发指导（C/C++）

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

## 功能介绍

从API版本26.1.0开始，多模为应用提供了事件末端拦截再分发能力。应用创建并启用输入事件handler后，系统会在输入事件到达目标应用前同步回调应用，应用可以读取事件内容，并对每条事件单独决定是拦截（事件不再分发给目标应用）还是再分发（事件继续分发给目标应用）。使用场景例如：

- 云桌面、投屏类应用：需要读取全局输入流，按规则拦截特定按键或手势，其余事件再分发。
- 输入录制、自动化测试类应用：观察按键、鼠标、触摸和轴事件，过滤无关事件后再进行录制或回放。

## 接口说明

事件末端拦截再分发相关接口如下表所示，接口详细介绍请参考[oh_input_manager.h](../../reference/apis-input-kit/capi-oh-input-manager-h.md)。

| 接口名称 | 描述 |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Input_Result OH_Input_EventHandler_Create(OH_Input_EventTypeMask mask, OH_Input_EventHandler_OnEventFunc onEventFunc, OH_Input_EventHandler_OnDisabledFunc onDisabledFunc, OH_Input_EventHandler** handler) | 创建输入事件handler。 |
| Input_Result OH_Input_EventHandler_Enable(OH_Input_EventHandler* handler, bool enable) | 启用或禁用输入事件handler。 |
| Input_Result OH_Input_EventHandler_IsEnabled(const OH_Input_EventHandler* handler, bool* enabled) | 查询是否启用了handler。 |
| Input_Result OH_Input_EventHandler_GetMask(const OH_Input_EventHandler* handler, OH_Input_EventTypeMask* mask) | 查询输入事件handler的事件类型掩码。 |
| void OH_Input_EventHandler_Destroy(OH_Input_EventHandler* handler) | 销毁输入事件的handler并释放资源。 |
| Input_Result OH_Input_Event_GetType(const OH_Input_Event* event, OH_Input_EventType* type) | 获取输入事件的类型。 |
| Input_Result OH_Input_Event_AsKeyEvent(const OH_Input_Event* event, const Input_KeyEvent** keyEvent) | 从输入事件中获取只读的按键事件视图。 |
| Input_Result OH_Input_Event_AsMouseEvent(const OH_Input_Event* event, const Input_MouseEvent** mouseEvent) | 从输入事件中获取只读的鼠标事件视图。 |
| Input_Result OH_Input_Event_AsTouchEvent(const OH_Input_Event* event, const Input_TouchEvent** touchEvent) | 从输入事件中获取只读的触摸事件视图。 |
| Input_Result OH_Input_Event_AsAxisEvent(const OH_Input_Event* event, const Input_AxisEvent** axisEvent) | 从输入事件中获取只读的轴事件视图。 |

## 约束与限制

1. 仅支持PC/2in1设备。
2. 每个进程同一时刻只允许启用一个handler。若本进程已有启用的handler，再次启用返回INPUT_REPEAT_HANDLER。
3. 事件回调为同步调用：返回原事件（非NULL）表示再分发，返回NULL表示拦截。回调中不要执行耗时操作（如同步I/O、长时间计算），否则系统会超时禁用handler，并通过onDisabledFunc通知应用，此后事件恢复默认分发。
4. OH_Input_Event对象在当前版本为只读。OH_Input_Event_AsKeyEvent等接口返回的是从event借用的只读视图，仅在当前回调执行期间有效：不要在回调外保存或使用，不要对其调用Set*接口修改，也不要调用Destroy接口销毁。

## 开发步骤

### 链接动态库

调用事件末端拦截再分发接口前，需链接相关动态库。在CMakeLists.txt文件中进行如下配置：

```txt
target_link_libraries(entry PUBLIC libohinput.so)
```

### 申请所需权限

应用需要在module.json5中声明所需权限，详细的配置方法参考[声明权限文档](../../security/AccessToken/declare-permissions.md)。

ohos.permission.HOOK_INPUT_EVENT（权限级别system_basic）：允许应用拦截输入事件。该权限的reason与usedScene字段必填；无法通过弹窗向用户申请授权，应用上架审核通过后，需引导用户在"设置 > 隐私 > 权限管理"中手动开启授权。

```json
"requestPermissions": [
    {
        "name": "ohos.permission.HOOK_INPUT_EVENT",
        "reason": "$string:hook_input_event_permission_reason",
        "usedScene": {
            "abilities": [
                "EntryAbility"
            ],
            "when": "inuse"
        }
    }
]
```

### 创建并启用输入事件handler

创建handler时，通过事件类型掩码指定要观测的事件类型（支持按键、鼠标、触摸、轴事件的任意组合），并注册事件回调和禁用回调。

<!-- @[event_handler_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputKit/NDKInputEventHook/entry/src/main/cpp/napi_init.cpp) -->

``` C++
// 事件回调的完整实现见“处理输入事件”小节
const OH_Input_Event* OnEvent(OH_Input_EventHandler* handler, const OH_Input_Event* event);

// 定义handler被禁用的回调（例如事件回调处理超时被系统禁用）
void OnDisabled(OH_Input_EventHandler* handler)
{
    // handler已被禁用，输入事件恢复默认分发；如需继续处理，可重新调用OH_Input_EventHandler_Enable启用
    // ...
}

static napi_value CreateAndEnableHandler(napi_env env, napi_callback_info info)
{
    // 观测全部四类事件，可按需组合掩码
    OH_Input_EventTypeMask mask = OH_INPUT_EVENT_TYPE_MASK_KEY | OH_INPUT_EVENT_TYPE_MASK_MOUSE |
        OH_INPUT_EVENT_TYPE_MASK_TOUCH | OH_INPUT_EVENT_TYPE_MASK_AXIS;
    OH_Input_EventHandler* handler = nullptr;
    Input_Result ret = OH_Input_EventHandler_Create(mask, OnEvent, OnDisabled, &handler);
    // ...

    // 启用handler，启用后开始接收输入事件
    ret = OH_Input_EventHandler_Enable(handler, true);
    // ...

    // 查询handler是否启用
    bool enabled = false;
    ret = OH_Input_EventHandler_IsEnabled(handler, &enabled);
    // ...

    // 查询handler的事件类型掩码
    OH_Input_EventTypeMask maskOfHandler = 0;
    ret = OH_Input_EventHandler_GetMask(handler, &maskOfHandler);
    // ...
    // ...
}
```

### 处理输入事件

在事件回调中，先调用OH_Input_Event_GetType获取事件类型，再转换为对应类型的事件视图读取字段，最后根据业务逻辑决定拦截或再分发。事件类型较多时，建议将各类型的事件处理逻辑拆分为独立函数，保持回调函数简短。

<!-- @[event_handler_process](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputKit/NDKInputEventHook/entry/src/main/cpp/napi_init.cpp) -->

``` C++
// 按键事件处理：转换为Input_KeyEvent视图读取字段，返回true表示拦截，返回false表示再分发
static bool HandleKeyEvent(const OH_Input_Event* event)
{
    const Input_KeyEvent* keyEvent = nullptr;
    if (OH_Input_Event_AsKeyEvent(event, &keyEvent) == INPUT_SUCCESS && keyEvent != nullptr) {
        int32_t action = OH_Input_GetKeyEventAction(keyEvent);
        int32_t keyCode = OH_Input_GetKeyEventKeyCode(keyEvent);
        int64_t actionTime = OH_Input_GetKeyEventActionTime(keyEvent);
        // ...
        // 按业务规则决策：例如拦截某个按键的按下事件，其余再分发
        if (action == KEY_ACTION_DOWN && keyCode == KEYCODE_1) {
            return true; // 拦截该事件
        }
    }
    return false;
}

// 鼠标事件处理：转换为Input_MouseEvent视图读取字段，返回true表示拦截，返回false表示再分发
static bool HandleMouseEvent(const OH_Input_Event* event)
{
    const Input_MouseEvent* mouseEvent = nullptr;
    if (OH_Input_Event_AsMouseEvent(event, &mouseEvent) == INPUT_SUCCESS && mouseEvent != nullptr) {
        int32_t action = OH_Input_GetMouseEventAction(mouseEvent);
        int32_t displayX = OH_Input_GetMouseEventDisplayX(mouseEvent);
        int32_t displayY = OH_Input_GetMouseEventDisplayY(mouseEvent);
        int32_t button = OH_Input_GetMouseEventButton(mouseEvent);
        int64_t actionTime = OH_Input_GetMouseEventActionTime(mouseEvent);
        // ...
        // ...
    }
    return false;
}

// 触摸事件处理：转换为Input_TouchEvent视图读取字段，返回true表示拦截，返回false表示再分发
static bool HandleTouchEvent(const OH_Input_Event* event)
{
    const Input_TouchEvent* touchEvent = nullptr;
    if (OH_Input_Event_AsTouchEvent(event, &touchEvent) == INPUT_SUCCESS && touchEvent != nullptr) {
        int32_t action = OH_Input_GetTouchEventAction(touchEvent);
        int32_t fingerId = OH_Input_GetTouchEventFingerId(touchEvent);
        int32_t displayX = OH_Input_GetTouchEventDisplayX(touchEvent);
        int32_t displayY = OH_Input_GetTouchEventDisplayY(touchEvent);
        int64_t actionTime = OH_Input_GetTouchEventActionTime(touchEvent);
        // ...
        // ...
    }
    return false;
}

// 轴事件处理：转换为Input_AxisEvent视图读取字段，返回true表示拦截，返回false表示再分发
static bool HandleAxisEvent(const OH_Input_Event* event)
{
    const Input_AxisEvent* axisEvent = nullptr;
    if (OH_Input_Event_AsAxisEvent(event, &axisEvent) == INPUT_SUCCESS && axisEvent != nullptr) {
        InputEvent_AxisAction action = AXIS_ACTION_CANCEL;
        InputEvent_AxisEventType axisEventType = AXIS_EVENT_TYPE_SCROLL;
        InputEvent_SourceType sourceType = SOURCE_TYPE_MOUSE;
        OH_Input_GetAxisEventAction(axisEvent, &action);
        OH_Input_GetAxisEventType(axisEvent, &axisEventType);
        OH_Input_GetAxisEventSourceType(axisEvent, &sourceType);
        if (axisEventType == AXIS_EVENT_TYPE_SCROLL) {
            double scrollValue = 0.0;
            OH_Input_GetAxisEventAxisValue(axisEvent, AXIS_TYPE_SCROLL_VERTICAL, &scrollValue);
            // ...
        }
        // ...
        // ...
    }
    return false;
}

// 事件回调：先获取事件类型，再分发给对应类型的事件处理函数决策
const OH_Input_Event* OnEvent(OH_Input_EventHandler* handler, const OH_Input_Event* event)
{
    OH_Input_EventType type = OH_INPUT_EVENT_KEY;
    if (OH_Input_Event_GetType(event, &type) != INPUT_SUCCESS) {
        return event; // 获取事件类型失败时默认再分发，避免影响正常输入
    }
    bool intercepted = false; // 是否拦截当前事件
    switch (type) {
        case OH_INPUT_EVENT_KEY: // 按键事件
            intercepted = HandleKeyEvent(event);
            break;
        case OH_INPUT_EVENT_MOUSE: // 鼠标事件
            intercepted = HandleMouseEvent(event);
            break;
        case OH_INPUT_EVENT_TOUCH: // 触摸事件
            intercepted = HandleTouchEvent(event);
            break;
        case OH_INPUT_EVENT_AXIS: // 轴事件
            intercepted = HandleAxisEvent(event);
            break;
        default:
            break;
    }
    return intercepted ? nullptr : event; // 返回nullptr表示拦截，返回原事件表示再分发
}
```

### 禁用并销毁输入事件handler

不需要继续处理输入事件时，先禁用handler再销毁，释放资源。

<!-- @[event_handler_destroy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputKit/NDKInputEventHook/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value DisableAndDestroyHandler(napi_env env, napi_callback_info info)
{
    // g_handler为“创建并启用输入事件handler”中创建的handler对象
    Input_Result ret = OH_Input_EventHandler_Enable(g_handler, false); // 禁用handler，事件恢复默认分发
    // ...
    OH_Input_EventHandler_Destroy(g_handler); // 销毁handler并释放资源
    // ...
    // ...
}
```

