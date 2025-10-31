# 事件监听开发指导（C/C++）

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

## 功能介绍

从API version 12开始，多模为应用提供了按键、输入事件（鼠标、触屏和轴事件）监听能力，当前仅支持录屏类应用。使用场景例如：用户在录屏应用开启录屏时，监听设备的按键、鼠标、触摸和轴事件。

## 接口说明

创建和删除事件监听相关接口如下表所示，接口详细介绍请参考[Input文档](../../reference/apis-input-kit/capi-input.md)。

| 接口名称  | 描述 |
| ------------------------------------------------------------ | -------------------------- |
| Input_Result OH_Input_AddKeyEventMonitor(Input_KeyEventCallback callback) |创建按键事件监听。  |
| Input_Result OH_Input_AddMouseEventMonitor(Input_MouseEventCallback callback) |创建鼠标事件监听。  |
| Input_Result OH_Input_AddTouchEventMonitor(Input_TouchEventCallback callback) |创建触摸事件监听。  |
| Input_Result OH_Input_AddAxisEventMonitorForAll(Input_AxisEventCallback callback) |创建所有类型轴事件监听。  |
| Input_Result OH_Input_AddAxisEventMonitor(InputEvent_AxisEventType axisEventType, Input_AxisEventCallback callback) |创建指定类型轴事件监听。  |
| Input_Result OH_Input_RemoveKeyEventMonitor(Input_KeyEventCallback callback) |删除按键事件监听。  |
| Input_Result OH_Input_RemoveMouseEventMonitor(Input_MouseEventCallback callback) |删除鼠标事件监听。  |
| Input_Result OH_Input_RemoveTouchEventMonitor(Input_TouchEventCallback callback) |删除触摸事件监听。  |
| Input_Result OH_Input_RemoveAxisEventMonitorForAll(Input_AxisEventCallback callback) |删除所有类型轴事件监听。  |
| Input_Result OH_Input_RemoveAxisEventMonitor(InputEvent_AxisEventType axisEventType, Input_AxisEventCallback callback) |删除指定类型轴事件监听。  |

## 开发步骤

### 链接动态库

调用创建和删除事件拦截前，需链接相关动态库。链接动态库的方法是，在CMakeList.txt文件中新增如下配置：

```txt
target_link_libraries(entry PUBLIC libohinput.so)
```

### 申请所需权限

应用需要在module.json5中添加下面权限的配置，详细的配置方法参考声明[声明权限文档](../../security/AccessToken/declare-permissions.md)。

```json
"requestPermissions": [
    {
        "name": "ohos.permission.INPUT_MONITORING"
    }
]
```

### 创建事件监听

- **按键事件**

<!-- @[key_event_monitor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/input/NDKInputEventMonitor/entry/src/main/cpp/napi_init.cpp) -->

``` C++
// [Start key_event_monitor]
struct KeyEvent {
    int32_t action;
    int32_t keyCode;
    int64_t actionTime { -1 };
};

//定义按键事件回调函数
void OnKeyEventCallback(const Input_KeyEvent* keyEvent)
{
    KeyEvent event;
    //Input_KeyEvent的生命周期仅限于回调函数内，回调函数执行完毕后会被自动销毁
    event.action = OH_Input_GetKeyEventAction(keyEvent);
    event.keyCode = OH_Input_GetKeyEventKeyCode(keyEvent);
    event.actionTime = OH_Input_GetKeyEventActionTime(keyEvent);
    // [StartExclude key_event_monitor]
    std::ostringstream oss;
    oss << "监听到按键事件 action:"  << event.action
    << " keyCode: " << event.keyCode
    << " actionTime:" << event.actionTime;
    g_value = oss.str();
    NotifyValueChange();
    // [EndExclude  key_event_monitor]
}

static napi_value AddKeyEventMonitor(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_AddKeyEventMonitor(OnKeyEventCallback);
    // [StartExclude key_event_monitor]
    std::string message = "";
    if (ret == INPUT_SUCCESS) {
        message = "Add key event monitor successfully, return " + std::to_string(ret);
    } else {
        message = "Add key event monitor failed, return " + std::to_string(ret);
    }
    napi_value result;
    napi_create_string_utf8(env, message.c_str(), message.size(), &result);
    return result;
    // [EndExclude  key_event_monitor]
}

static napi_value RemoveKeyEventMonitor(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_RemoveKeyEventMonitor(OnKeyEventCallback);
    // [StartExclude key_event_monitor]
    std::string message = "";
    if (ret == INPUT_SUCCESS) {
        message = "Remove key event monitor successfully, return " + std::to_string(ret);
    } else {
        message = "Remove key event monitor failed, return " + std::to_string(ret);
    }
    napi_value result;
    napi_create_string_utf8(env, message.c_str(), message.size(), &result);
    return result;
    // [EndExclude  key_event_monitor]
}
// [End key_event_monitor]

// [Start mouse_event_monitor]
struct MouseEvent {
    int32_t action;
    int32_t displayX;
    int32_t displayY;
    int32_t button { -1 };
    int32_t axisType { -1 };
    float axisValue { 0.0f };
    int64_t actionTime { -1 };
};

//定义鼠标事件回调函数
void OnMouseEventCallback(const Input_MouseEvent* mouseEvent)
{
    MouseEvent event;
    //Input_MouseEvent的生命周期仅限于回调函数内，回调函数执行完毕后会被自动销毁
    event.action = OH_Input_GetMouseEventAction(mouseEvent);
    event.displayX = OH_Input_GetMouseEventDisplayX(mouseEvent);
    event.displayY = OH_Input_GetMouseEventDisplayY(mouseEvent);
    event.button = OH_Input_GetMouseEventButton(mouseEvent);
    event.axisType = OH_Input_GetMouseEventAxisType(mouseEvent);
    event.axisValue = OH_Input_GetMouseEventAxisValue(mouseEvent);
    event.actionTime = OH_Input_GetMouseEventActionTime(mouseEvent);
    // [StartExclude mouse_event_monitor]
    std::ostringstream oss;
    oss << "监听到鼠标事件 action:"  << event.action
    << " displayX: " << event.displayX
    << " displayY:" << event.displayY
    << " button:" << event.button
    << " axisType:" << event.axisType
    << " axisValue:" << event.axisValue
    << " actionTime:" << event.actionTime;
    g_value = oss.str();
    NotifyValueChange();
    // [EndExclude  mouse_event_monitor]
}

static napi_value AddMouseEventMonitor(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_AddMouseEventMonitor(OnMouseEventCallback);
    // [StartExclude mouse_event_monitor]
    std::string message = "";
    if (ret == INPUT_SUCCESS) {
        message = "填加鼠标事件监听成功，返回码为" + std::to_string(ret);
    } else {
        message = "填加鼠标事件监听失败，返回码为" + std::to_string(ret);
    }
    napi_value result;
    napi_create_string_utf8(env, message.c_str(), message.size(), &result);
    return result;
    // [EndExclude  mouse_event_monitor]
}

static napi_value RemoveMouseEventMonitor(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_RemoveMouseEventMonitor(OnMouseEventCallback);
    // [StartExclude mouse_event_monitor]
    std::string message = "";
    if (ret == INPUT_SUCCESS) {
        message = "Remove mouse event monitor successfully, return " + std::to_string(ret);
    } else {
        message = "Remove mouse event monitor failed, return " + std::to_string(ret);
    }
    napi_value result;
    napi_create_string_utf8(env, message.c_str(), message.size(), &result);
    return result;
    // [EndExclude  mouse_event_monitor]
}
// [End mouse_event_monitor]

// [Start touch_event_monitor]
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
    //Input_TouchEvent的生命周期仅限于回调函数内，回调函数执行完毕后会被自动销毁
    event.action = OH_Input_GetTouchEventAction(touchEvent);
    event.id = OH_Input_GetTouchEventFingerId(touchEvent);
    event.displayX = OH_Input_GetTouchEventDisplayX(touchEvent);
    event.displayY = OH_Input_GetTouchEventDisplayY(touchEvent);
    event.actionTime = OH_Input_GetTouchEventActionTime(touchEvent);
    // [StartExclude touch_event_monitor]
    std::ostringstream oss;
    oss << "监听到触摸事件 action:"  << event.action
    << " displayX: " << event.displayX
    << " displayY:" << event.displayY
    << " id:" << event.id
    << " actionTime:" << event.actionTime;
    g_value = oss.str();
    NotifyValueChange();
    // [EndExclude  touch_event_monitor]
}

static napi_value AddTouchEventMonitor(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_AddTouchEventMonitor(OnTouchEventCallback);
    // [StartExclude touch_event_monitor]
    std::string message = "";
    if (ret == INPUT_SUCCESS) {
        message = "填加触摸事件监听成功，返回码为" + std::to_string(ret);
    } else {
        message = "填加触摸事件监听失败，返回码为" + std::to_string(ret);
    }
    napi_value result;
    napi_create_string_utf8(env, message.c_str(), message.size(), &result);
    return result;
    // [EndExclude  touch_event_monitor]
}

static napi_value RemoveTouchEventMonitor(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_RemoveTouchEventMonitor(OnTouchEventCallback);
    // [StartExclude touch_event_monitor]
    std::string message = "";
    if (ret == INPUT_SUCCESS) {
        message = "Remove touch event monitor successfully, return " + std::to_string(ret);
    } else {
        message = "Remove touch event monitor failed, return " + std::to_string(ret);
    }
    napi_value result;
    napi_create_string_utf8(env, message.c_str(), message.size(), &result);
    return result;
    // [EndExclude  touch_event_monitor]
}
// [End touch_event_monitor]

// [Start axis_event_monitor]
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
    //Input_AxisEvent的生命周期仅限于回调函数内，回调函数执行完毕后会被自动销毁
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
    // [StartExclude axis_event_monitor]
    std::ostringstream oss;
    oss << "监听到轴事件 axisAction:"  << event.axisAction
    << " displayX:" << event.displayX
    << " displayY:" << event.displayY
    << " sourceType:" << event.sourceType
    << " actionTime:" << event.actionTime
    << " axisEventType:" << event.axisEventType
    << "\n axisValues:";
    for (const auto& pair : event.axisValues) {
        oss << " axis" << pair.first << "=" << pair.second;
    }
    g_value = oss.str();
    NotifyValueChange();
    // [EndExclude  axis_event_monitor]
}

//定义捏合类型轴事件回调函数
void OnPinchAxisEventCallback(const Input_AxisEvent* axisEvent)
{
    AxisEvent event;
    //Input_AxisEvent的生命周期仅限于回调函数内，回调函数执行完毕后会被自动销毁
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
    // [StartExclude axis_event_monitor]
    std::ostringstream oss;
    oss << "监听到捏合类型轴事件 axisAction:"  << event.axisAction
    << " displayX: " << event.displayX
    << " displayY:" << event.displayY
    << " sourceType:" << event.sourceType
    << " actionTime:" << event.actionTime
    << " axisEventType:" << event.axisEventType
    << "\n axisValues:";
    for (const auto& pair : event.axisValues) {
        oss << " axis" << pair.first << "=" << pair.second;
    }
    g_value = oss.str();
    NotifyValueChange();
    // [EndExclude  axis_event_monitor]
}

void OnScrollAxisEventCallback(const Input_AxisEvent* axisEvent)
{
    AxisEvent event;
    //Input_AxisEvent的生命周期仅限于回调函数内，回调函数执行完毕后会被自动销毁
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
    // [StartExclude axis_event_monitor]
    std::ostringstream oss;
    oss << "监听到滚轮类型轴事件 axisAction:"  << event.axisAction
    << " displayX: " << event.displayX
    << " displayY:" << event.displayY
    << " sourceType:" << event.sourceType
    << " actionTime:" << event.actionTime
    << " axisEventType:" << event.axisEventType
    << "\n axisValues:";
    for (const auto& pair : event.axisValues) {
        oss << " axis" << pair.first << "=" << pair.second;
    }
    g_value = oss.str();
    NotifyValueChange();
    // [EndExclude  axis_event_monitor]
}

static napi_value AddAxisEventMonitorForAll(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_AddAxisEventMonitorForAll(OnAllAxisEventCallback);
    // [StartExclude axis_event_monitor]
    std::string message = "";
    if (ret == INPUT_SUCCESS) {
        message = "Add axis event monitor successfully, return " + std::to_string(ret);
    } else {
        message = "Add axis event monitor failed, return " + std::to_string(ret);
    }
    napi_value result;
    napi_create_string_utf8(env, message.c_str(), message.size(), &result);
    return result;
    // [EndExclude  axis_event_monitor]
}

static napi_value RemoveAxisEventMonitorForAll(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_RemoveAxisEventMonitorForAll(OnAllAxisEventCallback);
    // [StartExclude axis_event_monitor]
    std::string message = "";
    if (ret == INPUT_SUCCESS) {
        message = "Remove axis event monitor successfully, return " + std::to_string(ret);
    } else {
        message = "Remove axis event monitor failed, return " + std::to_string(ret);
    }
    napi_value result;
    napi_create_string_utf8(env, message.c_str(), message.size(), &result);
    return result;
    // [EndExclude  axis_event_monitor]
}

static napi_value AddPinchAxisEventMonitor(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_AddAxisEventMonitor(AXIS_EVENT_TYPE_PINCH, OnPinchAxisEventCallback);
    // [StartExclude axis_event_monitor]
    std::string message = "";
    if (ret == INPUT_SUCCESS) {
        message = "Add pinch axis event monitor successfully, return " + std::to_string(ret);
    } else {
        message = "Add pinch axis event monitor failed, return " + std::to_string(ret);
    }
    napi_value result;
    napi_create_string_utf8(env, message.c_str(), message.size(), &result);
    return result;
    // [EndExclude  axis_event_monitor]
}

static napi_value RemovePinchAxisEventMonitor(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_RemoveAxisEventMonitor(AXIS_EVENT_TYPE_PINCH, OnPinchAxisEventCallback);
    // [StartExclude axis_event_monitor]
    std::string message = "";
    if (ret == INPUT_SUCCESS) {
        message = "Remove pinch axis event monitor successfully, return " + std::to_string(ret);
    } else {
        message = "Remove pinch axis event monitor failed, return " + std::to_string(ret);
    }
    napi_value result;
    napi_create_string_utf8(env, message.c_str(), message.size(), &result);
    return result;
    // [EndExclude  axis_event_monitor]
}

static napi_value AddScrollAxisEventMonitor(napi_env env, napi_callback_info info)
{
    Input_Result ret = OH_Input_AddAxisEventMonitor(AXIS_EVENT_TYPE_SCROLL, OnScrollAxisEventCallback);
    // [StartExclude axis_event_monitor]
    std::string message = "";
    if (ret == INPUT_SUCCESS) {
        message = "Add scroll axis event monitor successfully, return " + std::to_string(ret);
    } else {
        message = "Add scroll axis event monitor failed, return " + std::to_string(ret);
    }
    napi_value result;
    napi_create_string_utf8(env, message.c_str(), message.size(), &result);
    return result;
    // [EndExclude  axis_event_monitor]
}

static napi_value RemoveScrollAxisEventMonitor(napi_env env, napi_callback_info info)
{
    Input_Result ret =  OH_Input_RemoveAxisEventMonitor(AXIS_EVENT_TYPE_SCROLL, OnScrollAxisEventCallback);
    // [StartExclude axis_event_monitor]
    std::string message = "";
    if (ret == INPUT_SUCCESS) {
        message = "移除滚轮事件监听成功，返回码为" + std::to_string(ret);
    } else {
        message = "移除滚轮事件监听失败，返回码为" + std::to_string(ret);
    }
    napi_value result;
    napi_create_string_utf8(env, message.c_str(), message.size(), &result);
    return result;
    // [EndExclude  axis_event_monitor]
}
// [End axis_event_monitor]

EXTERN_C_START
static napi_value Init(napi_env env, napi_value exports)
{
    napi_property_descriptor desc[] = {
        { "onChange", nullptr, OnChange, nullptr, nullptr, nullptr, napi_default, nullptr },
        { "addKeyEventMonitor", nullptr, AddKeyEventMonitor, nullptr, nullptr, nullptr, napi_default, nullptr },
        { "removeKeyEventMonitor", nullptr, RemoveKeyEventMonitor, nullptr, nullptr, nullptr, napi_default, nullptr },
        { "addMouseEventMonitor", nullptr, AddMouseEventMonitor, nullptr, nullptr, nullptr, napi_default, nullptr },
        { "removeMouseEventMonitor", nullptr, RemoveMouseEventMonitor, nullptr, nullptr, nullptr,
            napi_default, nullptr },
        { "addTouchEventMonitor", nullptr, AddTouchEventMonitor, nullptr, nullptr, nullptr, napi_default, nullptr },
        { "removeTouchEventMonitor", nullptr, RemoveTouchEventMonitor, nullptr, nullptr, nullptr,
            napi_default, nullptr },
        { "addAxisEventMonitorForAll", nullptr, AddAxisEventMonitorForAll, nullptr, nullptr, nullptr,
            napi_default, nullptr },
        { "removeAxisEventMonitorForAll", nullptr, RemoveAxisEventMonitorForAll, nullptr, nullptr, nullptr,
            napi_default, nullptr },
        { "addPinchAxisEventMonitor", nullptr, AddPinchAxisEventMonitor, nullptr, nullptr, nullptr,
            napi_default, nullptr },
        { "removePinchAxisEventMonitor", nullptr, RemovePinchAxisEventMonitor, nullptr, nullptr, nullptr,
            napi_default, nullptr },
        { "addScrollAxisEventMonitor", nullptr, AddScrollAxisEventMonitor, nullptr, nullptr, nullptr,
            napi_default, nullptr },
        { "removeScrollAxisEventMonitor", nullptr, RemoveScrollAxisEventMonitor, nullptr, nullptr, nullptr,
            napi_default, nullptr },
    };
    napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
    return exports;
}
EXTERN_C_END

static napi_module demoModule = {
    .nm_version = 1,
    .nm_flags = 0,
    .nm_filename = nullptr,
    .nm_register_func = Init,
    .nm_modname = "entry",
    .nm_priv = ((void*)0),
    .reserved = { 0 },
};

extern "C" __attribute__((constructor)) void RegisterEntryModule(void)
{
    napi_module_register(&demoModule);
}
```

