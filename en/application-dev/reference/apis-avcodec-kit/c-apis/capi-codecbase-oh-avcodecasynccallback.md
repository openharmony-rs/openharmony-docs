# OH_AVCodecAsyncCallback

```c
typedef struct OH_AVCodecAsyncCallback {...} OH_AVCodecAsyncCallback
```

## Overview

The struct defines all the asynchronous callback function pointers of an OH_AVCodec instance. To ensure the normal running of OH_AVCodec, you must register the instance of this struct with the OH_AVCodec instance and process the information reported by the callback function.

<!--Device-struct OH_AVCodecAsyncCallback {...}--><!--Device-struct OH_AVCodecAsyncCallback {...}-End-->

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 9

**Deprecated**: 11

**Replaced by**: OH_AVCodecCallback

**Related module**: [CodecBase](capi-avcodec-kit-codecbase.md)

**Header file**: [native_avcodec_base.h](capi-native-avcodec-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_AVCodecOnError](capi-native-avcodec-base-h.md#oh_avcodeconerror) onError | <!--Device-OH_AVCodecOnError onError--><!--Device-OH_AVCodecOnError onError-End--> |
| [OH_AVCodecOnStreamChanged](capi-native-avcodec-base-h.md#oh_avcodeconstreamchanged) onStreamChanged | <!--Device-OH_AVCodecOnStreamChanged onStreamChanged--><!--Device-OH_AVCodecOnStreamChanged onStreamChanged-End--> |
| [OH_AVCodecOnNeedInputData](capi-native-avcodec-base-h.md#oh_avcodeconneedinputdata) onNeedInputData | <!--Device-OH_AVCodecOnNeedInputData onNeedInputData--><!--Device-OH_AVCodecOnNeedInputData onNeedInputData-End--> |
| [OH_AVCodecOnNewOutputData](capi-native-avcodec-base-h.md#oh_avcodeconnewoutputdata) onNeedOutputData | <!--Device-OH_AVCodecOnNewOutputData onNeedOutputData--><!--Device-OH_AVCodecOnNewOutputData onNeedOutputData-End--> |


