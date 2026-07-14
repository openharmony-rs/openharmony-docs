# MediaDescriptionKey

媒体信息描述枚举。

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Media.Core

## MD_KEY_TRACK_INDEX

```TypeScript
MD_KEY_TRACK_INDEX = 'track_index'
```

表示轨道序号，其对应键值类型为number。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## MD_KEY_TRACK_TYPE

```TypeScript
MD_KEY_TRACK_TYPE = 'track_type'
```

表示轨道类型，其对应键值类型为number，参考[MediaType](media.MediaType)。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## MD_KEY_CODEC_MIME

```TypeScript
MD_KEY_CODEC_MIME = 'codec_mime'
```

表示codec_mime类型，其对应键值类型为string。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## MD_KEY_DURATION

```TypeScript
MD_KEY_DURATION = 'duration'
```

表示媒体时长，其对应键值类型为number，单位为毫秒（ms）。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## MD_KEY_BITRATE

```TypeScript
MD_KEY_BITRATE = 'bitrate'
```

表示比特率，其对应键值类型为number，单位为比特率（bps），值为undefined或0表示异常。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## MD_KEY_WIDTH

```TypeScript
MD_KEY_WIDTH = 'width'
```

表示视频宽度，其对应键值类型为number，单位为像素（px）。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## MD_KEY_HEIGHT

```TypeScript
MD_KEY_HEIGHT = 'height'
```

表示视频高度，其对应键值类型为number，单位为像素（px）。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## MD_KEY_FRAME_RATE

```TypeScript
MD_KEY_FRAME_RATE = 'frame_rate'
```

表示视频帧率，其对应键值类型为number，单位为每100秒的帧数。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## MD_KEY_AUD_CHANNEL_COUNT

```TypeScript
MD_KEY_AUD_CHANNEL_COUNT = 'channel_count'
```

表示声道数，其对应键值类型为number。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## MD_KEY_AUD_SAMPLE_RATE

```TypeScript
MD_KEY_AUD_SAMPLE_RATE = 'sample_rate'
```

表示采样率，其对应键值类型为number，单位为赫兹（Hz）。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## MD_KEY_AUD_SAMPLE_DEPTH

```TypeScript
MD_KEY_AUD_SAMPLE_DEPTH = 'sample_depth'
```

表示位深，其对应键值类型为number，单位为位（bit）。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## MD_KEY_LANGUAGE

```TypeScript
MD_KEY_LANGUAGE = 'language'
```

表示字幕语言，其对应键值类型为string。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## MD_KEY_TRACK_NAME

```TypeScript
MD_KEY_TRACK_NAME = 'track_name'
```

表示track名称，其对应键值类型为string。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## MD_KEY_HDR_TYPE

```TypeScript
MD_KEY_HDR_TYPE = 'hdr_type'
```

表示视频轨类型，其对应键值类型为string。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## MD_KEY_ORIGINAL_WIDTH

```TypeScript
MD_KEY_ORIGINAL_WIDTH = 'original_width'
```

表示视频原始宽度，其对应键值类型为number，单位为像素（px）。

**起始版本：** 21

**元服务API：** 从API版本21开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## MD_KEY_ORIGINAL_HEIGHT

```TypeScript
MD_KEY_ORIGINAL_HEIGHT = 'original_height'
```

表示视频原始高度，其对应键值类型为number，单位为像素（px）。

**起始版本：** 21

**元服务API：** 从API版本21开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## MD_KEY_MIME_TYPE

```TypeScript
MD_KEY_MIME_TYPE = 'mime_type'
```

表示轨道的mime_type类型，其对应键值类型为string。对于音视频轨道，该值与MD_KEY_CODEC_MIME相同。

**起始版本：** 23

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## MD_KEY_REFERENCE_TRACK_IDS

```TypeScript
MD_KEY_REFERENCE_TRACK_IDS = 'ref_track_ids'
```

表示此轨道与其他轨道的引用关系，其对应键值类型为string，以逗号分隔。

**起始版本：** 23

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## MD_KEY_TRACK_REFERENCE_TYPE

```TypeScript
MD_KEY_TRACK_REFERENCE_TYPE = 'track_ref_type'
```

表示此轨道作为辅助轨的辅助类型，其对应键值类型为string。

**起始版本：** 23

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

