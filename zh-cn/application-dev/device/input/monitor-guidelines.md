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

- **鼠标事件**

<!-- @[mouse_event_monitor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/input/NDKInputEventMonitor/entry/src/main/cpp/napi_init.cpp) -->

- **触摸事件**

<!-- @[touch_event_monitor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/input/NDKInputEventMonitor/entry/src/main/cpp/napi_init.cpp) -->

- **轴事件**

<!-- @[axis_event_monitor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/input/NDKInputEventMonitor/entry/src/main/cpp/napi_init.cpp) -->
