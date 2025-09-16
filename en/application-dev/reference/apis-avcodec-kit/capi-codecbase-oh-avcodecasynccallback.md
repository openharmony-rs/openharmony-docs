# OH_AVCodecAsyncCallback

## Overview

The struct defines all the asynchronous callback function pointers of an OH_AVCodec instance. To ensure the normal running of OH_AVCodec, you must register the instance of this struct with the OH_AVCodec instance and process the information reported by the callback function.

**Since**: 9

**Deprecated from**: 11

**Substitute**: [OH_AVCodecCallback](capi-codecbase-oh-avcodeccallback.md)

**Related module**: [CodecBase](capi-codecbase.md)

**Header file**: [native_avcodec_base.h](capi-native-avcodec-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_AVCodecOnError](capi-native-avcodec-base-h.md#oh_avcodeconerror) onError | Callback used to report a codec operation error.|
| [OH_AVCodecOnStreamChanged](capi-native-avcodec-base-h.md#oh_avcodeconstreamchanged) onStreamChanged | Callback used to report a codec stream change.|
| [OH_AVCodecOnNeedInputData](capi-native-avcodec-base-h.md#oh_avcodeconneedinputdata) onNeedInputData | Callback used to report input data required.|
| [OH_AVCodecOnNewOutputData](capi-native-avcodec-base-h.md#oh_avcodeconnewoutputdata) onNewOutputData | Callback used to report output data generated.|
