# OH_AVRecorder_EncoderInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_dyOv3Sds-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->

```c
typedef struct OH_AVRecorder_EncoderInfo {...} OH_AVRecorder_EncoderInfo
```

## Overview

Provides AVRecorder encoder capability information, including the MIME type, bit rate range, and frame rate range of the encoder. This struct is applicable to scenarios where you need to query and select a proper audio or video encoder configuration before recording, helping you select the optimal encoding configuration based on the encoder capability parameters. You can obtain this struct object by calling [OH_AVRecorder_GetAvailableEncoder](capi-avrecorder-h.md#oh_avrecorder_getavailableencoder).

**Since**: 18

**Related module**: [AVRecorder](capi-avrecorder.md)

**Header file**: [avrecorder_base.h](capi-avrecorder-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_AVRecorder_CodecMimeType](capi-avrecorder-base-h.md#oh_avrecorder_codecmimetype) mimeType | MIME type of the encoder. The value corresponds to **type**. If **type** is **audio**, the value is the audio MIME type. If **type** is **video**, the value is the video MIME type.|
| char *type | Encoder type. The value **audio** means an audio encoder, and **video** means a video encoder.|
| [OH_AVRecorder_Range](capi-avrecorder-oh-avrecorder-range.md) bitRate | Bit rates supported by the encoder, in bit/s. This parameter is applicable to both audio and video encoders.|
| [OH_AVRecorder_Range](capi-avrecorder-oh-avrecorder-range.md) frameRate | Video frame rates supported by the encoder, in FPS. This parameter is applicable only to video encoders.|
| [OH_AVRecorder_Range](capi-avrecorder-oh-avrecorder-range.md) width | Video frame widths supported by the encoder, in pixels. This parameter is applicable only to video encoders.|
| [OH_AVRecorder_Range](capi-avrecorder-oh-avrecorder-range.md) height | Video frame heights supported by the encoder, in pixels. This parameter is applicable only to video encoders.|
| [OH_AVRecorder_Range](capi-avrecorder-oh-avrecorder-range.md) channels | Number of audio channels supported by the encoder. The value is determined by the encoder capability of the device. The common values are **1** (mono) or **2** (stereo). This parameter is applicable only to audio encoders.|
| int32_t *sampleRate | List of audio sampling rates supported by the encoder. The value is determined by the encoder capability of the device. Common values include **8000**, **16000**, **44100**, and **48000**, in Hz. This parameter is used together with the **sampleRateLen** field, which indicates the length of the list. This parameter is applicable only to audio encoders.|
| int32_t sampleRateLen | Length of the audio sampling rate list. The value is an integer greater than 0. This parameter is used together with the **sampleRate** field to indicate the number of elements in the **sampleRate** array. This parameter is applicable only to audio encoders.|
