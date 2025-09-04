# OH_AVCodecCallback


## Overview

The struct defines all the asynchronous callback function pointers of an OH_AVCodec instance. To ensure the normal running of OH_AVCodec, you must register the instance of this struct with the OH_AVCodec instance and process the information reported by the callback function.

For details about the development guide, see step 4 in surface mode or step 3 in buffer mode in [Video Encoding](../../media/avcodec/video-encoding.md).

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 11

**Related module**: [CodecBase](_codec_base.md)

**Header file**: [native_avcodec_base.h](native__avcodec__base_8h.md)


## Summary


### Member Variables

| Name| Description| 
| -------- | -------- |
| [OH_AVCodecOnError](_codec_base.md#oh_avcodeconerror) [onError](#onerror) | Defines the callback used to report a codec operation error.| 
| [OH_AVCodecOnStreamChanged](_codec_base.md#oh_avcodeconstreamchanged) [onStreamChanged](#onstreamchanged) | Defines the callback used to report a codec stream change.| 
| [OH_AVCodecOnNeedInputBuffer](_codec_base.md#oh_avcodeconneedinputbuffer) [onNeedInputBuffer](#onneedinputbuffer) | Defines the callback used to report input data required.| 
| [OH_AVCodecOnNewOutputBuffer](_codec_base.md#oh_avcodeconnewoutputbuffer) [onNewOutputBuffer](#onnewoutputbuffer) | Defines the callback used to report output data generated.| 


## Member Variable Description


### onError

**Description**

Defines the callback used to report a codec operation error.

**Since**: 11


### onNeedInputBuffer

**Description**

Defines the callback used to report input data required.

**Since**: 11


### onNewOutputBuffer

**Description**

Defines the callback used to report output data generated.

**Since**: 11


### onStreamChanged

**Description**

Defines the callback used to report a codec stream change.

**Since**: 11
