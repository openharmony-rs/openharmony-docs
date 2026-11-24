# OH_NativeXComponent_TouchEvent

```c
typedef struct OH_NativeXComponent_TouchEvent {...} OH_NativeXComponent_TouchEvent
```

## 概述

触摸事件。 当用户在XComponent组件上进行触摸操作时，通过该结构体可获取触摸点的坐标、触摸类型、接触面积、压力、时间戳等信息，适用于需要在Native层处理XComponent触摸交互的场景。

<!--Device-typedef struct OH_NativeXComponent_TouchEvent {...} OH_NativeXComponent_TouchEvent--><!--Device-typedef struct OH_NativeXComponent_TouchEvent {...} OH_NativeXComponent_TouchEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 8

**相关模块：** [OH_NativeXComponent Native XComponent](capi-arkui-oh-nativexcomponent-native-xcomponent.md)

**所在头文件：** [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t id | 手指的唯一标识符。<br><!--Device-int32_t id--><!--Device-int32_t id-End--> |
| float screenX | 触摸点相对于XComponent所在应用窗口左上角的x坐标。<br><!--Device-float screenX--><!--Device-float screenX-End--> |
| float screenY | 触摸点相对于XComponent所在应用窗口左上角的y坐标。<br><!--Device-float screenY--><!--Device-float screenY-End--> |
| float x | 触摸点相对于XComponent组件左边缘的x坐标。<br><!--Device-float x--><!--Device-float x-End--> |
| float y | 触摸点相对于XComponent组件上边缘的y坐标。<br><!--Device-float y--><!--Device-float y-End--> |
| [OH_NativeXComponent_TouchEventType](capi-native-interface-xcomponent-h.md#oh_nativexcomponent_toucheventtype) type | 触摸事件的触摸类型。<br><!--Device-OH_NativeXComponent_TouchEventType type--><!--Device-OH_NativeXComponent_TouchEventType type-End--> |
| double size | 指垫和屏幕之间的接触面积。<br><!--Device-double size--><!--Device-double size-End--> |
| float force | 当前触摸事件的压力。<br><!--Device-float force--><!--Device-float force-End--> |
| int64_t deviceId | 产生当前触摸事件的设备的ID。<br><!--Device-int64_t deviceId--><!--Device-int64_t deviceId-End--> |
| int64_t timeStamp | 当前触摸事件的时间戳。触发事件时距离系统启动的时间间隔，单位纳秒。<br><!--Device-int64_t timeStamp--><!--Device-int64_t timeStamp-End--> |
| [OH_NativeXComponent_TouchPoint](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-touchpoint.md) touchPoints[OH_NATIVE_XCOMPONENT_MAX_TOUCH_POINTS_NUMBER] | 当前触摸点的数组。OH_NATIVE_XCOMPONENT_MAX_TOUCH_POINTS_NUMBER的介绍请参考[宏定义](capi-native-interface-xcomponent-h.md#宏定义)。<br><!--Device-OH_NativeXComponent_TouchPoint touchPoints[OH_NATIVE_XCOMPONENT_MAX_TOUCH_POINTS_NUMBER]--><!--Device-OH_NativeXComponent_TouchPoint touchPoints[OH_NATIVE_XCOMPONENT_MAX_TOUCH_POINTS_NUMBER]-End--> |
| uint32_t numPoints | 当前触摸点的数量，值为1时为单指触摸，大于1时为多指触摸。<br><!--Device-uint32_t numPoints--><!--Device-uint32_t numPoints-End--> |


