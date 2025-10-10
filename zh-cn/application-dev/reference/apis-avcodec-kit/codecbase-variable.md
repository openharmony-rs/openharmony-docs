# CodecBase

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @mr-chencxy-->
<!--Designer: @dpy2650--->
<!--Tester: @baotianhao-->
<!--Adviser: @w_Machine_cc-->

CodecBase模块提供用于音视频封装、解封装、编解码基础功能的常量字符串，开发者可通过下述表格，确认不同常量字符串的使用范围。

以下字符串常量在[native_avcodec_base.h](capi-native-avcodec-base-h.md#变量)中定义，开发者可在[native_avcodec_base.h](capi-native-avcodec-base-h.md#变量)中检索“常量字符串的名称”，查阅起始版本、取值范围等详细说明。

## 媒体编解码格式

用于描述媒体编解码格式的名字如下表。类型是常量字符串。

| 名称                                                         | 描述                                                   |
| ------------------------------------------------------------ | ------------------------------------------------------ |
| [OH_AVCODEC_MIMETYPE_AUDIO_AAC](#oh_avcodec_mimetype_audio_aac) | AAC音频编解码器的MIME类型。                            |
| [OH_AVCODEC_MIMETYPE_AUDIO_FLAC](#oh_avcodec_mimetype_audio_flac) | FLAC音频编解码器的MIME类型。                           |
| [OH_AVCODEC_MIMETYPE_AUDIO_OPUS](#oh_avcodec_mimetype_audio_opus) | OPUS音频编解码器的MIME类型。<!--Del-->（此规格暂未开放）<!--DelEnd-->        |
| [OH_AVCODEC_MIMETYPE_AUDIO_G711MU](#oh_avcodec_mimetype_audio_g711mu) | G711MU音频编解码器的MIME类型。                         |
| [OH_AVCODEC_MIMETYPE_AUDIO_G711A](#oh_avcodec_mimetype_audio_g711a) | G711A音频解码器的MIME类型。                         |
| [OH_AVCODEC_MIMETYPE_AUDIO_RAW](#oh_avcodec_mimetype_audio_raw) | RAW音频码流的MIME类型。                         |
| [OH_AVCODEC_MIMETYPE_AUDIO_VORBIS](#oh_avcodec_mimetype_audio_vorbis) | VORBIS音频解码器的MIME类型。                           |
| [OH_AVCODEC_MIMETYPE_AUDIO_MPEG](#oh_avcodec_mimetype_audio_mpeg) | MP3音频编解码器的MIME类型。                              |
| [OH_AVCODEC_MIMETYPE_AUDIO_VIVID](#oh_avcodec_mimetype_audio_vivid) | Audio Vivid音频解码器的MIME类型。<!--Del-->（此规格暂未开放）<!--DelEnd-->     |
| [OH_AVCODEC_MIMETYPE_AUDIO_AMR_NB](#oh_avcodec_mimetype_audio_amr_nb) | AMR_NB音频<!--RP4--><!--RP4End-->解码器的MIME类型。                           |
| [OH_AVCODEC_MIMETYPE_AUDIO_AMR_WB](#oh_avcodec_mimetype_audio_amr_wb) | AMR_WB音频<!--RP4--><!--RP4End-->解码器的MIME类型。                           |
| [OH_AVCODEC_MIMETYPE_AUDIO_APE](#oh_avcodec_mimetype_audio_ape) | APE音频解码器的MIME类型。                         |
| [OH_AVCODEC_MIMETYPE_VIDEO_VVC](#oh_avcodec_mimetype_video_vvc) | VVC(H.266)视频编解码器的MIME类型。                    |
| [OH_AVCODEC_MIMETYPE_VIDEO_HEVC](#oh_avcodec_mimetype_video_hevc) | HEVC(H.265)视频编解码器的MIME类型。                    |
| [OH_AVCODEC_MIMETYPE_VIDEO_AVC](#oh_avcodec_mimetype_video_avc) | AVC(H.264)视频编解码器的MIME类型。                     |
| [OH_AVCODEC_MIMETYPE_VIDEO_H263](#oh_avcodec_mimetype_video_h263) | H.263视频编解码器的MIME类型。                     |
| [OH_AVCODEC_MIMETYPE_VIDEO_MPEG4](#oh_avcodec_mimetype_video_mpeg4) | MPEG4视频编码的MIME类型，仅用于封装MPEG4视频码流使用。（API11废弃） |
| [OH_AVCODEC_MIMETYPE_VIDEO_MPEG4_PART2](#oh_avcodec_mimetype_video_mpeg4_part2) | 视频MPEG4 Part2编解码器的MIME类型。 |
| [OH_AVCODEC_MIMETYPE_VIDEO_MPEG2](#oh_avcodec_mimetype_video_mpeg2) | 视频MPEG2编解码器的MIME类型。 |
| [OH_AVCODEC_MIMETYPE_IMAGE_JPG](#oh_avcodec_mimetype_image_jpg) | JPG图片编码的MIME类型，仅用于封装JPG封面时使用。       |
| [OH_AVCODEC_MIMETYPE_IMAGE_PNG](#oh_avcodec_mimetype_image_png) | PNG图片编码的MIME类型，仅用于封装PNG封面时使用。       |
| [OH_AVCODEC_MIMETYPE_IMAGE_BMP](#oh_avcodec_mimetype_image_bmp) | BMP图片编码的MIME类型，仅用于封装BMP封面时使用。       |
| [OH_AVCODEC_MIMETYPE_SUBTITLE_WEBVTT](#oh_avcodec_mimetype_subtitle_webvtt) |WEBVTT字幕解封装器的MIME类型。                         |
| [OH_AVCODEC_MIMETYPE_SUBTITLE_SRT](#oh_avcodec_mimetype_subtitle_srt) |SRT字幕解封装器的MIME类型。                         |

## 媒体数据键值对

用于描述媒体数据的键值对查找表如下。键的类型是常量字符串，值的类型可以是int32_t/int64_t/float/double/char */uint8_t *。

使用以下key的主要接口是[OH_AVFormat](capi-core-oh-avformat.md)，通过以下key可以进行参数配置或查询。

### 能力查询专有的键值对

| 名称                                                         | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_FEATURE_PROPERTY_KEY_VIDEO_ENCODER_MAX_LTR_FRAME_COUNT](#oh_feature_property_key_video_encoder_max_ltr_frame_count)     | 在视频编码中获取长期参考帧的最大个数的键，值类型为int32_t。 |

音视频公共的键值对：

| 名称                                                         | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_MD_KEY_CODEC_CONFIG](#oh_md_key_codec_config)            | 编解码器特定数据的键，视频中表示传递SPS/PPS，音频中表示传递extraData，值类型为uint8_t\*。该键是可选的。 <!--Del-->（视频编解码此功能暂未支持）<!--DelEnd--> |
| [OH_MD_MAX_INPUT_BUFFER_COUNT](#oh_md_max_input_buffer_count) | 最大输入缓冲区个数的键，值类型为int32_t。该键是可选的。      |
| [OH_MD_MAX_OUTPUT_BUFFER_COUNT](#oh_md_max_output_buffer_count) | 最大输出缓冲区个数的键，值类型int32_t。该键是可选的。        |
| [OH_MD_KEY_BITRATE](#oh_md_key_bitrate)                      | 比特率的键，值类型为int64_t。该键用于音视频编码场景。在视频编码场景下该键是可选的。 |
| [OH_MD_KEY_PROFILE](#oh_md_key_profile)                      | 编码档次，值类型为int32_t，请参见[OH_AVCProfile](#oh_avcprofile)，[OH_HEVCProfile](#oh_hevcprofile)，[OH_AACProfile](#oh_aacprofile)。该键是可选的。 |
| [OH_MD_KEY_MAX_INPUT_SIZE](#oh_md_key_max_input_size)        | 设置解码输入码流大小最大值的键，值类型为int32_t。该键是可选的。           |
| [OH_MD_KEY_ENABLE_SYNC_MODE](#oh_md_key_enable_sync_mode)   | 使能音视频编解码同步模式的键，值类型为int32_t，1表示使能，0表示不使能，默认值为0。配置非0值将按照配置1处理，表示使能。该键是可选，在Configure阶段使用。 |


### 视频专有的键值对

| 名称                                                         | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_ED_KEY_TIME_STAMP](#oh_ed_key_time_stamp)                | 表示surfacebuffer时间戳的键，值类型为int64_t。该键是可选的。（API14废弃） |
| [OH_ED_KEY_EOS](#oh_ed_key_eos)                              | 表示surfacebuffer流结束符的键，值类型为int32_t。该键是可选的。（API14废弃）|
| [OH_MD_KEY_WIDTH](#oh_md_key_width)                          | 视频宽度的键，值类型为int32_t。                             |
| [OH_MD_KEY_HEIGHT](#oh_md_key_height)                        | 视频高度键，值类型为int32_t。                               |
| [OH_MD_KEY_PIXEL_FORMAT](#oh_md_key_pixel_format)            | 视频像素格式的键，值类型为int32_t，请参见[OH_AVPixelFormat](capi-native-avformat-h.md#oh_avpixelformat)。 |
| [OH_MD_KEY_FRAME_RATE](#oh_md_key_frame_rate)                | 视频帧率的键，值类型为double。该键是可选的。                 |
| [OH_MD_KEY_RANGE_FLAG](#oh_md_key_range_flag)                | 视频YUV值域标志的键，值类型为int32_t，1表示full range，0表示limited range。该键是可选的。 |
| [OH_MD_KEY_COLOR_PRIMARIES](#oh_md_key_color_primaries)      | 视频色域的键，值类型为int32_t，请参见[OH_ColorPrimary](#oh_colorprimary)，遵循H.273标准Table2。该键是可选的。 |
| [OH_MD_KEY_TRANSFER_CHARACTERISTICS](#oh_md_key_transfer_characteristics) | 视频传递函数的键，值类型为int32_t，请参见[OH_TransferCharacteristic](#oh_transfercharacteristic)，遵循H.273标准Table3。该键是可选的。 |
| [OH_MD_KEY_MATRIX_COEFFICIENTS](#oh_md_key_matrix_coefficients) | 视频矩阵系数的键，值类型为int32_t，请参见[OH_MatrixCoefficient](#oh_matrixcoefficient)，遵循H.273标准Table4。该键是可选的。 |
| [OH_MD_KEY_VIDEO_STRIDE](#oh_md_key_video_stride)       | 描述视频帧宽跨距的键，值类型为int32_t。该键是可选的。        |
| [OH_MD_KEY_VIDEO_SLICE_HEIGHT](#oh_md_key_video_slice_height)    | 描述视频帧高跨距的键，值类型为int32_t。该键是可选的。        |
| [OH_MD_KEY_VIDEO_PIC_WIDTH](#oh_md_key_video_pic_width)       | 描述视频帧真实宽度的键，值类型为int32_t。该键是可选的。        |
| [OH_MD_KEY_VIDEO_PIC_HEIGHT](#oh_md_key_video_pic_height)    | 描述视频帧真实高度的键，值类型为int32_t。该键是可选的。        |
| [OH_MD_KEY_VIDEO_ENCODE_BITRATE_MODE](#oh_md_key_video_encode_bitrate_mode) | 视频编码码率模式，值类型为int32_t，请参见[OH_BitrateMode](#oh_bitratemode-1)。该键是可选的。 |
| [OH_MD_KEY_QUALITY](#oh_md_key_quality)                      | 所需编码质量的键。值类型为int32_t，此键仅适用于配置在恒定质量模式下的编码器。该键是可选的。 |
| [OH_MD_KEY_REQUEST_I_FRAME](#oh_md_key_request_i_frame)      | 请求立即编码I帧的键。值类型为int32_t。该键是可选的。            |
| [OH_MD_KEY_I_FRAME_INTERVAL](#oh_md_key_i_frame_interval)    | 关键帧间隔的键，值类型为int32_t，单位为毫秒。该键是可选的且只用于视频编码。 |
| [OH_MD_KEY_VIDEO_ENCODER_ENABLE_TEMPORAL_SCALABILITY](#oh_md_key_video_encoder_enable_temporal_scalability)          | 使能分层编码的键，值类型为int32_t，1表示使能，0表示不使能，默认值为0。配置非0值将按照配置1处理，表示使能。该键是可选的且只用于视频编码，在Configure阶段使用。 |
| [OH_MD_KEY_VIDEO_ENCODER_TEMPORAL_GOP_SIZE](#oh_md_key_video_encoder_temporal_gop_size)       | 描述图片组基本层图片的间隔大小的键，值类型为int32_t，只在使能分层编码时生效。该键是可选的且只用于视频编码，在Configure阶段使用。 |
| [OH_MD_KEY_VIDEO_ENCODER_TEMPORAL_GOP_REFERENCE_MODE](#oh_md_key_video_encoder_temporal_gop_reference_mode)         | 描述图片组内参考模式的键，值类型为int32_t，请参见[OH_TemporalGopReferenceMode](#oh_temporalgopreferencemode-1)，只在使能分层编码时生效。该键是可选的且只用于视频编码，在Configure阶段使用。 |
| [OH_MD_KEY_VIDEO_ENCODER_LTR_FRAME_COUNT](#oh_md_key_video_encoder_ltr_frame_count)        | 描述长期参考帧个数的键，值类型为int32_t，必须在支持的值范围内使用。该键是可选的且只用于视频编码。|
| [OH_MD_KEY_VIDEO_ENCODER_PER_FRAME_MARK_LTR](#oh_md_key_video_encoder_per_frame_mark_ltr)  | 标记当前帧为长期参考帧的键，值类型为int32_t，1表示被标记，0表示未被标记，默认值为0。配置非0值将按照配置1处理，表示被标记。该键是可选的且只用于视频编码。 |
| [OH_MD_KEY_VIDEO_ENCODER_PER_FRAME_USE_LTR](#oh_md_key_video_encoder_per_frame_use_ltr)    | 	描述当前帧参考的长期参考帧帧的POC号的键，值类型为int32_t。该键是可选的且只用于视频编码。 |
| [OH_MD_KEY_VIDEO_PER_FRAME_IS_LTR](#oh_md_key_video_per_frame_is_ltr)      | 当前[OH_AVBuffer](capi-core-oh-avbuffer.md)中输出的码流对应的帧是否为长期参考帧的键，值类型为int32_t，1表示是LTR，0表示不是LTR，默认值为0。配置非0值将按照配置1处理，表示是LTR。该键是可选的且只用于视频编码。 |
| [OH_MD_KEY_VIDEO_PER_FRAME_POC](#oh_md_key_video_per_frame_poc)            | 描述帧的POC号的键，值类型为int32_t。该键是可选的且只用于视频编码。 |
| [OH_MD_KEY_VIDEO_ENCODER_QP_MAX](#oh_md_key_video_encoder_qp_max)       | 描述视频编码器允许的最大量化参数的键，值类型为int32_t。该键是可选的且只用于视频编码。 |
| [OH_MD_KEY_VIDEO_ENCODER_QP_MIN](#oh_md_key_video_encoder_qp_min)      | 描述视频编码器允许的最小量化参数的键，值类型为int32_t。该键是可选的且只用于视频编码。 |
| [OH_MD_KEY_VIDEO_ENCODER_QP_AVERAGE](#oh_md_key_video_encoder_qp_average)     |描述视频帧平均量化参数的键，值类型为int32_t。该键是可选的且只用于视频编码。  |
| [OH_MD_KEY_VIDEO_ENCODER_MSE](#oh_md_key_video_encoder_mse)     |描述视频帧平方误差的键，值类型为double。该键是可选的且只用于视频编码。  |
| [OH_MD_KEY_VIDEO_ENCODER_REPEAT_PREVIOUS_FRAME_AFTER](#oh_md_key_video_encoder_repeat_previous_frame_after)         | 如果在上一帧提交给编码器之后没有新的帧可用，则会以毫秒为单位重复提交最后一帧，值类型为int32_t。该键只用于视频编码Surface模式，在Configure阶段使用。 |
| [OH_MD_KEY_VIDEO_ENCODER_REPEAT_PREVIOUS_MAX_COUNT](#oh_md_key_video_encoder_repeat_previous_max_count)         | 描述编码器在没有新的帧可用的情况下，可以对之前的帧进行重复编码的最大次数，值类型为int32_t。该键仅在OH_MD_KEY_VIDEO_ENCODER_REPEAT_PREVIOUS_FRAME_AFTER可用时生效，在Configure阶段使用。|
| [OH_MD_KEY_SQR_FACTOR](#oh_md_key_sqr_factor)     | 描述SQR码控模式的质量参数，取值范围为[0, 51]（同编码量化参数QP），值越小，编码输出码率越大，质量越好，值类型为int32_t。该键值是可选的且只用于视频编码。 |
| [OH_MD_KEY_MAX_BITRATE](#oh_md_key_max_bitrate)     | 描述SQR码控模式的最大码率，使用[OH_AVCapability_GetEncoderBitrateRange](capi-native-avcapability-h.md#oh_avcapability_getencoderbitraterange)方法获取取值范围（同[OH_MD_KEY_BITRATE](#oh_md_key_bitrate)），单位bps，值类型为int64_t。该键值是可选的且只用于视频编码。 |
| [OH_MD_KEY_VIDEO_ENCODER_ROI_PARAMS](#oh_md_key_video_encoder_roi_params)    | 描述ROI编码参数，包括ROI区域和deltaQp，值类型为string。该键值是可选的且只用于视频编码。 |
| [OH_MD_KEY_VIDEO_ENCODER_ENABLE_PTS_BASED_RATECONTROL](#oh_md_key_video_encoder_enable_pts_based_ratecontrol)    | 使能基于显示时间戳(PTS)的码控模式的键，值类型为int32_t，1表示使能，0表示不使能，默认值为0。配置非0值将按照配置1处理，表示使能。该键值是可选的且只用于视频编码。如果使能，则必须在每个视频帧中携带PTS信息，并发送到编码器。在Configure阶段使用。 |
| [OH_MD_KEY_VIDEO_ENCODER_ENABLE_B_FRAME](#oh_md_key_video_encoder_enable_b_frame)    | 使能B帧编码的键，值类型为int32_t，1表示使能，0表示不使能。该键值是可选的且只用于视频编码，默认值为0，在Configure阶段使用。 |
| [OH_MD_KEY_VIDEO_ENCODER_MAX_B_FRAMES](#oh_md_key_video_encoder_max_b_frames)    | 在视频编码中获取B帧编码支持最大B帧数量的键，值类型为int32_t。 |
| [OH_MD_KEY_VIDEO_DECODER_OUTPUT_COLOR_SPACE](#oh_md_key_video_decoder_output_color_space)    | 设置视频解码器输出色彩空间的键，值类型为int32_t。 支持的值为OH_COLORSPACE_BT709_LIMIT。|
| [OH_MD_KEY_ROTATION](#oh_md_key_rotation)                    | surface旋转角度的键。值类型为int32_t：应为{0, 90, 180, 270}，默认值为0。该键只在视频解码Surface模式下使用。该键是可选的。 |
| [OH_MD_KEY_SCALING_MODE](#oh_md_key_scaling_mode)            | 视频缩放模式，值类型为int32_t，请参见[OH_ScalingMode](#oh_scalingmode)。该键是可选的且只用于视频解码Surface模式。建议直接调用[OH_NativeWindow_NativeWindowSetScalingModeV2](../apis-arkgraphics2d/capi-external-window-h.md#oh_nativewindow_nativewindowsetscalingmodev2)接口进行设置。（API14废弃）|
| [OH_MD_KEY_VIDEO_CROP_TOP](#oh_md_key_video_crop_top)       | 描述裁剪矩形顶部坐标(y)值的键，值类型为int32_t。该键是可选的且只用于视频解码。 |
| [OH_MD_KEY_VIDEO_CROP_BOTTOM](#oh_md_key_video_crop_bottom)        | 描述裁剪矩形底部坐标(y)值的键，值类型为int32_t。该键是可选的且只用于视频解码。 |
| [OH_MD_KEY_VIDEO_CROP_LEFT](#oh_md_key_video_crop_left)     | 描述裁剪矩形左坐标(x)值的键，值类型为int32_t。该键是可选的且只用于视频解码。 |
| [OH_MD_KEY_VIDEO_CROP_RIGHT](#oh_md_key_video_crop_right)     | 描述裁剪矩形右坐标(x)值的键，值类型为int32_t。该键是可选的且只用于视频解码。 |
| [OH_MD_KEY_VIDEO_ENABLE_LOW_LATENCY](#oh_md_key_video_enable_low_latency)   | 使能低时延视频解码的键，值类型为int32_t，1表示使能，0表示不使能，默认值为0。配置非0值将按照配置1处理，表示使能。该键是可选，在Configure阶段使用。 |
| [OH_MD_KEY_VIDEO_DECODER_OUTPUT_ENABLE_VRR](#oh_md_key_video_decoder_output_enable_vrr)     | 解码器是否打开视频可变帧率功能的键，值类型为int32_t。该键是可选的且只用于视频解码。 |
| [OH_MD_KEY_VIDEO_DECODER_BLANK_FRAME_ON_SHUTDOWN](#oh_md_key_video_decoder_blank_frame_on_shutdown)   | 用于指定视频解码器关闭时是否输出空白帧的键，值类型为int32_t，1表示使能，0表示不使能，默认值为0。配置非0值将按照配置1处理，表示使能。该键是可选的且仅用于视频解码Surface模式。 |


### 音频专有的键值对

| 名称                                                         | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_MD_KEY_AUDIO_SAMPLE_FORMAT](#oh_md_key_audio_sample_format) | 音频原始格式的键，值类型为int32_t。请参见[OH_BitsPerSample](#oh_bitspersample-1)。|
| [OH_MD_KEY_AUD_CHANNEL_COUNT](#oh_md_key_aud_channel_count)  | 音频通道计数键，值类型为int32_t。                           |
| [OH_MD_KEY_AUD_SAMPLE_RATE](#oh_md_key_aud_sample_rate)      | 音频采样率键，值类型为int32_t。                             |
| [OH_MD_KEY_AUDIO_COMPRESSION_LEVEL](#oh_md_key_audio_compression_level) | 音频编解码压缩水平的键，只在音频编码使用，值类型为int32_t。该键是可选的。     |
| [OH_MD_KEY_CHANNEL_LAYOUT](#oh_md_key_channel_layout)        | 所需编码通道布局的键。值类型为int64_t，此键仅适用于编码器。请参见[OH_AudioChannelLayout](capi-native-audio-channel-layout-h.md#oh_audiochannellayout)。  |
| [OH_MD_KEY_BITS_PER_CODED_SAMPLE](#oh_md_key_bits_per_coded_sample) | 每个编码样本位数的键，值类型为int32_t。该键是可选的。<br>API 20前，FLAC编码必须设置此参数，设置为1即可；未设置此参数配置FLAC编码器时，调用OH_AudioCodec_Configure会返回错误码AV_ERR_INVALID_VAL。该值无实际作用，不会影响编码结果。从API 20开始，无需设置此参数。|
| [OH_MD_KEY_SBR](#oh_md_key_sbr)                              | aac sbr模式的键，值类型为int32_t，aac编码器支持。该键是可选的。 |
| [OH_MD_KEY_COMPLIANCE_LEVEL](#oh_md_key_compliance_level)    | flac兼容性等级的键，值类型为int32_t，仅在音频编码使用。该键是可选的。          |
| [OH_MD_KEY_AAC_IS_ADTS](#oh_md_key_aac_is_adts)              | aac格式的键，aac格式分为ADTS格式和LATM格式。值类型为int32_t，aac解码器支持。该键是可选的。  |
| [OH_MD_KEY_IDENTIFICATION_HEADER](#oh_md_key_identification_header) | vorbis标识头的键，值类型为uint8_t\*，仅vorbis解码器支持。该键是可选的。 |
| [OH_MD_KEY_SETUP_HEADER](#oh_md_key_setup_header)            | vorbis设置头的键，值类型为uint8_t\*，仅vorbis解码器支持。该键是可选的。 |
| [OH_MD_KEY_AUDIO_OBJECT_NUMBER](#oh_md_key_audio_object_number) | 音频对象数目的键，值类型为int32_t，只有Audio Vivid解码使用。该键是可选的。            |
| [OH_MD_KEY_AUDIO_VIVID_METADATA](#oh_md_key_audio_vivid_metadata) | Audio Vivid元数据的键，值类型为uint8_t\*，只有Audio Vivid解码使用。该键是可选的。     |

### 封装/解封装专有的键值对

| 名称                                                         | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_MD_KEY_VIDEO_IS_HDR_VIVID](#oh_md_key_video_is_hdr_vivid) | 媒体文件中的视频轨是否为HDR Vivid的键，支持封装和解封装，值类型为int32_t。该键是可选的。  |
| [OH_MD_KEY_START_TIME](#oh_md_key_start_time) | 媒体文件中第一帧起始位置开始时间的键，以微秒为单位，值类型为int64_t。该键是可选的。            |
| [OH_MD_KEY_TRACK_START_TIME](#oh_md_key_track_start_time) | 轨道开始时间的键，以微秒为单位，值类型为int64_t。该键是可选的。            |
| [OH_MD_KEY_TRACK_TYPE](#oh_md_key_track_type)                | 轨道媒体类型的键，值类型为int32_t，请参见[OH_MediaType](#oh_mediatype-1)。该键是可选的。 |
| [OH_MD_KEY_DURATION](#oh_md_key_duration)                    | 媒体文件持续时间的键，值类型为int64_t。该键是可选的。                  |
| [OH_MD_KEY_TITLE](#oh_md_key_title)                          | 媒体文件标题的键，值类型为string。该键是可选的。               |
| [OH_MD_KEY_ARTIST](#oh_md_key_artist)                        | 艺术家的键，值类型为string。该键是可选的。             |
| [OH_MD_KEY_ALBUM](#oh_md_key_album)                          | 专辑的媒体文件的键，值类型为string。该键是可选的。               |
| [OH_MD_KEY_ALBUM_ARTIST](#oh_md_key_album_artist)            | 专辑艺术家的键，值类型为string。该键是可选的。               |
| [OH_MD_KEY_DATE](#oh_md_key_date)                            | 媒体文件日期的键，值类型为string，例如2024年。该键是可选的。    |
| [OH_MD_KEY_COMMENT](#oh_md_key_comment)                      | 媒体文件注释的键，值类型为string。该键是可选的。               |
| [OH_MD_KEY_GENRE](#oh_md_key_genre)                          | 媒体文件流派的键，值类型为string。该键是可选的。               |
| [OH_MD_KEY_COPYRIGHT](#oh_md_key_copyright)                  | 媒体文件版权的键，值类型为string。该键是可选的。               |
| [OH_MD_KEY_LANGUAGE](#oh_md_key_language)                    | 媒体文件语言的键，值类型为string。该键是可选的。               |
| [OH_MD_KEY_DESCRIPTION](#oh_md_key_description)              | 媒体文件描述的键，值类型为string。该键是可选的。               |
| [OH_MD_KEY_LYRICS](#oh_md_key_lyrics)                        | 媒体文件歌词的键，值类型为string。该键是可选的。               |
| [OH_MD_KEY_TRACK_COUNT](#oh_md_key_track_count)              | 媒体文件轨道数量的键，值类型为int32_t。该键是可选的。         |
| [OH_MD_KEY_BUFFER_DURATION](#oh_md_key_buffer_duration) | AVBuffer中携带的音视频或字幕的sample对应的持续时间的键，以微秒为单位，值类型为int64_t。该键是可选的。            |
| [OH_MD_KEY_DECODING_TIMESTAMP](#oh_md_key_decoding_timestamp) | AVBuffer中携带的音视频或字幕的sample对应的解码时间戳的键，以微秒为单位，值类型为int64_t。该键是可选的。            |
| [OH_MD_KEY_CODEC_MIME](#oh_md_key_codec_mime)                | 编解码器[MIME](#媒体编解码格式)类型的键，值类型为string。该键是可选的。         |
| [OH_MD_KEY_VIDEO_SAR](#oh_md_key_video_sar)                  | 样本长宽比的键，值类型为double。 |
| [OH_MD_KEY_CREATION_TIME](#oh_md_key_creation_time)          | 媒体文件创建时间的元数据，值类型为string。 |
| [OH_MD_KEY_REFERENCE_TRACK_IDS](#oh_md_key_reference_track_ids)          | 媒体文件轨道间参考、被参考关系，值类型为int32_t\*。 |
| [OH_MD_KEY_TRACK_REFERENCE_TYPE](#oh_md_key_track_reference_type)          | 媒体文件辅助轨类型，值类型为string。 |
| [OH_MD_KEY_TRACK_DESCRIPTION](#oh_md_key_track_description)          | 媒体文件辅助轨描述信息，值类型为string。 |
| [OH_MD_KEY_ENABLE_MOOV_FRONT](#oh_md_key_enable_moov_front)          | 媒体文件moov元数据是否前置标志，值类型为int32_t。|