# AudioOutputFormat


> **说明：**
> 
> 从API version 6开始支持，从API version 8 开始废弃，建议使用[ContainerFormatType](arkts-media-media-containerformattype-e.md)替代。
表示音频封装格式的枚举。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [ContainerFormatType](arkts-media-media-containerformattype-e.md)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## DEFAULT

```TypeScript
DEFAULT = 0
```

默认封装格式。仅做接口定义，暂不支持使用。  
**说明：** 从API version 6开始支持，从API version 8开始废弃，建议根据具体情况选择[ContainerFormatType](arkts-media-media-containerformattype-e.md)中的一 项替代。

**起始版本：** 6

**废弃版本：** 8

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## MPEG_4

```TypeScript
MPEG_4 = 2
```

封装为MPEG-4格式。  
**说明：** 从API version 6开始支持，从API version 8开始废弃，建议使用[ContainerFormatType](arkts-media-media-containerformattype-e.md)中的 CFT_MPEG_4替代。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [CFT_MPEG_4](arkts-media-media-containerformattype-e.md#cft_mpeg_4)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## AMR_NB

```TypeScript
AMR_NB = 3
```

封装为AMR_NB格式。仅做接口定义，暂不支持使用。  
**说明：** 从API version 6开始支持，从API version 8开始废弃，建议使用[ContainerFormatType](arkts-media-media-containerformattype-e.md)中的CFT_AMR ，编码格式使用[CodecMimeType](arkts-media-media-codecmimetype-e.md)中的AUDIO_AMR_NB替代。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [CFT_AMR](arkts-media-media-containerformattype-e.md#cft_amr)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## AMR_WB

```TypeScript
AMR_WB = 4
```

封装为AMR_WB格式。仅做接口定义，暂不支持使用。  
**说明：** 从API version 6开始支持，从API version 8开始废弃，建议使用[ContainerFormatType](arkts-media-media-containerformattype-e.md)中的CFT_AMR ，编码格式使用[CodecMimeType](arkts-media-media-codecmimetype-e.md)中的AUDIO_AMR_WB替代。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [CFT_AMR](arkts-media-media-containerformattype-e.md#cft_amr)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## AAC_ADTS

```TypeScript
AAC_ADTS = 6
```

封装为ADTS（Audio Data Transport Stream）格式，是AAC音频的传输流格式。  
**说明：** 从API version 6开始支持，从API version 8开始废弃，建议使用[ContainerFormatType](arkts-media-media-containerformattype-e.md)中的CFT_AAC 替代。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [CFT_AAC](arkts-media-media-containerformattype-e.md#cft_aac)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder
