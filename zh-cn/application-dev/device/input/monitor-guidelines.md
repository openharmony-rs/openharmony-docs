# 事件监听开发指导（C/C++）

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

## 功能介绍

从API版本12开始，多模为应用提供了按键、输入事件（鼠标、触屏和轴事件）监听能力。使用场景例如：

- 录屏类应用：应用开启录屏期间，监听设备的按键、鼠标、触摸和轴事件。
- 输入录制、自动化测试类应用（从API版本26.1.0开始，仅PC/2in1形态支持）：用户完成授权后，应用可在任意时刻监听设备的按键、鼠标、触摸和轴事件，监听不随录屏状态变化而中断。

## 接口说明

创建和删除事件监听相关接口如下表所示，接口详细介绍请参考[oh_input_manager.h](../../reference/apis-input-kit/capi-oh-input-manager-h.md)。

| 接口名称 | 描述 |
| ------------------------------------------------------------ | -------------------------- |
| Input_Result OH_Input_AddKeyEventMonitor(Input_KeyEventCallback callback) | 创建按键事件监听。 |
| Input_Result OH_Input_AddMouseEventMonitor(Input_MouseEventCallback callback) | 创建鼠标事件监听。 |
| Input_Result OH_Input_AddTouchEventMonitor(Input_TouchEventCallback callback) | 创建触摸事件监听。 |
| Input_Result OH_Input_AddAxisEventMonitorForAll(Input_AxisEventCallback callback) | 创建所有类型轴事件监听。 |
| Input_Result OH_Input_AddAxisEventMonitor(InputEvent_AxisEventType axisEventType, Input_AxisEventCallback callback) | 创建指定类型轴事件监听。 |
| Input_Result OH_Input_RemoveKeyEventMonitor(Input_KeyEventCallback callback) | 删除按键事件监听。 |
| Input_Result OH_Input_RemoveMouseEventMonitor(Input_MouseEventCallback callback) | 删除鼠标事件监听。 |
| Input_Result OH_Input_RemoveTouchEventMonitor(Input_TouchEventCallback callback) | 删除触摸事件监听。 |
| Input_Result OH_Input_RemoveAxisEventMonitorForAll(Input_AxisEventCallback callback) | 删除所有类型轴事件监听。 |
| Input_Result OH_Input_RemoveAxisEventMonitor(InputEvent_AxisEventType axisEventType, Input_AxisEventCallback callback) | 删除指定类型轴事件监听。 |

## 开发步骤

### 链接动态库

调用创建和删除事件监听前，需链接相关动态库。链接动态库的方法是，在CMakeLists.txt文件中新增如下配置：

```txt
target_link_libraries(entry PUBLIC libohinput.so)
```

### 申请所需权限

应用需要在module.json5中声明所需权限，详细的配置方法参考[声明权限文档](../../security/AccessToken/declare-permissions.md)。两种权限的授权方式不同，申请说明如下。

- **ohos.permission.INPUT_MONITORING**（系统授权）：面向录屏类应用，应用开启录屏期间可监听设备的按键、鼠标、触摸和轴事件。该权限需要通过ACL方式申请，具体请参考[申请受限权限](../../security/AccessToken/declare-permissions-in-a-cl.md)。

    ```json
    "requestPermissions": [
        {
            "name": "ohos.permission.INPUT_MONITORING"
        }
    ]
    ```

- **ohos.permission.INPUT_RECORDING**（手动设置授权，从API版本26.1.0开始支持，仅支持PC/2in1）：面向输入录制、自动化测试类应用，用户完成授权后，应用可在任意时刻监听设备的按键、鼠标、触摸和轴事件，监听不随录屏状态变化而中断。该权限的授权说明请参考[手动设置授权](../../security/AccessToken/app-permission-mgmt-overview.md#manual_settings手动设置授权)。

    该权限的reason与usedScene字段必填；无法通过弹窗向用户申请授权，应用上架审核通过后，需引导用户在"设置 > 隐私 > 权限管理"中手动开启授权。

    ```json
    "requestPermissions": [
        {
            "name": "ohos.permission.INPUT_RECORDING",
            "reason": "$string:input_recording_permission_reason",
            "usedScene": {
                "abilities": [
                    "EntryAbility"
                ],
                "when": "inuse"
            }
        }
    ]
    ```

### 创建事件监听

- **按键事件**

<!-- @[key_event_monitor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputKit/NDKInputEventMonitor/entry/src/main/cpp/napi_init.cpp) -->

``` C++
struct KeyEvent {
    int32_t action;
    int32_t keyCode;
    int64_t actionTime { -1 };
};

// 定义按键事件回调函数
void OnKeyEventCallback(const Input_KeyEvent* keyEvent)
{
    KeyEvent event;
    // Input_KeyEvent的生命周期仅限于回调函数内，回调函数执行完毕后会被自动销毁
    event.action = OH_Input_GetKeyEventAction(keyEvent);
    event.keyCode = OH_Input_GetKeyEventKeyCode(keyEvent);
    event.actionTime = OH_Input_GetKeyEventActionTime(keyEvent);
    // ...
}

static napi_value AddKeyEventMonitor(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_AddKeyEventMonitor(OnKeyEventCallback);
    // ...
}

static napi_value RemoveKeyEventMonitor(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_RemoveKeyEventMonitor(OnKeyEventCallback);
    // ...
}
```


- **鼠标事件**

<!-- @[mouse_event_monitor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputKit/NDKInputEventMonitor/entry/src/main/cpp/napi_init.cpp) -->

``` C++
struct MouseEvent {
    int32_t action;
    int32_t displayX;
    int32_t displayY;
    int32_t button { -1 };
    int32_t axisType { -1 };
    float axisValue { 0.0f };
    int64_t actionTime { -1 };
};

// 定义鼠标事件回调函数
void OnMouseEventCallback(const Input_MouseEvent* mouseEvent)
{
    MouseEvent event;
    // Input_MouseEvent的生命周期仅限于回调函数内，回调函数执行完毕后会被自动销毁
    event.action = OH_Input_GetMouseEventAction(mouseEvent);
    event.displayX = OH_Input_GetMouseEventDisplayX(mouseEvent);
    event.displayY = OH_Input_GetMouseEventDisplayY(mouseEvent);
    event.button = OH_Input_GetMouseEventButton(mouseEvent);
    event.axisType = OH_Input_GetMouseEventAxisType(mouseEvent);
    event.axisValue = OH_Input_GetMouseEventAxisValue(mouseEvent);
    event.actionTime = OH_Input_GetMouseEventActionTime(mouseEvent);
    // ...
}

static napi_value AddMouseEventMonitor(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_AddMouseEventMonitor(OnMouseEventCallback);
    // ...
}

static napi_value RemoveMouseEventMonitor(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_RemoveMouseEventMonitor(OnMouseEventCallback);
    // ...
}
```


- **触摸事件**

<!-- @[touch_event_monitor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputKit/NDKInputEventMonitor/entry/src/main/cpp/napi_init.cpp) -->

``` C++
struct TouchEvent {
    int32_t action;
    int32_t id;
    int32_t displayX;
    int32_t displayY;
    int64_t actionTime { -1 };
};

void OnTouchEventCallback(const Input_TouchEvent* touchEvent)
{
    TouchEvent event;
    // Input_TouchEvent的生命周期仅限于回调函数内，回调函数执行完毕后会被自动销毁
    event.action = OH_Input_GetTouchEventAction(touchEvent);
    event.id = OH_Input_GetTouchEventFingerId(touchEvent);
    event.displayX = OH_Input_GetTouchEventDisplayX(touchEvent);
    event.displayY = OH_Input_GetTouchEventDisplayY(touchEvent);
    event.actionTime = OH_Input_GetTouchEventActionTime(touchEvent);
    // ...
}

static napi_value AddTouchEventMonitor(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_AddTouchEventMonitor(OnTouchEventCallback);
    // ...
}

static napi_value RemoveTouchEventMonitor(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_RemoveTouchEventMonitor(OnTouchEventCallback);
    // ...
}
```


- **轴事件**

<!-- @[axis_event_monitor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputKit/NDKInputEventMonitor/entry/src/main/cpp/napi_init.cpp) --> 

``` C++
struct AxisEvent {
    int32_t axisAction;
    float displayX;
    float displayY;
    std::map<int32_t, double> axisValues;
    int64_t actionTime { -1 };
    int32_t sourceType;
    int32_t axisEventType { -1 };
};

void OnAllAxisEventCallback(const Input_AxisEvent* axisEvent)
{
    AxisEvent event;
    // Input_AxisEvent的生命周期仅限于回调函数内，回调函数执行完毕后会被自动销毁
    InputEvent_AxisAction action = static_cast<InputEvent_AxisAction>(0);
    Input_Result ret = OH_Input_GetAxisEventAction(axisEvent, &action);
    event.axisAction = action;
    ret = OH_Input_GetAxisEventDisplayX(axisEvent, &event.displayX);
    ret = OH_Input_GetAxisEventDisplayY(axisEvent, &event.displayY);
    ret = OH_Input_GetAxisEventActionTime(axisEvent, &event.actionTime);
    InputEvent_SourceType sourceType = static_cast<InputEvent_SourceType>(0);
    ret = OH_Input_GetAxisEventSourceType(axisEvent, &sourceType);
    event.sourceType = sourceType;
    InputEvent_AxisEventType axisEventType = static_cast<InputEvent_AxisEventType>(-1);
    ret = OH_Input_GetAxisEventType(axisEvent, &axisEventType);
    event.axisEventType = axisEventType;
    if (event.axisEventType == AXIS_EVENT_TYPE_PINCH) {
        double value = 0;
        ret = OH_Input_GetAxisEventAxisValue(axisEvent, AXIS_TYPE_PINCH, &value);
        event.axisValues.insert(std::make_pair(AXIS_TYPE_PINCH, value));
        ret = OH_Input_GetAxisEventAxisValue(axisEvent, AXIS_TYPE_ROTATE, &value);
        event.axisValues.insert(std::make_pair(AXIS_TYPE_ROTATE, value));
    } else if (event.axisEventType == AXIS_EVENT_TYPE_SCROLL) {
        double value = 0;
        ret = OH_Input_GetAxisEventAxisValue(axisEvent, AXIS_TYPE_SCROLL_VERTICAL, &value);
        event.axisValues.insert(std::make_pair(AXIS_TYPE_SCROLL_VERTICAL, value));
        ret = OH_Input_GetAxisEventAxisValue(axisEvent, AXIS_TYPE_SCROLL_HORIZONTAL, &value);
        event.axisValues.insert(std::make_pair(AXIS_TYPE_SCROLL_HORIZONTAL, value));
    }
    // ...
}

// 定义捏合类型轴事件回调函数
void OnPinchAxisEventCallback(const Input_AxisEvent* axisEvent)
{
    AxisEvent event;
    // Input_AxisEvent的生命周期仅限于回调函数内，回调函数执行完毕后会被自动销毁
    InputEvent_AxisAction action = static_cast<InputEvent_AxisAction>(0);
    Input_Result ret = OH_Input_GetAxisEventAction(axisEvent, &action);
    event.axisAction = action;
    ret = OH_Input_GetAxisEventDisplayX(axisEvent, &event.displayX);
    ret = OH_Input_GetAxisEventDisplayY(axisEvent, &event.displayY);
    ret = OH_Input_GetAxisEventActionTime(axisEvent, &event.actionTime);
    InputEvent_SourceType sourceType = static_cast<InputEvent_SourceType>(0);
    ret = OH_Input_GetAxisEventSourceType(axisEvent, &sourceType);
    event.sourceType = sourceType;
    InputEvent_AxisEventType axisEventType = static_cast<InputEvent_AxisEventType>(-1);
    ret = OH_Input_GetAxisEventType(axisEvent, &axisEventType);
    event.axisEventType = axisEventType;
    double value = 0;
    ret = OH_Input_GetAxisEventAxisValue(axisEvent, AXIS_TYPE_PINCH, &value);
    event.axisValues.insert(std::make_pair(AXIS_TYPE_PINCH, value));
    ret = OH_Input_GetAxisEventAxisValue(axisEvent, AXIS_TYPE_ROTATE, &value);
    event.axisValues.insert(std::make_pair(AXIS_TYPE_ROTATE, value));
    // ...
}

void OnScrollAxisEventCallback(const Input_AxisEvent* axisEvent)
{
    AxisEvent event;
    // Input_AxisEvent的生命周期仅限于回调函数内，回调函数执行完毕后会被自动销毁
    InputEvent_AxisAction action = static_cast<InputEvent_AxisAction>(0);
    Input_Result ret = OH_Input_GetAxisEventAction(axisEvent, &action);
    event.axisAction = action;
    ret = OH_Input_GetAxisEventDisplayX(axisEvent, &event.displayX);
    ret = OH_Input_GetAxisEventDisplayY(axisEvent, &event.displayY);
    ret = OH_Input_GetAxisEventActionTime(axisEvent, &event.actionTime);
    InputEvent_SourceType sourceType = static_cast<InputEvent_SourceType>(0);
    ret = OH_Input_GetAxisEventSourceType(axisEvent, &sourceType);
    event.sourceType = sourceType;
    InputEvent_AxisEventType axisEventType = static_cast<InputEvent_AxisEventType>(-1);
    ret = OH_Input_GetAxisEventType(axisEvent, &axisEventType);
    event.axisEventType = axisEventType;
    double value = 0;
    ret = OH_Input_GetAxisEventAxisValue(axisEvent, AXIS_TYPE_SCROLL_VERTICAL, &value);
    event.axisValues.insert(std::make_pair(AXIS_TYPE_SCROLL_VERTICAL, value));
    ret = OH_Input_GetAxisEventAxisValue(axisEvent, AXIS_TYPE_SCROLL_HORIZONTAL, &value);
    event.axisValues.insert(std::make_pair(AXIS_TYPE_SCROLL_HORIZONTAL, value));
    // ...
}

static napi_value AddAxisEventMonitorForAll(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_AddAxisEventMonitorForAll(OnAllAxisEventCallback);
    // ...
}

static napi_value RemoveAxisEventMonitorForAll(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_RemoveAxisEventMonitorForAll(OnAllAxisEventCallback);
    // ...
}

static napi_value AddPinchAxisEventMonitor(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_AddAxisEventMonitor(AXIS_EVENT_TYPE_PINCH, OnPinchAxisEventCallback);
    // ...
}

static napi_value RemovePinchAxisEventMonitor(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_RemoveAxisEventMonitor(AXIS_EVENT_TYPE_PINCH, OnPinchAxisEventCallback);
    // ...
}

static napi_value AddScrollAxisEventMonitor(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_AddAxisEventMonitor(AXIS_EVENT_TYPE_SCROLL, OnScrollAxisEventCallback);
    // ...
}

static napi_value RemoveScrollAxisEventMonitor(napi_env env, napi_callback_info info)
{
    Input_Result ret =  OH_Input_RemoveAxisEventMonitor(AXIS_EVENT_TYPE_SCROLL, OnScrollAxisEventCallback);
    // ...
}
```

