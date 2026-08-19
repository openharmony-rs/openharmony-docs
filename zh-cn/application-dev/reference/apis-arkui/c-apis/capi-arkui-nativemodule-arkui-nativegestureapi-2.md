# ArkUI_NativeGestureAPI_2

```c
typedef struct ArkUI_NativeGestureAPI_2 {...} ArkUI_NativeGestureAPI_2
```

## 概述

定义手势模块接口集合，在[ArkUI_NativeGestureAPI_1](capi-arkui-nativemodule-arkui-nativegestureapi-1.md)的基础上扩展提供设置手势打断事件回调函数的能力，用于在手势识别过程中根据回调结果继续或打断手势。开发者可以通过{@link gestureApi1}访问基础手势接口，配合[setGestureInterrupterToNode](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#setgestureinterruptertonode)处理手势打断。

**起始版本：** 18

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_gesture.h](capi-native-gesture-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [ArkUI_NativeGestureAPI_1*](capi-arkui-nativemodule-arkui-nativegestureapi-1.md) gestureApi1 | 指向ArkUI_NativeGestureAPI_1结构体的指针。 |


### 成员函数

| 名称 | 描述 |
| -- | -- |
| [int32_t (\*setGestureInterrupterToNode)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureInterruptResult (\*interrupter)(ArkUI_GestureInterruptInfo* info))](#setgestureinterruptertonode) | Sets the callback for gesture interruption events. |

## 成员函数说明

### setGestureInterrupterToNode()

```c
int32_t (*setGestureInterrupterToNode)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureInterruptResult (*interrupter)(ArkUI_GestureInterruptInfo* info))
```

**描述**

Sets the callback for gesture interruption events.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| node | Pointer to the ArkUI node for which you want to set a gesture interruption callback. |
| userData | Pointer to user-defined data. |
| interrupter | Gesture interruption callback to set. <b>info</b> indicates the gesture interruption data.If <b>interrupter</b> returns <b>GESTURE_INTERRUPT_RESULT_CONTINUE</b>, the gesture recognition processproceedsproperly. If it returns <b>GESTURE_INTERRUPT_RESULT_REJECT</b>, the gesture recognition process is paused. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.          <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |


