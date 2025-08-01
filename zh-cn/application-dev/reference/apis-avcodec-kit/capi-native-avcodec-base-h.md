# native_avcodec_base.h

## 概述

声明用于音视频封装、解封装、编解码基础功能的Native API。

**引用文件：** <multimedia/player_framework/native_avcodec_base.h>

**库：** libnative_media_codecbase.so

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 9

**相关模块：** [CodecBase](capi-codecbase.md)

**相关示例：** [AVCodec](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/AVCodec)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AVCodecAsyncCallback](capi-codecbase-oh-avcodecasynccallback.md) | OH_AVCodecAsyncCallback | （API11废弃）OH_AVCodec中所有异步回调函数指针的集合。将该结构体的实例注册到OH_AVCodec实例中，并处理回调上报的信息，以保证OH_AVCodec的正常运行。 |
| [OH_AVCodecCallback](capi-codecbase-oh-avcodeccallback.md) | OH_AVCodecCallback | OH_AVCodec中所有异步回调函数指针的集合。将该结构体的实例注册到OH_AVCodec实例中，并处理回调上报的信息，以保证OH_AVCodec的正常运行。 |
| [OH_AVDataSource](capi-codecbase-oh-avdatasource.md) | OH_AVDataSource | 用户自定义数据源。 |
| [OH_AVDataSourceExt](capi-codecbase-oh-avdatasourceext.md) | OH_AVDataSourceExt | 用户自定义数据源，回调支持通过userData传递用户自定义数据。 |
| [NativeWindow](../apis-arkgraphics2d/capi-nativewindow-nativewindow.md) | OHNativeWindow | 为图形接口定义native层对象。 |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) | OH_AVCodec | 为音视频编解码接口定义native层对象。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_MediaType](#oh_mediatype) | OH_MediaType | 媒体类型。 |
| [OH_AACProfile](#oh_aacprofile) | OH_AACProfile | AAC档次。<!--Del--><br/>（AAC_PROFILE_HE、AAC_PROFILE_HE_V2暂未开放）<!--DelEnd--> |
| [OH_AVCProfile](#oh_avcprofile) | OH_AVCProfile | AVC档次。 |
| [OH_HEVCProfile](#oh_hevcprofile) | OH_HEVCProfile | HEVC档次。 |
| [OH_VVCProfile](#oh_vvcprofile) | OH_VVCProfile | VVC档次。 |
| [OH_MPEG2Profile](#oh_mpeg2profile) | OH_MPEG2Profile | MPEG2档次。 |
| [OH_MPEG4Profile](#oh_mpeg4profile) | OH_MPEG4Profile | MPEG4档次。 |
| [OH_H263Profile](#oh_h263profile) | OH_H263Profile | H.263档次。 |
| [OH_AVOutputFormat](#oh_avoutputformat) | OH_AVOutputFormat | 封装器支持的输出文件格式。 |
| [OH_AVSeekMode](#oh_avseekmode) | OH_AVSeekMode | 跳转模式。 |
| [OH_ScalingMode](#oh_scalingmode) | OH_ScalingMode | 缩放模式，只在Surface模式下使用。 |
| [OH_BitsPerSample](#oh_bitspersample) | OH_BitsPerSample | 每个编码样本的音频位数。 |
| [OH_ColorPrimary](#oh_colorprimary) | OH_ColorPrimary | 色域。编解码都支持。 |
| [OH_TransferCharacteristic](#oh_transfercharacteristic) | OH_TransferCharacteristic | 转移特性。编解码都支持。 |
| [OH_MatrixCoefficient](#oh_matrixcoefficient) | OH_MatrixCoefficient | 矩阵系数。编解码都支持。 |
| [OH_AVCLevel](#oh_avclevel) | OH_AVCLevel | AVC级别。 |
| [OH_HEVCLevel](#oh_hevclevel) | OH_HEVCLevel | HEVC级别。 |
| [OH_VVCLevel](#oh_vvclevel) | OH_VVCLevel | VVC级别。 |
| [OH_MPEG2Level](#oh_mpeg2level) | OH_MPEG2Level | MPEG2级别。 |
| [OH_MPEG4Level](#oh_mpeg4level) | OH_MPEG4Level | MPEG4级别。 |
| [OH_H263Level](#oh_h263level) | OH_H263Level | H.263级别。 |
| [OH_TemporalGopReferenceMode](#oh_temporalgopreferencemode) | OH_TemporalGopReferenceMode | 时域图片组参考模式。 |
| [OH_BitrateMode](#oh_bitratemode) | OH_BitrateMode | 编码器的比特率模式。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_AVCodecOnError)(OH_AVCodec *codec, int32_t errorCode, void *userData)](#oh_avcodeconerror) | OH_AVCodecOnError | 当OH_AVCodec实例运行出错时，会调用来上报具体的错误信息的函数指针。 |
| [typedef void (\*OH_AVCodecOnStreamChanged)(OH_AVCodec *codec, OH_AVFormat *format, void *userData)](#oh_avcodeconstreamchanged) | OH_AVCodecOnStreamChanged | 当解码输入码流分辨率或者编码输出码流的分辨率发生变化时，将调用此函数指针报告新的流描述信息。需要注意的是，OH_AVFormat指针的生命周期只有在函数指针被调用时才有效，调用结束后禁止继续访问。 |
| [typedef void (\*OH_AVCodecOnNeedInputData)(OH_AVCodec *codec, uint32_t index, OH_AVMemory *data, void *userData)](#oh_avcodeconneedinputdata) | OH_AVCodecOnNeedInputData | 当OH_AVCodec在运行过程中需要新的输入数据时，将调用此函数指针，并携带可用的缓冲区来填充新的输入数据。 |
| [typedef void (\*OH_AVCodecOnNewOutputData)(OH_AVCodec *codec, uint32_t index, OH_AVMemory *data,OH_AVCodecBufferAttr *attr, void *userData)](#oh_avcodeconnewoutputdata) | OH_AVCodecOnNewOutputData | 当OH_AVCodec运行过程中生成新的输出数据时，将调用此函数指针，并携带包含新输出数据的缓冲区。需要注意的是，OH_AVCodecBufferAttr指针的生命周期仅在调用函数指针时有效，这将禁止调用结束后继续访问。 |
| [typedef void (\*OH_AVCodecOnNeedInputBuffer)(OH_AVCodec *codec, uint32_t index, OH_AVBuffer *buffer, void *userData)](#oh_avcodeconneedinputbuffer) | OH_AVCodecOnNeedInputBuffer | 当OH_AVCodec在运行过程中需要新的输入数据时，将调用此函数指针，并携带可用的缓冲区来填充新的输入数据。 |
| [typedef void (\*OH_AVCodecOnNewOutputBuffer)(OH_AVCodec *codec, uint32_t index, OH_AVBuffer *buffer, void *userData)](#oh_avcodeconnewoutputbuffer) | OH_AVCodecOnNewOutputBuffer | 当OH_AVCodec运行过程中生成新的输出数据时，将调用此函数指针，并携带包含新输出数据的缓冲区。 |
| [typedef int32_t (\*OH_AVDataSourceReadAt)(OH_AVBuffer *data, int32_t length, int64_t pos)](#oh_avdatasourcereadat) | OH_AVDataSourceReadAt | 函数指针定义，用于提供获取用户自定义媒体数据的能力。 |
| [typedef int32_t (\*OH_AVDataSourceReadAtExt)(OH_AVBuffer *data, int32_t length, int64_t pos, void *userData)](#oh_avdatasourcereadatext) | OH_AVDataSourceReadAtExt | 函数指针定义，用于提供获取用户自定义媒体数据的能力。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| const char * OH_AVCODEC_MIMETYPE_VIDEO_AVC | AVC(H.264)视频编解码器的MIME类型。<br>**起始版本：** 9<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_AUDIO_AAC | AAC音频编解码器的MIME类型。<br>**起始版本：** 9<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_AUDIO_FLAC | FLAC音频编解码器的MIME类型。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_AUDIO_VORBIS | VORBIS音频解码器的MIME类型。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_AUDIO_MPEG | MP3音频编解码器的MIME类型。。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_VIDEO_HEVC | HEVC(H.265)视频编解码器的MIME类型。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_VIDEO_MPEG4 | MPEG4视频编码的MIME类型，仅用于封装MPEG4视频码流使用。<br>**起始版本：** 10<br>**废弃版本：** 11<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_VIDEO_MPEG4_PART2 | 视频MPEG4 Part2编解码器的MIME类型。<br>**起始版本：** 17<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_VIDEO_MPEG2 | 视频MPEG2编解码器的MIME类型。<br>**起始版本：** 17<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_VIDEO_H263 | H.263视频编解码器的MIME类型。<br>**起始版本：** 17<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_IMAGE_JPG | JPG图片编码的MIME类型，仅用于封装JPG封面时使用。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_IMAGE_PNG | PNG图片编码的MIME类型，仅用于封装PNG封面时使用。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_IMAGE_BMP | BMP图片编码的MIME类型，仅用于封装BMP封面时使用。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_AUDIO_VIVID | Audio Vivid音频解码器的MIME类型。<!--Del-->（当前规格暂未开放）<!--DelEnd--><br>**起始版本：** 11<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_AUDIO_AMR_NB | AMR_NB音频解码器的MIME类型。<br>**起始版本：** 11<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_AUDIO_AMR_WB | AMR_WB音频解码器的MIME类型。<br>**起始版本：** 11<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_AUDIO_OPUS | OPUS音频编解码器的MIME类型。<!--Del-->（当前规格暂未开放）<!--DelEnd--><br>**起始版本：** 11<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_AUDIO_G711MU | G711MU音频编解码器的MIME类型。<br>**起始版本：** 11<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_VIDEO_VVC | VVC(H.266)视频编解码器的MIME类型。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_AUDIO_APE | APE音频解码器的MIME类型。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_SUBTITLE_SRT | SRT字幕解封装器的MIME类型。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_SUBTITLE_WEBVTT | WEBVTT字幕解封装器的MIME类型。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_AUDIO_RAW | RAW音频码流的MIME类型。<br>**起始版本：** 18<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_AVCODEC_MIMETYPE_AUDIO_G711A | G711A音频解码器的MIME类型。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_ED_KEY_TIME_STAMP | 表示surfacebuffer时间戳的键，值类型为int64_t。<br>**起始版本：** 9<br>**废弃版本：** 14<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_ED_KEY_EOS | 表示surfacebuffer流结束符的键，值类型为int32_t。<br>**起始版本：** 9<br>**废弃版本：** 14<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_TRACK_TYPE | 轨道媒体类型的键，值类型为int32_t，请参见[OH_MediaType](#oh_mediatype)。<br>**起始版本：** 9<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_CODEC_MIME | 编解码器MIME类型的键，值类型为string。<br>**起始版本：** 9<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_DURATION | 媒体文件持续时间的键，单位为微秒，值类型为int64_t。<br>**起始版本：** 9<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_BITRATE | 比特率的键，值类型为int64_t。<br>**起始版本：** 9<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_MAX_INPUT_SIZE | 设置解码输入码流大小最大值的键，值类型为int32_t。<br>**起始版本：** 9<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_WIDTH | 视频宽度的键，值类型为int32_t。<br>在视频编解码流程中调用Configure接口时，使用此接口来设置视频帧的显示宽度。<br>使用指导请参见：[视频编码](../../media/avcodec/video-encoding.md)中的Surface模式的“步骤-5”或Buffer模式“步骤-4”。<br>**起始版本：** 9<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_HEIGHT | 视频高度键，值类型为int32_t。<br>在视频编解码流程中调用Configure接口时，使用此接口来设置视频帧的显示高度。<br>使用指导请参见：[视频编码](../../media/avcodec/video-encoding.md)中的中的Surface模式的“步骤-5”或Buffer模式“步骤-4”。<br>**起始版本：** 9<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_PIXEL_FORMAT | 视频像素格式的键，值类型为int32_t，请参见[OH_AVPixelFormat](_core.md#oh_avpixelformat-1)。<br>**起始版本：** 9<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_AUDIO_SAMPLE_FORMAT | 音频原始格式的键，值类型为int32_t，请参见[OH_BitsPerSample](#oh_bitspersample)。<br>**起始版本：** 9<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_FRAME_RATE | 视频帧率的键，值类型为double。该值必须大于 0。<br>**起始版本：** 9<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_ENCODE_BITRATE_MODE | 视频编码码率模式，值类型为int32_t，请参见[OH_BitrateMode](#oh_bitratemode)。<br>**起始版本：** 9<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_PROFILE | 编码档次，值类型为int32_t，请参见[OH_AVCProfile](#oh_avcprofile)、[OH_HEVCProfile](#oh_hevcprofile)、[OH_AACProfile](#oh_aacprofile)。<br>**起始版本：** 9<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_AUD_CHANNEL_COUNT | 音频通道计数键，值类型为int32_t。<br>**起始版本：** 9<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_AUD_SAMPLE_RATE | 音频采样率键，值类型为int32_t。<br>**起始版本：** 9<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_I_FRAME_INTERVAL | 关键帧间隔的键，值类型为int32_t，单位为毫秒。该键是可选的且只用于视频编码。<br>负值表示只有第一帧是关键帧，零表示所有帧都是关键帧。<br>**起始版本：** 9<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_ROTATION | surface旋转角度的键。值类型为int32_t，应为{0, 90, 180, 270}，默认值为0。<br>该键只在视频解码Surface模式下使用。<br>**起始版本：** 9<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_RANGE_FLAG | 视频YUV值域标志的键，值类型为int32_t，1表示full range，0表示limited range。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_COLOR_PRIMARIES | 视频色域的键，值类型为int32_t，请参见[OH_ColorPrimary](#oh_colorprimary)，遵循H.273标准Table2。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_TRANSFER_CHARACTERISTICS | 视频传递函数的键，值类型为int32_t，请参见[OH_TransferCharacteristic](#oh_transfercharacteristic)，遵循H.273标准Table3。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_MATRIX_COEFFICIENTS | 视频矩阵系数的键，值类型为int32_t，请参见[OH_MatrixCoefficient](#oh_matrixcoefficient)，遵循H.273标准Table4。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_REQUEST_I_FRAME | 请求立即编码I帧的键。值类型为int32_t。在调用[OH_VideoEncoder_SetParameter](_video_encoder.md#oh_videoencoder_setparameter)阶段使用，或随帧立即生效。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_QUALITY | 所需编码质量的键。值类型为int32_t，在H.264、H.265编码场景值范围可以根据能力查询接口[OH_AVCapability_GetEncoderQualityRange](capi-native-avcapability-h.md#oh_avcapability_getencoderqualityrange)获取，此键仅适用于配置在恒定质量模式下的编码器。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_CODEC_CONFIG | 编解码器特定数据的键，视频中表示传递SPS/PPS，音频中表示传递extraData，值类型为uint8_t*。 <!--Del-->（视频编解码此功能暂未支持）<!--DelEnd--><br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_TITLE | 媒体文件标题的键，值类型为string。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_ARTIST | 媒体文件艺术家的键，值类型为string。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_ALBUM | 专辑的媒体文件的键，值类型为string。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_ALBUM_ARTIST | 专辑艺术家的键，值类型为string。<br>**起始版本：** 10。<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_DATE | 媒体文件日期的键，值类型为string，例如2024年。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_COMMENT | 媒体文件注释的键，值类型为string。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_GENRE | 媒体文件流派的键，值类型为string。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_COPYRIGHT | 媒体文件版权的键，值类型为string。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_LANGUAGE | 媒体文件语言的键，值类型为string。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_DESCRIPTION | 媒体文件描述的键，值类型为string。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_LYRICS | 媒体文件歌词的键，值类型为string。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_TRACK_COUNT | 媒体文件轨道数量的键，值类型为int32_t。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_CHANNEL_LAYOUT | 所需编码通道布局的键。值类型为int64_t，此键仅适用于编码器。请参见[OH_AudioChannelLayout](_core.md#oh_audiochannellayout-1)。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_BITS_PER_CODED_SAMPLE | 每个编码样本位数的键，值类型为int32_t。<br>API 20前，FLAC编码必须设置此参数，设置为1即可；未设置此参数配置FLAC编码器时，调用OH_AudioCodec_Configure会返回错误码AV_ERR_INVALID_VAL。该值无实际作用，不会影响编码结果。<br>从API 20开始，无需设置此参数。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_AAC_IS_ADTS | aac格式的键，aac格式分为ADTS格式和LATM格式。值类型为int32_t，0表示LATM格式，1表示ADTS格式。aac解码器支持。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_SBR | aac sbr模式的键，值类型为int32_t，aac编码器支持。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_COMPLIANCE_LEVEL | flac兼容性等级的键，值类型为int32_t，仅在音频编码使用。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_IDENTIFICATION_HEADER | vorbis标识头的键，值类型为uint8_t*，仅vorbis解码器支持。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_SETUP_HEADER | vorbis设置头的键，值类型为uint8_t*，仅vorbis解码器支持。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_SCALING_MODE | 视频缩放模式，值类型为int32_t，请参见[OH_ScalingMode](#oh_scalingmode)。<br>建议直接调用[OH_NativeWindow_NativeWindowSetScalingModeV2](../apis-arkgraphics2d/capi-external-window-h.md#oh_nativewindow_nativewindowsetscalingmodev2)接口进行设置。该键是可选的且只用于视频解码Surface模式。<br>**起始版本：** 10<br>**废弃版本：** 14<br>**替代接口：** [OH_NativeWindow_NativeWindowSetScalingModeV2](../apis-arkgraphics2d/capi-external-window-h.md#oh_nativewindow_nativewindowsetscalingmodev2)<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_MAX_INPUT_BUFFER_COUNT | 最大输入缓冲区个数的键，值类型为int32_t。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_MAX_OUTPUT_BUFFER_COUNT | 最大输出缓冲区个数的键，值类型int32_t。<br>**起始版本：** 10<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_AUDIO_COMPRESSION_LEVEL | 音频编解码压缩水平的键，只在音频编码使用，值类型为int32_t。<br>**起始版本：** 11<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_IS_HDR_VIVID | 媒体文件中的视频轨是否为HDR Vivid的键，支持封装和解封装，值类型为int32_t。<br>1代表是HDR Vivid视频轨，0表示其他情况。<br>**起始版本：** 11<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_AUDIO_OBJECT_NUMBER | 音频对象数目的键. 值类型为int32_t，只有Audio Vivid解码使用。<br>**起始版本：** 11<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_AUDIO_VIVID_METADATA | Audio Vivid元数据的键，值类型为uint8_t*，只有Audio Vivid解码使用。<br>**起始版本：** 11<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_FEATURE_PROPERTY_KEY_VIDEO_ENCODER_MAX_LTR_FRAME_COUNT | 在视频编码中获取长期参考帧的最大个数的键，值类型为int32_t。可以通过[OH_AVCapability_GetFeatureProperties](capi-native-avcapability-h.md#oh_avcapability_getfeatureproperties)接口和枚举值[OH_AVCapabilityFeature](capi-native-avcapability-h.md#oh_avcapabilityfeature)中的VIDEO_ENCODER_LONG_TERM_REFERENCE来查询这个最大值。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_ENCODER_ENABLE_TEMPORAL_SCALABILITY | 使能分层编码的键，值类型为int32_t，1表示使能，0表示其它情况。<br>使用前可以通过[OH_AVCapability_IsFeatureSupported](capi-native-avcapability-h.md#oh_avcapability_isfeaturesupported)接口和枚举值[OH_AVCapabilityFeature](capi-native-avcapability-h.md#oh_avcapabilityfeature)中的VIDEO_ENCODER_TEMPORAL_SCALABILITY来查询当前视频编码器是否支持分层编码。详情请参见：[时域可分层视频编码](../../media/avcodec/video-encoding-temporal-scalability.md#接口介绍)。<br>该键是可选的且只用于视频编码，在Configure阶段使用。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_ENCODER_TEMPORAL_GOP_SIZE | 描述图片组基本层图片的间隔大小的键，值类型为int32_t，只在使能分层编码时生效。<br>该键是可选的且只用于视频编码，在Configure阶段使用。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_ENCODER_TEMPORAL_GOP_REFERENCE_MODE | 描述图片组内参考模式的键，值类型为int32_t，请参见[OH_TemporalGopReferenceMode](#oh_temporalgopreferencemode)，只在使能分层编码时生效。<br>该键是可选的且只用于视频编码，在Configure阶段使用。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_ENCODER_LTR_FRAME_COUNT | 描述长期参考帧个数的键，值类型为int32_t，必须在支持的值范围内使用。<br>使用前可以通过[OH_AVCapability_GetFeatureProperties](capi-native-avcapability-h.md#oh_avcapability_getfeatureproperties)接口和枚举值[OH_AVCapabilityFeature](capi-native-avcapability-h.md#oh_avcapabilityfeature)中的VIDEO_ENCODER_LONG_TERM_REFERENCE来查询支持的LTR数目。<br>该键是可选的且只用于视频编码，在Configure阶段使用。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_ENCODER_PER_FRAME_MARK_LTR | 标记当前帧为长期参考帧的键，值类型为int32_t，1表示被标记，0表示其它情况。<br>只在长期参考帧个数被配置后生效。<br>该键是可选的且只用于视频编码输入轮转中，配置后立即生效。<br>详情请参见：[时域可分层视频编码](../../media/avcodec/video-encoding-temporal-scalability.md#接口介绍)。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_ENCODER_PER_FRAME_USE_LTR | 描述当前帧参考的长期参考帧帧的POC号的键，值类型为int32_t。<br>该键是可选的且只用于视频编码输入轮转中，配置后立即生效。<br>详情请参见：[时域可分层视频编码](../../media/avcodec/video-encoding-temporal-scalability.md#接口介绍)。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_PER_FRAME_IS_LTR | 当前OH_AVBuffer中输出的码流对应的帧是否为长期参考帧的键，值类型为int32_t，1表示是LTR，0表示其它情况。<br>该键是可选的且只用于视频编码输出轮转中。<br>表示帧的属性。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_PER_FRAME_POC | 描述帧的POC的键，值类型为int32_t。<br>该键是可选的且只用于视频编码输出轮转中。<br>表示帧的属性。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_CROP_TOP | 描述裁剪矩形顶部坐标(y)值的键，值类型为int32_t。<br>包含裁剪框顶部的行，行索引从0开始。<br>该键只用于视频解码。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_CROP_BOTTOM | 描述裁剪矩形底部坐标(y)值的键，值类型为int32_t。<br>包含裁剪框底部的行，行索引从0开始。<br>该键只用于视频解码。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_CROP_LEFT | 描述裁剪矩形左坐标(x)值的键，值类型为int32_t。<br>包含裁剪框最左边的列，列索引从0开始。<br>该键只用于视频解码。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_CROP_RIGHT | 描述裁剪矩形右坐标(x)值的键，值类型为int32_t。<br>包含裁剪框最右边的列，列索引从0开始。<br>该键只用于视频解码。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_STRIDE | 描述视频帧宽跨距的键，值类型为int32_t。<br>宽跨距是像素的索引与正下方像素的索引之间的差。<br>对于YUV420格式，宽跨距对应于Y平面，U和V平面的跨距可以根据颜色格式计算，但通常未定义，并且取决于设备和版本。<br>使用指导请参见：[视频编码Buffer模式](../../media/avcodec/video-encoding.md#buffer模式)的“步骤-3”。<br>width、height、wStride、hStride图像排布与使用示例请参考：[视频编码Buffer模式](../../media/avcodec/video-encoding.md#buffer模式)的“步骤-8”或[视频解码Buffer模式](../../media/avcodec/video-decoding.md#buffer模式)“步骤-11”。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_SLICE_HEIGHT | 描述视频帧高跨距的键，值类型为int32_t。<br>高跨距是指从Y平面顶部到U平面顶部必须偏移的行数。本质上，U平面的偏移量是sliceHeight \* stride。<br>U/V平面的高度可以根据颜色格式计算，尽管它通常是未定义的，并且取决于设备和版本。<br>使用指导请参见：[视频编码Buffer模式](../../media/avcodec/video-encoding.md#buffer模式)的“步骤-3”。<br>width、height、wStride、hStride图像排布与使用示例请参考：[视频编码Buffer模式](../../media/avcodec/video-encoding.md#buffer模式)的“步骤-8”或[视频解码Buffer模式](../../media/avcodec/video-decoding.md#buffer模式)“步骤-11”。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_PIC_WIDTH | 描述视频帧真实宽度的键，值类型为int32_t。<br>视频解码时调用[OH_VideoDecoder_GetOutputDescription](_video_decoder.md#oh_videodecoder_getoutputdescription)接口，可以从其返回的OH_AVFormat中解析出宽度值。<br>当解码输出码流<!--RP2--><!--RP2End-->变化时，也可从[OH_AVCodecOnStreamChanged](#oh_avcodeconstreamchanged)返回的OH_AVForamt实例中解析出宽度值。<br>从OH_AVForamt实例中解析出来的是对齐后的宽、高与调用Configure接口设置的OH_MD_KEY_WIDTH、OH_MD_KEY_HEIGHT不一样。<br>width、height、wStride、hStride图像排布与使用示例请参考：[视频编码Buffer模式](../../media/avcodec/video-encoding.md#buffer模式)的“步骤-8”或[视频解码Buffer模式](../../media/avcodec/video-decoding.md#buffer模式)“步骤-11”。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_PIC_HEIGHT | 描述视频帧真实高度的键，值类型为int32_t。<br>视频解码时调用[OH_VideoDecoder_GetOutputDescription](_video_decoder.md#oh_videodecoder_getoutputdescription)接口，可以从其返回的OH_AVFormat中解析出高度值。<br>当解码输出码流<!--RP2--><!--RP2End-->变化时，也可从[OH_AVCodecOnStreamChanged](#oh_avcodeconstreamchanged)返回的OH_AVForamt实例中解析出高度值。<br>从OH_AVForamt实例中解析出来的是对齐后的宽、高与调用Configure接口设置的OH_MD_KEY_WIDTH、OH_MD_KEY_HEIGHT不一样。<br>width、height、wStride、hStride图像排布与使用示例请参考：[视频编码Buffer模式](../../media/avcodec/video-encoding.md#buffer模式)的“步骤-8”或[视频解码Buffer模式](../../media/avcodec/video-decoding.md#buffer模式)“步骤-11”。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_ENABLE_LOW_LATENCY | 使能低时延视频编解码的键，值类型为int32_t，1表示使能，0表示其它情况。<br>该键是可选的，在Configure阶段使用。<br>如果使能，则视频编码器或视频解码器持有的输入和输出数据不会超过编解码器标准所要求的数量。<br>若平台支持，当使能此接口时，视频解码器将按照解码序输出帧。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_ENCODER_QP_MAX | 描述视频编码器允许的最大量化参数的键，值类型为int32_t。<br>在Configure/SetParameter阶段使用，或随帧立即生效。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_ENCODER_QP_MIN | 描述视频编码器允许的最小量化参数的键，值类型为int32_t。<br>在在Configure/SetParameter阶段使用，或随帧立即生效。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_ENCODER_QP_AVERAGE | 描述视频帧平均量化参数的键，值类型为int32_t。<br>表示当前帧编码块的平均qp值，随[OH_AVBuffer](_core.md#oh_avbuffer)输出。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_ENCODER_MSE | 描述视频帧平方误差的键，值类型为double。<br>表示当前帧编码块的MSE统计值，随[OH_AVBuffer](_core.md#oh_avbuffer)输出。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_DECODING_TIMESTAMP | AVBuffer中携带的音视频或字幕的sample对应的解码时间戳的键，以微秒为单位，值类型为int64_t。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_BUFFER_DURATION | AVBuffer中携带的音视频或字幕的sample对应的持续时间的键，以微秒为单位，值类型为int64_t。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_SAR | 样本长宽比的键，值类型为double。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_START_TIME | 媒体文件中第一帧起始位置开始时间的键，以微秒为单位，值类型为int64_t。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_TRACK_START_TIME | 轨道开始时间的键，以微秒为单位，值类型为int64_t。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_DECODER_OUTPUT_COLOR_SPACE | 设置视频解码器输出色彩空间的键，值类型为int32_t。<br>支持的值为OH_COLORSPACE_BT709_LIMIT，请参见[OH_NativeBuffer_ColorSpace](../apis-arkgraphics2d/capi-buffer-common-h.md#oh_nativebuffer_colorspace)。<br>在视频解码调用[OH_VideoDecoder_Configure](_video_decoder.md#oh_videodecoder_configure)接口时使用此接口。<br>在启动OH_VideoDecoder_Start接口前，必须要先调用OH_VideoDecoder_Prepare接口。<br>如果支持色彩空间转换功能并配置了此键，则视频解码器会自动将HDR Vivid视频转码为指定的色彩空间。<br>如果不支持色彩空间转换功能，则接口[OH_VideoDecoder_Configure](_video_decoder.md#oh_videodecoder_configure)返回错误码[OH_AVErrCode](_core.md#oh_averrcode-1)中的AV_ERR_VIDEO_UNSUPPORTED_COLOR_SPACE_CONVERSION。<br>如果输入视频不是HDR Vivid视频，则会通过回调函数[OH_AVCodecOnError](#oh_avcodeconerror)报告错误码[OH_AVErrCode](_core.md#oh_averrcode-1)中的AV_ERR_VIDEO_UNSUPPORTED_COLOR_SPACE_CONVERSION。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_DECODER_OUTPUT_ENABLE_VRR | 解码器是否打开视频可变帧率功能的键，值类型为int32_t。<br>1代表使能视频可变帧率功能，0代表不使能。<br>**起始版本：** 15<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_CREATION_TIME | 媒体文件创建时间的元数据，值类型为string。使用ISO 8601标准的时间格式且为UTC时间，时间格式参考："2024-12-28T00:00:00:000000Z"。<br>**起始版本：** 14<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_ENCODER_REPEAT_PREVIOUS_FRAME_AFTER | 如果在上一帧提交给编码器之后没有新的帧可用，则会以毫秒为单位重复提交最后一帧，值类型为int32_t。<br>该键只用于视频编码Surface模式，在Configure阶段使用。<br>配置的值：<br>- 小于等于0：Configure阶段会被拦截，返回ERROR AV_ERR_INVALID_VAL。<br>- 大于0：如果在上一帧提交给编码器之后没有新的帧可用，则会以毫秒为单位重复提交最后一帧。<br>**起始版本：** 18<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_ENCODER_REPEAT_PREVIOUS_MAX_COUNT | 描述编码器在没有新的帧可用的情况下，可以对之前的帧进行重复编码的最大次数，值类型为int32_t。<br>该键仅在OH_MD_KEY_VIDEO_ENCODER_REPEAT_PREVIOUS_FRAME_AFTER可用时生效，在Configure阶段使用。<br>配置的值：<br>- 等于0：Configure阶段会被拦截，返回ERROR AV_ERR_INVALID_VAL。<br>- 小于0：在没有新的帧提交给编码器的这段时间内，编码器会一直重复编上一帧，直到达到系统上限。<br>- 大于0：在没有新的帧提交给编码器的这段时间内，最多可以重复编码的帧数。<br>**起始版本：** 18<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_ENCODER_ROI_PARAMS | 用于视频编码中，使能ROI编码并下发ROI参数，随帧设置且实时生效。<br>参数需满足"Top1,Left1-Bottom1,Right1=Offset1;Top2,Left2-Bottom2,Right2=Offset2;"的格式，多个ROI参数之间使用";"连接。<br>Top、Left、Bottom、Right指定一个ROI区域的上、左、下、右边界，Offset指定deltaQP，“=Offset”可以省略，省略时使用默认值（-3）。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_SQR_FACTOR | 指定SQR码控模式的质量参数，取值范围为[0, 51]（同编码量化参数QP），值越小，编码输出码率越大，质量越好。<br>在Configure/SetParameter阶段使用。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_MAX_BITRATE | 指定SQR码控模式的最大码率，使用[OH_AVCapability_GetEncoderBitrateRange](capi-native-avcapability-h.md#oh_avcapability_getencoderbitraterange)方法获取取值范围（同OH_MD_KEY_BITRATE），单位bps。<br>在Configure/SetParameter阶段使用。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_VIDEO_ENCODER_ENABLE_PTS_BASED_RATECONTROL | 使能基于显示时间戳(PTS)的码控模式的键，值类型为int32_t，1表示使能，0表示其它情况。<br>该键值是可选的且只用于视频编码，默认值为0。<br>如果使能，则必须在每个视频帧中携带PTS信息，并发送到编码器。Surface模式下，通过[OH_NativeWindow_NativeWindowHandleOpt](../apis-arkgraphics2d/capi-external-window-h.md#oh_nativewindow_nativewindowhandleopt)接口设置PTS，时间单位为纳秒(ns)；Buffer模式下，通过[OH_AVBuffer_SetBufferAttr](_core.md#oh_avbuffer_setbufferattr)接口设置PTS，时间单位为微秒(us)。<br>在Configure阶段使用。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_REFERENCE_TRACK_IDS | 媒体文件轨道间参考、被参考关系，值类型为int32_t\*。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_TRACK_REFERENCE_TYPE | 媒体文件辅助轨类型，值类型为string。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_TRACK_DESCRIPTION | 媒体文件辅助轨描述信息，值类型为string。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |
| const char * OH_MD_KEY_ENABLE_SYNC_MODE | 使能视频编解码同步模式的键，值类型为int32_t，1表示使能，0表示其它情况。该键是可选，默认值为0。<br>如果使能，需要注意：<br> 1. 编解码器不可设置回调函数。<br> 2. 必须使用缓冲区查询接口替代回调。<br> 3. 只能在Configure阶段使用。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Media.CodecBase |

## 枚举类型说明

### OH_MediaType

```
enum OH_MediaType
```

**描述**

媒体类型。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| MEDIA_TYPE_AUD = 0 | 音频轨。 |
| MEDIA_TYPE_VID = 1 | 视频轨。 |
| MEDIA_TYPE_SUBTITLE = 2 | 字幕轨。<br>**起始版本：** 12 |
| MEDIA_TYPE_TIMED_METADATA = 5 | timed metadata轨。<br>**起始版本：** 20 |
| MEDIA_TYPE_AUXILIARY = 6 | 辅助轨。<br>**起始版本：** 20 |

### OH_AACProfile

```
enum OH_AACProfile
```

**描述**

AAC档次。<!--Del--><br/>（AAC_PROFILE_HE、AAC_PROFILE_HE_V2暂未开放）<!--DelEnd-->

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| AAC_PROFILE_LC = 0 | AAC编码档次为Low Complexity级别。 |
| AAC_PROFILE_HE  | AAC编码档次为High Efficiency级别。<!--Del-->（此规格暂未开放）<!--DelEnd--> <br>**起始版本：** 14 |
| AAC_PROFILE_HE_V2 | AAC编码档次为High Efficiency v2级别。<!--Del-->（此规格暂未开放）<!--DelEnd--> <br>**起始版本：** 14 |

### OH_AVCProfile

```
enum OH_AVCProfile
```

**描述**

AVC档次。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| AVC_PROFILE_BASELINE = 0 | AVC编码档次为基本档次。 |
| AVC_PROFILE_HIGH = 4 | AVC编码档次为高档次。 |
| AVC_PROFILE_MAIN = 8 | AVC编码档次为主档次。 |

### OH_HEVCProfile

```
enum OH_HEVCProfile
```

**描述**

HEVC档次。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| HEVC_PROFILE_MAIN = 0 | HEVC编码档次为主档次。 |
| HEVC_PROFILE_MAIN_10 = 1 | HEVC编码档次为10bit主档次。 |
| HEVC_PROFILE_MAIN_STILL = 2 | HEVC编码档次为静止图像主档次。 |
| HEVC_PROFILE_MAIN_10_HDR10 = 3 | HEVC编码档次为HDR10主档次。<br>**废弃版本：** 14 |
| HEVC_PROFILE_MAIN_10_HDR10_PLUS = 4 | HEVC编码档次为HDR10+主档次。<br>**废弃版本：** 14 |

### OH_VVCProfile

```
enum OH_VVCProfile
```

**描述**

VVC档次。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| VVC_PROFILE_MAIN_10 = 1 | VVC编码档次为10bit主档次。 |
| VVC_PROFILE_MAIN_12 = 2 | VVC编码档次为12bit主档次。 |
| VVC_PROFILE_MAIN_12_INTRA = 10 | VVC编码档次为12bit帧内主档次。 |
| VVC_PROFILE_MULTI_MAIN_10 = 17 | VVC编码档次为多层编码10bit主档次。 |
| VVC_PROFILE_MAIN_10_444 = 33 | VVC编码档次为10bit全采样主档次。 |
| VVC_PROFILE_MAIN_12_444 = 34 | VVC编码档次为12bit全采样主档次。 |
| VVC_PROFILE_MAIN_16_444 = 36 | VVC编码档次为16bit全采样主档次。 |
| VVC_PROFILE_MAIN_12_444_INTRA = 42 | VVC编码档次为12bit全采样帧内主档次。 |
| VVC_PROFILE_MAIN_16_444_INTRA = 44 | VVC编码档次为16bit全采样帧内主档次。 |
| VVC_PROFILE_MULTI_MAIN_10_444 = 49 | VVC编码档次为多层编码10bit全采样主档次。 |
| VVC_PROFILE_MAIN_10_STILL = 65 | VVC编码档次为10bit静止图像主档次。 |
| VVC_PROFILE_MAIN_12_STILL = 66 | VVC编码档次为12bit静止图像主档次。 |
| VVC_PROFILE_MAIN_10_444_STILL = 97 | VVC编码档次为10bit全采样静止图像主档次。 |
| VVC_PROFILE_MAIN_12_444_STILL = 98 | VVC编码档次为12bit全采样静止图像主档次。 |
| VVC_PROFILE_MAIN_16_444_STILL = 100 | VVC编码档次为16bit全采样静止图像主档次。 |

### OH_MPEG2Profile

```
enum OH_MPEG2Profile
```

**描述**

MPEG2档次。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 17

| 枚举项 | 描述 |
| -- | -- |
| MPEG2_PROFILE_SIMPLE = 0 | 简单档次。 |
| MPEG2_PROFILE_MAIN  = 1 | 主档次。 |
| MPEG2_PROFILE_SNR_SCALABLE  = 2 | 信噪比可分级档次。 |
| MPEG2_PROFILE_SPATIALLY_SCALABLE = 3 | 空间可分级档次。 |
| MPEG2_PROFILE_HIGH = 4 | 高级档次。 |
| MPEG2_PROFILE_422 = 5 | 4:2:2档次。 |

### OH_MPEG4Profile

```
enum OH_MPEG4Profile
```

**描述**

MPEG4档次。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 17

| 枚举项 | 描述 |
| -- | -- |
| MPEG4_PROFILE_SIMPLE = 0 | 简单档次。 |
| MPEG4_PROFILE_SIMPLE_SCALABLE = 1 | 简单可分级档次。 |
| MPEG4_PROFILE_CORE = 2 | 核心档次。 |
| MPEG4_PROFILE_MAIN = 3 | 主档次。 |
| MPEG4_PROFILE_N_BIT  = 4 | N位档次。 |
| MPEG4_PROFILE_HYBRID = 5 | 混合档次。 |
| MPEG4_PROFILE_BASIC_ANIMATED_TEXTURE = 6 | 基本动画纹理档次。 |
| MPEG4_PROFILE_SCALABLE_TEXTURE = 7 | 可分级纹理档次。 |
| MPEG4_PROFILE_SIMPLE_FA = 8 | 简单FA档次。 |
| MPEG4_PROFILE_ADVANCED_REAL_TIME_SIMPLE = 9 | 高级实时简单档次。 |
| MPEG4_PROFILE_CORE_SCALABLE = 10 | 核心可分级档次。 |
| MPEG4_PROFILE_ADVANCED_CODING_EFFICIENCY = 11 | 高级编码效率档次。 |
| MPEG4_PROFILE_ADVANCED_CORE = 12 | 高级核心档次。 |
| MPEG4_PROFILE_ADVANCED_SCALABLE_TEXTURE = 13 | 高级可分级纹理档次。 |
| MPEG4_PROFILE_ADVANCED_SIMPLE = 17 | 高级简单档次。 |

### OH_H263Profile

```
enum OH_H263Profile
```

**描述**

H.263档次。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 17

| 枚举项 | 描述 |
| -- | -- |
| H263_PROFILE_BASELINE = 0 | 基线档次。 |
| H263_PROFILE_VERSION_1_BACKWARD_COMPATIBILITY = 2 | 版本1向后兼容档次。 |

### OH_AVOutputFormat

```
enum OH_AVOutputFormat
```

**描述**

封装器支持的输出文件格式。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| AV_OUTPUT_FORMAT_DEFAULT = 0 | 输出文件格式默认值，默认为MP4格式。 |
| AV_OUTPUT_FORMAT_MPEG_4 = 2 | 输出文件格式为MP4格式。 |
| AV_OUTPUT_FORMAT_M4A = 6 | 输出文件格式为M4A格式。 |
| AV_OUTPUT_FORMAT_AMR = 8 | 输出文件格式为AMR格式。<br>**起始版本：** 12 |
| AV_OUTPUT_FORMAT_MP3 = 9 | 输出文件格式为MP3格式。<br>**起始版本：** 12 |
| AV_OUTPUT_FORMAT_WAV = 10 | 输出文件格式为WAV格式。<br>**起始版本：** 12 |
| AV_OUTPUT_FORMAT_AAC = 11 | 输出文件格式为AAC格式。<br>**起始版本：** 18 |
| AV_OUTPUT_FORMAT_FLAC = 12 | 输出文件格式为FLAC格式。<br>**起始版本：** 20 |

### OH_AVSeekMode

```
enum OH_AVSeekMode
```

**描述**

跳转模式。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| SEEK_MODE_NEXT_SYNC = 0 | 指定时间位置的下一I帧。若时间点后没有I帧，该模式可能跳转失败。 |
| SEEK_MODE_PREVIOUS_SYNC | 指定时间位置的上一I帧。 |
| SEEK_MODE_CLOSEST_SYNC | 指定时间位置的最近I帧。 |

### OH_ScalingMode

```
enum OH_ScalingMode
```

**描述**

缩放模式，只在Surface模式下使用。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 10

**废弃版本：** 14

**替代接口：** [OHScalingModeV2](../apis-arkgraphics2d/capi-external-window-h.md#ohscalingmodev2)

| 枚举项 | 描述 |
| -- | -- |
| SCALING_MODE_SCALE_TO_WINDOW = 1 | 根据窗口尺寸自适应调整图像大小。<br>**废弃版本：** 14 <br>**替代接口：** [OHScalingModeV2](../apis-arkgraphics2d/capi-external-window-h.md#ohscalingmodev2).OH_SCALING_MODE_SCALE_TO_WINDOW_V2 |
| SCALING_MODE_SCALE_CROP = 2 | 根据窗口尺寸裁剪图像大小。<br>**废弃版本：** 14 <br>**替代接口：** [OHScalingModeV2](../apis-arkgraphics2d/capi-external-window-h.md#ohscalingmodev2).OH_SCALING_MODE_SCALE_CROP_V2  |

### OH_BitsPerSample

```
enum OH_BitsPerSample
```

**描述**

每个编码样本的音频位数。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| SAMPLE_U8 = 0 | 8位无符号整数采样。 |
| SAMPLE_S16LE = 1 | 16位有符号整数交样。 |
| SAMPLE_S24LE = 2 | 24位有符号整数采样。 |
| SAMPLE_S32LE = 3 | 32位有符号整数采样。 |
| SAMPLE_F32LE = 4 | 32位浮点采样。 |
| SAMPLE_U8P = 5 | 8位无符号整数平面采样。 |
| SAMPLE_S16P = 6 | 16位有符号整数平面采样。 |
| SAMPLE_S24P = 7 | 24位有符号整数平面采样。 |
| SAMPLE_S32P = 8 | 32位有符号整数平面采样。 |
| SAMPLE_F32P = 9 | 32位浮点平面采样。 |
| INVALID_WIDTH = -1 | 无效采样格式。 |

### OH_ColorPrimary

```
enum OH_ColorPrimary
```

**描述**

色域。编解码都支持。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| COLOR_PRIMARY_BT709 = 1 | BT709色域。 |
| COLOR_PRIMARY_UNSPECIFIED = 2 | 未指定色域。 |
| COLOR_PRIMARY_BT470_M = 4 | BT470_M色域。 |
| COLOR_PRIMARY_BT601_625 = 5 | BT601_625色域。 |
| COLOR_PRIMARY_BT601_525 = 6 | BT601_525色域。 |
| COLOR_PRIMARY_SMPTE_ST240 = 7 | SMPTE_ST240色域。 |
| COLOR_PRIMARY_GENERIC_FILM = 8 | GENERIC_FILM色域。 |
| COLOR_PRIMARY_BT2020 = 9 | BT2020色域。 |
| COLOR_PRIMARY_SMPTE_ST428 = 10 | SMPTE_ST428色域。 |
| COLOR_PRIMARY_P3DCI = 11 | P3DCI色域。 |
| COLOR_PRIMARY_P3D65 = 12 | P3D65色域。 |

### OH_TransferCharacteristic

```
enum OH_TransferCharacteristic
```

**描述**

转移特性。编解码都支持。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| TRANSFER_CHARACTERISTIC_BT709 = 1 | BT709传递函数。 |
| TRANSFER_CHARACTERISTIC_UNSPECIFIED = 2 | 未指定传递函数。 |
| TRANSFER_CHARACTERISTIC_GAMMA_2_2 = 4 | GAMMA_2_2传递函数。 |
| TRANSFER_CHARACTERISTIC_GAMMA_2_8 = 5 | GAMMA_2_8传递函数。 |
| TRANSFER_CHARACTERISTIC_BT601 = 6 | BT601传递函数。 |
| TRANSFER_CHARACTERISTIC_SMPTE_ST240 = 7 | SMPTE_ST240传递函数。 |
| TRANSFER_CHARACTERISTIC_LINEAR = 8 | LINEAR传递函数。 |
| TRANSFER_CHARACTERISTIC_LOG = 9 | LOG传递函数。 |
| TRANSFER_CHARACTERISTIC_LOG_SQRT = 10 | LOG_SQRT传递函数。 |
| TRANSFER_CHARACTERISTIC_IEC_61966_2_4 = 11 | IEC_61966_2_4传递函数。 |
| TRANSFER_CHARACTERISTIC_BT1361 = 12 | BT1361传递函数。 |
| TRANSFER_CHARACTERISTIC_IEC_61966_2_1 = 13 | IEC_61966_2_1传递函数。 |
| TRANSFER_CHARACTERISTIC_BT2020_10BIT = 14 | BT2020_10BIT传递函数。 |
| TRANSFER_CHARACTERISTIC_BT2020_12BIT = 15 | BT2020_12BIT传递函数。 |
| TRANSFER_CHARACTERISTIC_PQ = 16 | PQ传递函数。 |
| TRANSFER_CHARACTERISTIC_SMPTE_ST428 = 17 | SMPTE_ST428传递函数。 |
| TRANSFER_CHARACTERISTIC_HLG = 18 | HLG传递函数。 |

### OH_MatrixCoefficient

```
enum OH_MatrixCoefficient
```

**描述**

矩阵系数。编解码都支持。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| MATRIX_COEFFICIENT_IDENTITY = 0 | 单位矩阵。 |
| MATRIX_COEFFICIENT_BT709 = 1 | BT709转换矩阵。 |
| MATRIX_COEFFICIENT_UNSPECIFIED = 2 | 未指定转换矩阵。 |
| MATRIX_COEFFICIENT_FCC = 4 | FCC转换矩阵。 |
| MATRIX_COEFFICIENT_BT601_625 = 5 | BT601_625转换矩阵。 |
| MATRIX_COEFFICIENT_BT601_525 = 6 | BT601_525转换矩阵。 |
| MATRIX_COEFFICIENT_SMPTE_ST240 = 7 | SMPTE_ST240转换矩阵。 |
| MATRIX_COEFFICIENT_YCGCO = 8 | YCGCO转换矩阵。 |
| MATRIX_COEFFICIENT_BT2020_NCL = 9 | BT2020_NCL转换矩阵。 |
| MATRIX_COEFFICIENT_BT2020_CL = 10 | BT2020_CL转换矩阵。 |
| MATRIX_COEFFICIENT_SMPTE_ST2085 = 11 | SMPTE_ST2085转换矩阵。 |
| MATRIX_COEFFICIENT_CHROMATICITY_NCL = 12 | CHROMATICITY_NCL转换矩阵。 |
| MATRIX_COEFFICIENT_CHROMATICITY_CL = 13 | CHROMATICITY_CL转换矩阵。 |
| MATRIX_COEFFICIENT_ICTCP = 14 | ICTCP转换矩阵。 |

### OH_AVCLevel

```
enum OH_AVCLevel
```

**描述**

AVC级别。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| AVC_LEVEL_1 = 0 | 级别1 |
| AVC_LEVEL_1b = 1 | 级别1b |
| AVC_LEVEL_11 = 2 | 级别1.1 |
| AVC_LEVEL_12 = 3 | 级别1.2 |
| AVC_LEVEL_13 = 4 | 级别1.3 |
| AVC_LEVEL_2 = 5 | 级别2 |
| AVC_LEVEL_21 = 6 | 级别2.1 |
| AVC_LEVEL_22 = 7 | 级别2.2 |
| AVC_LEVEL_3 = 8 | 级别3 |
| AVC_LEVEL_31 = 9 | 级别3.1 |
| AVC_LEVEL_32 = 10 | 级别3.2 |
| AVC_LEVEL_4 = 11 | 级别4 |
| AVC_LEVEL_41 = 12 | 级别4.1 |
| AVC_LEVEL_42 = 13 | 级别4.2 |
| AVC_LEVEL_5 = 14 | 级别5 |
| AVC_LEVEL_51 = 15 | 级别5.1 |
| AVC_LEVEL_52 = 16 | 级别5.2 |
| AVC_LEVEL_6 = 17 | 级别6 |
| AVC_LEVEL_61 = 18 | 级别6.1 |
| AVC_LEVEL_62 = 19 | 级别6.2 |

### OH_HEVCLevel

```
enum OH_HEVCLevel
```

**描述**

HEVC级别。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| HEVC_LEVEL_1 = 0 | 级别1 |
| HEVC_LEVEL_2 = 1 | 级别2 |
| HEVC_LEVEL_21 = 2 | 级别2.1 |
| HEVC_LEVEL_3 = 3 | 级别3 |
| HEVC_LEVEL_31 = 4 | 级别3.1 |
| HEVC_LEVEL_4 = 5 | 级别4 |
| HEVC_LEVEL_41 = 6 | 级别4.1 |
| HEVC_LEVEL_5 = 7 | 级别5 |
| HEVC_LEVEL_51 = 8 | 级别5.1 |
| HEVC_LEVEL_52 = 9 | 级别5.2 |
| HEVC_LEVEL_6 = 10 | 级别6 |
| HEVC_LEVEL_61 = 11 | 级别6.1 |
| HEVC_LEVEL_62 = 12 | 级别6.2 |

### OH_VVCLevel

```
enum OH_VVCLevel
```

**描述**

VVC级别。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| VVC_LEVEL_1 = 16 | 级别1.0 |
| VVC_LEVEL_2 = 32 | 级别2.0 |
| VVC_LEVEL_21 = 35 | 级别2.1 |
| VVC_LEVEL_3 = 48 | 级别3.0 |
| VVC_LEVEL_31 = 51 | 级别3.1 |
| VVC_LEVEL_4 = 64 | 级别4.0 |
| VVC_LEVEL_41 = 67 | 级别4.1 |
| VVC_LEVEL_5 = 80 | 级别5.0 |
| VVC_LEVEL_51 = 83 | 级别5.1 |
| VVC_LEVEL_52 = 86 | 级别5.2 |
| VVC_LEVEL_6 = 96 | 级别6.0 |
| VVC_LEVEL_61 = 99 | 级别6.1 |
| VVC_LEVEL_62 = 102 | 级别6.2 |
| VVC_LEVEL_63 = 105 | 级别6.3 |
| VVC_LEVEL_155 = 255 | 级别15.5 |

### OH_MPEG2Level

```
enum OH_MPEG2Level
```

**描述**

MPEG2级别。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 17

| 枚举项 | 描述 |
| -- | -- |
| MPEG2_LEVEL_LOW = 0 | 低级别。 |
| MPEG2_LEVEL_MAIN = 1 | 主级别。 |
| MPEG2_LEVEL_HIGH_1440 = 2 | 高1440级别。 |
| MPEG2_LEVEL_HIGH = 3 | 高级别。 |

### OH_MPEG4Level

```
enum OH_MPEG4Level
```

**描述**

MPEG4级别。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 17

| 枚举项 | 描述 |
| -- | -- |
| MPEG4_LEVEL_0  = 0 | 级别0 |
| MPEG4_LEVEL_0B = 1 | 级别0B。 |
| MPEG4_LEVEL_1  = 2 | 级别1。 |
| MPEG4_LEVEL_2  = 3 | 级别2。 |
| MPEG4_LEVEL_3  = 4 | 级别3。 |
| MPEG4_LEVEL_3B = 5 | 级别3B。 |
| MPEG4_LEVEL_4  = 6 | 级别4。 |
| MPEG4_LEVEL_4A = 7 | 级别4A。 |
| MPEG4_LEVEL_5  = 8 | 级别5。 |
| MPEG4_LEVEL_6  = 9 | 级别6。 |

### OH_H263Level

```
enum OH_H263Level
```

**描述**

H.263级别。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 17

| 枚举项 | 描述 |
| -- | -- |
| H263_LEVEL_10 = 0 | 级别10。 |
| H263_LEVEL_20 = 1 | 级别20。 |
| H263_LEVEL_30 = 2 | 级别30。 |
| H263_LEVEL_40 = 3 | 级别40。 |
| H263_LEVEL_45 = 4 | 级别45。 |
| H263_LEVEL_50 = 5 | 级别50。 |
| H263_LEVEL_60 = 6 | 级别60。 |
| H263_LEVEL_70 = 7 | 级别70。 |

### OH_TemporalGopReferenceMode

```
enum OH_TemporalGopReferenceMode
```

**描述**

时域图片组参考模式。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ADJACENT_REFERENCE = 0 | 参考最近的短期参考帧。 |
| JUMP_REFERENCE = 1 | 参考最近的长期参考帧。 |
| UNIFORMLY_SCALED_REFERENCE = 2 | 均匀分层参考结构，在丢弃最高层级视频帧后，视频帧均匀分布。其中时域图片组个数必须为2的幂。 |

### OH_BitrateMode

```
enum OH_BitrateMode
```

**描述**

编码器的比特率模式。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| BITRATE_MODE_CBR = 0 | 恒定比特率模式。 |
| BITRATE_MODE_VBR = 1 | 可变比特率模式。 |
| BITRATE_MODE_CQ = 2 | 恒定质量模式。 |
| BITRATE_MODE_SQR = 3 | 质量稳定模式，仅支持H265（HEVC）。<br>**起始版本：** 20 |


## 函数说明

### OH_AVCodecOnError()

```
typedef void (*OH_AVCodecOnError)(OH_AVCodec *codec, int32_t errorCode, void *userData)
```

**描述**

当OH_AVCodec实例运行出错时，会调用来上报具体的错误信息的函数指针。

| 使用场景| 错误码 |
| -------- | -------- |
| 音频编解码 | AV_ERR_DRM_DECRYPT_FAILED：DRM解密失败。  |
| 视频编解码 | AV_ERROR_NO_MEMORY：系统资源不足。<br>AV_ERROR_UNKNOWN：未知错误，请通过具体日志分析。<br>AV_ERR_SERVICE_DIED：服务状态已消亡。  |
| 视频解码 | AV_ERR_VIDEO_UNSUPPORTED_COLOR_SPACE_CONVERSION：当前输入不支持色彩空间转换功能。  |
<!--RP1--><!--RP1End-->

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 9


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) *codec | OH_AVCodec实例。 |
|  int32_t errorCode | 特定错误代码。 |
|  void *userData | 开发者执行回调所依赖的数据。 |

### OH_AVCodecOnStreamChanged()

```
typedef void (*OH_AVCodecOnStreamChanged)(OH_AVCodec *codec, OH_AVFormat *format, void *userData)
```

**描述**

当视频解码输入码流分辨率或者视频编码输出码流的分辨率发生变化时，调用此函数指针报告新的流描述信息。<br>从API 15开始，支持音频解码时，码流采样率、声道数或者音频采样格式发生变化时，将调用此函数指针报告新的流描述信息，支持检测此变化的解码格式有：<!--RP3--><!--RP3End-->AAC，FLAC，MP3，VORBIS。<br>需要注意的是，OH_AVFormat指针的生命周期只有在函数指针被调用时才有效，调用结束后禁止继续访问。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 9


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) *codec | OH_AVCodec实例。 |
| [OH_AVFormat](_core.md#oh_avformat) *format | 新输出流描述信息。 |
|  void *userData | 开发者执行回调所依赖的数据。 |

### OH_AVCodecOnNeedInputData()

```
typedef void (*OH_AVCodecOnNeedInputData)(OH_AVCodec *codec, uint32_t index, OH_AVMemory *data, void *userData)
```

**描述**

当OH_AVCodec在运行过程中需要新的输入数据时，将调用此函数指针，并携带可用的缓冲区来填充新的输入数据。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [OH_AVCodecOnNeedInputBuffer](#oh_avcodeconneedinputbuffer)


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) *codec | OH_AVCodec实例。 |
|  uint32_t index | 与新可用的输入缓冲区相对应的索引。 |
|  [OH_AVMemory](_core.md#oh_avmemory) *data | 新的可用输入缓冲区。 |
|  void *userData | 开发者执行回调所依赖的数据。 |

### OH_AVCodecOnNewOutputData()

```
typedef void (*OH_AVCodecOnNewOutputData)(OH_AVCodec *codec, uint32_t index, OH_AVMemory *data,OH_AVCodecBufferAttr *attr, void *userData)
```

**描述**

当OH_AVCodec运行过程中生成新的输出数据时，将调用此函数指针，并携带包含新输出数据的缓冲区。需要注意的是，OH_AVCodecBufferAttr指针的生命周期仅在调用函数指针时有效，这将禁止调用结束后继续访问。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [OH_AVCodecOnNewOutputBuffer](#oh_avcodeconnewoutputbuffer)


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) *codec | OH_AVCodec实例。 |
|  uint32_t index | 与新输出缓冲区对应的索引。 |
|  [OH_AVMemory](_core.md#oh_avmemory) *data | 包含新输出数据的缓冲区。 |
| [OH_AVCodecBufferAttr](_o_h___a_v_codec_buffer_attr.md) *attr | 新输出缓冲区的说明。 |
|  void *userData | 开发者执行回调所依赖的数据。 |

### OH_AVCodecOnNeedInputBuffer()

```
typedef void (*OH_AVCodecOnNeedInputBuffer)(OH_AVCodec *codec, uint32_t index, OH_AVBuffer *buffer, void *userData)
```

**描述**

当OH_AVCodec在运行过程中需要新的输入数据时，将调用此函数指针，并携带可用的缓冲区来填充新的输入数据。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) *codec | OH_AVCodec实例。 |
|  uint32_t index | 与新可用的输入缓冲区相对应的索引。 |
|  [OH_AVBuffer](_core.md#oh_avbuffer) *buffer | 新的可用输入缓冲区。 |
|  void *userData | 开发者执行回调所依赖的数据。 |

### OH_AVCodecOnNewOutputBuffer()

```
typedef void (*OH_AVCodecOnNewOutputBuffer)(OH_AVCodec *codec, uint32_t index, OH_AVBuffer *buffer, void *userData)
```

**描述**

当OH_AVCodec运行过程中生成新的输出数据时，将调用此函数指针，并携带包含新输出数据的缓冲区。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) *codec | OH_AVCodec实例。 |
|  uint32_t index | 与新输出缓冲区对应的索引。 |
|  [OH_AVBuffer](_core.md#oh_avbuffer) *buffer | 包含新输出数据的缓冲区。 |
|  void *userData | 开发者执行回调所依赖的数据。 |

### OH_AVDataSourceReadAt()

```
typedef int32_t (*OH_AVDataSourceReadAt)(OH_AVBuffer *data, int32_t length, int64_t pos)
```

**描述**

函数指针定义，用于提供获取用户自定义媒体数据的能力。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVBuffer](_core.md#oh_avbuffer) *data | 要填充的缓冲区。 |
|  int32_t length | 要读取的数据长度。 |
|  int64_t pos | 从偏移量位置读取。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 读取到缓冲区的数据的实际长度。 |

### OH_AVDataSourceReadAtExt()

```
typedef int32_t (*OH_AVDataSourceReadAtExt)(OH_AVBuffer *data, int32_t length, int64_t pos, void *userData)
```

**描述**

函数指针定义，用于提供获取用户自定义媒体数据的能力。

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVBuffer](_core.md#oh_avbuffer) *data | 要填充的缓冲区。 |
|  int32_t length | 要读取的数据长度。 |
|  int64_t pos | 从偏移量位置读取。 |
|  void *userData | 用户自定义数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 读取到缓冲区的数据的实际长度。 |


