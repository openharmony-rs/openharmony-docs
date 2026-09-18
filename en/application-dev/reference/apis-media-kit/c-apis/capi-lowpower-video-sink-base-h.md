# lowpower_video_sink_base.h

## Overview

The file declares the structs and enums of the LowPowerVideoSink.

**Library**: liblowpower_avsink.so

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Related module**: [LowPowerVideoSink](capi-lowpowervideosink.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_LowPowerVideoSink](capi-lowpowervideosink-oh-lowpowervideosink.md) | OH_LowPowerVideoSink | The struct describes the declaration for the LowPowerVideoSink. |
| [OH_LowPowerVideoSinkCallback](capi-lowpowervideosink-oh-lowpowervideosinkcallback.md) | OH_LowPowerVideoSinkCallback | The struct contains a set of callback function pointers for the LowPowerVideoSink. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_LowPowerVideoSink_OnDataNeeded)(OH_LowPowerVideoSink* sink, OH_AVSamplesBuffer* buffer, void *userData)](#oh_lowpowervideosink_ondataneeded) | OH_LowPowerVideoSink_OnDataNeeded | Called when the LowPowerVideoSink needs more data. This callback is included in [OH_LowPowerVideoSinkCallback](capi-lowpowervideosink-oh-lowpowervideosinkcallback.md). |
| [typedef void (\*OH_LowPowerVideoSink_OnError)(OH_LowPowerVideoSink* sink, OH_AVErrCode errCode, const char* errMsg, void* userData)](#oh_lowpowervideosink_onerror) | OH_LowPowerVideoSink_OnError | Called when an error occurs in the LowPowerVideoSink. |
| [typedef void (\*OH_LowPowerVideoSink_OnTargetArrived)(OH_LowPowerVideoSink* sink, const int64_t targetPts, const bool isTimeout, void* userData)](#oh_lowpowervideosink_ontargetarrived) | OH_LowPowerVideoSink_OnTargetArrived | Called when the LowPowerVideoSink reaches the target point. This callback is included in [OH_LowPowerVideoSinkCallback](capi-lowpowervideosink-oh-lowpowervideosinkcallback.md). |
| [typedef void (\*OH_LowPowerVideoSink_OnRenderStarted)(OH_LowPowerVideoSink* sink, void* userData)](#oh_lowpowervideosink_onrenderstarted) | OH_LowPowerVideoSink_OnRenderStarted | Called when the LowPowerVideoSink starts rendering. This callback is included in [OH_LowPowerVideoSinkCallback](capi-lowpowervideosink-oh-lowpowervideosinkcallback.md). |
| [typedef void (\*OH_LowPowerVideoSink_OnStreamChanged)(OH_LowPowerVideoSink* sink, OH_AVFormat* format, void* userData)](#oh_lowpowervideosink_onstreamchanged) | OH_LowPowerVideoSink_OnStreamChanged | Called when the stream changes in the LowPowerVideoSink. This callback is included in [OH_LowPowerVideoSinkCallback](capi-lowpowervideosink-oh-lowpowervideosinkcallback.md). |
| [typedef void (\*OH_LowPowerVideoSink_OnFirstFrameDecoded)(OH_LowPowerVideoSink* sink, void* userData)](#oh_lowpowervideosink_onfirstframedecoded) | OH_LowPowerVideoSink_OnFirstFrameDecoded | Called when the first frame is successfully decoded in the LowPowerVideoSink. This callback is included in [OH_LowPowerVideoSinkCallback](capi-lowpowervideosink-oh-lowpowervideosinkcallback.md). |
| [typedef void (\*OH_LowPowerVideoSink_OnEos)(OH_LowPowerVideoSink* sink, void* userData)](#oh_lowpowervideosink_oneos) | OH_LowPowerVideoSink_OnEos | Called when the playback is completed in the LowPowerVideoSink. This callback is included in [OH_LowPowerVideoSinkCallback](capi-lowpowervideosink-oh-lowpowervideosinkcallback.md). |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_LowPowerVideoSink_OnDataNeeded)( OH_LowPowerVideoSink* sink, OH_AVSamplesBuffer* buffer, void *userData) | Called when the LowPowerVideoSink needs more data. This callback is included in [OH_LowPowerVideoSinkCallback](capi-lowpowervideosink-oh-lowpowervideosinkcallback.md).<br>**Since**: 20 |
| void (*OH_LowPowerVideoSink_OnError)( OH_LowPowerVideoSink* sink, OH_AVErrCode errCode, const char* errMsg, void* userData) | Called when an error occurs in the LowPowerVideoSink.<br>**Since**: 20 |
| void (*OH_LowPowerVideoSink_OnTargetArrived)( OH_LowPowerVideoSink* sink, const int64_t targetPts, const bool isTimeout, void* userData) | Called when the LowPowerVideoSink reaches the target point. This callback is included in [OH_LowPowerVideoSinkCallback](capi-lowpowervideosink-oh-lowpowervideosinkcallback.md).<br>**Since**: 20 |
| void (*OH_LowPowerVideoSink_OnRenderStarted)(OH_LowPowerVideoSink* sink, void* userData) | Called when the LowPowerVideoSink starts rendering. This callback is included in [OH_LowPowerVideoSinkCallback](capi-lowpowervideosink-oh-lowpowervideosinkcallback.md).<br>**Since**: 20 |
| void (*OH_LowPowerVideoSink_OnStreamChanged)(OH_LowPowerVideoSink* sink, OH_AVFormat* format, void* userData) | Called when the stream changes in the LowPowerVideoSink. This callback is included in [OH_LowPowerVideoSinkCallback](capi-lowpowervideosink-oh-lowpowervideosinkcallback.md).<br>**Since**: 20 |
| void (*OH_LowPowerVideoSink_OnFirstFrameDecoded)(OH_LowPowerVideoSink* sink, void* userData) | Called when the first frame is successfully decoded in the LowPowerVideoSink. This callback is included in [OH_LowPowerVideoSinkCallback](capi-lowpowervideosink-oh-lowpowervideosinkcallback.md).<br>**Since**: 20 |
| void (*OH_LowPowerVideoSink_OnEos)(OH_LowPowerVideoSink* sink, void* userData) | Called when the playback is completed in the LowPowerVideoSink. This callback is included in [OH_LowPowerVideoSinkCallback](capi-lowpowervideosink-oh-lowpowervideosinkcallback.md).<br>**Since**: 20 |

## Function description

### OH_LowPowerVideoSink_OnDataNeeded()

```c
typedef void (*OH_LowPowerVideoSink_OnDataNeeded)(OH_LowPowerVideoSink* sink, OH_AVSamplesBuffer* buffer, void *userData)
```

**Description**

Called when the LowPowerVideoSink needs more data. This callback is included in [OH_LowPowerVideoSinkCallback](capi-lowpowervideosink-oh-lowpowervideosinkcallback.md).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_LowPowerVideoSink](capi-lowpowervideosink-oh-lowpowervideosink.md)\* sink | OH_LowPowerVideoSink instance |
| OH_AVSamplesBuffer\* buffer | OH_AVSamplesBuffer instance that will be written in |
| void \*userData | User specific data |

### OH_LowPowerVideoSink_OnError()

```c
typedef void (*OH_LowPowerVideoSink_OnError)(OH_LowPowerVideoSink* sink, OH_AVErrCode errCode, const char* errMsg, void* userData)
```

**Description**

Called when an error occurs in the LowPowerVideoSink.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_LowPowerVideoSink](capi-lowpowervideosink-oh-lowpowervideosink.md)\* sink | OH_LowPowerVideoSink instance |
| errorCode | The error code returned when an error occurs during service operation. See the definition of {@OH_AVErrCode} |
| errorMsg | string of Error description information returned when an error occurs during service operation |
| void\* userData | User specific data |

### OH_LowPowerVideoSink_OnTargetArrived()

```c
typedef void (*OH_LowPowerVideoSink_OnTargetArrived)(OH_LowPowerVideoSink* sink, const int64_t targetPts, const bool isTimeout, void* userData)
```

**Description**

Called when the LowPowerVideoSink reaches the target point. This callback is included in [OH_LowPowerVideoSinkCallback](capi-lowpowervideosink-oh-lowpowervideosinkcallback.md).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_LowPowerVideoSink](capi-lowpowervideosink-oh-lowpowervideosink.md)\* sink | OH_LowPowerVideoSink instance |
| const int64_t targetPts | Target pts of renderred frame, in microseconds |
| const bool isTimeout | If wait target pts timeout, it is false |
| void\* userData | User specific data |

### OH_LowPowerVideoSink_OnRenderStarted()

```c
typedef void (*OH_LowPowerVideoSink_OnRenderStarted)(OH_LowPowerVideoSink* sink, void* userData)
```

**Description**

Called when the LowPowerVideoSink starts rendering. This callback is included in [OH_LowPowerVideoSinkCallback](capi-lowpowervideosink-oh-lowpowervideosinkcallback.md).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_LowPowerVideoSink](capi-lowpowervideosink-oh-lowpowervideosink.md)\* sink | OH_LowPowerVideoSink instance |
| void\* userData | User specific data |

### OH_LowPowerVideoSink_OnStreamChanged()

```c
typedef void (*OH_LowPowerVideoSink_OnStreamChanged)(OH_LowPowerVideoSink* sink, OH_AVFormat* format, void* userData)
```

**Description**

Called when the stream changes in the LowPowerVideoSink. This callback is included in [OH_LowPowerVideoSinkCallback](capi-lowpowervideosink-oh-lowpowervideosinkcallback.md).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_LowPowerVideoSink](capi-lowpowervideosink-oh-lowpowervideosink.md)\* sink | OH_LowPowerVideoSink instance |
| OH_AVFormat\* format | Carrying changing parameters and corresponding values |
| void\* userData | User specific data |

### OH_LowPowerVideoSink_OnFirstFrameDecoded()

```c
typedef void (*OH_LowPowerVideoSink_OnFirstFrameDecoded)(OH_LowPowerVideoSink* sink, void* userData)
```

**Description**

Called when the first frame is successfully decoded in the LowPowerVideoSink. This callback is included in [OH_LowPowerVideoSinkCallback](capi-lowpowervideosink-oh-lowpowervideosinkcallback.md).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_LowPowerVideoSink](capi-lowpowervideosink-oh-lowpowervideosink.md)\* sink | OH_LowPowerVideoSink instance |
| void\* userData | User specific data |

### OH_LowPowerVideoSink_OnEos()

```c
typedef void (*OH_LowPowerVideoSink_OnEos)(OH_LowPowerVideoSink* sink, void* userData)
```

**Description**

Called when the playback is completed in the LowPowerVideoSink. This callback is included in [OH_LowPowerVideoSinkCallback](capi-lowpowervideosink-oh-lowpowervideosinkcallback.md).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_LowPowerVideoSink](capi-lowpowervideosink-oh-lowpowervideosink.md)\* sink | OH_LowPowerVideoSink instance |
| void\* userData | User specific data |


