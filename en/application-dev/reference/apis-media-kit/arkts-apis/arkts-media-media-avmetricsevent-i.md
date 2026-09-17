# AVMetricsEvent

Describes the information of an Metrics Event.

**Since:** 23

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

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## event

```TypeScript
event: AVMetricsEventType
```

Type of the metrics event.

**Type:** [AVMetricsEventType](arkts-media-media-avmetricseventtype-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## playbackPosition

```TypeScript
playbackPosition: number
```

The playback progress position when the event occurs.

**Type:** number

**Since:** 23

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## timeStamp

```TypeScript
timeStamp: number
```

Absolute timestamp when the event occurred.

**Type:** number

**Since:** 23

**System capability:** SystemCapability.Multimedia.Media.AVPlayer
