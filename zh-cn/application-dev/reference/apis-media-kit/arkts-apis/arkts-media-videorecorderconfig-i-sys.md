# VideoRecorderConfig（系统接口）

Provides the video recorder configuration definitions.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## audioSourceType

```TypeScript
audioSourceType?: AudioSourceType
```

audio source type, details see @AudioSourceType .

**类型：** AudioSourceType

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## location

```TypeScript
location?: Location
```

geographical location information.

**类型：** Location

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## profile

```TypeScript
profile: VideoRecorderProfile
```

video recorder profile, can get by "getVideoRecorderProfile", details see @VideoRecorderProfile .=

**类型：** VideoRecorderProfile

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## rotation

```TypeScript
rotation?: number
```

Sets the video rotation angle in output file, and for the file to playback. mp4 support.
the range of rotation angle should be {0, 90, 180, 270}, default is 0.

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## url

```TypeScript
url: string
```

video output uri.support two kind of uri now.
format like: scheme + "://" + "context".
fd: fd://fd

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## videoSourceType

```TypeScript
videoSourceType: VideoSourceType
```

video source type, details see @VideoSourceType .

**类型：** VideoSourceType

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

