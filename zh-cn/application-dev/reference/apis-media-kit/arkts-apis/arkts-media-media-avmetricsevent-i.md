# AVMetricsEvent

Describes the information of an Metrics Event.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-media-interface AVMetricsEvent--><!--Device-media-interface AVMetricsEvent-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## details

```TypeScript
details: Record<string, Object>
```

The detailed information of the event.

**类型：** Record&lt;string, Object&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMetricsEvent-details: Record<string, Object>--><!--Device-AVMetricsEvent-details: Record<string, Object>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## event

```TypeScript
event: AVMetricsEventType
```

Type of the metrics event.

**类型：** AVMetricsEventType

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMetricsEvent-event: AVMetricsEventType--><!--Device-AVMetricsEvent-event: AVMetricsEventType-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## playbackPosition

```TypeScript
playbackPosition: int
```

The playback progress position when the event occurs.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AVMetricsEvent-playbackPosition: int--><!--Device-AVMetricsEvent-playbackPosition: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## timeStamp

```TypeScript
timeStamp: long
```

Absolute timestamp when the event occurred.

**类型：** long

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AVMetricsEvent-timeStamp: long--><!--Device-AVMetricsEvent-timeStamp: long-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

