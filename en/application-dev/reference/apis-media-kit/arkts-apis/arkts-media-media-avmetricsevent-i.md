# AVMetricsEvent

```TypeScript
interface AVMetricsEvent
```

Describes the information of an Metrics Event.

**Since:** 23

<!--Device-media-interface AVMetricsEvent--><!--Device-media-interface AVMetricsEvent-End-->

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## details

```TypeScript
details: Record<string, Object>
```

The detailed information of the event.

**Type:** Record&lt;string, Object&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVMetricsEvent-details: Record<string, Object>--><!--Device-AVMetricsEvent-details: Record<string, Object>-End-->

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## event

```TypeScript
event: AVMetricsEventType
```

Type of the metrics event.

**Type:** [AVMetricsEventType](arkts-media-media-avmetricseventtype-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVMetricsEvent-event: AVMetricsEventType--><!--Device-AVMetricsEvent-event: AVMetricsEventType-End-->

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## playbackPosition

```TypeScript
playbackPosition: number
```

The playback progress position when the event occurs.

**Type:** number

**Since:** 23

<!--Device-AVMetricsEvent-playbackPosition: int--><!--Device-AVMetricsEvent-playbackPosition: int-End-->

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## timeStamp

```TypeScript
timeStamp: number
```

Absolute timestamp when the event occurred.

**Type:** number

**Since:** 23

<!--Device-AVMetricsEvent-timeStamp: long--><!--Device-AVMetricsEvent-timeStamp: long-End-->

**System capability:** SystemCapability.Multimedia.Media.AVPlayer
