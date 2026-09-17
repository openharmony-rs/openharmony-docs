# VideoRecorderConfig（系统接口）

表示视频录制的参数设置。

通过audioSourceType和videoSourceType区分纯视频录制和音视频录制（纯音频录制请使用[AVRecorder](arkts-media-media-avrecorder-i.md)或[AudioRecorder](arkts-media-media-audiorecorder-i.md)）。纯视频录制时，仅需要设置videoSourceType；音视频录制时，audioSourceType和videoSourceType均需要设置。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## audioSourceType

```TypeScript
audioSourceType?: AudioSourceType
```

视频录制的音频源类型，选择音频录制时必填。

**类型：** [AudioSourceType](arkts-media-media-audiosourcetype-e.md)

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## location

```TypeScript
location?: Location
```

录制视频的地理位置，默认不记录地理位置信息。

**类型：** [Location](arkts-media-media-location-i.md)

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## profile

```TypeScript
profile: VideoRecorderProfile
```

视频录制的profile。

**类型：** [VideoRecorderProfile](arkts-media-media-videorecorderprofile-i-sys.md)

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## rotation

```TypeScript
rotation?: number
```

录制的视频旋转角度，单位为度（°）。仅支持0°、90°、180°和270°，默认值为0°。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## url

```TypeScript
url: string
```

视频输出URL：fd://xx&nbsp;(fd&nbsp;number)<br>

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## videoSourceType

```TypeScript
videoSourceType: VideoSourceType
```

视频录制的视频源类型。

**类型：** [VideoSourceType](arkts-media-media-videosourcetype-e.md)

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。
