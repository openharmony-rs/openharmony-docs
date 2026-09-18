# AVMetricsEventType

Enumerates the metric events supported by the media service.

**Since:** 23

**System capability:** SystemCapability.Multimedia.Media.Core

## AV_METRICS_EVENT_STALLING

```TypeScript
AV_METRICS_EVENT_STALLING = 1
```

Metric event indicating playback stalling.

**Since:** 23

**System capability:** SystemCapability.Multimedia.Media.Core

## AV_METRICS_EVENT_LIP_ASYNC

```TypeScript
AV_METRICS_EVENT_LIP_ASYNC  = 2
```

It is reported when the video sending and rendering time deviation is greater than expected, for example, video frame alignment or display in advance.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

## AV_METRICS_EVENT_LOADINGRATE_CHANGE

```TypeScript
AV_METRICS_EVENT_LOADINGRATE_CHANGE = 3
```

Load rate change event. This event is triggered when the difference between the data loading rate and the previous data loading rate is greater than 10%.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

## AV_METRICS_EVENT_LOADING_ERROR

```TypeScript
AV_METRICS_EVENT_LOADING_ERROR = 4
```

Data loading failure event, which carries the error information returned during data loading, such as connection timeout, access error, and server rejection.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

## AV_METRICS_EVENT_CONTENT_CHANGED

```TypeScript
AV_METRICS_EVENT_CONTENT_CHANGED = 5
```

Reported when the played media content changes, for example, advertisement insertion.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

## AV_METRICS_EVENT_CONTENT_DISCONTINUITY

```TypeScript
AV_METRICS_EVENT_CONTENT_DISCONTINUITY = 6
```

Content discontinuity event. This event is triggered when audio and video parameter changes are detected.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

## AV_METRICS_EVENT_AUDIO_ABNORMAL

```TypeScript
AV_METRICS_EVENT_AUDIO_ABNORMAL = 7
```

Audio device status change event, including underload or out-of-focus.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core
