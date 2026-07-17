# FrameMetrics

帧率指标。

**起始版本：** 22

<!--Device-window-interface FrameMetrics--><!--Device-window-interface FrameMetrics-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## firstDrawFrame

```TypeScript
firstDrawFrame: boolean
```

是否是首帧。true表示首帧，false表示非首帧。

**类型：** boolean

**起始版本：** 22

<!--Device-FrameMetrics-firstDrawFrame: boolean--><!--Device-FrameMetrics-firstDrawFrame: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

## inputHandlingDuration

```TypeScript
inputHandlingDuration: number
```

一帧中的手势处理耗时（单位：纳秒）。

**类型：** number

**起始版本：** 22

<!--Device-FrameMetrics-inputHandlingDuration: long--><!--Device-FrameMetrics-inputHandlingDuration: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

## layoutMeasureDuration

```TypeScript
layoutMeasureDuration: number
```

一帧中的布局测量耗时（单位：纳秒）。

**类型：** number

**起始版本：** 22

<!--Device-FrameMetrics-layoutMeasureDuration: long--><!--Device-FrameMetrics-layoutMeasureDuration: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

## vsyncTimestamp

```TypeScript
vsyncTimestamp: number
```

当前帧的开始时间戳（单位：纳秒）。

**类型：** number

**起始版本：** 22

<!--Device-FrameMetrics-vsyncTimestamp: long--><!--Device-FrameMetrics-vsyncTimestamp: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

