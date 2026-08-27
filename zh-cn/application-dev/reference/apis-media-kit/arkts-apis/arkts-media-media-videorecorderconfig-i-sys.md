# VideoRecorderConfig（系统接口）

视频录制配置定义。

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

音频源类型，详见AudioSourceType。

**类型：** [AudioSourceType](arkts-media-media-audiosourcetype-e.md)

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## location

```TypeScript
location?: Location
```

地理位置信息。

**类型：** Location

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## profile

```TypeScript
profile: VideoRecorderProfile
```

视频录制配置参数，可通过getVideoRecorderProfile获取，详见VideoRecorderProfile。

**类型：** [VideoRecorderProfile](arkts-media-media-videorecorderprofile-i-sys.md)

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## rotation

```TypeScript
rotation?: number
```

设置视频输出文件中的旋转角度，用于文件播放。仅mp4格式支持。 旋转角度取值为{0, 90, 180, 270}，默认值为0。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## url

```TypeScript
url: string
```

视频输出URI。支持两种URI格式。 格式：scheme + "://" + "context"。 fd格式：fd://fd

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## videoSourceType

```TypeScript
videoSourceType: VideoSourceType
```

视频源类型，详见VideoSourceType。

**类型：** [VideoSourceType](arkts-media-media-videosourcetype-e.md)

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。
