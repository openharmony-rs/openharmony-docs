# AVRecorderConfig

表示音视频录制的参数设置。通过audioSourceType和videoSourceType区分纯音频录制、纯视频录制或音视频录制。纯音频录制时，仅需要设置audioSourceType；纯视频录制时，仅需要设置videoSourceType； 音视频录制时，audioSourceType和videoSourceType均需要设置。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## audioSourceType

```TypeScript
audioSourceType?: AudioSourceType
```

选择录制的音频源类型。选择音频录制时必填。  
 **原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** [AudioSourceType](arkts-media-media-audiosourcetype-e.md)

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## fileGenerationMode

```TypeScript
fileGenerationMode?: FileGenerationMode
```

创建媒体文件的模式，配合on('photoAssetAvailable')监听使用。

**类型：** [FileGenerationMode](arkts-media-media-filegenerationmode-e.md)

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## location

```TypeScript
location?: Location
```

录制的地理位置，默认不记录地理位置信息。从API version 6开始支持，从API version 12开始废弃。建议使用 [AVMetadata](arkts-media-media-avmetadata-i.md).location。如果同时设置两个值，将会采用[AVMetadata](arkts-media-media-avmetadata-i.md).location。

**类型：** Location

**起始版本：** 9

**废弃版本：** 12

**替代接口：** [location](arkts-media-media-avmetadata-i.md#location)

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## maxDuration

```TypeScript
maxDuration?: number
```

设置录制的最大时长，单位为秒，有效值取值范围[1, 2^31-1]，无效输入会重置为最大值。 录制到达设定时长后，录制会自动停止，并通过stateChange回调录制状态，[AVRecorderState](arkts-media-media-avrecorderstate-t.md) = 'stopped'， [StateChangeReason](arkts-media-media-statechangereason-e.md) = BACKGROUND。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## metadata

```TypeScript
metadata?: AVMetadata
```

设置元数据信息。详细内容请参考 [AVMetadata](arkts-media-media-avmetadata-i.md)。

**类型：** AVMetadata

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## profile

```TypeScript
profile: AVRecorderProfile
```

录制的profile，必要参数。  
 **原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** [AVRecorderProfile](arkts-media-media-avrecorderprofile-i.md)

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## rotation

```TypeScript
rotation?: number
```

录制的视频旋转角度，单位为度（°）。mp4格式支持0°、90°、180°和270°，默认值为0°。从API version 6开始支持，从API version 12开始废弃。建议使用[AVMetadata](arkts-media-media-avmetadata-i.md).videoOrientation替代。如果同时设置两个值，将会采用[AVMetadata](arkts-media-media-avmetadata-i.md).videoOrientation。

**类型：** number

**起始版本：** 9

**废弃版本：** 12

**替代接口：** [videoOrientation](arkts-media-media-avmetadata-i.md#videoorientation)

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## url

```TypeScript
url: string
```

录制输出URL：fd://xx (fd number)，必要参数。   
 **原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## videoSourceType

```TypeScript
videoSourceType?: VideoSourceType
```

选择录制的视频源类型。选择视频录制时必填。

**类型：** [VideoSourceType](arkts-media-media-videosourcetype-e.md)

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder
