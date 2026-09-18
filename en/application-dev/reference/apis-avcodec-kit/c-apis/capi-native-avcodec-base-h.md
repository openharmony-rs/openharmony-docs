# native_avcodec_base.h

## Overview

Declare the Native API used for audio and video muxer, demuxer and basic encoding and decoding functions.

**Library**: libnative_media_codecbase.so

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 9

**Related module**: [CodecBase](capi-codecbase.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVCodecAsyncCallback](capi-codecbase-oh-avcodecasynccallback.md) | OH_AVCodecAsyncCallback | The struct defines all the asynchronous callback function pointers of an OH_AVCodec instance. To ensure the normal running of OH_AVCodec, you must register the instance of this struct with the OH_AVCodec instance and process the information reported by the callback function. |
| [OH_AVCodecCallback](capi-codecbase-oh-avcodeccallback.md) | OH_AVCodecCallback | The struct defines all the asynchronous callback function pointers of an OH_AVCodec instance. To ensure the normal running of OH_AVCodec, you must register the instance of this struct with the OH_AVCodec instance and process the information reported by the callback function. |
| [OH_AVDataSource](capi-codecbase-oh-avdatasource.md) | OH_AVDataSource | The struct describes a user-defined data source. |
| [OH_AVDataSourceExt](capi-codecbase-oh-avdatasourceext.md) | OH_AVDataSourceExt | The struct describes a user-defined data source. User-defined data can be passed to its callback functions through the **userData** parameter. |
| [NativeWindow](capi-codecbase-nativewindow.md) | OHNativeWindow | Describes a native object for the graphics interface. |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) | OH_AVCodec | Describes a native object for the audio and video codec interface. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_MediaType](#oh_mediatype) | OH_MediaType | Enumerates the media types. |
| [OH_AACProfile](#oh_aacprofile) | OH_AACProfile | Enumerates the AAC profiles. |
| [OH_AVCProfile](#oh_avcprofile) | OH_AVCProfile | Enumerates the AVC profiles. |
| [OH_HEVCProfile](#oh_hevcprofile) | OH_HEVCProfile | Enumerates the HEVC profiles. |
| [OH_VVCProfile](#oh_vvcprofile) | OH_VVCProfile | Enumerates the VVC profiles. |
| [OH_MPEG2Profile](#oh_mpeg2profile) | OH_MPEG2Profile | Enumerates the MPEG2 profiles. |
| [OH_MPEG4Profile](#oh_mpeg4profile) | OH_MPEG4Profile | Enumerates the MPEG4 profiles. |
| [OH_H263Profile](#oh_h263profile) | OH_H263Profile | Enumerates the H.263 profiles. |
| [OH_VC1Profile](#oh_vc1profile) | OH_VC1Profile | Enumerates the VC-1 profiles. |
| [OH_AV1Profile](#oh_av1profile) | OH_AV1Profile | AV1 profile. |
| [OH_VP9Profile](#oh_vp9profile) | OH_VP9Profile | VP9 profile. |
| [OH_WVC1Profile](#oh_wvc1profile) | OH_WVC1Profile | WVC1 profile. |
| [OH_WMV3Profile](#oh_wmv3profile) | OH_WMV3Profile | Enumerates the WMV3 profiles. |
| [OH_AVOutputFormat](#oh_avoutputformat) | OH_AVOutputFormat | Enumerates the output file formats supported by a muxer. |
| [OH_AVSeekMode](#oh_avseekmode) | OH_AVSeekMode | Enumerates the seek modes. |
| [OH_ScalingMode](#oh_scalingmode) | OH_ScalingMode | Enumerates the scaling modes. This enum is used only in surface mode.(Deprecated in API14) |
| [OH_BitsPerSample](#oh_bitspersample) | OH_BitsPerSample | Enumerates the number of audio bits for each coded sample. |
| [OH_ColorPrimary](#oh_colorprimary) | OH_ColorPrimary | Enumerates the primary colors. This enum is used for both encoding and decoding. |
| [OH_TransferCharacteristic](#oh_transfercharacteristic) | OH_TransferCharacteristic | Enumerates the transfer characteristics. This enum is used for both encoding and decoding. |
| [OH_MatrixCoefficient](#oh_matrixcoefficient) | OH_MatrixCoefficient | Enumerates the matrix coefficients. This enum is used for both encoding and decoding. |
| [OH_AVCLevel](#oh_avclevel) | OH_AVCLevel | Enumerates the AVC levels. |
| [OH_HEVCLevel](#oh_hevclevel) | OH_HEVCLevel | Enumerates the HEVC levels. |
| [OH_VVCLevel](#oh_vvclevel) | OH_VVCLevel | Enumerates the VVC levels. |
| [OH_MPEG2Level](#oh_mpeg2level) | OH_MPEG2Level | Enumerates the MPEG2 levels. |
| [OH_MPEG4Level](#oh_mpeg4level) | OH_MPEG4Level | Enumerates the MPEG4 levels. |
| [OH_H263Level](#oh_h263level) | OH_H263Level | Enumerates the H.263 levels. |
| [OH_VC1Level](#oh_vc1level) | OH_VC1Level | Enumerates the VC-1 levels. |
| [OH_AV1Level](#oh_av1level) | OH_AV1Level | AV1 level. |
| [OH_VP9Level](#oh_vp9level) | OH_VP9Level | VP9 level. |
| [OH_WVC1Level](#oh_wvc1level) | OH_WVC1Level | WVC1 level. |
| [OH_WMV3Level](#oh_wmv3level) | OH_WMV3Level | Enumerates the WMV3 levels. |
| [OH_TemporalGopReferenceMode](#oh_temporalgopreferencemode) | OH_TemporalGopReferenceMode | Enumerates the reference modes of temporal image groups. |
| [OH_BitrateMode](#oh_bitratemode) | OH_BitrateMode | Enumerates the bit rate modes of an encoder. |
| [OH_FrameRetentionMode](#oh_frameretentionmode) | OH_FrameRetentionMode | The video decoding frame retention mode. |
| [OH_AudioEncoderPTSMode](#oh_audioencoderptsmode) | OH_AudioEncoderPTSMode | The PTS mode of audio encoder. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_AVCodecOnError)(OH_AVCodec *codec, int32_t errorCode, void *userData)](#oh_avcodeconerror) | OH_AVCodecOnError | Defines the pointer to the function that is called to report error information when an error occurs during the running of an OH_AVCodec instance. 
\| Use Case\| Error Code\|
\| -------- \| -------- \|
\| Audio encoding/decoding\| **AV_ERR_DRM_DECRYPT_FAILED**: DRM decryption failed. \|
\| Video encoding/decoding\| **AV_ERROR_NO_MEMORY**: System resources are insufficient.<br>**AV_ERROR_UNKNOWN**: An unknown error occurs. Analyze the error based on specific logs.<br>**AV_ERR_SERVICE_DIED**: The service is dead. \|
\| Video decoding\| **AV_ERR_VIDEO_UNSUPPORTED_COLOR_SPACE_CONVERSION**: The current input does not support CSC. \| <!--RP1--><!--RP1End--> |
| [typedef void (\*OH_AVCodecOnStreamChanged)(OH_AVCodec *codec, OH_AVFormat *format, void *userData)](#oh_avcodeconstreamchanged) | OH_AVCodecOnStreamChanged | Defines the pointer to the function that is called to report the new stream description when the resolution of the input video stream being decoded or the output video stream that has been encoded changes.<br> Starting from API version 15, this function pointer is called to report the new stream description when the stream sampling rate, number of audio channels, or audio sampling format changes during audio decoding. The decoding formats that can detect these changes include <!--RP3--><!--RP3End-->AAC, FLAC, MP3, and VORBIS.<br> Note that the lifecycle of the pointer to the OH_AVFormat instance is valid only when the function pointer is being called. Do not access the pointer to the instance after the function pointer is called. |
| [typedef void (\*OH_AVCodecOnNeedInputData)(OH_AVCodec *codec, uint32_t index, OH_AVMemory *data, void *userData)](#oh_avcodeconneedinputdata) | OH_AVCodecOnNeedInputData | Defines the pointer to the function that is called when new input data is required during the running of an OH_AVCodec instance. The function carries a buffer to fill in new input data.(Deprecated in API11) |
| [typedef void (\*OH_AVCodecOnNewOutputData)(OH_AVCodec *codec, uint32_t index, OH_AVMemory *data, OH_AVCodecBufferAttr *attr, void *userData)](#oh_avcodeconnewoutputdata) | OH_AVCodecOnNewOutputData | Defines the pointer to the function that is called when new output data is generated during the running of an OH_AVCodec instance. The function carries a buffer filled with new output data. Note that the lifecycle of the pointer to the OH_AVCodecBufferAttr instance is valid only when the function pointer is being called. Do not access the pointer to the instance after the function pointer is called.(Deprecated in API11) |
| [typedef void (\*OH_AVCodecOnNeedInputBuffer)(OH_AVCodec *codec, uint32_t index, OH_AVBuffer *buffer, void *userData)](#oh_avcodeconneedinputbuffer) | OH_AVCodecOnNeedInputBuffer | Defines the pointer to the function that is called when new input data is required during the running of an OH_AVCodec instance. The function carries a buffer to fill in new input data. |
| [typedef void (\*OH_AVCodecOnNewOutputBuffer)(OH_AVCodec *codec, uint32_t index, OH_AVBuffer *buffer, void *userData)](#oh_avcodeconnewoutputbuffer) | OH_AVCodecOnNewOutputBuffer | Defines the pointer to the function that is called when new output data is generated during the running of an OH_AVCodec instance. The function carries a buffer filled with new output data. |
| [typedef int32_t (\*OH_AVDataSourceReadAt)(OH_AVBuffer *data, int32_t length, int64_t pos)](#oh_avdatasourcereadat) | OH_AVDataSourceReadAt | Defines a function pointer used to provide the capability of obtaining user-defined media data. |
| [typedef int32_t (\*OH_AVDataSourceReadAtExt)(OH_AVBuffer *data, int32_t length, int64_t pos, void *userData)](#oh_avdatasourcereadatext) | OH_AVDataSourceReadAtExt | Defines a function pointer used to provide the capability of obtaining user-defined media data. |

### Variable

| Name | Description |
| -- | -- |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_AVC | Pointer to the key that describes the MIME type of the AVC (H.264) video codec.<br>**Since**: 9 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_AAC | Pointer to the key that describes the MIME type of the AAC audio codec.<br>**Since**: 9 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_FLAC | Pointer to the key that describes the MIME type of the FLAC audio codec.<br>**Since**: 10 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_VORBIS | Pointer to the key that describes the MIME type of the Vorbis audio decoder.<br>**Since**: 10 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_MPEG | Pointer to the key that describes the MIME type of the MP3 audio codec.<br>**Since**: 10 |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_HEVC | Pointer to the key that describes the MIME type of the HEVC (H.265) video codec.<br>**Since**: 10 |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_MPEG4 | Pointer to the key that describes the MIME type of the MPEG4 video encoder, which is used only for multiplexing MPEG4 video streams.<br>**Since**: 10<br>**Deprecated**: 11<br>**Replaced by**: OH_AVCODEC_MIMETYPE_VIDEO_MPEG4_PART2 |
| const char *OH_AVCODEC_MIMETYPE_IMAGE_JPG | Pointer to the key that describes the MIME type of the JPG image encoder, which is used only for multiplexing JPG covers.<br>**Since**: 10 |
| const char *OH_AVCODEC_MIMETYPE_IMAGE_PNG | Pointer to the key that describes the MIME type of the PNG image encoder, which is used only for multiplexing PNG covers.<br>**Since**: 10 |
| const char *OH_AVCODEC_MIMETYPE_IMAGE_BMP | Pointer to the key that describes the MIME type of the BMP image encoder, which is used only for multiplexing BMP covers.<br>**Since**: 10 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_VIVID | Pointer to the key that describes the MIME type of the Audio Vivid audio codec.<br>**Since**: 11 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_AMR_NB | Pointer to the key that describes the MIME type of the AMR-NB audio <!--RP4--><!--RP4End--> decoder.<br>**Since**: 11 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_AMR_WB | Pointer to the key that describes the MIME type of the AMR-WB audio <!--RP4--><!--RP4End--> decoder.<br>**Since**: 11 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_OPUS | Pointer to the key that describes the MIME type of the Opus audio codec.<br>**Since**: 11 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_G711MU | Pointer to the key that describes the MIME type of the G.711 mu-law audio codec.<br>**Since**: 11 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_APE | Pointer to the key that describes the MIME type of the APE audio decoder.<br>**Since**: 12 |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_VVC | Pointer to the key that describes the MIME type of the VVC (H.266) video codec.<br>**Since**: 12 |
| const char *OH_AVCODEC_MIMETYPE_SUBTITLE_SRT | Pointer to the key that describes the MIME type of the SRT subtitle demuxer.<br>**Since**: 12 |
| const char *OH_AVCODEC_MIMETYPE_SUBTITLE_WEBVTT | Pointer to the key that describes the MIME type of the WEBVTT subtitle demuxer.<br>**Since**: 12 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_RAW | Pointer to the key that describes the MIME type of raw audio streams.<br>**Since**: 18 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_G711A | Pointer to the key that describes the MIME type of the G.711 a-law audio decoder.<br>**Since**: 20 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_ALAC | Pointer to the key that describes the MIME type of the Apple Lossless Audio Codec (ALAC) audio decoder.<br>**Since**: 22 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_AC3 | Pointer to the key that describes the MIME type of the Dolby Audio Coding 3 (AC 3) audio decoder.<br>**Since**: 22 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_EAC3 | Pointer to the key that describes the MIME type of the Enhanced AC-3 (EAC3) audio decoder.<br>**Since**: 22 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_WMAV1 | Pointer to the key that describes the MIME type of the Windows Media Audio (WMA) V1 audio decoder.<br>**Since**: 22 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_WMAV2 | Pointer to the key that describes the MIME type of the WMA V2 audio decoder.<br>**Since**: 22 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_WMAPRO | Pointer to the key that describes the MIME type of the WMA Pro audio decoder.<br>**Since**: 22 |
| const char *OH_MD_KEY_BLOCK_ALIGN | Size of the audio data block, in bytes. The value type is int32_t. This key is used only for WMA (V1, V2, and PRO) decoders.<br> The allowed MIME types include **OH_AVCODEC_MIMETYPE_AUDIO_WMAV1**, **OH_AVCODEC_MIMETYPE_AUDIO_WMAV2**, and **<br>OH_AVCODEC_MIMETYPE_AUDIO_WMAPRO**.<br>**Since**: 22 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_GSM | Pointer to the key that describes the MIME type of the Global System for Mobile Communications (GSM) audio decoder.<br>**Since**: 22 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_GSM_MS | Pointer to the key that describes the MIME type of the GSM Microsoft variant (MS) audio decoder.<br>**Since**: 22 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_TWINVQ | Pointer to the key that describes the MIME type of the Transform-domain Weighted Interleave Vector Quantization (TWINVQ) audio decoder.<br>**Since**: 23 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_ILBC | Pointer to the key that describes the MIME type of the Internet Low Bitrate Codec (ILBC) audio decoder.<br>**Since**: 23 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_TRUEHD | Pointer to the key that describes the MIME type of the True High Definition (TRUEHD) audio decoder.<br>**Since**: 23 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_DVAUDIO | MIME type of the DVAUDIO (Digital Video Audio) audio decoder.<br>**Since**: 23 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_DTS | MIME type of the DTS (Digital Theater Systems) audio decoder.<br>**Since**: 23 |
| const char *OH_AVCODEC_MIMETYPE_AUDIO_COOK | MIME type of the Cook (RealAudio Cook) audio decoder.<br>**Since**: 23 |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_MPEG2 | Pointer to the key that describes the MIME type of the MPEG2 video codec.<br>**Since**: 17 |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_MPEG4_PART2 | Pointer to the key that describes the MIME type of the MPEG4 video encoder, which is used only for multiplexing MPEG4 video streams.<br>**Since**: 17 |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_H263 | Pointer to the key that describes the MIME type of the H.263 video codec.<br>**Since**: 17 |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_VC1 | Pointer to the key that describes the MIME type of the VC-1 video codec.<br>**Since**: 22 |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_AV1 | MIME type of the AV1 video codec.<br>**Since**: 23 |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_VP9 | MIME type of the VP9 video codec.<br>**Since**: 23 |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_VP8 | MIME type of the VP8 video codec.<br>**Since**: 23 |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_RV30 | MIME type of the RV30 video codec.<br>**Since**: 23 |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_RV40 | MIME type of the RV40 video codec.<br>**Since**: 23 |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_WVC1 | MIME type of the WVC1 video codec.<br>**Since**: 23 |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_DVVIDEO | MIME type of the DVVIDEO (Digital Video) video codec. Supports DV NTSC, DV PAL, and DVCPRO HD.<br>**Since**: 23 |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_RAWVIDEO | MIME type of the RAWVIDEO video codec.<br>**Since**: 23 |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_MPEG1 | MIME type of the MPEG1 video codec.<br>**Since**: 23 |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_CINEPAK | MIME type of the Cinepak video codec.<br>**Since**: 24 |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_MSVIDEO1 | Pointer to the key that describes the MIME type of the Microsoft Video 1 (MSVIDEO1) video codec.<br>**Since**: 22 |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_WMV3 | Pointer to the key that describes the MIME type of the WMV3 video codec.<br>**Since**: 22 |
| const char *OH_AVCODEC_MIMETYPE_VIDEO_MJPEG | Pointer to the key that describes the MIME type of the Motion JPEG (MJPEG) video codec.<br>**Since**: 22 |
| const char *OH_ED_KEY_TIME_STAMP | Pointer to the key that describes the surface buffer timestamp. The value is of the int64_t type.<br>**Since**: 9<br>**Deprecated**: 14 |
| const char *OH_ED_KEY_EOS | Pointer to the key that describes the end of stream for the surface buffer. The value type is int32_t.<br>**Since**: 9<br>**Deprecated**: 14 |
| const char *OH_MD_KEY_TRACK_TYPE | Pointer to the key that describes the track type in a media file. The value type is int32_t. For details, see [OH_MediaType](capi-native-avcodec-base-h.md#oh_mediatype).<br>**Since**: 9 |
| const char *OH_MD_KEY_CODEC_MIME | Pointer to the key that describes the MIME type of the codec. The value type is char *.<br>**Since**: 9 |
| const char *OH_MD_KEY_DURATION | Pointer to the key that describes the duration in a media file, in microseconds. The value type is int64_t.<br>**Since**: 9 |
| const char *OH_MD_KEY_BITRATE | Pointer to the key that describes the bit rate. The value type is int64_t. You can call {@link OH_AVCapability_GetEncoderBitrateRange} to obtain the value range.<br>**Since**: 9 |
| const char *OH_MD_KEY_MAX_INPUT_SIZE | Pointer to the key that describes the maximum size of an input stream to decode. The value type is int32_t.<br>**Since**: 9 |
| const char *OH_MD_KEY_WIDTH | Pointer to the key that describes the video width. The value type is int32_t.<br> For video encoding, this key is used to set the target encoding resolution. For video decoding, this key serves as a resolution hint for the decoder to pre-allocate internal buffers. The actual decoded output dimensions are provided by **OH_MD_KEY_VIDEO_PIC_WIDTH**. This key is mainly used to control memory allocation. You can call {@link OH_AVCapability_GetVideoWidthRange} to obtain the recommended value range. This API defines the decoding width range supported by the codec.<br>**Since**: 9 |
| const char *OH_MD_KEY_HEIGHT | Pointer to the key that describes the video height. The value type is int32_t.<br> For video encoding, this key is used to set the target encoding resolution. For video decoding, this key serves as a resolution hint for the decoder to pre-allocate internal buffers. The actual decoded output dimensions are provided by **OH_MD_KEY_VIDEO_PIC_HEIGHT**. This key is mainly used to control memory allocation. You can call {@link OH_AVCapability_GetVideoHeightRange} to obtain the recommended value range. This API defines the decoding height range supported by the codec.<br>**Since**: 9 |
| const char *OH_MD_KEY_PIXEL_FORMAT | Pointer to the key that describes the video pixel format. The value type is int32_t. For details, see {@link OH_AVPixelFormat}.<br>**Since**: 9 |
| const char *OH_MD_KEY_AUDIO_SAMPLE_FORMAT | Pointer to the key that describes the original audio format. The value type is int32_t. For details, see [OH_BitsPerSample](capi-native-avcodec-base-h.md#oh_bitspersample).<br>**Since**: 9 |
| const char *OH_MD_KEY_FRAME_RATE | Pointer to the key that describes the video frame rate. The value type is double. The value must be greater than **0**. You can call {@link OH_AVCapability_GetVideoFrameRateRange} to obtain the value range.<br>**Since**: 9 |
| const char *OH_MD_KEY_VIDEO_ENCODE_BITRATE_MODE | Pointer to the key that describes the video encoding bit rate mode. The value type is int32_t. For details, see [OH_BitrateMode](capi-native-avcodec-base-h.md#oh_bitratemode).<br>**Since**: 9 |
| const char *OH_MD_KEY_PROFILE | Pointer to the key that describes the encoding grading. The value type is int32_t. For details, see [OH_AVCProfile](capi-native-avcodec-base-h.md#oh_avcprofile), [OH_HEVCProfile](capi-native-avcodec-base-h.md#oh_hevcprofile), and [OH_AACProfile](capi-native-avcodec-base-h.md#oh_aacprofile). You can call {@link OH_AVCapability_GetSupportedProfiles} to obtain the supported profiles.<br>**Since**: 9 |
| const char *OH_MD_KEY_AUD_CHANNEL_COUNT | Pointer to the key that describes the number of audio channels. The value type is int32_t.<br>**Since**: 9 |
| const char *OH_MD_KEY_AUD_SAMPLE_RATE | Pointer to the key that describes the audio sampling rate. The value type is int32_t.<br>**Since**: 9 |
| const char *OH_MD_KEY_I_FRAME_INTERVAL | Pointer to the key that describes the key frame interval, in milliseconds. The value type is int32_t. This key is optional and is used only for video encoding.<br> A negative value means that only the first frame is a keyframe. The value **0** means that all frames are keyframes. A positive value means one keyframe every (frameRate * value)/1000 frames. The default value is **1000**.<br>**Since**: 9 |
| const char *OH_MD_KEY_VIDEO_TRANSFORM_TYPE | Key for video transform type, value type is int32_t, see {@link OH_NativeBuffer_TransformType}.<br>This key is used to set the surface transform for video decoders (surface mode).<br>If not specified, the default value is 0 ({@link NATIVEBUFFER_ROTATE_NONE}).<br>This key and {@link OH_MD_KEY_ROTATION} are mutually exclusive. If both are provided,<br>OH_MD_KEY_VIDEO_TRANSFORM_TYPE takes precedence.<br>Note that the degrees specified in {@link OH_NativeBuffer_TransformType} represent counter-clockwise rotation,<br>which are opposite to the direction of rotation defined by {@link OH_MD_KEY_ROTATION}.<br>The correspondence is:<br>- {@link NATIVEBUFFER_ROTATE_NONE} => same as OH_MD_KEY_ROTATION = 0<br>- {@link NATIVEBUFFER_ROTATE_90} => same as OH_MD_KEY_ROTATION = 270<br>- {@link NATIVEBUFFER_ROTATE_180} => same as OH_MD_KEY_ROTATION = 180<br>- {@link NATIVEBUFFER_ROTATE_270} => same as OH_MD_KEY_ROTATION = 90<br>**Since**: 22 |
| const char *OH_MD_KEY_ROTATION | Pointer to the key that describes the rotation angle of the surface, with a clockwise direction. The value type is int32_t, and the value range is {0, 90, 180, 270}. The default value is 0. This key is optional and is used only for video decoding in surface mode You are advised to use the **OH_MD_KEY_VIDEO_TRANSFORM_TYPE** key to set the rotation angle of the surface for video decoding.<br>**Since**: 9 |
| const char *OH_MD_KEY_RANGE_FLAG | Pointer to the key that describes the video YUV value range flag. The value type is int32_t. The value **1**<br>means a full range, and **0** means a limited range. The default value is **0**. If this parameter is set to a non- zero value, the value **1** is used.<br>**Since**: 10 |
| const char *OH_MD_KEY_COLOR_PRIMARIES | Pointer to the key that describes the video primary colors. The value type is int32_t. The default value is **COLOR_PRIMARY_UNSPECIFIED**. For details, see [OH_ColorPrimary](capi-native-avcodec-base-h.md#oh_colorprimary). The value complies with Table 2 in H.273.<br>**Since**: 10 |
| const char *OH_MD_KEY_TRANSFER_CHARACTERISTICS | Pointer to the key that describes the video transfer characteristics. The value type is int32_t. The default value is **TRANSFER_CHARACTERISTIC_UNSPECIFIED**. For details, see [OH_TransferCharacteristic](capi-native-avcodec-base-h.md#oh_transfercharacteristic). The value complies with Table 3 in H.273.<br>**Since**: 10 |
| const char *OH_MD_KEY_MATRIX_COEFFICIENTS | Pointer to the key that describes the video matrix coefficients. The value type is int32_t. The default value is **MATRIX_COEFFICIENT_UNSPECIFIED**. For details, see [OH_MatrixCoefficient](capi-native-avcodec-base-h.md#oh_matrixcoefficient). The value must comply with Table 4 in H.273.<br>**Since**: 10 |
| const char *OH_MD_KEY_REQUEST_I_FRAME | Pointer to the key that describes the request for immediate encoding of I-frames. The value type is int32_t. This key is used in {@link OH_VideoEncoder_SetParameter} or takes effect immediately with each frame.<br>**Since**: 10 |
| const char *OH_MD_KEY_QUALITY | Pointer to the key that describes the required encoding quality. The value type is int32_t. The default value is **50**. In H.264 and H.265 encoding scenarios, the value range can be obtained by calling {@link OH_AVCapability_GetEncoderQualityRange}. This key applies only to the encoder in constant quality mode.<br>**Since**: 10 |
| const char *OH_MD_KEY_CODEC_CONFIG | Pointer to the key that describes the codec-specific data. In the case of video, data carried in **SPS/PPS**<br>is transferred. In the case of audio, data carried in **extraData** is transferred. The value type is uint8_t\*.<br>**Since**: 10 |
| const char *OH_MD_KEY_TITLE | Pointer to the key that describes the title of a media file . The value type is char *.<br>**Since**: 10 |
| const char *OH_MD_KEY_ARTIST | Pointer to the key that describes the artist in a media file. The value type is char *.<br>**Since**: 10 |
| const char *OH_MD_KEY_ALBUM | Pointer to the key that describes the album in a media file. The value type is char *.<br>**Since**: 10 |
| const char *OH_MD_KEY_ALBUM_ARTIST | Pointer to the key that describes the album artist of the input media. The value type is char *.<br>**Since**: 10 |
| const char *OH_MD_KEY_DATE | Pointer to the key that describes the date in a media file, for example, 2024. The value type is char *.<br>**Since**: 10 |
| const char *OH_MD_KEY_COMMENT | Pointer to the key that describes the comment in a media file. The value type is char *.<br>**Since**: 10 |
| const char *OH_MD_KEY_GENRE | Pointer to the key that describes the genre in a media file. The value type is char *.<br>**Since**: 10 |
| const char *OH_MD_KEY_COPYRIGHT | Pointer to the key that describes the copyright of a media file. The value type is char *.<br>**Since**: 10 |
| const char *OH_MD_KEY_LANGUAGE | Pointer to the key that describes language of a media file. The value type is char *.<br>**Since**: 10 |
| const char *OH_MD_KEY_DESCRIPTION | Pointer to the key that describes the description of a media file. The value type is char *.<br>**Since**: 10 |
| const char *OH_MD_KEY_LYRICS | Pointer to the key that describes the lyrics in a media file. The value type is char *.<br>**Since**: 10 |
| const char *OH_MD_KEY_TRACK_COUNT | Pointer to the key that describes the number of tracks in a media file. The value type is int32_t.<br>**Since**: 10 |
| const char *OH_MD_KEY_CHANNEL_LAYOUT | Pointer to the key that describes the required encoding channel layout. The value type is int64_t. This key applies only to encoders. For details, see {@link OH_AudioChannelLayout}.<br>**Since**: 10 |
| const char *OH_MD_KEY_BITS_PER_CODED_SAMPLE | Pointer to the key that describes the number of bits per sample. The value type is int32_t.<br> In versions earlier than API version 20, this parameter must be set to **1** for FLAC encoding. Otherwise, {@link OH_AudioCodec_Configure} returns the error code {@link AV_ERR_INVALID_VAL}. However, this parameter has no actual effect and does not affect the encoding result.<br> Starting from API version 20, you do not need to set it anymore.<br>**Since**: 10 |
| const char *OH_MD_KEY_AAC_IS_ADTS | Pointer to the key that describes the AAC format, which can be ADTS or LATM. The value type is int32_t. The value **0** means the LATM format, and **1** means the ADTS format. This key is supported by AAC decoders.<br>**Since**: 10 |
| const char *OH_MD_KEY_SBR | Pointer to the key that describes the AAC SBR format. The value type is int32_t. This key applies to AAC encoders.<br>**Since**: 10 |
| const char *OH_MD_KEY_COMPLIANCE_LEVEL | Pointer to the key that describes the FLAC compliance level. The value type is int32_t. This key is used only for audio encoding.<br>**Since**: 10 |
| const char *OH_MD_KEY_IDENTIFICATION_HEADER | Pointer to the key that describes the vorbis identification header. The value type is uint8_t*. This key applies only to Vorbis decoders.<br>**Since**: 10 |
| const char *OH_MD_KEY_SETUP_HEADER | Pointer to the key that describes the vorbis setup header. The value type is uint8_t*. This key applies only to Vorbis decoders.<br>**Since**: 10 |
| const char *OH_MD_KEY_SCALING_MODE | Pointer to the key that describes the video scaling mode. The value type is int32_t. For details, see [OH_ScalingMode](capi-native-avcodec-base-h.md#oh_scalingmode). You are advised to set the scaling mode by calling {@link OH_NativeWindow_NativeWindowSetScalingModeV2}. This key is optional and is used only for video decoding in surface mode.<br>**Since**: 10<br>**Deprecated**: 14<br>**Replaced by**: OH_NativeWindow_NativeWindowSetScalingModeV2 |
| const char *OH_MD_MAX_INPUT_BUFFER_COUNT | Pointer to the key that describes the maximum number of input buffers. The value type is int32_t.<br>**Since**: 10 |
| const char *OH_MD_MAX_OUTPUT_BUFFER_COUNT | Pointer to the key that describes the maximum number of output buffers. The value type is int32_t.<br>**Since**: 10 |
| const char *OH_MD_KEY_AUDIO_COMPRESSION_LEVEL | Pointer to the key that describes the audio codec compression level. The value type is int32_t type. This key is used only for audio encoding.<br>**Since**: 11 |
| const char *OH_MD_KEY_VIDEO_IS_HDR_VIVID | Pointer to the key that specifies whether the video track in a media file is HDR Vivid. The value type is int32_t. This key is used for both multiplexing and demultiplexing.<br> The value **1** means the HDR Vivid video track, and **0** means other cases.<br>**Since**: 11 |
| const char *OH_MD_KEY_AUDIO_OBJECT_NUMBER | Pointer to the key that describes the number of audio objects. The value type is int32_t. This key is used for Audio Vivid.<br>**Since**: 11 |
| const char *OH_MD_KEY_AUDIO_VIVID_METADATA | Pointer to the key that describes the Audio Vivid metadata. The value type is uint8_t*. This key is used for Audio Vivid.<br>**Since**: 11 |
| const char *OH_FEATURE_PROPERTY_KEY_VIDEO_ENCODER_MAX_LTR_FRAME_COUNT | Pointer to the key that describes the maximum number of long-term reference (LTR) frames obtained during video encoding. The value type is int32_t.<br> You can use the API {@link OH_AVCapability_GetFeatureProperties} and the enumerated value<br>**VIDEO_ENCODER_LONG_TERM_REFERENCE** in {@link OH_AVCapabilityFeature} to query the maximum number.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_ENCODER_ENABLE_TEMPORAL_SCALABILITY | Pointer to the key that describes the enabled status of temporal scalability. The value type is int32_t. **1**<br>if enabled, **0** otherwise. The default value is **0**. If this parameter is set to a non-zero value, the value **<br>1** is used.<br> You can use the API {@link OH_AVCapability_IsFeatureSupported} and the enumerated value<br>**VIDEO_ENCODER_TEMPORAL_SCALABILITY** in {@link OH_AVCapabilityFeature}<br>to check whether the current video encoder supports temporal scalability.<br>For details, see {@link Temporally Scalable Video Coding}.<br> This key is optional and used only in the configuration phase of video encoding.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_ENCODER_TEMPORAL_GOP_SIZE | Pointer to the key that describes the size of a temporal image group. The value type is int32_t. This key is valid only when temporal scalability is enabled.<br> This key is optional and used only in the configuration phase of video encoding.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_ENCODER_TEMPORAL_GOP_REFERENCE_MODE | Pointer to the key that describes the reference mode in a temporal image group. The value type is int32_t. For details, see [OH_TemporalGopReferenceMode](capi-native-avcodec-base-h.md#oh_temporalgopreferencemode). This key is valid only when temporal scalability is enabled.<br> This key is optional and used only in the configuration phase of video encoding.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_ENCODER_TEMPORAL_LAYER_ID | Pointer to the key that describes the temporal layer ID in a group of pictures (GOP). The value type is int32_t.<br> Temporal layer ID **0** indicates the base layer. Temporal layer IDs **1** and above indicate enhancement layers. The maximum temporal layer ID is determined by **OH_MD_KEY_VIDEO_ENCODER_TEMPORAL_GOP_REFERENCE_MODE** and **OH_MD_KEY_VIDEO_ENCODER_TEMPORAL_GOP_SIZE**. Currently, this key is used only to query the temporal layer ID carried in **AVBuffer** output by the encoder. The process is as follows: 1. Use [OH_AVCodecOnNewOutputBuffer](capi-native-avcodec-base-h.md#oh_avcodeconnewoutputbuffer) or {@link OH_VideoEncoder_GetOutputBuffer} to<br>obtain the buffer instance (**AVBuffer**).<br>2. Use {@link OH_AVBuffer_GetParameter} to obtain the parameter instance (**OH_AVFormat**),<br>which does not contain basic properties.<br>3. Use {@link OH_AVFormat_GetIntValue} and this key to obtain the temporal layer ID of the corresponding frame.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_VIDEO_ENCODER_PREPROC_DOWNSAMPLING_WIDTH | Key for describing the downsampling width in video encoder preprocess, value type is int32_t.<br> It is used in configure or set parameter. This key must be used with {@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_DOWNSAMPLING_HEIGHT} together.<br>Using restrictions:<br>1. The downsampling width and height must be configured or set together.<br> If only one of them is configured, {@link AV_ERR_INVALID_VAL} will be returned.<br>2. When the downsampling width and height are the same and qualified as zero, the downsampling is disabled.<br>3. When the downsampling width and height are within the supported range, the downsampling is enabled.<br> It's recommended to query the supported downsampling range through<br> the interface {@link OH_AVCapability_IsVideoSizeSupported}.<br>4. When the downsampling width and height are not within the supported range,<br> {@link AV_ERR_INVALID_VAL} will be returned.<br>5. Cannot be used together with crop parameters ({@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_LEFT},<br> {@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_TOP}, {@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_RIGHT},<br> {@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_BOTTOM}).<br> If both downsampling and crop parameters are set through {@link OH_VideoEncoder_Configure} or<br> {@link OH_VideoEncoder_SetParameter}, {@link AV_ERR_INVALID_VAL} will be returned.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_VIDEO_ENCODER_PREPROC_DOWNSAMPLING_HEIGHT | Key for describing the downsampling height in video encoder preprocess, value type is int32_t.<br> It is used in configure or set parameter. This key must be used with {@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_DOWNSAMPLING_WIDTH} together.<br>Refer to {@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_DOWNSAMPLING_WIDTH} for more details on usage and restrictions.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_LEFT | Key for describing the left-coordinate (x) of the crop rectangle in video encoder preprocess, value type is int32_t.<br> The value represents the left-most column included in the crop frame, where column indices start at 0. The Caller must use "left, top, right, bottom" together to define the crop rectangle, corresponding to: - {@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_LEFT}<br>- {@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_TOP}<br>- {@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_RIGHT}<br>- {@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_BOTTOM}<br>(left, top) is the coordinate of the top-left corner of the crop rectangle.<br>(right, bottom) is the coordinate of the bottom-right corner of the crop rectangle.<br>The width and height of the crop rectangle can be calculated as:<br>- width = right - left + 1<br>- height = bottom - top + 1<br>Using restrictions:<br>1. Crop left, top, right, bottom must be configured together. If only part of them is configured,<br> {@link AV_ERR_INVALID_VAL} will be returned.<br>2. When crop left, top, right, bottom are all 0, the crop is disabled.<br>3. When the crop width, height are within the supported range, the crop is enabled.<br> It's recommended to query the supported crop range through<br> the interface {@link OH_AVCapability_IsVideoSizeSupported}.<br>4. When the crop values are not within the supported range,<br> {@link AV_ERR_INVALID_VAL} will be returned.<br>5. Cannot be used together with downsampling parameters<br> ({@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_DOWNSAMPLING_WIDTH},<br> {@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_DOWNSAMPLING_HEIGHT}).<br> If both crop and downsampling parameters are set through {@link OH_VideoEncoder_Configure} or<br> {@link OH_VideoEncoder_SetParameter}, {@link AV_ERR_INVALID_VAL} will be returned. 6. When crop is enabled, the encoder will only encode the cropped area of the input frame. The content outside the crop rectangle will be discarded and not participate in encoding.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_TOP | Key for describing the top-coordinate (y) of the crop rectangle in video encoder preprocess, value type is int32_t.<br> The value represents the top-most row included in the crop frame, where row indices start at 0. Refer to {@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_LEFT} for more details on usage and restrictions.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_RIGHT | Key for describing the right-coordinate (x) of the crop rectangle in video encoder preprocess, value type is int32_t.<br> The value represents the right-most column included in the crop frame, where column indices start at 0. Refer to {@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_LEFT} for more details on usage and restrictions.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_BOTTOM | Key for describing the bottom-coordinate (y) of the crop rectangle in video encoder preprocess, value type is int32_t.<br> The value represents the bottom-most row included in the crop frame, where row indices start at 0. Refer to {@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_LEFT} for more details on usage and restrictions.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_VIDEO_ENCODER_PREPROC_DROP_TO_FRAME_RATE | Key for describing the drop frame rate in video encoder preprocess, value type is double.<br> It is used in configure or set parameter. The caller must ensure original frame rate is set, refer to {@link OH_MD_KEY_FRAME_RATE}.<br>The value precision is retained to 2 decimal places using round half up.<br>Using restrictions:<br>1. When value is set to 0.0, the drop frame is disabled.<br>2. When value is set to positive value and less than original frame rate,<br> it will drop frames to match the set frame rate.<br>3. When value is set to negative value or equal to or greater than original frame rate,<br> {@link AV_ERR_INVALID_VAL} will be returned.<br>4. Can be used together with downsampling parameters<br> ({@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_DOWNSAMPLING_WIDTH},<br> {@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_DOWNSAMPLING_HEIGHT}).<br>5. Can be used together with crop parameters<br> ({@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_LEFT},<br> {@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_TOP},<br> {@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_RIGHT},<br> {@link OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_BOTTOM}). 6. Processing order when combined: drop frame will be executed first, then downsampling or crop.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_VIDEO_ENCODER_LTR_FRAME_COUNT | Pointer to the key that describes the number of LTR frames. The value type is int32_t. The value must be within the supported value range.<br> Before using this key, you can use the API {@link OH_AVCapability_GetFeatureProperties} and the enumerated value<br>**VIDEO_ENCODER_LONG_TERM_REFERENCE** in {@link OH_AVCapabilityFeature} to query the number of supported LTR frames. This key is optional and used only in the configuration phase of video encoding.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_ENCODER_PER_FRAME_MARK_LTR | Pointer to the key that specifies whether the current frame is marked as an LTR frame. The value type is int32_t. **1** if marked, **0** otherwise. The default value is **0**. If this parameter is set to a non-zero value, the value **1** is used. This key takes effect only after the number of LTR frames is configured.<br> This key is optional and is used only for video encoding input rotation. The configuration takes effect immediately.<br> For details, see {@link Temporally Scalable Video Coding}.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_ENCODER_PER_FRAME_USE_LTR | Pointer to the key that describes the POC number of the LTR frame referenced by the current frame. The value type is int32_t.<br> This key is optional and is used only for video encoding input rotation. The configuration takes effect immediately. For details, see {@link Temporally Scalable Video Coding}.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_PER_FRAME_IS_LTR | Pointer to the key that specifies whether the frame corresponding to the stream output from the current OH_AVBuffer is marked as an LTR frame. The value type is int32_t. **1** if marked, **0** otherwise. The default value is **0**. If this parameter is set to a non-zero value, the value **1** is used.<br> This key is optional and is used only for video encoding output rotation.<br> It indicates the attribute of a frame.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_PER_FRAME_POC | Pointer to the key that describes the POC of the frame. The value type is int32_t.<br> This key is optional and is used only for video encoding output rotation.<br> It indicates the attribute of a frame.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_CROP_TOP | Pointer to the key that describes the top coordinate (y) of the cropped rectangle. The value type is int32_t.<br> The row at the top of the cropped rectangle is contained, and the row index starts from 0.<br> This key is used only for video decoding.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_CROP_BOTTOM | Pointer to the key that describes the bottom coordinate (y) of the cropped rectangle. The value type is int32_t.<br> The row at the bottom of the cropped rectangle is contained, and the row index starts from 0.<br> This key is used only for video decoding.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_CROP_LEFT | Pointer to the key that describes the left coordinate (x) of the cropped rectangle. The value type is int32_t.<br> The leftmost column of the cropped rectangle is contained, and the column index starts from 0.<br> This key is used only for video decoding.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_CROP_RIGHT | Pointer to the key that describes the right coordinate (x) of the cropped rectangle. The value type is int32_t.<br> The rightmost column of the cropped rectangle is contained, and the column index starts from 0.<br> This key is used only for video decoding.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_STRIDE | Pointer to the key that describes the stride of the video frame. The value type is int32_t.<br> Stride indicates the byte distance between the start positions of two consecutive rows in memory. Due to hardware alignment requirements, the stride is typically greater than or equal to the image's active width. When the stride equals the width, there is no horizontal padding. You should always obtain the actual stride through {@link OH_VideoEncoder_GetInputDescription} (for encoding),<br>{@link OH_VideoDecoder_GetOutputDescription} (for decoding), or **OH_AVFormat** in the [OH_AVCodecOnStreamChanged](capi-native-avcodec-base-h.md#oh_avcodeconstreamchanged) callback, instead of assuming a fixed value.<br>For details about the example, see step 8 in [video encoding](../../../media/avcodec/video-encoding.md#buffer-mode)<br>in buffer mode or step 11 in [video decoding](../../../media/avcodec/video-decoding.md#buffer-mode) in buffer mode.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_SLICE_HEIGHT | Pointer to the key that describes the height of the video frame. The value type is int32_t.<br> Height indicates the total number of rows allocated in the memory for a single plane. Due to hardware alignment requirements, **sliceHeight** is typically greater than or equal to the image's active height. The offset of the start address of the U plane relative to the origin of the Y plane is **sliceHeight** x **stride**. You should always obtain the actual height through {@link OH_VideoEncoder_GetInputDescription} (for encoding),<br>{@link OH_VideoDecoder_GetOutputDescription} (for decoding), or **OH_AVFormat** in the [OH_AVCodecOnStreamChanged](capi-native-avcodec-base-h.md#oh_avcodeconstreamchanged) callback, instead of assuming a fixed value.<br>For details about the example, see step 8 in [video encoding](../../../media/avcodec/video-encoding.md#buffer-mode)<br>in buffer mode or step 11 in [video decoding](../../../media/avcodec/video-decoding.md#buffer-mode) in buffer mode.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_PIC_WIDTH | Pointer to the key that describes the actual active width of a decoded video frame. The value type is int32_t. This key is read-only and used only for video decoding.<br> You can obtain the width from the returned **OH_AVFormat** instance when {@link OH_VideoDecoder_GetOutputDescription} is called or decoded output stream changes are detected through the [OH_AVCodecOnStreamChanged](capi-native-avcodec-base-h.md#oh_avcodeconstreamchanged)<br>callback. This value indicates the visible width after cropping, which is different from **OH_MD_KEY_WIDTH** set in<br>the configuration phase. The latter is a configuration hint used for pre-allocating buffers. When cropping is<br>applied, this value (rather than the stride) should be used as the actual width for displaying or saving the image.<br>For details about the image layout and usage example, see step 8 in<br>[video encoding](../../../media/avcodec/video-encoding.md#buffer-mode) in buffer mode or<br>step 11 in [video decoding](../../../media/avcodec/video-decoding.md#buffer-mode) in buffer mode.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_PIC_HEIGHT | Pointer to the key that describes the actual active height of a decoded video frame. The value type is int32_t. This key is read-only and used only for video decoding.<br> You can obtain the height from the returned **OH_AVFormat** instance when {@link OH_VideoDecoder_GetOutputDescription} is called or decoded output bitstream changes are detected through the [OH_AVCodecOnStreamChanged](capi-native-avcodec-base-h.md#oh_avcodeconstreamchanged) callback. This value indicates the visible height after cropping,<br>which is different from **OH_MD_KEY_HEIGHT** set in the configuration phase. The latter is a configuration hint used<br>for pre-allocating buffers. When cropping is applied, this value (rather than **sliceHeight**) should be used as the<br>actual height for displaying or saving the image.<br>For details about the image layout and usage example, see step 8<br>in [video encoding](../../../media/avcodec/video-encoding.md#buffer-mode) in buffer mode or<br>step 11 in [video decoding](../../../media/avcodec/video-decoding.md#buffer-mode) in buffer mode.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_ENABLE_LOW_LATENCY | Pointer to the key that describes the enabled status of low-latency video decoding. The value type is int32_t. **1** if enabled, **0** otherwise. The default value is **0**. If this parameter is set to a non-zero value, the value **1** is used.<br> This key is optional and used only in the configuration phase.<br> If enabled, the input and output data held by the video decoder does not exceed the amount required by the decoder standard.<br> You can call {@link OH_AVCapability_IsFeatureSupported} to check whether a specific decoder supports low-latency decoding. If supported, the video decoder outputs frames in the decoding sequence when low-latency video codec is enabled.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_ENCODER_QP_MAX | Pointer to the key that describes the maximum Quantization Parameter (QP) allowed by the video encoder. The value type is int32_t.<br> Tt is used in configure/setparameter or takes effect immediately with the frame.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_ENCODER_QP_MIN | Pointer to the key that describes the minimum QP allowed by the video encoder. The value type is int32_t.<br> It is used in configure/setparameter or takes effect immediately with the frame.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_ENCODER_QP_AVERAGE | Pointer to the key that describes the average QP of video frames. The value type is int32_t.<br> Pointer to the key that describes the average QP value of the current frame encoding block. It is output with {@link OH_AVBuffer}.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_ENCODER_MSE | Pointer to the key that describes the Mean Squared Error (MSE) of video frames. The value type is double.<br> Pointer to the key that describes the average MSE value of the current frame encoding block. It is output with {@link OH_AVBuffer}.<br>**Since**: 12 |
| const char *OH_MD_KEY_DECODING_TIMESTAMP | Pointer to the key that describes the decoding timestamp corresponding to the audio, video, or subtitle sample carried in AVBuffer, in microseconds. The value type is int64_t.<br>**Since**: 12 |
| const char *OH_MD_KEY_BUFFER_DURATION | Pointer to the key that describes the duration corresponding to the audio, video, or subtitle sample carried in AVBuffer, in microseconds. The value type is int64_t.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_SAR | Pointer to the key that describes the aspect ratio of the sample. The value type is double.<br>**Since**: 12 |
| const char *OH_MD_KEY_START_TIME | Pointer to the key that describes the start time of the first frame in a media file, measured in microseconds. The value type is int64_t.<br>**Since**: 12 |
| const char *OH_MD_KEY_TRACK_START_TIME | Pointer to the key that describes the start time of the track, measured in microseconds. The value type is int64_t.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_DECODER_OUTPUT_COLOR_SPACE | Pointer to the key that describes the output color space of the video decoder. The value type is int32_t.<br> The supported value is **OH_COLORSPACE_BT709_LIMIT**. For details, see {@link OH_NativeBuffer_ColorSpace}.<br>It is used in {@link OH_VideoDecoder_Configure}.<br>Before calling {@link OH_VideoDecoder_Start}, you must call {@link OH_VideoDecoder_Prepare}.<br>If Color Space Conversion (CSC) is supported and this key is configured, the video decoder automatically transcodes<br>the HDR Vivid video to the specified color space.<br>If CSC is not supported, the error code **AV_ERR_VIDEO_UNSUPPORTED_COLOR_SPACE_CONVERSION** in {@link OH_AVErrCode}<br>is returned when {@link OH_VideoDecoder_Configure} is called. If the input video is not an HDR Vivid video,<br>the callback function [OH_AVCodecOnError](capi-native-avcodec-base-h.md#oh_avcodeconerror) is invoked to report the error code<br>**AV_ERR_VIDEO_UNSUPPORTED_COLOR_SPACE_CONVERSION** in {@link OH_AVErrCode}.<br>**Since**: 12 |
| const char *OH_MD_KEY_VIDEO_DECODER_OUTPUT_ENABLE_VRR | Pointer to the key that specifies whether the decoder enables the video variable frame rate feature. The value type is int32_t. **1** if enabled, **0** otherwise.<br>**Since**: 15 |
| const char *OH_MD_KEY_CREATION_TIME | Pointer to the key that describes the media file creation time. The value type is char *. The value must be in the UTC time format complying with ISO 8601. Time format example: 2024-12-28T00:00:00:000000Z<br>**Since**: 14 |
| const char *OH_MD_KEY_VIDEO_ENCODER_REPEAT_PREVIOUS_FRAME_AFTER | Pointer to the key that describes the duration (in milliseconds) for which the last frame will be resubmitted repeatedly, if no new frame is available after the previous frame is submitted to the encoder. The value type is int32_t.<br> This key is used only in the configuration phase of video encoding in surface mode.<br> Configured value:<br> - If the value is less than or equal to 0, the request is intercepted in the configuration phase and {@link ERROR<br>AV_ERR_INVALID_VAL} is returned.<br> - If the value is greater than 0, the last frame will be resubmitted repeatedly in the specified duration, measured in milliseconds.<br>**Since**: 18 |
| const char *OH_MD_KEY_VIDEO_ENCODER_REPEAT_PREVIOUS_MAX_COUNT | Pointer to the key that describes the maximum number of times the encoder can repeat encoding the previous frame when no new frame is available. The value type is int32_t.<br> This key takes effect only when **OH_MD_KEY_VIDEO_ENCODER_REPEAT_PREVIOUS_FRAME_AFTER** is available and is used only in the configuration phase.<br> Configured value.<br> - If the value is equal to 0, the request is intercepted in the configuration phase and **ERROR AV_ERR_INVALID_VAL**<br>is returned.<br> - If the value is less than 0 and no new frame is available, the encoder repeatedly encodes the previous frame until the upper limit of the system is reached.<br> - If the value is greater than 0 and no new frame is available, the encoder repeatedly encodes the previous frame until the maximum number specified is reached.<br>**Since**: 18 |
| const char *OH_MD_KEY_VIDEO_ENCODER_ENABLE_B_FRAME | Pointer to the key that describes the enabled status of B-frame encoding. The value type is int32_t (**0** or **1**). **1** if enabled, **0** otherwise. This key is optional and used only for video encoding. The default value is **0**.<br> If enabled, the video encoder uses B-frames, resulting in a different decoding order from the display order.<br> If the platform does not support this feature, the configuration of this key does not take effect.<br> To check whether the platform supports B-frame encoding, use the {@link OH_AVCapability_IsFeatureSupported} API and<br>the enumerated value {@link OH_AVCapabilityFeature} VIDEO_ENCODER_B_FRAME.<br> This key is used only in the configuration phase.<br>**Since**: 20 |
| const char *OH_MD_KEY_VIDEO_ENCODER_MAX_B_FRAMES | Pointer to the key that describes the maximum number of consecutive B-frames supported by the video encoder. The value type is int32_t. Note: This key is used only to query the encoder capability.<br> The usage specifications are as follows:<br> 1. To check whether the platform supports B-frame encoding, use the {@link OH_AVCapability_IsFeatureSupported} API<br>and the enumerated value {@link OH_AVCapabilityFeature} VIDEO_ENCODER_B_FRAME.<br>2. Obtain the OH_AVFormat pointer through the {@link OH_AVCapability_GetFeatureProperties} API and<br>the enumerated value {@link OH_AVCapabilityFeature} VIDEO_ENCODER_B_FRAME.<br>3. Obtain the maximum number of B-frames through the {@link OH_AVFormat_GetIntValue} API and this key.<br>**Since**: 20 |
| const char *OH_MD_KEY_VIDEO_ENCODER_ROI_PARAMS | Key to set the region of interest(ROI) parameters. Value type is string in the format "Top1,Left1-Bottom1,Right1[=Params1];Top2,Left2-Bottom2,Right2[=Params2];".<br>Each "Top,Left-Bottom,Right" represents the coordinate information of one ROI.<br>The "[=Params]" is optional.<br>The format of "[=Params]" varies by version: 1. Prior to version 26.0.0: Only a single int32_t value representing the quantization parameter offset is supported (e.g., "=Offset"). 2. Since version 26.0.0: A Key-Value format is additionally supported and recommended. It uses comma-separated key-value pairs (e.g., "=dqp:-6,slb:1"). Supported keys: - "dqp": Quantization parameter offset. - "slb": Semantic label. The value must correspond to {@link OH_VideoMetadataRoiSemanticLabel}.<br>If "=Params" is omitted entirely, like "Top1,Left1-Bottom1,Right1;Top2,Left2-Bottom2,Right2=dqp:-6;",<br>the encoder will use the default parameters to perform the ROI encoding on the first ROI and<br>use the specified parameters on the second ROI.<br>Note that the number of ROIs that can be applied simultaneously does not exceed six, and the total area must<br>not exceed one-fifth of the total image area.<br>This is an optional key that applies only to video encoder.<br>It is used in running process and is set with each frame.<br>In surface mode, it is used in {@link OH_VideoEncoder_OnNeedInputParameter}.<br>In buffer mode, it is configured via {@link OH_AVBuffer_SetParameter}.<br>**Since**: 20 |
| const char *OH_MD_KEY_ENABLE_MOOV_FRONT | Pointer to the key that specifies whether the moov metadata should be at the front of a media file. The value type is int32_t. The value **1** indicates that the moov metadata should be at the front of a media file, and **0**<br>indicates that the moov metadata should not be at the front of a media file. The default value is **0**.<br>**Since**: 20 |
| const char *OH_MD_KEY_SQR_FACTOR | Pointer to the key that describes the quality parameter in SQR mode. The value range is [0, 51] (same as the QP value in encoding). A smaller value indicates a higher output bit rate and better quality.<br> It is used in the configuration or parameter setting phase.<br>**Since**: 20 |
| const char *OH_MD_KEY_MAX_BITRATE | Pointer to the key that describes the maximum bit rate in SQR mode. The value range can be obtained by calling {@link OH_AVCapability_GetEncoderBitrateRange} and is the same as that of **OH_MD_KEY_BITRATE**. The unit is bit/s. The value type is int64_t.<br> It is used in the configuration or parameter setting phase.<br>**Since**: 20 |
| const char *OH_MD_KEY_REFERENCE_TRACK_IDS | Pointer to the key that describes the reference relationship between media file tracks. The value type is int32_t*.<br>**Since**: 20 |
| const char *OH_MD_KEY_TRACK_REFERENCE_TYPE | Pointer to the key that describes the auxiliary track type of a media file. The value type is char *.<br>**Since**: 20 |
| const char *OH_MD_KEY_TRACK_DESCRIPTION | Pointer to the key that describes the auxiliary track description of a media file. The value type is char *.<br>**Since**: 20 |
| const char *OH_MD_KEY_VIDEO_ENCODER_ENABLE_PTS_BASED_RATECONTROL | Pointer to the key that describes the enabled status of the PTS-based bit rate control mode. The value type is int32_t. **1** if enabled, **0** otherwise. The default value is **0**. If this parameter is set to a non-zero value, the value **1** is used.<br> This key is optional and is used only for video encoding.<br> If this feature is enabled, each video frame must contain PTS information and be sent to the encoder. In surface mode, the PTS is set by calling {@link OH_NativeWindow_NativeWindowHandleOpt}, in units of nanosecond (ns).<br>In buffer mode, the PTS is set by calling {@link OH_AVBuffer_SetBufferAttr}, in units of microsecond (us).<br> It is used in the configuration phase.<br>**Since**: 20 |
| const char *OH_MD_KEY_ENABLE_SYNC_MODE | Pointer to the key that describes the enabled status of audio/video codec synchronization. The value type is int32_t. **1** if enabled, **0** otherwise. The default value is **0**. If this parameter is set to a non-zero value, the value **1** is used. This key is optional.<br> If this feature is enabled, pay attention to the following: 1. The codec cannot have a callback function. 2. You must use the buffer query API instead of the callback function. 3. The key can be used only in the configuration phase.<br>**Since**: 20 |
| const char *OH_MD_KEY_VIDEO_DECODER_BLANK_FRAME_ON_SHUTDOWN | Pointer to the key that specifies whether to output blank frames when the video decoder is disabled. The value type is int32_t. **1** to output, **0** otherwise. The default value is **0**. If this parameter is set to a non-zero value, the value **1** is used. This key is optional and is used only for video decoding in surface mode. After this function is enabled, the video decoder outputs a blank frame (usually black) when the {@link OH_VideoDecoder_Stop} or {@link OH_VideoDecoder_Destroy} API is called. This mechanism prevents frozen frames caused by sudden termination of the decoder.<br>**Since**: 20 |
| const char *OH_MD_KEY_VIDEO_NATIVE_BUFFER_FORMAT | Pointer to the key that is used to query the native buffer pixel format in video encoding and decoding. The value type is int32_t.<br> For details, see the pixel formats defined in {@link OH_NativeBuffer_Format}. This key is used in the following<br>scenarios:<br>1. Video decoding: Call {@link OH_VideoDecoder_GetOutputDescription} or [OH_AVCodecOnStreamChanged](capi-native-avcodec-base-h.md#oh_avcodeconstreamchanged) to obtain<br>the current output format from the returned OH_AVFormat object.<br>2. Video encoding: Call {@link OH_VideoEncoder_GetInputDescription} to obtain the current input format from the returned OH_AVFormat object.<br>**Since**: 22 |
| const char *OH_MD_KEY_BUFFER_SKIP_SAMPLES_INFO | Pointer to the key carried in the OH_AVBuffer used to skip part of the decoded audio data. It is measured in sample points, with a value type of uint8_t*. This key is supported when using MP3, Vorbis, or OPUS decoders.<br> It is carried only by the first and last frames of an audio stream and is optional. Method 1: Obtain the information during demultiplexing and set it to the input OH_AVBuffer used for decoding.<br> 1. Obtain the OH_AVBuffer used for decoding from the callback function [OH_AVCodecOnNeedInputBuffer](capi-native-avcodec-base-h.md#oh_avcodeconneedinputbuffer) of<br>[OH_AVCodecCallback](capi-codecbase-oh-avcodeccallback.md).<br>2. Call {@link OH_AVDemuxer_ReadSampleBuffer} to read audio data. This function automatically sets **<br>OH_MD_KEY_BUFFER_SKIP_SAMPLES_INFO** when needed.<br>3. Call {@link OH_AudioCodec_PushInputBuffer} to push the input OH_AVBuffer for decoding.<br>Method 2: Construct the data required by the key and set it to the input OH_AVBuffer used for decoding.<br>Create a 10-byte uint8_t[] array with the structure as follows:<br> 1. Bytes 0-3 (uint32_t, little-endian): number of samples to skip from the beginning of this frame.<br> 2. Bytes 4-7 (uint32_t, little-endian): number of samples to skip from the end of this frame (must not exceed the frame's total sample count).<br> 3. Bytes 8-9: reserved; set to **0**.<br>**Since**: 23 |
| const char *OH_MD_KEY_ENABLE_BUFFER_SKIP_SAMPLES | Pointer to the key for enabling {@link OH_MD_KEY_BUFFER_SKIP_SAMPLES_INFO} in the audio decoder. The value type is int32_t. **1** to enable, **0** otherwise. The default value is **0**. If this parameter is set to a value other than **1**, the value **0** is used. This key is optional. It is for the audio decoder only.<br>**Since**: 24 |
| const char *OH_MD_KEY_LATITUDE | Key for latitude, value type is float, The range is [-90.0, 90.0].<br> Represents the latitude of the geographic location.<br>**Since**: 24 |
| const char *OH_MD_KEY_LONGITUDE | Longitude key. The value is of the float type, and the value range is [-180.0, 180.0]. It indicates the longitude in geographic location information.<br>**Since**: 24 |
| const char *OH_MD_KEY_ALTITUDE | Altitude key. The value is of the float type. This key is optional. It indicates the altitude in geographic location information.<br>**Since**: 24 |
| const char *OH_MD_KEY_VIDEO_ENCODER_NUMBER_OF_PENDING_FRAMES | Pointer to the key that describes the number of pending frames in the video encoder. The value type is int32_t.<br> This key is read-only and used to query the current number of frames that are pending for encoding. It can be obtained through {@link OH_VideoEncoder_GetInputDescription}.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_VIDEO_DECODER_OUTPUT_IN_DECODING_ORDER | Pointer to the key that describes the decoder output mode. The value type is int32_t (0 or 1). 1 indicates outputting frames in decoding order, and 0 indicates outputting frames in display order (default).<br> This is an optional key that applies only to video decoder and is used only in the Configure phase. The default value is 0, which means the decoder outputs frames in display order. Before setting this key, you can use {@link OH_AVCapability_IsFeatureSupported} and the enumerated value<br>**VIDEO_DECODER_OUTPUT_IN_DECODING_ORDER** in {@link OH_AVCapabilityFeature} to check<br>whether this feature is supported.<br>If the video decoder does not support this feature, setting this key through {@link OH_VideoDecoder_Configure} return<br>{@link AV_ERR_INVALID_VAL}.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_VIDEO_ENCODER_MAX_FRAME_DELAY_COUNT | Pointer to the key that describes the maximum number of frames that the video encoder is allowed to hold before outputting a compressed frame. The value type is int32_t, and the value range is [1, 5].<br>This is an optional key that applies only to video encoder and is used only in the Configure phase.<br>If the value is within [1, 5], it takes effect normally. If the value is out of range (<1 or >5), {@link OH_VideoEncoder_Configure} returns {@link AV_ERR_INVALID_VAL}.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_VIDEO_ENCODER_REPEAT_HEADER_BEFORE_SYNC_FRAMES | Pointer to the key that describes whether to repeat headers before sync frames. The value type is int32_t (0 or 1): 1 is enabled, 0 disabled.<br> This is an optional key that applies only to video encoder and is used only in the Configure phase. The default value is 0, which means this feature is disabled by default. When enabled, the encoder inserts codec-specific configuration data (such as SPS/PPS for H.264/H.265) before each sync frame.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_AUDIO_VIVID_SIGNAL_FORMAT | Key for setting the Audio Vivid signal input format.<br> Required for Audio Vivid encoder. Specifies the signal format of input data. The value should be from {@link OH_AudioVividSignalFormat}.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_AUDIO_SOUNDBED_LAYOUT | Key for setting the soundbed channel layout.<br> Configures the channel layout for soundbed. The value should be from {@link OH_AudioChannelLayout}.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_AUDIO_SOUNDBED_BITRATE | Key for setting the soundbed bitrate in bits per second.<br> Configures the bitrate for soundbed channels. The actual bitrate may be adjusted by the encoder based on codec capabilities and constraints.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_AUDIO_OBJECT_BITRATE | Key for setting the audio object bitrate in bits per second.<br> Configures the bitrate for audio objects. The actual bitrate may be adjusted by the encoder based on codec capabilities and constraints.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_MODE | Key for setting the video decoding frame retention mode. The value type is int32_t.<br> The value represents a frame retention mode defined in [OH_FrameRetentionMode](capi-native-avcodec-base-h.md#oh_frameretentionmode). Please refer to the enumeration definition for detailed descriptions of each mode and their behaviors.This key can be configured via the {@link OH_VideoDecoder_Configure} and<br>{@link OH_VideoDecoder_SetParameter} interfaces.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_RATIO | Key for setting the video decoding frame retention ratio. The value type is double.<br> This parameter takes effect when {@link OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_MODE} is set to<br>{@link OH_FrameRetentionMode#OH_FRAME_RETENTION_MODE_UNIFORM}, or when the retention mode is not<br>configured (implicitly defaulting to uniform behavior). This configuration is ignored ONLY when<br>the retention mode is explicitly set to {@link OH_FrameRetentionMode#OH_FRAME_RETENTION_MODE_ADAPTIVE}<br>or {@link OH_FrameRetentionMode#OH_FRAME_RETENTION_MODE_FULL}.<br>The valid range is [0.01, 1.0] (where 1.0 means all frames retained and 0.01 is the minimum limit);<br>any value outside this range is considered invalid and will be ignored. This key can be configured<br>via the {@link OH_VideoDecoder_Configure} and {@link OH_VideoDecoder_SetParameter} interfaces.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_VIDEO_DECODER_SPEED | Key for configuring the video decoder playback speed. The value type is double.<br> This key specifies the target playback speed of the video. It is primarily recommended for use in conjunction with {@link OH_FrameRetentionMode#OH_FRAME_RETENTION_MODE_ADAPTIVE}<br>to assist the adaptive algorithm in accurately evaluating the perceptual impact of frame<br>drops. The value must be strictly greater than 0.0, with recommended standard values<br>including 0.5, 0.75, 1.0 (normal speed), 1.25, 1.5, 2.0, and 3.0; any value less than<br>or equal to 0.0 is considered invalid. This key can be configured via the<br>{@link OH_VideoDecoder_Configure} and {@link OH_VideoDecoder_SetParameter} interfaces.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_AUDIO_MAX_INPUT_BUFFER_SIZE | Key for setting or querying the maximum input buffer size (in bytes) for audio codec, value type is int32_t.<br> This key is used to configure or retrieve the maximum size of the input buffer for audio codec. The actual buffer size is limited by the codec implementation. Setting a value larger than the codec's maximum supported size can not take effect. This configuration is optional. If not set, the codec will use its default buffer size.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_AUDIO_ENCODER_PTS_MODE | Key for configuring the PTS output mode of the audio encoder.<br> Sets the PTS output behavior mode. The value type is int32_t from [OH_AudioEncoderPTSMode](capi-native-avcodec-base-h.md#oh_audioencoderptsmode). Optional. Defaults to [OH_AUDIO_ENCODER_PTS_MODE_DEFAULT](capi-native-avcodec-base-h.md#oh_audioencoderptsmode) if not set.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_AUDIO_ENCODER_ENABLE_SAMPLE_FORMAT_CONVERT | Key for enabling sample format conversion in the audio encoder. Optional. The value type is int32_t (0 or 1). 1 is enabled, 0 is disabled. Defaults to 0.<br> The audio encoder supports only a limited number of sample formats. After this configuration is enabled, if an unsupported sampling format is used, the audio encoder will convert the sample format to an supported one for encoding. The supported sample formats before conversion are as follows: [SAMPLE_U8](capi-native-avcodec-base-h.md#oh_bitspersample), [SAMPLE_S16LE](capi-native-avcodec-base-h.md#oh_bitspersample), [SAMPLE_S24LE](capi-native-avcodec-base-h.md#oh_bitspersample), [SAMPLE_S32LE](capi-native-avcodec-base-h.md#oh_bitspersample), [SAMPLE_F32LE](capi-native-avcodec-base-h.md#oh_bitspersample).<br>**Since**: 26.0.0 |
| void (*OH_AVCodecOnError)(OH_AVCodec *codec, int32_t errorCode, void *userData) | Defines the pointer to the function that is called to report error information when an error occurs during the running of an OH_AVCodec instance. \| Use Case\| Error Code\|\| -------- \| -------- \|\| Audio encoding/decoding\| **AV_ERR_DRM_DECRYPT_FAILED**: DRM decryption failed. \|\| Video encoding/decoding\| **AV_ERROR_NO_MEMORY**: System resources are insufficient.<br>**AV_ERROR_UNKNOWN**: An unknown error occurs. Analyze the error based on specific logs.<br>**AV_ERR_SERVICE_DIED**: The service is dead. \|\| Video decoding\| **AV_ERR_VIDEO_UNSUPPORTED_COLOR_SPACE_CONVERSION**: The current input does not support CSC. \| <!--RP1--><!--RP1End--><br>**Since**: 9 |
| void (*OH_AVCodecOnStreamChanged)(OH_AVCodec *codec, OH_AVFormat *format, void *userData) | Defines the pointer to the function that is called to report the new stream description when the resolution of the input video stream being decoded or the output video stream that has been encoded changes.<br> Starting from API version 15, this function pointer is called to report the new stream description when the stream sampling rate, number of audio channels, or audio sampling format changes during audio decoding. The decoding formats that can detect these changes include <!--RP3--><!--RP3End-->AAC, FLAC, MP3, and VORBIS.<br> Note that the lifecycle of the pointer to the OH_AVFormat instance is valid only when the function pointer is being called. Do not access the pointer to the instance after the function pointer is called.<br>**Since**: 9 |
| void (*OH_AVCodecOnNeedInputData)(OH_AVCodec *codec, uint32_t index, OH_AVMemory *data, void *userData) | Defines the pointer to the function that is called when new input data is required during the running of an OH_AVCodec instance. The function carries a buffer to fill in new input data.<br>**Since**: 9<br>**Deprecated**: 11<br>**Replaced by**: OH_AVCodecOnNeedInputBuffer |
| void (*OH_AVCodecOnNewOutputData)(OH_AVCodec *codec, uint32_t index, OH_AVMemory *data, OH_AVCodecBufferAttr *attr, void *userData) | Defines the pointer to the function that is called when new output data is generated during the running of an OH_AVCodec instance. The function carries a buffer filled with new output data. Note that the lifecycle of the pointer to the OH_AVCodecBufferAttr instance is valid only when the function pointer is being called. Do not access the pointer to the instance after the function pointer is called.<br>**Since**: 9<br>**Deprecated**: 11<br>**Replaced by**: OH_AVCodecOnNewOutputBuffer |
| void (*OH_AVCodecOnNeedInputBuffer)(OH_AVCodec *codec, uint32_t index, OH_AVBuffer *buffer, void *userData) | Defines the pointer to the function that is called when new input data is required during the running of an OH_AVCodec instance. The function carries a buffer to fill in new input data.<br>**Since**: 11 |
| void (*OH_AVCodecOnNewOutputBuffer)(OH_AVCodec *codec, uint32_t index, OH_AVBuffer *buffer, void *userData) | Defines the pointer to the function that is called when new output data is generated during the running of an OH_AVCodec instance. The function carries a buffer filled with new output data.<br>**Since**: 11 |
| int32_t (*OH_AVDataSourceReadAt)(OH_AVBuffer *data, int32_t length, int64_t pos) | Defines a function pointer used to provide the capability of obtaining user-defined media data.<br>**Since**: 12 |
| int32_t (*OH_AVDataSourceReadAtExt)(OH_AVBuffer *data, int32_t length, int64_t pos, void *userData) | Defines a function pointer used to provide the capability of obtaining user-defined media data.<br>**Since**: 20 |

## Enum type description

### OH_MediaType

```c
enum OH_MediaType
```

**Description**

Enumerates the media types.

**Since**: 9

| Enum item | Description |
| -- | -- |
| MEDIA_TYPE_AUD = 0 |  |
| MEDIA_TYPE_VID = 1 |  |
| MEDIA_TYPE_SUBTITLE = 2 |  |
| MEDIA_TYPE_TIMED_METADATA = 5 |  |
| MEDIA_TYPE_AUXILIARY = 6 |  |

### OH_AACProfile

```c
enum OH_AACProfile
```

**Description**

Enumerates the AAC profiles.

**Since**: 9

| Enum item | Description |
| -- | -- |
| AAC_PROFILE_LC = 0 |  |
| AAC_PROFILE_HE = 3 |  |
| AAC_PROFILE_HE_V2 = 4 |  |

### OH_AVCProfile

```c
enum OH_AVCProfile
```

**Description**

Enumerates the AVC profiles.

**Since**: 9

| Enum item | Description |
| -- | -- |
| AVC_PROFILE_BASELINE = 0 |  |
| AVC_PROFILE_HIGH = 4 |  |
| AVC_PROFILE_MAIN = 8 |  |

### OH_HEVCProfile

```c
enum OH_HEVCProfile
```

**Description**

Enumerates the HEVC profiles.

**Since**: 10

| Enum item | Description |
| -- | -- |
| HEVC_PROFILE_MAIN = 0 |  |
| HEVC_PROFILE_MAIN_10 = 1 |  |
| HEVC_PROFILE_MAIN_STILL = 2 |  |
| HEVC_PROFILE_MAIN_10_HDR10 = 3 |  |
| HEVC_PROFILE_MAIN_10_HDR10_PLUS = 4 |  |

### OH_VVCProfile

```c
enum OH_VVCProfile
```

**Description**

Enumerates the VVC profiles.

**Since**: 15

| Enum item | Description |
| -- | -- |
| VVC_PROFILE_MAIN_10 = 1 |  |
| VVC_PROFILE_MAIN_12 = 2 |  |
| VVC_PROFILE_MAIN_12_INTRA = 10 |  |
| VVC_PROFILE_MULTI_MAIN_10 = 17 |  |
| VVC_PROFILE_MAIN_10_444 = 33 |  |
| VVC_PROFILE_MAIN_12_444 = 34 |  |
| VVC_PROFILE_MAIN_16_444 = 36 |  |
| VVC_PROFILE_MAIN_12_444_INTRA = 42 |  |
| VVC_PROFILE_MAIN_16_444_INTRA = 44 |  |
| VVC_PROFILE_MULTI_MAIN_10_444 = 49 |  |
| VVC_PROFILE_MAIN_10_STILL = 65 |  |
| VVC_PROFILE_MAIN_12_STILL = 66 |  |
| VVC_PROFILE_MAIN_10_444_STILL = 97 |  |
| VVC_PROFILE_MAIN_12_444_STILL = 98 |  |
| VVC_PROFILE_MAIN_16_444_STILL = 100 |  |

### OH_MPEG2Profile

```c
enum OH_MPEG2Profile
```

**Description**

Enumerates the MPEG2 profiles.

**Since**: 17

| Enum item | Description |
| -- | -- |
| MPEG2_PROFILE_SIMPLE = 0 |  |
| MPEG2_PROFILE_MAIN = 1 |  |
| MPEG2_PROFILE_SNR_SCALABLE = 2 |  |
| MPEG2_PROFILE_SPATIALLY_SCALABLE = 3 |  |
| MPEG2_PROFILE_HIGH = 4 |  |
| MPEG2_PROFILE_422 = 5 |  |

### OH_MPEG4Profile

```c
enum OH_MPEG4Profile
```

**Description**

Enumerates the MPEG4 profiles.

**Since**: 17

| Enum item | Description |
| -- | -- |
| MPEG4_PROFILE_SIMPLE = 0 |  |
| MPEG4_PROFILE_SIMPLE_SCALABLE = 1 |  |
| MPEG4_PROFILE_CORE = 2 |  |
| MPEG4_PROFILE_MAIN = 3 |  |
| MPEG4_PROFILE_N_BIT = 4 |  |
| MPEG4_PROFILE_HYBRID = 5 |  |
| MPEG4_PROFILE_BASIC_ANIMATED_TEXTURE = 6 |  |
| MPEG4_PROFILE_SCALABLE_TEXTURE = 7 |  |
| MPEG4_PROFILE_SIMPLE_FA = 8 |  |
| MPEG4_PROFILE_ADVANCED_REAL_TIME_SIMPLE = 9 |  |
| MPEG4_PROFILE_CORE_SCALABLE = 10 |  |
| MPEG4_PROFILE_ADVANCED_CODING_EFFICIENCY = 11 |  |
| MPEG4_PROFILE_ADVANCED_CORE = 12 |  |
| MPEG4_PROFILE_ADVANCED_SCALABLE_TEXTURE = 13 |  |
| MPEG4_PROFILE_ADVANCED_SIMPLE = 17 |  |

### OH_H263Profile

```c
enum OH_H263Profile
```

**Description**

Enumerates the H.263 profiles.

**Since**: 17

| Enum item | Description |
| -- | -- |
| H263_PROFILE_BASELINE = 0 |  |
| H263_PROFILE_VERSION_1_BACKWARD_COMPATIBILITY = 2 |  |

### OH_VC1Profile

```c
enum OH_VC1Profile
```

**Description**

Enumerates the VC-1 profiles.

**Since**: 22

| Enum item | Description |
| -- | -- |
| VC1_PROFILE_SIMPLE = 0 |  |
| VC1_PROFILE_MAIN = 1 |  |
| VC1_PROFILE_ADVANCED = 2 |  |

### OH_AV1Profile

```c
enum OH_AV1Profile
```

**Description**

AV1 profile.

**Since**: 23

| Enum item | Description |
| -- | -- |
| AV1_PROFILE_MAIN = 0 |  |
| AV1_PROFILE_HIGH = 1 |  |
| AV1_PROFILE_PROFESSIONAL = 2 |  |

### OH_VP9Profile

```c
enum OH_VP9Profile
```

**Description**

VP9 profile.

**Since**: 23

| Enum item | Description |
| -- | -- |
| VP9_PROFILE_0 = 0 |  |
| VP9_PROFILE_1 = 1 |  |
| VP9_PROFILE_2 = 2 |  |
| VP9_PROFILE_3 = 3 |  |

### OH_WVC1Profile

```c
enum OH_WVC1Profile
```

**Description**

WVC1 profile.

**Since**: 23

| Enum item | Description |
| -- | -- |
| WVC1_PROFILE_ADVANCED = 0 |  |

### OH_WMV3Profile

```c
enum OH_WMV3Profile
```

**Description**

Enumerates the WMV3 profiles.

**Since**: 22

| Enum item | Description |
| -- | -- |
| WMV3_PROFILE_SIMPLE = 0 |  |
| WMV3_PROFILE_MAIN = 1 |  |

### OH_AVOutputFormat

```c
enum OH_AVOutputFormat
```

**Description**

Enumerates the output file formats supported by a muxer.

**Since**: 10

| Enum item | Description |
| -- | -- |
| AV_OUTPUT_FORMAT_DEFAULT = 0 | Default format, which is MP4.<br>**Since**: 10 |
| AV_OUTPUT_FORMAT_MPEG_4 = 2 | The muxer output MP4 file format.<br>**Since**: 10 |
| AV_OUTPUT_FORMAT_M4A = 6 | The muxer output M4A file format.<br>**Since**: 10 |
| AV_OUTPUT_FORMAT_AMR = 8 | The muxer output amr file format.<br>**Since**: 12 |
| AV_OUTPUT_FORMAT_MP3 = 9 | The muxer output mp3 file format.<br>**Since**: 12 |
| AV_OUTPUT_FORMAT_WAV = 10 | The muxer output wav file format.<br>**Since**: 12 |
| AV_OUTPUT_FORMAT_AAC = 11 | The muxer output aac file format.<br>**Since**: 18 |
| AV_OUTPUT_FORMAT_FLAC = 12 | The muxer output flac file format.<br>**Since**: 20 |
| AV_OUTPUT_FORMAT_OGG = 13 | The muxer output ogg file format.<br>**Since**: 23 |
| AV_OUTPUT_FORMAT_FLV = 14 | The muxer output flv file format.<br>**Since**: 26.0.0 |

### OH_AVSeekMode

```c
enum OH_AVSeekMode
```

**Description**

Enumerates the seek modes.

**Since**: 10

| Enum item | Description |
| -- | -- |
| SEEK_MODE_NEXT_SYNC = 0 | Seeks to the next I-frame at the specified position. If there is no I-frame after the specified position, the seek operation may fail.<br>**Since**: 10 |
| SEEK_MODE_PREVIOUS_SYNC | Seeks to the previous I-frame at the specified position.<br>**Since**: 10 |
| SEEK_MODE_CLOSEST_SYNC | Seeks to the closest I-frame at the specified position.<br>**Since**: 10 |

### OH_ScalingMode

```c
enum OH_ScalingMode
```

**Description**

Enumerates the scaling modes. This enum is used only in surface mode.

**Since**: 10

**Deprecated**: 14

**Replaced by**: OHScalingModeV2

| Enum item | Description |
| -- | -- |
| SCALING_MODE_SCALE_TO_WINDOW = 1 | Scales the image based on the window size.<br>**Since**: 10<br>**Deprecated**: 14<br>**Replaced by**: OH_SCALING_MODE_SCALE_TO_WINDOW_V2 |
| SCALING_MODE_SCALE_CROP = 2 | Crops the image based on the window size.<br>**Since**: 10<br>**Deprecated**: 14<br>**Replaced by**: OH_SCALING_MODE_SCALE_CROP_V2 |

### OH_BitsPerSample

```c
enum OH_BitsPerSample
```

**Description**

Enumerates the number of audio bits for each coded sample.

**Since**: 10

| Enum item | Description |
| -- | -- |
| SAMPLE_U8 = 0 |  |
| SAMPLE_S16LE = 1 |  |
| SAMPLE_S24LE = 2 |  |
| SAMPLE_S32LE = 3 |  |
| SAMPLE_F32LE = 4 |  |
| SAMPLE_U8P = 5 |  |
| SAMPLE_S16P = 6 |  |
| SAMPLE_S24P = 7 |  |
| SAMPLE_S32P = 8 |  |
| SAMPLE_F32P = 9 |  |
| INVALID_WIDTH = -1 |  |

### OH_ColorPrimary

```c
enum OH_ColorPrimary
```

**Description**

Enumerates the primary colors. This enum is used for both encoding and decoding.

**Since**: 10

| Enum item | Description |
| -- | -- |
| COLOR_PRIMARY_BT709 = 1 |  |
| COLOR_PRIMARY_UNSPECIFIED = 2 |  |
| COLOR_PRIMARY_BT470_M = 4 |  |
| COLOR_PRIMARY_BT601_625 = 5 |  |
| COLOR_PRIMARY_BT601_525 = 6 |  |
| COLOR_PRIMARY_SMPTE_ST240 = 7 |  |
| COLOR_PRIMARY_GENERIC_FILM = 8 |  |
| COLOR_PRIMARY_BT2020 = 9 |  |
| COLOR_PRIMARY_SMPTE_ST428 = 10 |  |
| COLOR_PRIMARY_P3DCI = 11 |  |
| COLOR_PRIMARY_P3D65 = 12 |  |

### OH_TransferCharacteristic

```c
enum OH_TransferCharacteristic
```

**Description**

Enumerates the transfer characteristics. This enum is used for both encoding and decoding.

**Since**: 10

| Enum item | Description |
| -- | -- |
| TRANSFER_CHARACTERISTIC_BT709 = 1 |  |
| TRANSFER_CHARACTERISTIC_UNSPECIFIED = 2 |  |
| TRANSFER_CHARACTERISTIC_GAMMA_2_2 = 4 |  |
| TRANSFER_CHARACTERISTIC_GAMMA_2_8 = 5 |  |
| TRANSFER_CHARACTERISTIC_BT601 = 6 |  |
| TRANSFER_CHARACTERISTIC_SMPTE_ST240 = 7 |  |
| TRANSFER_CHARACTERISTIC_LINEAR = 8 |  |
| TRANSFER_CHARACTERISTIC_LOG = 9 |  |
| TRANSFER_CHARACTERISTIC_LOG_SQRT = 10 |  |
| TRANSFER_CHARACTERISTIC_IEC_61966_2_4 = 11 |  |
| TRANSFER_CHARACTERISTIC_BT1361 = 12 |  |
| TRANSFER_CHARACTERISTIC_IEC_61966_2_1 = 13 |  |
| TRANSFER_CHARACTERISTIC_BT2020_10BIT = 14 |  |
| TRANSFER_CHARACTERISTIC_BT2020_12BIT = 15 |  |
| TRANSFER_CHARACTERISTIC_PQ = 16 |  |
| TRANSFER_CHARACTERISTIC_SMPTE_ST428 = 17 |  |
| TRANSFER_CHARACTERISTIC_HLG = 18 |  |

### OH_MatrixCoefficient

```c
enum OH_MatrixCoefficient
```

**Description**

Enumerates the matrix coefficients. This enum is used for both encoding and decoding.

**Since**: 10

| Enum item | Description |
| -- | -- |
| MATRIX_COEFFICIENT_IDENTITY = 0 |  |
| MATRIX_COEFFICIENT_BT709 = 1 |  |
| MATRIX_COEFFICIENT_UNSPECIFIED = 2 |  |
| MATRIX_COEFFICIENT_FCC = 4 |  |
| MATRIX_COEFFICIENT_BT601_625 = 5 |  |
| MATRIX_COEFFICIENT_BT601_525 = 6 |  |
| MATRIX_COEFFICIENT_SMPTE_ST240 = 7 |  |
| MATRIX_COEFFICIENT_YCGCO = 8 |  |
| MATRIX_COEFFICIENT_BT2020_NCL = 9 |  |
| MATRIX_COEFFICIENT_BT2020_CL = 10 |  |
| MATRIX_COEFFICIENT_SMPTE_ST2085 = 11 |  |
| MATRIX_COEFFICIENT_CHROMATICITY_NCL = 12 |  |
| MATRIX_COEFFICIENT_CHROMATICITY_CL = 13 |  |
| MATRIX_COEFFICIENT_ICTCP = 14 |  |

### OH_AVCLevel

```c
enum OH_AVCLevel
```

**Description**

Enumerates the AVC levels.

**Since**: 12

| Enum item | Description |
| -- | -- |
| AVC_LEVEL_1 = 0 |  |
| AVC_LEVEL_1b = 1 |  |
| AVC_LEVEL_11 = 2 |  |
| AVC_LEVEL_12 = 3 |  |
| AVC_LEVEL_13 = 4 |  |
| AVC_LEVEL_2 = 5 |  |
| AVC_LEVEL_21 = 6 |  |
| AVC_LEVEL_22 = 7 |  |
| AVC_LEVEL_3 = 8 |  |
| AVC_LEVEL_31 = 9 |  |
| AVC_LEVEL_32 = 10 |  |
| AVC_LEVEL_4 = 11 |  |
| AVC_LEVEL_41 = 12 |  |
| AVC_LEVEL_42 = 13 |  |
| AVC_LEVEL_5 = 14 |  |
| AVC_LEVEL_51 = 15 |  |
| AVC_LEVEL_52 = 16 |  |
| AVC_LEVEL_6 = 17 |  |
| AVC_LEVEL_61 = 18 |  |
| AVC_LEVEL_62 = 19 |  |

### OH_HEVCLevel

```c
enum OH_HEVCLevel
```

**Description**

Enumerates the HEVC levels.

**Since**: 12

| Enum item | Description |
| -- | -- |
| HEVC_LEVEL_1 = 0 |  |
| HEVC_LEVEL_2 = 1 |  |
| HEVC_LEVEL_21 = 2 |  |
| HEVC_LEVEL_3 = 3 |  |
| HEVC_LEVEL_31 = 4 |  |
| HEVC_LEVEL_4 = 5 |  |
| HEVC_LEVEL_41 = 6 |  |
| HEVC_LEVEL_5 = 7 |  |
| HEVC_LEVEL_51 = 8 |  |
| HEVC_LEVEL_52 = 9 |  |
| HEVC_LEVEL_6 = 10 |  |
| HEVC_LEVEL_61 = 11 |  |
| HEVC_LEVEL_62 = 12 |  |

### OH_VVCLevel

```c
enum OH_VVCLevel
```

**Description**

Enumerates the VVC levels.

**Since**: 15

| Enum item | Description |
| -- | -- |
| VVC_LEVEL_1 = 16 |  |
| VVC_LEVEL_2 = 32 |  |
| VVC_LEVEL_21 = 35 |  |
| VVC_LEVEL_3 = 48 |  |
| VVC_LEVEL_31 = 51 |  |
| VVC_LEVEL_4 = 64 |  |
| VVC_LEVEL_41 = 67 |  |
| VVC_LEVEL_5 = 80 |  |
| VVC_LEVEL_51 = 83 |  |
| VVC_LEVEL_52 = 86 |  |
| VVC_LEVEL_6 = 96 |  |
| VVC_LEVEL_61 = 99 |  |
| VVC_LEVEL_62 = 102 |  |
| VVC_LEVEL_63 = 105 |  |
| VVC_LEVEL_155 = 255 |  |

### OH_MPEG2Level

```c
enum OH_MPEG2Level
```

**Description**

Enumerates the MPEG2 levels.

**Since**: 17

| Enum item | Description |
| -- | -- |
| MPEG2_LEVEL_LOW = 0 |  |
| MPEG2_LEVEL_MAIN = 1 |  |
| MPEG2_LEVEL_HIGH_1440 = 2 |  |
| MPEG2_LEVEL_HIGH = 3 |  |

### OH_MPEG4Level

```c
enum OH_MPEG4Level
```

**Description**

Enumerates the MPEG4 levels.

**Since**: 17

| Enum item | Description |
| -- | -- |
| MPEG4_LEVEL_0 = 0 |  |
| MPEG4_LEVEL_0B = 1 |  |
| MPEG4_LEVEL_1 = 2 |  |
| MPEG4_LEVEL_2 = 3 |  |
| MPEG4_LEVEL_3 = 4 |  |
| MPEG4_LEVEL_3B = 5 |  |
| MPEG4_LEVEL_4 = 6 |  |
| MPEG4_LEVEL_4A = 7 |  |
| MPEG4_LEVEL_5 = 8 |  |
| MPEG4_LEVEL_6 = 9 |  |

### OH_H263Level

```c
enum OH_H263Level
```

**Description**

Enumerates the H.263 levels.

**Since**: 17

| Enum item | Description |
| -- | -- |
| H263_LEVEL_10 = 0 |  |
| H263_LEVEL_20 = 1 |  |
| H263_LEVEL_30 = 2 |  |
| H263_LEVEL_40 = 3 |  |
| H263_LEVEL_45 = 4 |  |
| H263_LEVEL_50 = 5 |  |
| H263_LEVEL_60 = 6 |  |
| H263_LEVEL_70 = 7 |  |

### OH_VC1Level

```c
enum OH_VC1Level
```

**Description**

Enumerates the VC-1 levels.

**Since**: 22

| Enum item | Description |
| -- | -- |
| VC1_LEVEL_L0 = 0 |  |
| VC1_LEVEL_L1 = 1 |  |
| VC1_LEVEL_L2 = 2 |  |
| VC1_LEVEL_L3 = 3 |  |
| VC1_LEVEL_L4 = 4 |  |
| VC1_LEVEL_LOW = 5 |  |
| VC1_LEVEL_MEDIUM = 6 |  |
| VC1_LEVEL_HIGH = 7 |  |

### OH_AV1Level

```c
enum OH_AV1Level
```

**Description**

AV1 level.

**Since**: 23

| Enum item | Description |
| -- | -- |
| AV1_LEVEL_20 = 0 |  |
| AV1_LEVEL_21 = 1 |  |
| AV1_LEVEL_22 = 2 |  |
| AV1_LEVEL_23 = 3 |  |
| AV1_LEVEL_30 = 4 |  |
| AV1_LEVEL_31 = 5 |  |
| AV1_LEVEL_32 = 6 |  |
| AV1_LEVEL_33 = 7 |  |
| AV1_LEVEL_40 = 8 |  |
| AV1_LEVEL_41 = 9 |  |
| AV1_LEVEL_42 = 10 |  |
| AV1_LEVEL_43 = 11 |  |
| AV1_LEVEL_50 = 12 |  |
| AV1_LEVEL_51 = 13 |  |
| AV1_LEVEL_52 = 14 |  |
| AV1_LEVEL_53 = 15 |  |
| AV1_LEVEL_60 = 16 |  |
| AV1_LEVEL_61 = 17 |  |
| AV1_LEVEL_62 = 18 |  |
| AV1_LEVEL_63 = 19 |  |
| AV1_LEVEL_70 = 20 |  |
| AV1_LEVEL_71 = 21 |  |
| AV1_LEVEL_72 = 22 |  |
| AV1_LEVEL_73 = 23 |  |

### OH_VP9Level

```c
enum OH_VP9Level
```

**Description**

VP9 level.

**Since**: 23

| Enum item | Description |
| -- | -- |
| VP9_LEVEL_1 = 0 |  |
| VP9_LEVEL_11 = 1 |  |
| VP9_LEVEL_2 = 2 |  |
| VP9_LEVEL_21 = 3 |  |
| VP9_LEVEL_3 = 4 |  |
| VP9_LEVEL_31 = 5 |  |
| VP9_LEVEL_4 = 6 |  |
| VP9_LEVEL_41 = 7 |  |
| VP9_LEVEL_5 = 8 |  |
| VP9_LEVEL_51 = 9 |  |
| VP9_LEVEL_52 = 10 |  |
| VP9_LEVEL_6 = 11 |  |
| VP9_LEVEL_61 = 12 |  |
| VP9_LEVEL_62 = 13 |  |

### OH_WVC1Level

```c
enum OH_WVC1Level
```

**Description**

WVC1 level.

**Since**: 23

| Enum item | Description |
| -- | -- |
| WVC1_LEVEL_L0 = 0 |  |
| WVC1_LEVEL_L1 = 1 |  |
| WVC1_LEVEL_L2 = 2 |  |
| WVC1_LEVEL_L3 = 3 |  |
| WVC1_LEVEL_L4 = 4 |  |

### OH_WMV3Level

```c
enum OH_WMV3Level
```

**Description**

Enumerates the WMV3 levels.

**Since**: 22

| Enum item | Description |
| -- | -- |
| WMV3_LEVEL_LOW = 0 |  |
| WMV3_LEVEL_MEDIUM = 1 |  |
| WMV3_LEVEL_HIGH = 2 |  |

### OH_TemporalGopReferenceMode

```c
enum OH_TemporalGopReferenceMode
```

**Description**

Enumerates the reference modes of temporal image groups.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ADJACENT_REFERENCE = 0 |  |
| JUMP_REFERENCE = 1 |  |
| UNIFORMLY_SCALED_REFERENCE = 2 |  |

### OH_BitrateMode

```c
enum OH_BitrateMode
```

**Description**

Enumerates the bit rate modes of an encoder.

**Since**: 10

| Enum item | Description |
| -- | -- |
| BITRATE_MODE_CBR = 0 |  |
| BITRATE_MODE_VBR = 1 |  |
| BITRATE_MODE_CQ = 2 |  |
| BITRATE_MODE_SQR = 3 |  |
| BITRATE_MODE_CBR_HIGH_QUALITY = 4 | CBR for High Quality.<br>**Since**: 26.0.0 |

### OH_FrameRetentionMode

```c
enum OH_FrameRetentionMode
```

**Description**

The video decoding frame retention mode.

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_FRAME_RETENTION_MODE_FULL = 0 | Full frame retention mode. The decoder operates in a transparent passthrough state, retaining 100% of the input frames and effectively disabling the frame dropping feature. All underlying visual perception algorithms are completely bypassed, resulting in zero algorithmic overhead.<br>**Since**: 26.0.0 |
| OH_FRAME_RETENTION_MODE_ADAPTIVE = 1 | Adaptive frame retention mode. The decoder dynamically analyzes video characteristics to drop frames with the least perceptual impact, preserving visual smoothness with minimal degradation to the playback experience. For optimal algorithmic accuracy, it is highly recommended to explicitly configure the current playback speed via {@link OH_MD_KEY_VIDEO_DECODER_SPEED}.<br>**Since**: 26.0.0 |
| OH_FRAME_RETENTION_MODE_UNIFORM = 2 | Uniform frame retention mode. Retains frames evenly according to a user-configured retention ratio (configured via {@link OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_RATIO}). If the retention ratio is not explicitly configured, the decoder limits the output to a maximum of 30 fps.<br>**Since**: 26.0.0 |

### OH_AudioEncoderPTSMode

```c
enum OH_AudioEncoderPTSMode
```

**Description**

The PTS mode of audio encoder.

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_AUDIO_ENCODER_PTS_MODE_DEFAULT = 0 | Default PTS mode of audio encoder. Different encoders may perform differently.<br>**Since**: 26.0.0 |
| OH_AUDIO_ENCODER_PTS_MODE_ZERO_START = 1 | PTS starts from zero.<br>**Since**: 26.0.0 |
| OH_AUDIO_ENCODER_PTS_MODE_FIRST_INPUT_START = 2 | PTS starts from the first input PTS.<br>**Since**: 26.0.0 |


## Function description

### OH_AVCodecOnError()

```c
typedef void (*OH_AVCodecOnError)(OH_AVCodec *codec, int32_t errorCode, void *userData)
```

**Description**

Defines the pointer to the function that is called to report error information when an error occurs during the running of an OH_AVCodec instance. 
\| Use Case\| Error Code\|
\| -------- \| -------- \|
\| Audio encoding/decoding\| **AV_ERR_DRM_DECRYPT_FAILED**: DRM decryption failed. \|
\| Video encoding/decoding\| **AV_ERROR_NO_MEMORY**: System resources are insufficient.<br>**AV_ERROR_UNKNOWN**: An unknown error occurs. Analyze the error based on specific logs.<br>**AV_ERR_SERVICE_DIED**: The service is dead. \|
\| Video decoding\| **AV_ERR_VIDEO_UNSUPPORTED_COLOR_SPACE_CONVERSION**: The current input does not support CSC. \| <!--RP1--><!--RP1End-->

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) \*codec | Pointer to an OH_AVCodec instance. |
| int32_t errorCode | Error code. |
| void \*userData | Pointer to the data on which the caller depends when executing the callback. |

### OH_AVCodecOnStreamChanged()

```c
typedef void (*OH_AVCodecOnStreamChanged)(OH_AVCodec *codec, OH_AVFormat *format, void *userData)
```

**Description**

Defines the pointer to the function that is called to report the new stream description when the resolution of the input video stream being decoded or the output video stream that has been encoded changes.<br> Starting from API version 15, this function pointer is called to report the new stream description when the stream sampling rate, number of audio channels, or audio sampling format changes during audio decoding. The decoding formats that can detect these changes include <!--RP3--><!--RP3End-->AAC, FLAC, MP3, and VORBIS.<br> Note that the lifecycle of the pointer to the OH_AVFormat instance is valid only when the function pointer is being called. Do not access the pointer to the instance after the function pointer is called.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) \*codec | Pointer to an OH_AVCodec instance. |
| OH_AVFormat \*format | Pointer to the description information about the new output stream. |
| void \*userData | Pointer to the data on which the caller depends when executing the callback. |

### OH_AVCodecOnNeedInputData()

```c
typedef void (*OH_AVCodecOnNeedInputData)(OH_AVCodec *codec, uint32_t index, OH_AVMemory *data, void *userData)
```

**Description**

Defines the pointer to the function that is called when new input data is required during the running of an OH_AVCodec instance. The function carries a buffer to fill in new input data.

**Since**: 9

**Deprecated**: 11

**Replaced by**: OH_AVCodecOnNeedInputBuffer

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) \*codec | Pointer to an OH_AVCodec instance. |
| uint32_t index | Index of the new input buffer. |
| OH_AVMemory \*data | Pointer to the data to fill in the new input buffer. |
| void \*userData | Pointer to the data on which the caller depends when executing the callback. |

### OH_AVCodecOnNewOutputData()

```c
typedef void (*OH_AVCodecOnNewOutputData)(OH_AVCodec *codec, uint32_t index, OH_AVMemory *data, OH_AVCodecBufferAttr *attr, void *userData)
```

**Description**

Defines the pointer to the function that is called when new output data is generated during the running of an OH_AVCodec instance. The function carries a buffer filled with new output data. Note that the lifecycle of the pointer to the OH_AVCodecBufferAttr instance is valid only when the function pointer is being called. Do not access the pointer to the instance after the function pointer is called.

**Since**: 9

**Deprecated**: 11

**Replaced by**: OH_AVCodecOnNewOutputBuffer

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) \*codec | Pointer to an OH_AVCodec instance. |
| uint32_t index | Index of the new output buffer. |
| OH_AVMemory \*data | Pointer to the data filled in the new output buffer. |
| OH_AVCodecBufferAttr \*attr | Pointer to the description information about the new output buffer. |
| void \*userData | Pointer to the data on which the caller depends when executing the callback. |

### OH_AVCodecOnNeedInputBuffer()

```c
typedef void (*OH_AVCodecOnNeedInputBuffer)(OH_AVCodec *codec, uint32_t index, OH_AVBuffer *buffer, void *userData)
```

**Description**

Defines the pointer to the function that is called when new input data is required during the running of an OH_AVCodec instance. The function carries a buffer to fill in new input data.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) \*codec | Pointer to an OH_AVCodec instance. |
| uint32_t index | Index of the new input buffer. |
| OH_AVBuffer \*buffer | Pointer to the data to fill in the new input buffer. |
| void \*userData | Pointer to the data on which the caller depends when executing the callback. |

### OH_AVCodecOnNewOutputBuffer()

```c
typedef void (*OH_AVCodecOnNewOutputBuffer)(OH_AVCodec *codec, uint32_t index, OH_AVBuffer *buffer, void *userData)
```

**Description**

Defines the pointer to the function that is called when new output data is generated during the running of an OH_AVCodec instance. The function carries a buffer filled with new output data.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) \*codec | Pointer to an OH_AVCodec instance. |
| uint32_t index | Index of the new output buffer. |
| OH_AVBuffer \*buffer | Pointer to the data filled in the new output buffer. |
| void \*userData | Pointer to the data on which the caller depends when executing the callback. |

### OH_AVDataSourceReadAt()

```c
typedef int32_t (*OH_AVDataSourceReadAt)(OH_AVBuffer *data, int32_t length, int64_t pos)
```

**Description**

Defines a function pointer used to provide the capability of obtaining user-defined media data.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVBuffer \*data | Pointer to the buffer to be filled in. |
| int32_t length | Length of the data to read. |
| int64_t pos | Offset from which the data is read. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Actual length of the data read to the buffer. |

### OH_AVDataSourceReadAtExt()

```c
typedef int32_t (*OH_AVDataSourceReadAtExt)(OH_AVBuffer *data, int32_t length, int64_t pos, void *userData)
```

**Description**

Defines a function pointer used to provide the capability of obtaining user-defined media data.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVBuffer \*data | Pointer to the buffer to be filled in. |
| int32_t length | Length of the data to read. |
| int64_t pos | Offset from which the data is read. |
| void \*userData | Pointer to user-defined data. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Actual length of the data read to the buffer. |


