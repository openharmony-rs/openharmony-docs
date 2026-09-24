# ArkUI_ParallelGestureEvent

```c
typedef struct ArkUI_ParallelGestureEvent ArkUI_ParallelGestureEvent
```

## 概述

定义手势模块接口集合，包含{@link ArkUI_NativeGestureAPI_1}、{@link ArkUI_NativeGestureAPI_2}结构体中的手势接口及新增手势接口。<br><br>该接口集合支持为ArkUI节点设置并行手势事件回调。回调可从响应链中的冲突手势识别器中选择需要与当前手势并行识别的对象。相关事件数据请参见{@link ArkUI_ParallelGestureEvent}。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.0

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_gesture.h](capi-native-gesture-h.md)

