# AVMetricsEvent

描述一个指标事件的信息。

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## details

```TypeScript
details: Record<string, Object>
```

事件的详细信息。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## event

```TypeScript
event: AVMetricsEventType
```

指标事件的类型。

**类型：** [AVMetricsEventType](arkts-media-media-avmetricseventtype-e.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## playbackPosition

```TypeScript
playbackPosition: number
```

事件发生时的播放进度位置。

**类型：** number

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## timeStamp

```TypeScript
timeStamp: number
```

事件发生的绝对时间戳。

**类型：** number

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer
