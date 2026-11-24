# OH_NativeXComponent_TouchPoint

```c
typedef struct OH_NativeXComponent_TouchPoint {...} OH_NativeXComponent_TouchPoint
```

## 概述

触摸事件中触摸点的信息。 该结构体由系统在触摸事件回调中填充，开发者可通过回调获取各触摸点的状态数据（包括相对于应用窗口和组件的坐标、触摸类型、接触面积、压力大小、时间戳以及按下状态等信息）。适用于需要精确获取和处理多点触控信息的场景。

<!--Device-typedef struct OH_NativeXComponent_TouchPoint {...} OH_NativeXComponent_TouchPoint--><!--Device-typedef struct OH_NativeXComponent_TouchPoint {...} OH_NativeXComponent_TouchPoint-End-->

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
| int64_t timeStamp | 当前触摸事件的时间戳。触发事件时距离系统启动的时间间隔，单位纳秒。<br><!--Device-int64_t timeStamp--><!--Device-int64_t timeStamp-End--> |
| bool isPressed | 当前点是否被按下，按下时为true，离开时为false。<br><!--Device-bool isPressed--><!--Device-bool isPressed-End--> |


