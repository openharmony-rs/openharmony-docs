# FrameMetrics

```TypeScript
interface FrameMetrics
```

Enumerates the metrics for frame performance.

**Since:** 22

<!--Device-window-interface FrameMetrics--><!--Device-window-interface FrameMetrics-End-->

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## animationDuration

```TypeScript
animationDuration?: number
```

The total duration spent executing all animation callbacks in a frame. Unit: nanosecond.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FrameMetrics-animationDuration?: long--><!--Device-FrameMetrics-animationDuration?: long-End-->

**System capability:** SystemCapability.Window.SessionManager

## firstDrawFrame

```TypeScript
firstDrawFrame: boolean
```

Whether the frame is the first frame. **true** for first frame, **false** otherwise.

**Type:** boolean

**Since:** 22

<!--Device-FrameMetrics-firstDrawFrame: boolean--><!--Device-FrameMetrics-firstDrawFrame: boolean-End-->

**System capability:** SystemCapability.Window.SessionManager

## inputHandlingDuration

```TypeScript
inputHandlingDuration: number
```

Duration of gesture handling in a frame, in nanoseconds.

**Type:** number

**Since:** 22

<!--Device-FrameMetrics-inputHandlingDuration: long--><!--Device-FrameMetrics-inputHandlingDuration: long-End-->

**System capability:** SystemCapability.Window.SessionManager

## intendedVsyncTimestamp

```TypeScript
intendedVsyncTimestamp?: number
```

The expected start timestamp of the current frame. Unit: nanosecond.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FrameMetrics-intendedVsyncTimestamp?: long--><!--Device-FrameMetrics-intendedVsyncTimestamp?: long-End-->

**System capability:** SystemCapability.Window.SessionManager

## layoutMeasureDuration

```TypeScript
layoutMeasureDuration: number
```

Duration of layout measurement in a frame, in nanoseconds.

**Type:** number

**Since:** 22

<!--Device-FrameMetrics-layoutMeasureDuration: long--><!--Device-FrameMetrics-layoutMeasureDuration: long-End-->

**System capability:** SystemCapability.Window.SessionManager

## totalDuration

```TypeScript
totalDuration?: number
```

Total duration required to render this frame and send it to the display subsystem. Unit: nanosecond.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FrameMetrics-totalDuration?: long--><!--Device-FrameMetrics-totalDuration?: long-End-->

**System capability:** SystemCapability.Window.SessionManager

## vsyncTimestamp

```TypeScript
vsyncTimestamp: number
```

Timestamp marking the start of the current frame, in nanoseconds.

**Type:** number

**Since:** 22

<!--Device-FrameMetrics-vsyncTimestamp: long--><!--Device-FrameMetrics-vsyncTimestamp: long-End-->

**System capability:** SystemCapability.Window.SessionManager
