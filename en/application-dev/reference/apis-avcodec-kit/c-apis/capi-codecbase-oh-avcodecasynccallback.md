# OH_AVCodecAsyncCallback

```c
struct OH_AVCodecAsyncCallback {...}
```

## Overview

The struct defines all the asynchronous callback function pointers of an OH_AVCodec instance. To ensure the normal running of OH_AVCodec, you must register the instance of this struct with the OH_AVCodec instance and process the information reported by the callback function.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 9

**Deprecated**: 11

**Replaced by**: OH_AVCodecCallback

**Related module**: [CodecBase](capi-others-codecbase.md)

**Header file**: [native_avcodec_base.h](capi-native-avcodec-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_AVCodecOnError](capi-native-avcodec-base-h.md#oh_avcodeconerror) onError |  |
| [OH_AVCodecOnStreamChanged](capi-native-avcodec-base-h.md#oh_avcodeconstreamchanged) onStreamChanged |  |
| [OH_AVCodecOnNeedInputData](capi-native-avcodec-base-h.md#oh_avcodeconneedinputdata) onNeedInputData |  |
| [OH_AVCodecOnNewOutputData](capi-native-avcodec-base-h.md#oh_avcodeconnewoutputdata) onNeedOutputData |  |


