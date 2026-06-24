# AVRecorderConfig

Describes the audio and video recording parameters.

The **audioSourceType** and **videoSourceType** parameters are used to distinguish audio-only recording,
video-only recording, and audio and video recording. For audio-only recording, set only **audioSourceType**.
For video-only recording, set only **videoSourceType**. For audio and video recording, set both **audioSourceType**
and **videoSourceType**.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## metaSourceTypes

```TypeScript
metaSourceTypes?: Array<MetaSourceType>
```

Meta source types, details see @MetaSourceType .

**类型：** Array<MetaSourceType>

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**系统接口：** 此接口为系统接口。

