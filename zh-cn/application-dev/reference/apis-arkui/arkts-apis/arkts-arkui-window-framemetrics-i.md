# FrameMetrics

帧率指标。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-window-interface FrameMetrics--><!--Device-window-interface FrameMetrics-End-->

**系统能力：** SystemCapability.Window.SessionManager

## firstDrawFrame

```TypeScript
firstDrawFrame: boolean
```

是否是首帧。true表示首帧，false表示非首帧。

**类型：** boolean

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-FrameMetrics-firstDrawFrame: boolean--><!--Device-FrameMetrics-firstDrawFrame: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

## inputHandlingDuration

```TypeScript
inputHandlingDuration: long
```

一帧中的手势处理耗时（单位：纳秒）。

**类型：** long

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-FrameMetrics-inputHandlingDuration: long--><!--Device-FrameMetrics-inputHandlingDuration: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

## layoutMeasureDuration

```TypeScript
layoutMeasureDuration: long
```

一帧中的布局测量耗时（单位：纳秒）。

**类型：** long

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-FrameMetrics-layoutMeasureDuration: long--><!--Device-FrameMetrics-layoutMeasureDuration: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

## vsyncTimestamp

```TypeScript
vsyncTimestamp: long
```

当前帧的开始时间戳（单位：纳秒）。

**类型：** long

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-FrameMetrics-vsyncTimestamp: long--><!--Device-FrameMetrics-vsyncTimestamp: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

