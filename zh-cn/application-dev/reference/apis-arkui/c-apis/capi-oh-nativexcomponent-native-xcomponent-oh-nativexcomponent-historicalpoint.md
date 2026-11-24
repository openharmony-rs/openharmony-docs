# OH_NativeXComponent_HistoricalPoint

```c
typedef struct OH_NativeXComponent_HistoricalPoint {...} OH_NativeXComponent_HistoricalPoint
```

## 概述

历史触摸点。 在触摸事件处理中，系统会记录触摸轨迹中的历史触摸点信息，用于还原高速滑动等场景下的完整触摸轨迹。每个历史触摸点包含该时刻触摸点的坐标、类型、压力、时间戳、倾斜角度等属性，适用于需要分析触摸轨迹、手势识别等场景。

<!--Device-typedef struct OH_NativeXComponent_HistoricalPoint {...} OH_NativeXComponent_HistoricalPoint--><!--Device-typedef struct OH_NativeXComponent_HistoricalPoint {...} OH_NativeXComponent_HistoricalPoint-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 10

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
| float titlX | 平面X-Y上的投影与当前触摸事件的Z轴之间的角度。<br><!--Device-float titlX--><!--Device-float titlX-End--> |
| float titlY | 当前触摸事件在平面Y-Z和轴Z上的投影之间的角度。<br><!--Device-float titlY--><!--Device-float titlY-End--> |
| [OH_NativeXComponent_TouchEvent_SourceTool](capi-native-interface-xcomponent-h.md#oh_nativexcomponent_touchevent_sourcetool) sourceTool | 当前触摸事件的源工具。<br><!--Device-OH_NativeXComponent_TouchEvent_SourceTool sourceTool--><!--Device-OH_NativeXComponent_TouchEvent_SourceTool sourceTool-End--> |


