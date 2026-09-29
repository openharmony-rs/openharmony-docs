# IntervalInfo

```TypeScript
interface IntervalInfo
```

You can obtain the timestamp information from the event callback, including the timestamp when the current frame arrives and the timestamp when the next frame is expected to arrive.

**Since:** 11

<!--Device-displaySync-interface IntervalInfo--><!--Device-displaySync-interface IntervalInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { displaySync } from '@kit.ArkGraphics2D';
```

## targetTimestamp

```TypeScript
targetTimestamp: number
```

Expected arrival time of the next frame, in nanoseconds.

**Type:** number

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.2.0.

<!--Device-IntervalInfo-targetTimestamp: long--><!--Device-IntervalInfo-targetTimestamp: long-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## timestamp

```TypeScript
timestamp: number
```

Time when the current frame arrives, in nanoseconds.

**Type:** number

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.2.0.

<!--Device-IntervalInfo-timestamp: long--><!--Device-IntervalInfo-timestamp: long-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
